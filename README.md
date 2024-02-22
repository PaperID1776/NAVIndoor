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
