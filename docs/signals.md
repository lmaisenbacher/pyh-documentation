# Signals

* TOC
{:toc}

## Overview

In `pyh`, a signal is an experimental observable or the simulation of such an observable. Currently, all signals correspond to fluorescence from atoms, i.e., photons emitted by the decay of an atom from a higher-lying state to a lower-lying state.

Signals are grouped into signal sets. The underlying idea is that certain simulations will only produce certain signals, e.g., a simulation that only includes two energy levels will only have one fluorescence signal corresponding to the transition between the two levels. All signal sets and signals are defined in [`pyha.def_signals`](https://gitlab.mpcdf.mpg.de/lmaisen/pyha/-/blob/master/def_signals.py), with each signal set and signal identified by a unique IDs, `SignalSetID` and `SignalID`, respectively.

Some signals are composites of other signals, e.g., the Lyman signal is the sum of all Lyman decays, Lyman-$\alpha$, Lyman-$\beta$, ... Other signals might have the same numerical value, e.g., if there is only a single Lyman decay allowed then the sum of all Lyman decays is identical to that decay. Thus, we here distinguish between non-compsite signals, each corresponding to the output of a signal equation of the simulation, and composite signals constructed by a weighted sum over non-composite signals.

## Implementation

Upon evaluation, [`pyha.def_signals`](https://gitlab.mpcdf.mpg.de/lmaisen/pyha/-/blob/master/def_signals.py) defines three DataFrames, `dfSignalSets`, `dfSignals`, and `dfSignalMappings`.

A list of the signals defined for a given signal set with ID `SignalSetID` is returned by

```Python
from pyha import def_signals
def_signals.get_signals(SignalSetID)
```

## Signal sets and signals

### `OBEDMS2S6P` signal set

The `OBEDMS2S6P` signal set is a signal set used in the OBE implementation of the discrete momentum space (DMS) model, used to model the light force shift (LFS) of the 2S-6P transition in atomic hydrogen. Since these equations only include the 1S, 2S, and 6P levels, only Lyman-$\epsilon$ (6P $\rightarrow$ 1S) and Balmer-$\delta$ (6P $\rightarrow$ 2S) decays are included. This leads to a total of 4 signal equations for non-composite signals `Lyman`, `Balmer`, `LymanNoBD`, and `LymanBDCorrOnly`, from which an additional 3 signals are constructed.

### `OBEDMSLymanEpsilon` signal set

The `OBEDMSLymanEpsilon` signal set is a signal set used in the trajectory interpolation of the OBE implementation of the discrete momentum space (DMS) model for the 2S-6P transition in atomic hydrogen and deuterium. It only includes a single signal for Lyman-$\epsilon$ (6P $\rightarrow$ 1S) decays, `Lyman-epsilon`.

### `All2S6P` signal set

The `All2S6P` signal set is a signal set used in the OBE implementation of the big model, used to model quantum interference and light shifts of the 2S-6P transition in atomic hydrogen. There are a total of 42 signal equations, and a total of 77 signals.

### `LymanEpsilon` signal set

The `LymanEpsilon` signal set is a signal set used in the trajectory implementation of the OBE implementation of the big model for the 2S-6P transition in atomic hydrogen and deuterium. There are a total of 3 signal equations, and a total of 4 signals.
