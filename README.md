# NAVIndoor

| Parameter            | Description                                                              | Range            | Default |
|----------------------|--------------------------------------------------------------------------|------------------|---------|
| **coin_proba**       | Probability of a coin appearing in each maze cell.                       | [0,1]          | 1       |
| **obstacle_proba**   | Probability of an obstacle appearing in each maze cell.                  | [0,1]           | 0.3     |
| **move_speed**       | The speed at which the agent moves forward or backward.                  | ≥0 | 1       |
| **turn_speed**       | The speed at which the agent rotates.                                    | ≥0               | 150     |
| **momentum**         | Inertial moment kept by the agent when changing direction.               | [0,1]           | 0       |
| **decreasing_reward**| Decreases the reward when agent stays in contact with a collider (wall/obstacle). | True/False       | False   |
| **coin_visible**     | Coins visibility by the camera.                                         | True/False       | True    |


## Navigation in the maze after training

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/explore.gif" alt="Navigation in the maze after training">
</div>

## Real world deployment

We show in our submission that the model's outputs correlates well with real world characteristics. Due to the lack of benchmarks for visually impaired navigation, we focus on images. Below is a real life video sample with $V_{\theta}$ plot (left), frame (center) and segmented map (right). The semantic segmentation map arrow length is related to $V_{\theta}$ and its color is a treshold on it.

<div align="center">
  <img src="https://github.com/PaperID1776/NAVIndoor/blob/main/output.gif" alt="Real world deployment">
</div>
