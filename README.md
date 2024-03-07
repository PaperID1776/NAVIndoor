# NAVIndoor

NavIndoor is a program developped for implementation of the NavImpaired method. It is designed for the acquisition of navigational data within procedurally generated environments and was developed with Unity and its MLAgents library. It starts from closed cells and a virtual agent wearing a head-mounted camera (a), leverages Depth First Search algorithm for mazes procedural generation (b) and fill it with obstacles and coins (c). Observations include current view of the scene from a basic camera (d), and from a camera designed to output semantic segmentation maps highlighting floor, walls, obstacles, and coins (e). Both views has size 128 x 128 x 3.

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/images/maze_gen.png" alt="Navigation in the maze after training">
</div>

Possible actions for the agent are forward, backward, rotation right, rotation left.
List of customizable parameters for the environments is presented below.



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

We propose a `Demo_01` notebook implementing D3QN for training in NavIndoor.

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/images/arch.png" alt="Navigation in the maze after training">
</div>


## Navigation in the maze after training

A model checkpoint is available in `checkpoint/checkpoint.pt` and allows to clip virtual navigation easily through `Demo_02` notebook.

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/images/explore.gif" alt="Navigation in the maze after training">
</div>

## Real world deployment

We showed in our submission that the model's outputs correlates well with real world characteristics for static images with small FOV. `Demo_03` allows to process a real-world videos (sample output displayed below). The generated figures includes a dynamic plot of $V_{\theta}$ over time (left) and the resizes video (center).

The generated figures exhibit a dynamic plot of $V_{\theta}$ over time on the left, providing insights into the temporal evolution of the environment. The resized video is on the center.

To the right, the final image displays the input semantic segmentation maps used by NavImpaired. T top arrow length is proportional to $V_{\theta}(s)$,  with its color indicating a simple thresholding mechanism applied to simulate a potential signal for sensory substitution systems.

Moreover, the bottom arrows' lengths represent the softmax values on $A_{\theta}(s,a)$ for forward, backward, rotate left, and rotate right actions. The colored arrow, depicted in dark green, signifies the optimal action policy determined by the model.. We observe correlation between  $A_{\theta}(s,forward)$, $V_{\theta}(s)$ and the path clearance in front of the cameraman.

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/video_processing/output_sample.gif" alt="Real world deployment">
</div>
