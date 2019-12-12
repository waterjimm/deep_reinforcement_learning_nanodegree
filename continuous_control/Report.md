
[image1]: https://github.com/waterjimm/deep_reinforcement_learning_nanodegree/blob/master/continuous_control/continuous_control.JPG?raw=true "Rewards Plot"

# Report
## Learning Algorithm
This DRL implemented Double DQN model with two networks: target network and local network. (dqn_agent.py)

- **Experience Replay:** In order to utlize all the past experience and reduce the correlation of consecutive records, experience replay is implemented to mix history together and randomly select the batches to train the local neural network. The limited buffer size and FIFO strategy to save experience would allow the neural network training evolved over time to capture recent but not only latest information. 

- **Double Actor and Critic Networks:** Due to the recursive formula of the Q function, using single neural network would lead to overestimate action values since the response Y also relies on the Q function. Therefore, two neural networks were introduced. The target network is updated periodically or much slower than the local network to make the training more stable to random noise. As a result, this could lead to better convergence. 

- **UO Noise:**

### Hyperparameters
max_t=1000, eps_start=1.0, eps_end=0.01, eps_decay=0.995

### Q Neural Network
3 linear layers + 2 relu transformation (model.py)

## Plot of Rewards
The DQN agent is able to earn over 13 after 600 episodes.  
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
- Episode 70	Average Score: 37.43	Score: 37.733



## Ideas of Future work
1. Change the architecture of neural network such as number of layers, add convolutional layers, neuro size, adding dropout layers etc.
2. Change the hyperparameters to evaluate its impact on the learning speed.
3. Try different DRL structures such as dueling DQN

