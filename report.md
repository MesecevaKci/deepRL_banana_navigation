# Report 

The Banana navigation problem is solved using the deep Q-learning technique, an extension of the Q-learning.
I will first briefly describe the theroretical background of the solution, then I will summarise the details of the algorithm used to solve the problem and end up with suggesting how to extend the project. 

## Algorithm Background

### Q-learning

The goal of Q-learning is to learn a policy based on which a reinforcement agent will choose which action to take under what circumstances. For any finite Markov decision process, Q-learning finds a policy that is optimal in a way that it maximizes the expected value of the total reward over any and all successive steps, starting from the current state. 

Q-learning uses a table to store the maximum expected future rewards for each action-state pair. At each step t, the agent observes the current state S(t) of the environment and, using the π policy, selects and executes the action a(t). By executing the action, the agent obtains the reward R(t+1) and the new state S(t+1). At this point, the agent is able to calculate Q(S(t), a(t)), updating the estimate. Over time, based on the agent's experience, this Q-table becomes a reference table for the agent to select the best action based on the Q-value.


### Epsilon-policy
The environment's dynamic is initially unknown to the agent. In order to maximize the return, the agent must learn about the environment through interactions. At every time step, when the agent selects an action, this decision is based on its past experience with the environment. 

In early episodes, the agent's knowledge is quite limited and in order to discover the optimal policy it has to explore all possibile state-action pairs. However, the agent should always act somewhat greedily, towards its goal of maximizing return as quickly as possible. 

The need to balance these two competing requirements in known as the Exploration versus Exploitation problem. One potential solution to this problem is implemented by using epsilonϵ-greedy policies and evolving epsilon over time.

More precisely, the agent starts by exploring i.e. choosing a random action with some probability epsilon. Simultaneously, the agent continues to exploit its knowledge of the environment by choosing actions based on the policy with probability (1-epsilon). At the beginning, the value of epsilon is large and as the time goes on, the value of epsilon decays. In this way the agent gains more experience over time by increasingly rellying on the exploitation. The usual practice is to start with epsilon = 1 corresponding to 100% random actions and slowly decrease it to a small value such as 5% or less of random actions. 


### Deep Q-learning

The Deep Q-Learning (DQN) algorithm represents the optimal action-value function as a neural network instead of a table. It turns out that reinforcement learning is very unstable when neural networks are used to represent the action values. These instabilities are fixed by using two key features:
    Experience Replay and Fixed Q-Targets, described below.
 

As the agent interacts with the environment, the experiences are added to a reply buffer, but the sequence of experience tuples can be highly correlated. This correlation can be broken by sampling a small batch of tuples from the replay buffer. This is  known as experience replay. Moreover, by using the experience replay one can learn more from individual tuples multiple times.

   
Another potential problem with deep Q-learning is if the Q-network’s parameters are getting updated after each move, instabilities can arise. The problem is that the actual rewards may be sparse (there is a significant positive reward only when the game is won or a significant penalty upon losing) and the algorithm can start behaving erratically if updated after every step. To make training more stable, one can use two netoworks: a target network, whose predicted Q-values are used to backpropagate through and train the main Q-network. The parameters of the target network are not trained, but are periodically synchronized with the Q-network’s parameters. 


### Enhancements 

Since the DQN algorithm first came out several enhancements have been proposed. 
They include:
- Double DQN: 
The basic DQN has a tendency to overestimate values for Q, which may be harmful to training performance and sometimes can lead to suboptimal policies. Double Q-Learning has been shown to work well in practice to help with this. The idea of double DQN is very simple: when selecting the best action to take in the next state one should use the main trained network, but values corresponding to this action should come from the target network. 

- Prioritized Experience Replay:
The basic idea behind the Prioritized experienced replay is not all transitions are equally important and the more important transitions should be sampled with higher probability. In this way the agent will learn more efficiently. 

- Dueling DQN:
The Dueling DQN is based on a network that separately computes the advantage and value functions, combining them into a single Q-function only at the final layer. In this way, one can assess the value of each state without needing to learn the effect of each action.



### This work

To solve the task I have run experiements with two different networks: 
- (Basic) DQN algorithm 
- Double DQN algorithm.


Neural Network: 
The used network architecture consists of three fully connected layers with 64, 64, and 4 nodes (arch1) and 128, 128, and 4 nodes (arch2) using relu activation.


Epsilon-policy: 
Epsilon-decay was the other hyperparameter that was modifed in order to improve learning. Two values of epsilon-decay were tried: 0.995 (pars1) and 0.99 (pars2).

In all models the rest of the (hyper)parameters were the same:

    Agent Parameters

     BUFFER_SIZE = 100,000  # replay buffer size
     BATCH_SIZE = 64        # minibatch size
     GAMMA = 0.99           # discount factor
     TAU = 0.001            # for soft update of target parameters
     LR = 0.0005            # learning rate 
     UPDATE_EVERY = 4       # how often to update the network   


    Fixed Training Parameters

     Number of training episodes: 2000 or when average score reached
     Maximum number of timesteps per episode: 1000
     Starting value of epsilon, for epsilon-greedy action selection: 1.0
     End value of epsilon: 0.01
        

### Results

In the table below is the number of iterations-100 needed to reach the average score of 13 with different algorithms and parameters (not all possible combinations were tried): 

| Algorithm | Number of iterations-100 |
| --- | --- | 
| DQN+pars1_arch1 | 427 |
| DQN+pars2_arch1 | 296 |
| DQN+pars2_arch2 | 330 |
| DoubleDQN+pars1+arch1 | 378 |
| DoubleDQN+pars2+arch1 | 308 |
| DoubleDQN+pars2+arch2 | 369 |
 

The best performing learning algorithm, i.e. the algorithm in which the average score of 13 from the last 100 episodes was reached is basic DQN with the 64 nodes in the hidden layers and epsilon-decay=0.99.


### Future improvements

- As discussed above, there are multiple improvements to the DQN proposed. In this project only the basic DQN and doubleDQN were tested, leaving the space for implenting the Prioritized Replay Experience or Dueling DQN in the future. 

- Moreover, in this work a tuning only a few parameters was tested. In the future one should carru out a more systematic exploration of the various hyperparameters.

### References

1. This report is mainly based on the learning material of the [Udacity Deep Reinforcement Learning Nanodegree Program](https://eu.udacity.com/course/deep-reinforcement-learning-nanodegree--nd893) and references therein.
2. https://en.wikipedia.org/wiki/Reinforcement_learning
3. Maxim Lapan: Deep Reinforcement Learning Hands-On, Packt Publishing, Release Date: June 2018, 
ISBN: 9781788834247
4. Rajalingappaa Shanmugamani, Yang Wenzhuo, Sean Saito:vPython Reinforcement Learning Projects, Packt Publishing, Release Date: September 2018, ISBN: 9781788991612
5. https://pytorch.org/tutorials/intermediate/reinforcement_q_learning.html
