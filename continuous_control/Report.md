
[image1]: https://github.com/waterjimm/deep_reinforcement_learning_nanodegree/blob/master/continuous_control/continuous_control.JPG?raw=true "Rewards Plot"

[image2]: https://github.com/waterjimm/deep_reinforcement_learning_nanodegree/blob/master/continuous_control/leaky_relu_pic.JPG?raw=true "Rewards Plot2"



# Report
## Learning Algorithm  (ddpg.py)
This DRL implemented DDPG model. Both actor and critic networks have two copies of networks: target network and local network. (ddpg.py)

- **Experience Replay:** In order to utlize all the past experience from multiple (20 in our case) Reacher environments and reduce the correlation of consecutive records, experience replay is implemented to mix all history together and randomly select the batches to train the local neural network. The limited buffer size and FIFO strategy to save experience would allow the neural network training evolved over time to capture recent but not only latest information. 

- **Double Actor and Critic Networks:** Two neural networks were introduced. The target network is soft-updated much slower than the local network to make the training more stable to random noise. As a result, this could lead to better convergence. 

- **Ornstein Uhlenbeck process (OU Noise):** The Ornstein-Uhlenbeck Process generates noise added to the actions. The noise is correlated with the previous noise to prevent the noise from canceling out or “freezing” the overall dynamic. This greatly helps the DDPG agent train faster.  

### Hyperparameters (ddpg.py)
- BUFFER_SIZE = int(1e5)  (replay buffer size)
- BATCH_SIZE = 128        (minibatch size)
- GAMMA = 0.99            (discount factor)
- TAU = 1e-3              (for soft update of target parameters)
- LR_ACTOR = 1e-4         (learning rate of the actor)
- LR_CRITIC = 1e-4        (learning rate of the critic)
- WEIGHT_DECAY = 0        (L2 weight decay)
 

### Actor Neural Network
3 linear layers + 2 relu transformation + 1 tanh transformation since action spaces are (-1,1) (model.py)

### Critic Neural Network
3 linear layers + 2 relu transformation (model.py)

## Plot of Rewards
The DDPG agent is able to earn over 30 after 48 episodes with relu() activation function in critic network.  
![Rewards Plot][image1]

Partial Reward History:
- Episode 1	Average Score: 1.03	Score: 1.032
- Episode 20	Average Score: 3.03	Score: 5.214
- Episode 30	Average Score: 10.03	Score: 13.759
- Episode 40	Average Score: 19.48	Score: 23.750
- Episode 47	Average Score: 26.92	Score: 29.865
- Episode 48	Average Score: 27.90	Score: 31.763
- Episode 49	Average Score: 28.79	Score: 32.608
- Episode 50	Average Score: 29.73	Score: 33.144
- Episode 60	Average Score: 36.33	Score: 37.670 

The DQN agent is able to earn over 30 after 33 episodes with leaky_relu() activation function in critic network.
![Rewards Plot2][image2]
- Episode 1	Average Score: 0.44	Score: 0.443
- Episode 20	Average Score: 2.88	Score: 4.507
- Episode 32	Average Score: 16.51	Score: 28.633
- Episode 33	Average Score: 18.87	Score: 30.554
- Episode 34	Average Score: 21.30	Score: 32.594
- Episode 40	Average Score: 33.64	Score: 37.473
 

## Ideas of Future work
1. Change the architecture of neural network such as number of layers, add convolutional layers, neuro size, adding dropout layers etc.
2. Change the hyperparameters to evaluate its impact on the learning speed.
3. Try different DRL structures such as A3C etc.

