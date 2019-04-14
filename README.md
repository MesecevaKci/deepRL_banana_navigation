# deepRL_banana_navigation
Project 1 of Udacity Deep Reinforcement Learning Nanodegree 

The goal of this project is to train an reinforcement learning agent to navigate and collect bananas. A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana. Thus, the goal of the agent is to collect as many yellow bananas as possible while avoiding blue bananas.

The problem is set up in a large, square world. The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around the agent's forward direction. Given this information, the agent has to learn how to best select actions. Four discrete actions are available, corresponding to:

    0 - move forward
    1 - move backward
    2 - turn left
    3 - turn right

The task is episodic, and in order to solve the environment, the agent must get an average score of +13 over 100 consecutive episodes.
