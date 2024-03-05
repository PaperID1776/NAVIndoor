# NAVIndoor

NavIndoor is a sophisticated tool developped for implementation of the NavImpaired method. It is designed for the acquisition of navigational data within procedurally generated environments and was developed with Unity and its MLAgents library. NavIndoor generates it generates static indoor environments that are filled with obstacles, walls and collectible coins. 

Observations include two 128 x 128 x 3 frames for RGB and semantic segmentation maps of the current view.


List of customizable parameters for the enrivonments is presented below.



| Parameter            | Description                                                              | Range            | Default |
|----------------------|--------------------------------------------------------------------------|------------------|---------|
| **coin_proba**       | Probability of a coin appearing in each maze cell.                       | [0,1]          | 1       |
| **obstacle_proba**   | Probability of an obstacle appearing in each maze cell.                  | [0,1]           | 0.3     |
| **move_speed**       | The speed at which the agent moves forward or backward.                  | ≥0 | 1       |
| **turn_speed**       | The speed at which the agent rotates.                                    | ≥0               | 150     |
| **momentum**         | Inertial moment kept by the agent when changing direction.               | [0,1]           | 0       |
| **decreasing_reward**| Decreases the reward when agent stays in contact with a collider (wall/obstacle). | True/False       | False   |
| **coin_visible**     | Coins visibility by the camera.                                         | True/False       | True    |


With decrease reward parameter False, the reward function `R(t)` at time `t` is defined as follows:
- `-1` if the agent collides with an obstacle,
- `-0.5` if the agent collides with a wall,
- `5` if the agent collects a coin,
- `0` otherwise.


## Navigation in the maze after training

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/explore.gif" alt="Navigation in the maze after training">
</div>

## Real world deployment

We show in our submission that the model's outputs correlates well with real world characteristics. Due to the lack of benchmarks for visually impaired navigation, we focus on images. Below is a real life video sample with $V_{\theta}$ plot (left), frame (center) and segmented map (right). The semantic segmentation map arrow length is related to $V_{\theta}$ and its color is a treshold on it.

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/output.gif" alt="Real world deployment">
</div>
