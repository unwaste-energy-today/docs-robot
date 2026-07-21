---
description: Learn how Unwaste handles time, data intervals, and historical data storage.
---

# Time model and data storage

### Raw readings

When the system is STARTED:

* the Unwaste Robot reads configured sensors every **5 seconds**.

These readings may include, depending on configuration:

* power sensors (W, kW),
* energy counters (Wh / kWh),
* state-of-charge, modes, and other device-specific values.

### Aggregation blocks

To store consistent history and align with control decisions:

* readings are aggregated into **15-minute blocks**,
* blocks are aligned to full quarters (00, 15, 30, 45 minutes).

A 15-minute block is a practical compromise:

* small enough to reflect typical changes in production and load,
* large enough to store efficiently and produce stable charts.

### Storage rule

* Aggregated 15-minute totals are stored in the database.
* Power Flow "current" values are not stored.
* Graphs and historical views rely on stored aggregation, not raw samples.

### STOPPED periods

When the system is STOPPED:

* there is no data collection,
* and therefore no aggregation for that period.

This is why:

* daily totals "pause" while STOPPED,
* historical graphs show zeros for those intervals (timeline continuity),
* and aggregated totals exclude those missing intervals.
