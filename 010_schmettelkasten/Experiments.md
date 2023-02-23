
### Data quality test

Checkpoint: /home/mikkel/workspace/Produce101/outputs/2023-02-13/12-53-41
Trained on full quality jpeg

Checkpoint: /home/mikkel/workspace/Produce101/outputs/2023-02-13/10-53-02

Trent på sequence quality jpeg

reposet_multiprocessing er høy kvalitet, reposet_async er sequences kvalitet


Big jpeg - mp
small jpg - async

| f1  |  async  |  multiprocessing |
|---|---|---|
| async  | 0.7043  | 0.7055 |
| multiprocessing  | 0.6969  | 0.6969 |

| prec  |  async  |  multiprocessing |
|---|---|---|
| async  | 0.7822 |  0.7871 |
| multiprocessing  | 0.7783 |  0.7753 |

| recall |  async  |  multiprocessing |
|---|---|---|
| async  | 0.64 | 0.6392 |
| multiprocessing  | 0.6310  |  0.6296 |

### Cosine annealing unlimited restart