# Banana Navigation

### Project 1 of Udacity Deep Reinforcement Learning Nanodegree 

The goal of this project is to train an reinforcement learning agent to navigate and collect bananas. A reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana. Thus, the goal of the agent is to collect as many yellow bananas as possible while avoiding blue bananas.

The problem is set up in a large, square world. The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around the agent's forward direction. Given this information, the agent has to learn how to best select actions. Four discrete actions are available, corresponding to:

    0 - move forward
    1 - move backward
    2 - turn left
    3 - turn right

The task is episodic, and in order to solve the environment, the agent must get an average score of +13 over 100 consecutive episodes.

### Setup - instructions from Udacity


#### Step 1: Clone the repo
Clone this repo using `git clone https://github.com/danielnbarbosa/drlnd_navigation.git`.


#### Step 2: Install Dependencies
Create an anaconda environment that contains all the required dependencies to run the project.

Mac:
```
conda create --name drlnd_navigation python=3.6
source activate drlnd_navigation
conda install -y python.app
conda install -y pytorch -c pytorch
pip install torchsummary unityagents
```

Windows:
```
conda create --name drlnd_navigation python=3.6
activate drlnd_navigation
conda install -y pytorch -c pytorch
pip install torchsummary unityagents
```

#### Step 3: Download Banana environment
You will also need to install the pre-built Unity environment, you will NOT need to install Unity itself.  Select the appropriate file for your operating system:

- Linux: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
- Mac OSX: click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
- Windows (32-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
- Windows (64-bit): click [here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)

Download the file into the top level directory of this repo and unzip it.


### Solution

The problem is solved using the deep Q-learning. The code is stored in the notebook "Navigation.ipynb" and some theoretical background and the description of the solution is described in the "report.md" document.
