---
description: Understand how energy prices influence automated device operating modes.
---

# Price-based device control

This page explains how the Unwaste Robot chooses **Off**, **Eco**, **Comfort**, and **Boost** operating modes from electricity prices.

How these modes are sent to devices, and how they interact with schedules, overrides, and Surplus mode, is described in [Device control](../../unwaste-robot-configuration/device/device-control.md) and [Profiles, schedules and overrides](../../unwaste-robot-configuration/profiles-schedules-and-overrides/profiles-schedules-and-overrides.md).

***

## Control interval

The Unwaste Robot re-evaluates price-based modes every **15 minutes** — at the start of each control period.

For that period it decides whether energy is cheap or expensive and which operating mode to use as the default for managed devices (unless a schedule or override applies).

***

## Static tariffs

For **static tariffs** (fixed time-of-day zones, for example day/night rates), mapping is straightforward:

* the **cheaper zone** maps to **Comfort**
* the **more expensive zone** maps to **Eco**

Off and Boost are typically not used with simple two-zone static tariffs.

***

## Dynamic tariffs

For **dynamic tariffs** (prices that change frequently, often hourly), the Unwaste Robot assigns **Off**, **Eco**, **Comfort**, or **Boost** to each 15-minute period.

The algorithm compares:

* prices across the **current day**, and
* a **reference built from the last 30 days** of price history.

You do **not** configure price thresholds yourself. The system calculates them automatically from available price data.

The goal is to:

* use **Comfort** (and sometimes **Boost**) when energy is relatively cheap,
* use **Eco** or **Off** when energy is relatively expensive, and
* spread **Comfort** periods across the day rather than concentrating them at a single time.

***

## When prices are unavailable

Dynamic tariffs require the Unwaste Robot to download prices from Unwaste Cloud. If valid prices for the current day cannot be obtained, affected devices switch to **Unmanaged mode** until prices are available again.

The system does **not** reuse yesterday's prices as a fallback.

See [Connection — Dynamic Tariffs](../../unwaste-robot-configuration/connection.md) for details and alerts.

***

## Relation to Surplus mode

Price-based control and Surplus mode are evaluated **independently**. Surplus depends on grid export/import, not on tariffs.

When both apply, **Boost** from price-based control takes precedence over **Surplus**. See [Surplus mode](surplus-mode.md).
