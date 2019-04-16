# Banana Navigation

### Project 1 of Udacity Deep Reinforcement Learning Nanodegree 

The goal of this project is to train an reinforcement learning agent to navigate and collect bananas. A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana. Thus, the goal of the agent is to collect as many yellow bananas as possible while avoiding blue bananas.

The problem is set up in a large, square world. The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around the agent's forward direction. Given this information, the agent has to learn how to best select actions. Four discrete actions are available, corresponding to:

    0 - move forward
    1 - move backward
    2 - turn left
    3 - turn right

The task is episodic, and in order to solve the environment, the agent must get an average score of +13 over 100 consecutive episodes.

The project environment is similar to, but not identical to the Banana Collector environment on the [Unity ML-Agents GitHub page](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Learning-Environment-Examples.md#banana-collector). 

### Setup 

The project uses 
- Python 3.6 with necessary packages: numpy, random, collections, matplotlib 
- PyTorch v0.4 
- and the pre-built Unity Banana environment. 

The Python environment can be set up following the [Udacity instructions](https://github.com/udacity/deep-reinforcement-learning).
Depending on the operating system, the pre-built Unity environment can be downloaded from:

- Linux: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
- Mac OSX: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
- Windows (32-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
- Windows (64-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)


### Solution

The problem is solved using the deep Q-learning. The code is stored in the notebook [Navigation.ipynb](Navigation.ipynb) and some theoretical background and the description of the solution is described in the [report.md](report.md) document.
