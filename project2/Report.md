
[image1]: https://github.com/waterjimm/deep_reinforcement_learning_nanodegree/blob/master/project2/rewards_plot.png?raw=true "Rewards Plot"

# Report
## Learning Algorithm
This DRL implemented Double DQN model with two networks: target network and local network. (dqn_agent.py)

### Hyperparameters
max_t=1000, eps_start=1.0, eps_end=0.01, eps_decay=0.995

### Q Neural Network
3 linear layers + 2 relu transformation (model.py)

## Plot of Rewards
The DQN agent is able to earn over 13 after 600 episodes.  
![Rewards Plot][image1]

Reward History:
- Episode 100	Average Score: 1.00
- Episode 200	Average Score: 4.52
- Episode 300	Average Score: 8.26
- Episode 400	Average Score: 9.80
- Episode 500	Average Score: 11.98
- Episode 600	Average Score: 13.07
- Episode 700	Average Score: 14.77
- Episode 800	Average Score: 15.38
- Episode 900	Average Score: 15.92
- Episode 1000	Average Score: 16.17
- Episode 1100	Average Score: 15.47
- Episode 1200	Average Score: 15.76
- Episode 1300	Average Score: 15.48
- Episode 1400	Average Score: 15.99
- Episode 1500	Average Score: 15.31
- Episode 1600	Average Score: 15.83
- Episode 1700	Average Score: 16.09
- Episode 1800	Average Score: 15.05
- Episode 1900	Average Score: 14.64
- Episode 2000	Average Score: 15.94



## Ideas of Future work
1. Change the architecture of neural network such as number of layers, neuro size, adding dropout layers etc.
2. Change the hyperparameters to evaluate its impact on the learning speed.
3. Try different DRL structures such as dueling DQN
