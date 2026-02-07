# Savings calculation

Savings represent money saved due to:

* local production used locally,
* local production stored and used later,
* device operation shifted to cheaper energy periods.

### Self Use Savings

Self Use Savings represents the value of using produced energy locally instead of exporting it.

At a high level, it is driven by:

* how much production overlaps with consumption in time,
* and how expensive energy would have been if taken from the grid instead.

### Storage Savings

Storage Savings represents the additional value gained by:

* storing surplus energy when it is available,
* and retrieving it later when it is needed.

This is typically higher when:

* production and consumption are separated in time,
* storage capacity and control allow shifting energy effectively.

### Unwasted savings (price shifting)

Unwasted savings represent savings from running devices during cheaper energy periods because the Unwaste Robot selected a mode that caused the device to run then.

**Important: this is an estimate**\nUnwaste can measure:

* when the device ran,
* how much energy it used,
* what the price was at that time.

But Unwaste cannot directly observe the "what if" scenario:

* what the device would have done without Unwaste Robot control.

Therefore Unwasted savings are estimated by comparing:

* actual price during device operation, vs
* average price during the whole day

The rationale is:

* over long time, an uncontrolled device would tend to consume energy more uniformly (or at least not consistently aligned with the cheapest periods).

This estimate should be treated as:

* a helpful indicator of optimisation benefit,
* not a guaranteed invoice-level calculation.