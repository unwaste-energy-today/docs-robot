---
description: Learn how price rules, schedules, and overrides determine device control.
---

# Determining what controls a device

## Determining what controls a device

## Why it is needed

Sometimes it might be needed to determine what element is now in force (that is, if the mode is determined by schedules or overrides or by default mechanism.

That's why we show this information directly in dashboard, because it could be useful for "debugging" your installation, where this rule comes from.

It is only a way to see this information, you cannot change it here.

## Devices

In dashboard, on the graph, each device is labeled with two important pieces of information:

* what mode it operates on
* what is the source of this mode

Mode, as usual, takes one of these values:

* Disabled
* Unmanaged
* Off
* Eco
* Comfort
* Surplus
* Boost

Mode source can take one of these values:

* **Tariff** — the mode was determined from electricity prices (default price-based control). When the active mode is Boost, price-based control took precedence over Surplus even if export conditions were also met.
* **Surplus** — Surplus mode was applied because [Surplus mode](../Configuration/Connection.md#surplus-mode) is enabled, export/import conditions were met, and the price-based mode was not Boost
* **Schedule** — a schedule determined this mode
* **Override** — an override forced this mode

Unmanaged indicates the device is not under tariff, schedule, or override control.

Mode source is not shown for Disabled or Unmanaged modes.

Surplus is not available in schedules or overrides — it applies only through the default control mechanism when Surplus mode is configured on the connection.

### Examples for devices

It can look like in these examples of the same device:

!\[]\(../.gitbook/assets/Profiles, schedules and overrides\_2bea1b35-535b-4922-a269-7e69a30af326\_Screenshot\_tryby.png " =853x127")

## Storages

Storages use a different control model than devices, so they do not have a mode source parameter — they show only their current mode, and it is one of valid storage operating modes:

* Disabled
* Unmanaged
* Default
* Force charge
* Force discharge
* Lock discharge
* Lock both
