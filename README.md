[//]: # (Image References)

[image1]: https://video.udacity-data.com/topher/2018/June/5b1ea778_reacher/reacher.gif "Trained Agent"

# Project 1: Navigation

### Introduction
This is the final project of the section 'Policy-Based Methods' of the Udacity Deep Reinforcement Learning 
nanodegree .

![Trained Agent][image1]

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

The task is continuous, and in order to solve the environment, your agent must get an average score of +13 over 100 consecutive episodes.

### Project description

The sample Deep Q-Network solution for 'LunarLander-v2' was used as a starting point for this
project. This sample solution, as-is, does allow to train the agent and obtain decent performance.
In fact, the agent can get to an average reward of about 11 at around the 900th episode (rolling 
average of latest 100 episodes.)

From that starting point, the following improvements were added:
1. Using Double DQN when evaluating Q-values (method 'q_targets' of class Agent.)
2. Implemented Prioritized Experience Replay (using
   implementation from https://github.com/rlcode/per)
3. Change the model architeture to Dueling DQN (model.py)

From these improvements, the agent converges to that same average reward to 11 in less than
400 episodes.

### Trained agent

To use the trained agent, simply import weights:
```
from dqn_agent import Agent
agent = Agent()
agent.save('./model_weights')
```

## Dependencies

To set up your python environment to run the code in this repository, follow the instructions below.

1. Create (and activate) a new environment with Python 3.6.

	- __Linux__ or __Mac__: 
	```bash
	conda create --name drlnd python=3.6
	source activate drlnd
	```
	- __Windows__: 
	```bash
	conda create --name drlnd python=3.6 
	activate drlnd
	```
	
2. Follow the instructions in [this repository](https://github.com/openai/gym) to perform a minimal install of OpenAI gym.  
	- Next, install the **classic control** environment group by following the instructions [here](https://github.com/openai/gym#classic-control).
	- Then, install the **box2d** environment group by following the instructions [here](https://github.com/openai/gym#box2d).
	
3. Clone the repository (if you haven't already!), and navigate to the `python/` folder.  Then, install several dependencies.
```bash
git clone https://github.com/udacity/deep-reinforcement-learning.git
cd deep-reinforcement-learning/python
pip install .
```

4. We will be using Shangtong Zhang's implementation of DDPG. Create a folder named 'DeepRL' in the root of your project and clone https://github.com/ShangtongZhang/DeepRL into it.
   
5. DeepRL requires some other packages/different versions. Install the following in your environment:
- conda install mpi4py (pip did not work for myself)
- pip install baselines
- pip install torch==1.4.0
- pip install --upgrade tensorboard
- pip install scikit-image==0.14.2
- pip install torchmeta && pip install torchvision

6. Download the Unity environment from one of the links below.  You need only select the environment that matches your operating system:
    - Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
    - Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
    - Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
    - Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)
    
    (_For Windows users_) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

    (_For AWS_) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux_NoVis.zip) to obtain the environment.

Then, place the file in the p1_navigation/ folder in the DRLND GitHub repository, and unzip (or decompress) the file.

7. Create an [IPython kernel](http://ipython.readthedocs.io/en/stable/install/kernel_install.html) for the `drlnd` environment.  
```bash
python -m ipykernel install --user --name drlnd --display-name "drlnd"
```

8. Before running code in a notebook, change the kernel to match the `drlnd` environment by using the drop-down `Kernel` menu. 

![image info](./jnb.png)

### Training the agent

Execute the cells in `Navigation.ipynb` to train the agent.