[//]: # (Image References)

[image1]: https://video.udacity-data.com/topher/2018/June/5b1ab4b0_banana/banana.gif "Trained Agent"
[image2]: https://user-images.githubusercontent.com/10624937/43851646-d899bf20-9b00-11e8-858c-29b5c2c94ccc.png "Crawler"


# Project 2: Navigation
Information is collected from the DRL nanodegree project instruction. 

### Introduction

This project is to train a computer program to intelligently navigate (and collect bananas!) in a large, square world.

![Trained Agent][image1]

A deep reinforcement learning is a good fit of such kind of computer games. It train an agent built with neural networks to make a decision (action) based on the observation of the screen status (state) instantly. In training process, agent adjusts its strategy (update the neural networks) based on the past logs (experience).  

In this navigation game, a reward of +1 is provided for collecting a yellow banana, and a reward of -1 is provided for collecting a blue banana. Thus, the goal of the agent is to collect as many yellow bananas as possible while avoiding blue bananas.

The state space has 37 dimensions and contains the agent's velocity, along with ray-based perception of objects around the agent's forward direction. Given this information, the agent has to learn how to best select actions. Four discrete actions are available, corresponding to:

- 0 - move forward.
- 1 - move backward.
- 2 - turn left.
- 3 - turn right.

The task is episodic, and in order to solve the environment, your agent must get an average score of +13 over 100 consecutive episodes.

### The Environment
Follow the instructions below to explore the environment on your own machine! You will also learn how to use the Python API to control your agent.

#### Step 1: Clone the DRLND Repository
If you haven't already, [please follow the instructions in the DRLND GitHub repository](https://github.com/udacity/deep-reinforcement-learning#dependencies) to set up your Python environment. These instructions can be found in README.md at the root of the repository. By following these instructions, you will install PyTorch, the ML-Agents toolkit, and a few more Python packages required to complete the project.

(For Windows users) The ML-Agents toolkit supports Windows 10. While it might be possible to run the ML-Agents toolkit using other versions of Windows, it has not been tested on other versions. Furthermore, the ML-Agents toolkit has not been tested on a Windows VM such as Bootcamp or Parallels.

#### Step 2: Download the Unity Environment
For this project, you will not need to install Unity - this is because we have already built the environment for you, and you can download it from one of the links below. You need only select the environment that matches your operating system:
- Linux: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux.zip)
- Mac OSX: [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana.app.zip)
- Windows (32-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86.zip)
- Windows (64-bit): [click here](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Windows_x86_64.zip)
Then, place the file in the p1_navigation/ folder in the DRLND GitHub repository, and unzip (or decompress) the file.

(For Windows users) Check out [this link](https://support.microsoft.com/en-us/help/827218/how-to-determine-whether-a-computer-is-running-a-32-bit-version-or-64) if you need help with determining if your computer is running a 32-bit version or 64-bit version of the Windows operating system.

(For AWS) If you'd like to train the agent on AWS (and have not [enabled a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md)), then please use [this link](https://s3-us-west-1.amazonaws.com/udacity-drlnd/P1/Banana/Banana_Linux_NoVis.zip) to obtain the "headless" version of the environment. You will **not** be able to watch the agent without enabling a virtual screen, but you will be able to train the agent. (To watch the agent, you should follow the instructions to [enable a virtual screen](https://github.com/Unity-Technologies/ml-agents/blob/master/docs/Training-on-Amazon-Web-Service.md), and then download the environment for the Linux operating system above.)


#### Step 3: Explore the Environment
After you have followed the instructions above, open Navigation.ipynb (located in this GitHub repository) and follow the instructions to learn how to use the Python API to control the agent.

In the "Take Random Actions in the Environment" code cell of the notebook, you'll learn how to design and observe an agent that always selects random actions at each timestep. 

### DRL Model 
#### Model Summary
In the "DQN learning" code cell, a DRL agent is provided and trained to perform much better than the random action. It is able to reach the goal (on average 15+ over 100 consecutive episodes). 

The double DQN implemented contains two neural networks: target and local to make the training more stable and reliable. It utilizes pytorch to build the neural networks with 3 linear layers and Relu transformations. It is fast to train the neural network even witho only CPU (< 1hour).  

#### Training Method
Experience replay is used to train the local neural network to draw samples from history logs and reduce the correlation of consecutive samples. A fixed sized buffer is used to keep the recent experience. 

#### Interesting findings
Learning rate is important. When its value is too large, the agent performance would not be very good since the network would easily get stuck in local optimal weights. 
The episode number of the training step doesn't need to be too large since the average rewards would decrease due to "catastrophic forgetting" of too long training.

 
