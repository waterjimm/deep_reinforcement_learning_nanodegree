
[image1]: https://github.com/waterjimm/deep_reinforcement_learning_nanodegree/blob/master/Collaboration%20and%20Competition/cc_DDPG_test_result.JPG?raw=true "Rewards Plot"


# Report
## Learning Algorithm   
This DRL implemented DDPG model. Both actor and critic networks have two copies of networks: target network and local network. (ddpg.py)

- **Sharing observations and actions information:** Since the goal is to play longer without dropping the ball or hitting out of bounds, two agents need 
to collaborate with each other. The final reward is the maximal of the two agents' scores. Therefore, sharing the states observed by each agent
and the actions taken by each agent in the same DDPG speeds up the training process. The input states are the comination of two states observed by each agent. The actions is also 
the combination of actions of each agent. Meanwhile, the reward of each step is defined as the maximal of agents' reward which is the same direction of final reward score. Therefore, a global DDPG agent decides the actions of both players collaboratively based on observations/states of both agents.  

- **Experience Replay:** In order to utlize all the past experience of plays and reduce the correlation of consecutive records, experience replay is implemented to keep recent history together and randomly select the batches to train the local neural network. The limited buffer size and FIFO strategy to save experience would allow the neural network training evolved over time to capture recent but not only latest information. 

- **Double Actor and Critic Networks:** Two neural networks were introduced. The target network is soft-updated much slower than the local network to make the training more stable to random noise. As a result, this could lead to better convergence. 

- **Ornstein Uhlenbeck process (OU Noise):** The Ornstein-Uhlenbeck Process generates noise added to the actions. The noise is correlated with the previous noise to prevent the noise from canceling out or “freezing” the overall dynamic. This greatly helps the DDPG agent train faster.  

### Hyperparameters (ddpg.py)
- BUFFER_SIZE = int(1e5)  (replay buffer size)
- BATCH_SIZE = 128        (minibatch size)
- GAMMA = 0.99            (discount factor)
- TAU = 5e-3              (for soft update of target parameters)
- LR_ACTOR = 1e-3         (learning rate of the actor)
- LR_CRITIC = 1e-3        (learning rate of the critic)
- WEIGHT_DECAY = 0        (L2 weight decay)
 

### Actor Neural Network
3 linear layers + 2 relu transformation + 1 tanh transformation since action spaces are (-1,1) (model.py)

### Critic Neural Network
3 linear layers + 2 relu transformation (model.py)

## Plot of Rewards
The DDPG agent is able to earn over target 0.5 after 2784 episodes.  
![Rewards Plot][image1]

Partial Reward History:
- Episode 100	Average Score: 0.00	Score: 0.000
- Episode 500	Average Score: 0.01	Score: 0.000
- Episode 1000	Average Score: 0.09	Score: 0.090
- Episode 1500	Average Score: 0.07	Score: 0.100
- Episode 2000	Average Score: 0.13	Score: 0.200
- Episode 2500	Average Score: 0.18	Score: 0.100
- Episode 2700	Average Score: 0.37	Score: 0.090
- Episode 2784	Average Score: 0.51	Score: 2.600
- Episode 2785	Average Score: 0.51	Score: 2.700
- Episode 2786	Average Score: 0.53	Score: 2.600
- Episode 2787	Average Score: 0.55	Score: 2.200
- Episode 2788	Average Score: 0.55	Score: 0.100
- Episode 2789	Average Score: 0.54	Score: 0.000
- Episode 2790	Average Score: 0.54	Score: 0.100
- Episode 2791	Average Score: 0.54	Score: 0.100
- Episode 2792	Average Score: 0.56	Score: 2.600
- Episode 2793	Average Score: 0.57	Score: 0.800
- Episode 2794	Average Score: 0.57	Score: 0.100


## Ideas of Future work
1. Change the architecture of neural network such as number of layers, add convolutional layers, neuro size, adding dropout layers etc.
2. Change the hyperparameters to evaluate its impact on the learning speed. LR appears to be quite important. 
3. Try different DRL structures like MADDPG to explore more stable training process. 

