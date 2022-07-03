# Data structures

Overview of the data structures of the `pyh` family.

## Trajectory sets

Trajectory sets are sets of random atomic trajectories representing the atomic beam, and thus form a Monte Carlo simulation of the atomic beam. The trajectory sets are genererated with [`MCTrajectories`](https://gitlab.mpcdf.mpg.de/lmaisen/MCTrajectories). The metadata of trajectory sets is managed by [`pyha.trajs.Trajs`](https://gitlab.mpcdf.mpg.de/lmaisen/pyha/-/blob/master/trajs.py) and is contained in two DataFrames, `dfTrajParams` and `dfTrajAnalysis`.

### `dfTrajParams`

Each row of the DataFrame `dfTrajParams` contains metadata describing a single trajectory set, and is generated along with the trajectory set itself. At this time, each trajectory set is also assigned a unique UID, the `TrajUID`, consisting of 8 random alphanumeric characters. The `TrajUID` serves as index of `dfTrajParams`, and there is only a single entry per `TrajUID`.

### `dfTrajAnalysis`

### `dfTrajsParams`

`dfTrajsParams` is an inner join of `dfTrajParams` and `dfTrajAnalysis` on the index of the two DataFrames, which is the trajectory UID `TrajUID`.
