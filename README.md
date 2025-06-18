# AI Game with Reinforcement Learning

![Game Screenshot](game_screenshot.png)

## Game Description

This project features a grid-based game environment where an AI agent learns to navigate towards a goal while avoiding moving enemies. The environment is visualized using colored squares:

- **Player**: Green square, controlled by the AI agent.
- **Enemies**: Red squares, which move at a constant speed and bounce off screen edges.
- **Goal**: Blue square, representing the target location the agent must reach.

The agent can move in four directions: up, down, left, and right.

## Agent

The AI agent serves as the player and is trained using **Deep Q-Learning**. Its goal is to maximize cumulative rewards by learning optimal movement strategies to reach the goal while avoiding enemies.

## Actions

The agent can choose from four discrete actions:
- Move Up
- Move Down
- Move Left
- Move Right

## Observations

At each timestep, the agent observes the full game state, which includes:
- The position of the player
- The positions of all enemies
- The position of the goal

## Reward Function

The agent’s behavior is guided by a custom reward function composed of:

- **Goal Reward**: +1000 for reaching the goal.
- **Enemy Penalty**: -100 for colliding with an enemy.
- **Idle Penalty**: A small penalty when the distance to the goal doesn’t decrease:  
  \[
  -3 + e^{-2 \times \text{distance\_term}}
  \]

This encourages efficient movement toward the goal while penalizing unnecessary steps and collisions.

## Deep Q-Learning (DQL)

The agent is trained using Deep Q-Learning, which combines reinforcement learning with deep neural networks to estimate Q-values. The key components include:

- A replay buffer for storing past experiences.
- A target network for stable learning.
- An ε-greedy policy for balancing exploration and exploitation.

## QNetwork Class

The `QNetwork` is a deep neural network consisting of six fully connected layers with ReLU activations (except the output layer). It takes the current state as input and outputs Q-values for all possible actions.

## Results

After training:

- **Goals Reached**: 12 times  
- **Deaths (Enemy Collisions)**: 1777 times

The agent's performance is sensitive to several parameters, such as:
- Game seed
- Screen width and height
- Number of enemies
- Goal size
- Game friction
- Frames per second (FPS)

Tuning these parameters can significantly influence learning outcomes.

## How to Run

1. Clone the repository:
   ```bash
   git clone <repository_url>
   cd <project_directory>
```
2. Run the game:
```python game.py```

Feel free to modify hyperparameters or game settings to experiment with training dynamics and improve the agent's performance.