# Surplus mode

This page explains how the Unwaste Robot decides when to request **Surplus** operating mode on managed devices.

Configuration (thresholds, required readings, States Map) is described in [Connection](../Configuration/Connection.md#surplus-mode) and [Device control](../Configuration/Device/Device%20control.md).


---

## Purpose

Surplus mode increases local use of photovoltaic production when the installation is **exporting energy to the grid**. The goal is to absorb excess solar energy with controllable loads instead of feeding it back to the grid.

Surplus is a separate control signal from price-based modes. You map what Surplus means for each device in the States Map, just like Eco or Comfort.


---

## Where Surplus sits among operating modes

For devices, operating modes form a scale from lower to higher energy use:

```text
Off < Eco < Comfort < Surplus < Boost
```

Surplus sits between Comfort and Boost. It encourages more consumption than Comfort, but it is not the same as Boost — Boost is driven by favourable **electricity prices**, while Surplus is driven by **export to the grid**.


---

## Independent from electricity prices

The decision to enter or leave Surplus mode is based on **import and export measurements** on the main circuit and the thresholds you configure on the connection.

Price-based control runs **in parallel**. The Unwaste Robot evaluates both:

* the mode suggested by **tariffs** (Off, Eco, Comfort, or Boost), and
* whether **surplus conditions** are currently met.

If surplus conditions are met and the price-based mode is Off, Eco, or Comfort, the device may receive **Surplus** instead.

If surplus conditions are met but the price-based mode is **Boost**, **Boost wins**. Boost can increase consumption beyond Surplus and may draw energy from the grid; the system treats that as the economically preferred choice when prices justify it.


---

## When the system enters Surplus mode

Surplus entry is evaluated at the end of each **15-minute** control interval.

The system looks at **average export power** over the **previous** completed 15-minute period. If that average is at or above your **Surplus on threshold**, surplus conditions become active for managed devices (subject to the Boost rule above).

This means entry is not instantaneous — the robot waits for a full 15-minute window of sustained export before reacting.


---

## When the system leaves Surplus mode

While Surplus is active, exit is checked much more often — on each **5-second** reading cycle.

The system tracks **import energy** in the **current** 15-minute period. If import reaches the level implied by your **Surplus off threshold**, Surplus ends immediately and the device returns to the current **price-based mode** (Off, Eco, Comfort, or Boost).

So entry is evaluated every 15 minutes, but exit can happen within seconds when import rises.


---

## Anti-oscillation

If Surplus ends because import crossed the off threshold, the system **does not re-enter Surplus in the same 15-minute period** based on that export window.

This reduces rapid switching when export and import alternate quickly — for example when a load turns on and off near the threshold.

Re-entry is only considered after the next full 15-minute evaluation cycle, and only if export conditions are met again.


---

## Energy storage and export

Surplus reacts to **export at the grid connection**. In practice, export usually means energy that was not used locally and was not stored in the battery.

Typical order of use for PV production:

1. Cover immediate consumption in the installation
2. Charge storage (if available and not full)
3. Export any remaining surplus to the grid

Surplus mode targets loads when step 3 would otherwise occur — that is, when there is a measurable export despite local consumption and storage.


---

## What Surplus does not do

* Surplus is **not** available in schedules or overrides — only through the default control mechanism when Surplus mode is enabled on the connection.
* Surplus does **not** replace manufacturer safety logic or guarantee that a device will absorb a specific amount of energy.
* Surplus does **not** control battery charging directly; storage follows its own rules (see [Storage control](Storage%20control.md)).
