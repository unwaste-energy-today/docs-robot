---
description: Learn how Unwaste decides when to request battery charging from the grid.
---

# Storage control

## What is storage control

**Storage control** describes how the **Unwaste Robot** decides _when to request charging an energy storage from the grid_.

The Unwaste Robot does **not** control whether surplus energy from local production (for example photovoltaic panels) is stored.&#x20;

**Any surplus production that is not consumed immediately is always stored**, regardless of settings or prices.

What the Unwaste Robot controls is the **Force Charge mode**, which is effectively a signal meaning:

> "Charge the storage from the grid now."

The purpose of storage control is to request grid charging only when it is economically justified.

***

## How it works (high level)

The Unwaste Robot evaluates three main factors:

* **Energy usage forecast** An estimate of how much energy the household is likely to consume.
* **Energy production forecast** An estimate of expected local production (for example from solar PV).
* **Energy price** Information about whether grid energy is currently cheap or expensive.

Based on these inputs, the Unwaste Robot decides **whether or not to activate Force Charge**.

In general, it:

* **enables Force Charge when grid energy is cheap**, and future energy demand is expected,
* **avoids Force Charge when grid energy is expensive**,
* **avoids Force Charge if significant local production is expected**, even if the storage is not currently full.

***

## What this means in practice

* Surplus photovoltaic energy is **always stored automatically** if storage capacity is available.
* The Unwaste Robot does **not block or delay PV charging** in any way.
* The only decision made by the Unwaste Robot is whether to **actively charge the storage from the grid**.
* If high solar production is expected later, the system may intentionally **leave the storage partially empty**, waiting to fill it with local energy instead of grid energy.

This helps reduce costs while preserving full use of locally produced energy.

***

## Important notes

**Signal, not direct control**\nThe Unwaste Robot sends a **Force Charge signal**.\nThe storage device:

* decides how to execute it,
* may limit charging power,
* may ignore it for safety, health, or internal logic reasons.

**Device and installation dependency**\nActual behavior depends on:

* whether the storage supports Force Charge from external control,
* correct installation and configuration,
* availability of production forecasts and price data.

If required data is missing, the system may fall back to conservative behavior.

***

## Example

A household with:

* a battery,
* solar panels,
* a dynamic electricity tariff.

If:

* electricity is expensive now,
* high solar production is expected later today,

the Unwaste Robot will:

* **not enable Force Charge**, even if the battery is not full,
* allow the battery to fill later using surplus solar energy.

If:

* electricity becomes cheap at night,
* no production is expected,

the Unwaste Robot may enable **Force Charge** to prepare for next-day consumption.

***

## Surplus mode for devices (separate topic)

**Device Surplus mode** (when enabled on the connection) increases load during PV export. It is unrelated to storage Force Charge and is described in [Connection](../../unwaste-robot-configuration/connection.md#surplus-mode) and [Device control](../../unwaste-robot-configuration/device/device-control.md).
