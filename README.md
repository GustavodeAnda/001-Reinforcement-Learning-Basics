# 001-Reinforcement-Learning-Basics
# Blackjack DQL Agent

## Team members
- Alejandro Frizard
- Gustavo de Anda

This repository contains an implementation of a Deep Q-Learning (DQL) agent trained to play Blackjack using Reinforcement Learning (RL). The agent learns optimal strategies by interacting with the environment and updating its Q-values.

## Table of Contents
- [Installation](#installation)
- [How It Works](#how-it-works)
- [Training the Agent](#training-the-agent)
- [Visualizing Results](#visualizing-results)
- [Main Reinforcement Learning Components](#main-reinforcement-learning-components)
- [Results](#results)
- [References](#references)

## Installation

To run the project, install the required dependencies:

```bash
pip install requirements.txt
```

## How It Works

The project utilizes the `gymnasium` Blackjack environment (`Blackjack-v1`). The agent employs the Q-learning algorithm with an epsilon-greedy policy to balance exploration and exploitation.

The key components include:
- **State Representation**: (Player's total, Dealer's face-up card, Usable Ace flag)
- **Actions**: `0` (stick), `1` (hit)
- **Rewards**: +1 for a win, -1 for a loss, 0 for a draw
- **Q-Learning Update Rule**:
  
  ```python
  Q(s, a) = Q(s, a) + learning_rate * (reward + discount_factor * max(Q(s', a')) - Q(s, a))
  ```

## Training the Agent

Run the following command to train the agent:

```bash
python Blackjack.py
```

The training process consists of:
1. Initializing Q-values for each state-action pair.
2. Playing multiple episodes of Blackjack.
3. Updating Q-values based on rewards received.
4. Gradually reducing epsilon to shift from exploration to exploitation.

## Visualizing Results

After training, the script generates:
- **Reward trends** over episodes
- **Episode lengths** to track decision efficiency
- **Training error** over time
- **State-value function** plots
- **Optimal policy heatmaps**

## Main Reinforcement Learning Components

1. **Agent (`BlackjackAgent` Class)**
   - Implements Q-learning.
   - Uses an epsilon-greedy policy for action selection.
   - Updates Q-values using rewards.

2. **Environment (`gymnasium.make('Blackjack-v1')`)**
   - Simulates the game dynamics.
   - Provides state transitions and rewards.

3. **Policy (Epsilon-Greedy Strategy)**
   - Chooses random actions with probability `epsilon` (exploration).
   - Chooses the best-known action with probability `1 - epsilon` (exploitation).

4. **Training Loop**
   - Runs episodes where the agent interacts with the environment.
   - Updates Q-values iteratively.
   - Decays `epsilon` over time to ensure convergence.

## Results

The trained agent can, identify when to hit or stick optimally, maximize expected returns over time and Adapt dynamically to different game situations.


## References
- [Reinforcement Learning: An Introduction - Sutton & Barto](http://incompleteideas.net/book/RLbook2020.pdf)
- [OpenAI Gymnasium Documentation](https://www.gymlibrary.dev/)

