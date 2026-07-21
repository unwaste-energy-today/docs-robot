---
description: Learn how Unwaste calculates and balances energy flows in an installation.
---

# Energy flow calculation and balancing

### Why balancing is needed

Real installations are rarely fully metered at every point.\nUnwaste models energy flow as a graph of connected elements (connection → circuits → devices), but:

* some devices may not have meters,
* some circuits may have meters while sub-devices also have meters,
* production and storage can be bidirectional relative to circuits.

To keep the model understandable, Unwaste applies balancing rules that prioritize:

* measured values where available,
* and residual handling where measurement is incomplete.

### Net flow principle

For any connection between two nodes, Unwaste can compute net flow for the chosen period:

* if energy can flow in both directions, net flow is the difference between the two directions.

This is why you see one arrow per connection, not two arrows.

### Unmetered usage as residual

When a circuit meter exists, Unwaste can compare:

* total energy reported by the circuit meter, vs
* sum of energy attributed to metered sub-elements.

If the circuit meter is higher, the difference is shown as **unmetered usage**.

Unmetered usage therefore means:

* "energy that passed through this circuit, but is not explained by known metered elements below it."

### Why negative residual is hidden

A negative residual can occur if production exists "below" a circuit but is not separately metered in the expected way.\nDisplaying "unmetered usage producing energy" is misleading for most users, so negative residual is suppressed.
