---
description: Prepare Home Assistant devices and integrations for use with Unwaste EMS.
---

# Connecting devices

## Connecting devices

## Before You Configure Unwaste

Unwaste EMS reads data from and sends control signals through **Home Assistant entities**.

Before you add production sources, storage, or devices in Unwaste **Design mode**, those integrations must already work in Home Assistant.

***

### What to Prepare in Home Assistant

#### Energy metering

For the **main circuit**, you need Home Assistant **energy** sensors that report:

* energy imported from the grid
* energy returned to the grid (if you have PV or export)

Use the same entities you would add to the Home Assistant **Energy** dashboard, or dedicated smart meter integrations.

#### Production (PV)

Configure your inverter integration so that **energy production** (and optionally forecast) entities are available.

#### Storage (battery)

Configure battery integration entities for:

* energy stored and retrieved (cumulative counters)
* charge level (percent or kWh), if available
* control entities (switches or selects) if the Unwaste Robot should manage the battery

#### Controllable devices

For devices you want the Unwaste Robot to manage, identify Home Assistant entities that can:

* switch operating modes, or
* set power levels / temperature targets

Examples: heat pump climate entities, EV charger switches, SG Ready inputs.

You will map these entities in [Device control](../unwaste-robot-configuration/device/device-control.md).

***

### Entity Naming

Entity names depend on your integrations. Unwaste shows a list of compatible entities when you configure each field.

If an expected sensor does not appear:

* confirm the integration is running in Home Assistant,
* check that the entity reports the correct device class (energy, power, etc.),
* wait for the entity to receive at least one update.

***

### Next Steps

When Home Assistant entities are ready:

1. Complete [Initial configuration](initial-configuration.md) if you have not already.
2. Follow [Designing your electrical installation](../unwaste-robot-configuration/designing-your-electrical-installation.md) to build the installation graph.
3. Map entities on each form (connection, circuit, production, storage, device).

Optional readings and alerts can be added later via [Optional monitoring](../unwaste-robot-configuration/optional-monitoring/) and [Monitoring alerts](../unwaste-robot-configuration/optional-monitoring/monitoring-alerts.md).
