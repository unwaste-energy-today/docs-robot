---
description: Understand how Unwaste calculates savings from direct solar energy use.
---

# Self-use calculation

### Why daily totals are misleading

If you compute self-use using daily totals only, you can get incorrect conclusions.

Example (one day):

* Produced total: 10 kWh (mostly daylight)
* Used total: 22 kWh (mostly evening/night)
* Used during daylight: 2 kWh

If you assumed all production could be "used", you might incorrectly conclude:

* self-used energy = 10 kWh

But in reality, only the overlap in time matters:

* self-used energy should be close to 2 kWh (unless storage shifted energy).

### 15-minute block method

To avoid this mistake, Unwaste calculates self-use per 15-minute block:

For each 15-minute interval:

* `self_used_interval = min(produced_interval, used_interval)`

Then:

* `Self Used = sum(self_used_interval over all intervals)`
* `Self Use (%) = Self Used / Produced`
* `Self Sufficiency (%) = Self Used / Used`

This method ensures:

* self-use reflects actual time overlap,
* and storage effects can be captured via stored/retrieved behavior.

**Note:**\nThis is a deliberate design choice to keep results realistic for typical household and small business patterns.
