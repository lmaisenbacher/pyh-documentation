# Signals

In `pyh`, a signal is an experimental observable or the simulation of such an observable. Currently, all signals correspond to fluorescence from atoms, i.e., photons emitted by the decay of an atom from a higher-lying state to a lower-lying state.

Signals are grouped into signal sets. The underlying idea is that certain simulations will only produce certain signals, e.g., a simulation that only includes two energy levels will only have one fluorescence signal corresponding to the transition between the two levels. All signal sets and signals are defined in [`pyha.def_signals`](https://gitlab.mpcdf.mpg.de/lmaisen/pyha/-/blob/master/def_signals.py), with each signal set and signal identified by a unique `SignalSetID` and `SignalID`, respectively.

## Implementation

Upon evaluation, [`pyha.def_signals`](https://gitlab.mpcdf.mpg.de/lmaisen/pyha/-/blob/master/def_signals.py) defines three DataFrames, `dfSignalSets`, `dfSignals`, and `dfSignalMappings`.

## Signal sets and signals

### The `OBEDMS` signal set

The `OBEDMS` signal set is the signal set used by the discrete momentum space (DMS) optical Bloch equations (OBEs), used to model the light force shift (LFS) of the 2S-6P transition in atomic hydrogen. Since these equations only include the 1S, 2S, and 6P levels, only Lyman-$\epsilon$ (6P $\rightarrow$ 1S) and Balmer-$\delta$ (6P $\rightarrow$ 2S) decays are included.
