The solution to this problem is obtained by using the deep Q learning, extension of the Q-learning.

Algorithm

Q-learning

The goal of Q-learning is to learn a policy telling an agent what action to take under what circumstances. For any finite Markov decision process (FMDP), Q-learning finds a policy that is optimal in the sense that it maximizes the expected value of the total reward over any and all successive steps, starting from the current state. Q-learing is a model-free reinforcement learning algorithm, meaning that it can be used to solve problems with stochastic transitions and rewards not requiring adaptations (Wikipedia).

Q-learning uses a table to store each state-action pair and the exoected reward (i.e. Q-value). At each step, the agent observes the current state of the environment and, using the π policy, selects and executes the action. By executing the action, the agent obtains the reward Rt+1 and the new state St+1. At this point, the agent is able to calculate Q(St, at), updating the estimate. Over time, based on the agent's experience, this Q-table becomes a reference table for our agent to select the best action based on the Q-value.


Epsilon-policy
The environment's dynamics are initially unknown to the agent. Towards maximizing return, the agent must learn about the environment through interaction. At every time step, when the agent selects an action, it bases its decision on past experience with the environment. In early episodes, the agent's knowledge is quite limited and it is highly likely that actions estimated to be non-greedy by the agent are in fact better than the estimated greedy action.

In order to discover the optimal policy, it has to continue to refine the estimated return for all state-action pairs (in other words, it has to continue to explore the range of possibilities by visiting every state-action pair). That said, the agent should always act somewhat greedily, towards its goal of maximizing return as quickly as possible. This motivated the idea of an ϵ\epsilonϵ-greedy policy.

The need to balance these two competing requirements in known as the Exploration-Exploitation Dilemma. One potential solution to this dilemma is implemented by gradually modifying the value of ϵ\epsilonϵ when constructing ϵ\epsilonϵ-greedy policies.

More preciesly, The agent starts by exploring i.e. choosing a random action with some probability epsilon 𝛜. However, the agent continues to "exploit" its knowledge of the environment by choosing actions based on the policy with probability (1-𝛜).
As the time goes on, the value of epsilon is decayed over time, so that over time as the agent gains more experience it increasingly relies on the exploitation.

Deep Q-learning

The Deep Q-Learning algorithm represents the optimal action-value function as a neural network instead of a table.

Unfortunately, reinforcement learning is very unstable when neural networks are used to represent the action values. These instabilities are fixed by using two key features:
    Experience Replay
    Fixed Q-Targets
