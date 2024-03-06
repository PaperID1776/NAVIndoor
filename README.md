# NAVIndoor

NavIndoor is a program developped for implementation of the NavImpaired method. It is designed for the acquisition of navigational data within procedurally generated environments and was developed with Unity and its MLAgents library. It starts from closed cells and a virtual agent wearing a head-mounted camera (a), leverages Depth First Search algorithm for mazes procedural generation (b) and fill it with obstacles and coins (c). Observations include current view of the scene from a basic camera (d), and from a camera designed to output semantic segmentation maps highlighting floor, walls, obstacles, and coins (e). Both views has size 128 x 128 x 3.

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/images/maze.png" alt="Navigation in the maze after training">
</div>


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


The default reward function `R` is defined as follows:
- `-1` if the agent collides with an obstacle,
- `-0.5` if the agent collides with a wall,
- `5` if the agent collects a coin,
- `0` otherwise.


## Training in NavIndoor

We propose a demo notebook implementing D3QN for training in NavIndoor

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/images/arch.png" alt="Navigation in the maze after training">
</div>


## Navigation in the maze after training

A model checkpoint is available in `checkpoint/checkpoint.pt`. 

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/images/explore.gif" alt="Navigation in the maze after training">
</div>

## Real world deployment

We show in our submission that the model's outputs correlates well with real world characteristics. Due to the lack of benchmarks for visually impaired navigation, we focus on images. Below is a real life video sample with $V_{\theta}$ plot (left), frame (center) and segmented map (right). The semantic segmentation map arrow length is related to $V_{\theta}$ and its color is a treshold on it.

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/imagesoutput.gif" alt="Real world deployment">
</div>
