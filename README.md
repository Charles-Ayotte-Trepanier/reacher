[//]: # (Image References)

[image1]: https://video.udacity-data.com/topher/2018/June/5b1ea778_reacher/reacher.gif "Trained Agent"

# Project 2: Continuous Control

### Introduction
This is the final project of the section 'Policy-Based Methods' of the Udacity Deep Reinforcement Learning 
nanodegree .

![Trained Agent][image1]

In this environment, a double-jointed arm can move to target locations. A reward of +0.1 is provided for each step that the agent's hand is in the goal location. Thus, the goal of your agent is to maintain its position at the target location for as many time steps as possible.

The observation space consists of 33 variables corresponding to position, rotation, velocity, and angular velocities of the arm. Each action is a vector with four numbers, corresponding to torque applicable to two joints. Every entry in the action vector should be a number between -1 and 1.

The task is continuous, and in order to solve the environment, your agent must get an average score of +30 over 100 consecutive episodes.

### Project description

This project consists in developing a reinforcement learning agent whose task is to solve the Reacher environment. More precisly:
- Reviewing litterature to determine which algorithms is best suited for this environment, considering the continuous actions-space.
- Learning and understanding the different alternatives (DDPG, D4PG, PPO), how they are different and when they are best performing.
- Implementing the agent based on selected algorithm.
- Training the agent to solve the environment.

There are also two versions of the Reacher environment:
- The first version contains a single agent.
- The second version contains 20 identical agents, each with its own copy of the environment.

This project is looking to solve the first version, with a single agent.

### Trained agent

To use the trained agent, instantiate an agent with the class DDPGAgent (in the "Continuous_Control.ipynb" notebook) and load the model weights with:

```
agent = DDPGAgent()
agent.load('successfull_model')
```
Note: make sure note to re-run the cell where the agent is trained, as training takes over 1 hour.
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

Execute the cells in `Continuous_Control.ipynb` to train the agent.