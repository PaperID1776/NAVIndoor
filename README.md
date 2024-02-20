# NAVIndoor

| Parameter          | Description                                                              | Default |
|--------------------|--------------------------------------------------------------------------|---------|
| **coin\_proba**    | Probability of a coin appearing in each maze cell.                       | 1       |
| **obstacle\_proba**| Probability of an obstacle appearing in each maze cell.                  | 0.3     |
| **move\_speed**    | The speed at which the agent moves forward or backward.                  | 1       |
| **turn\_speed**    | The speed at which the agent rotates.                                   | 150     |
| **momentum**       | Inertial moment kept by the agent when changing direction.               | 0       |
| **decreasing\_reward** | Decreases the reward when agent stays in contact with a collider (wall/obstacle). | False |
| **coin\_visible**  | Coins visibility by the camera.                                         | True    |
