# Deep Reinforcement Learning with Topology Data Analysis

This repository contains a Q-learning implementation for the classic Mountain Car reinforcement learning problem from OpenAI Gym. The agent learns to drive an underpowered car up a steep hill by building momentum through oscillations in the valley.

## Overview

The **Mountain** Car problem is a classic reinforcement learning task where an underpowered car must drive up a steep hill. Since the car's engine is not strong enough to climb the hill directly, the agent must learn to drive back and forth to build up momentum.

This implementation uses:
- Q-learning with discretized state space
- Multiple random seeds for statistical robustness
- Detailed data collection and visualization
- Configurable learning and exploration parameters

## Features

- **Multiple Seeds**: Runs experiments with multiple random seeds to ensure statistical robustness
- **Comprehensive Data Collection**: Records detailed information about each step of the learning process
- **Visualization**: Generates plots for individual seeds and mean performance across all seeds
- **CSV Export**: Saves all experiment data in CSV format for further analysis
- **Video Recording**: Captures videos of the agent's performance at specified intervals
- **Progress Tracking**: Shows real-time progress during training

## Requirements

- Python 3.6+
- NumPy
- Pandas
- Matplotlib
- OpenAI Gym
- scikit-learn
- OpenCV (for video recording)

Install the required packages using:

```bash
pip install numpy pandas matplotlib gym scikit-learn opencv-python
```

## Usage

Simply run the script:

```bash
python mountain_car.py
```

## Configuration

You can modify the following parameters in the script:

- `n_episodes`: Number of episodes to run for each seed
- `SEEDS`: List of random seeds to use
- `learning_coeff` and `learning_decay`: Control the learning rate
- `exploration_coeff` and `exploration_decay`: Control the exploration rate
- `n_bins`: Size of the discretization bins for the state space
- `capture_eps`: Episodes at which to capture videos

## Output

The script creates an `Experiments` directory with a timestamped folder for each run, containing:

### Mountain Car DataSet
Data generated for the mountain car game.

### Data Files
- `data/seed_X/seed_X_data.csv`: Detailed step-by-step data for each seed
- `data/seed_X/summary.csv`: Episode-level summary for each seed
- `data/global_summary.csv`: Overall performance summary across all seeds
- `data.csv`: Raw data for all seeds in a single file
- `variables.json`: Configuration parameters used for the experiment

### Visualizations
- `img/seed_X.png`: Performance plot for each individual seed
- `img/mean_performance.png`: Mean performance plot across all seeds

### Videos
- `video/seed_X/iter_Y.avi`: Videos of the agent's performance at specified intervals

## Understanding the Results

### Success Rate
The success rate indicates how often the agent successfully reached the goal (position ≥ 0.5). A higher success rate indicates better performance.

### Reward Plots
The reward plots show:
- Raw episode rewards (blue dots)
- Rolling average reward (red line)
- Learning rate (green line)
- Exploration rate (orange line)

As training progresses, you should see the rolling average reward increase, indicating that the agent is learning to solve the task more efficiently.

### CSV Data
The CSV files contain detailed information about each step of the learning process, including:
- Position and velocity of the car
- Action taken
- Reward received
- Whether the episode terminated or was truncated
- Whether the car succeeded in reaching the goal

## Customization

You can customize the experiment by modifying the parameters at the top of the script. For example:

- To run more episodes: Increase `n_episodes`
- To use different random seeds: Modify the `SEEDS` list
- To adjust the learning behavior: Modify `learning_coeff`, `learning_decay`, `exploration_coeff`, and `exploration_decay`

## How Q-Learning Works

The implementation uses Q-learning, a model-free reinforcement learning algorithm that learns the value of actions in states. The key components are:

1. **State Discretization**: Continuous state space (position and velocity) is discretized into bins
2. **Q-Table**: Stores the expected future reward for each state-action pair
3. **Exploration vs. Exploitation**: Balances random exploration with exploiting known good actions
4. **Learning Rate**: Controls how quickly the agent updates its Q-values
5. **Discount Factor**: Determines the importance of future rewards

## License

This code is provided under the MIT License.

## Acknowledgments

This material is based upon work supported by the National Science Foundation under Award No. OIA-1946391.
