---
description: >-
  Configure energy storage systems for monitoring and optional automated
  control.
---

# Storage

## Storage

## What Is an Energy Storage?

An energy storage is any device designed to store electrical energy.

The main role of a storage is to improve overall system efficiency by storing surplus energy and releasing it later when energy is needed.

Both standalone storage systems and storages integrated with hybrid inverters are supported, provided the Unwaste Robot can read their data and control their operating modes.

***

## Configuration

Configuring an energy storage requires mapping Home Assistant sensors to capacity, energy counters, and optional control entities. The form is the same for all supported battery types.

***

### Name and Description

**Name** is required. **Description** is optional.

***

### Capacity Total

**Mandatory.** Defines the total capacity of the energy storage.

Available options:

* **Constant Energy** – enter a fixed capacity value in kWh
* **Reading Energy** – select a Home Assistant entity from which the total capacity is read, for batteries that have dynamic or configurable capacity.

***

### Capacity Reserved

**Mandatory.** Defines the portion of capacity that must always remain unused to protect the storage from degradation (see _Storage energy levels_ in Notes).

Available options:

* **Constant Energy** – fixed reserved capacity in kWh
* **Constant Percent** – reserved capacity as a percentage of total capacity
* **Reading Energy** – Home Assistant entity providing reserved capacity in kWh, for batteries that have dynamic or configurable capacity.
* **Reading Percent** – Home Assistant entity providing reserved capacity as a percentage, for batteries that have dynamic or configurable capacity.

**Important:** Incorrect configuration may prevent charging or discharging.

***

### Energy Stored

**Mandatory.** Defines one or three Home Assistant entities (depending on storage type) used to read how much energy has been stored.

For a three-phase storage, you can provide:

* one sensor for summed energy (leaving the rest empty) - it must be specified in the L1 field
* three sensors, each corresponding to one phase - L1, L2, L3.

For a single-phase storage in a three-phase installation, only one field is used. It should correspond to the phase of the circuit the storage is connected to.

It is not the same as charge level. Energy stored represents the total amount of energy charged into the storage over a longer period of time (across multiple charging cycles).

Charge level is current value of energy stored in storage.

Each reading block has a **Monitoring alerts** button. See [Monitoring alerts](optional-monitoring/monitoring-alerts.md).

***

### Energy Retrieved

**Mandatory.** Defines one or three Home Assistant entities (depending on storage type) used to read how much energy has been retrieved from the storage.

For a three-phase storage, you can provide:

* one sensor for summed energy (leaving the rest empty) - it must be specified in the L1 field
* three sensors, each corresponding to one phase - L1, L2, L3.

For a single-phase storage in a three-phase installation, only one field is used. It should correspond to the phase of the circuit the storage is connected to.

Energy retrieved represents the total amount of energy retrieved from the storage over a longer period of time (across multiple discharging cycles).

***

### Power Charge

**Optional.** Defines one to three entities used to read the current charging power.

For a three-phase storage, you can provide:

* one sensor for summed power (leaving the rest empty) - it must be specified in the L1 field
* three sensors, each corresponding to one phase - L1, L2, L3.

For a single-phase storage in a three-phase installation, only one field is used. It should correspond to the phase of the circuit the storage is connected to.

***

### Power Discharge

**Optional.** Defines one to three entities used to read the current discharging power.

For a three-phase storage, you can provide:

* one sensor for summed power (leaving the rest empty) - it must be specified in the L1 field
* three sensors, each corresponding to one phase - L1, L2, L3.

For a single-phase storage in a three-phase installation, only one field is used. It should correspond to the phase of the circuit the storage is connected to.

***

### Charge Level

Defines the entity used to read the current charge level of the storage.

The charge level can be provided as:

* "None" - no charge level reading available
* "Energy" - an **energy value** (kWh), or
* "Percent" - a **percentage value**

See _Storage energy levels_ in Notes for details.

Charge level is optional, but it is needed to properly control a storage when the Unwaste Robot manages charging from the grid.

It is not always equal to total energy stored minus total energy retrieved, as all storages experience some energy loss.

***

### Control

***

### Enabling Control

To allow the Unwaste Robot to control a storage, control must first be enabled.

Without enabled control, the storage is only monitored and it would remain in "Unmanaged" mode.

Next, you need to select type of control:

* "None" - no control available. It is like a disabled control, but not the same.
* "State" - storage is controlled via setting states for each mode. Control entities must be selected, and finally values must be defined for each entity and for each supported control mode (or disabled for specific modes if required).

The selected control type determines whether the **States Map** section is available for configuration.

Note: "None" and "Disabled" are separate concepts and serve different purposes.

"None" means that there is no control available at all.

"Disabled" allows to temporarily disable control, without losing all the configuration stored in "State" form.

***

### Selecting Entities

The first step is selecting which Home Assistant entities are used to control the storage.

Supported control entity types include **Switch**, **Select**, and **Number** entities.

***

#### Switch Entities

Switch entities accept a simple on/off (true/false) value, similar to a light switch.

***

#### Select Entities

Select entities allows choosing one value from a predefined list, for example selecting an operating mode supported by the device.

***

### Storage Control Modes

A storage can operate in one of the following modes:

* **Disabled mode** – the storage is temporarily disabled by user or the Unwaste Robot
* **Unmanaged mode** – the storage is not controlled by the Unwaste Robot
* **Default mode** – the storage follows its internal logic - used when the storage is managed, but there is no need for any action.
* **Force charge** – the storage is instructed to charge from the grid
* **Force discharge** – the storage is instructed to discharge to the grid
* **Lock discharge** – the storage is told to not discharge
* **Lock both** – the storage is told to not charge or discharge

Enable only the modes your storage hardware supports. For modes you do not use, leave them disabled in the States Map.

***

### Selecting Values for Each Mode

Each control mode can be configured independently. For each mode we are setting a "state" - that is a collection of values for each control entity. When a mode becomes active, all enabled control entities for that mode are set simultaneously.

For each mode:

* enable or disable the mode using the switch next to its name (if available)
* define what value should be set to each control entity, or disable a specific entity for that mode

Note: Each state must have at least one entity enabled.

Note 2: (important) If a storage doesn't support selected mode, it applies **Default mode** instead.

***

### Optional Monitoring

Optional voltage, current, power, and additional sensors are configured in the **Optional monitoring** section. See [Optional monitoring](optional-monitoring/) and [Additional readings](optional-monitoring/additional-readings.md).

***

## Important Notes

***

### Storage Energy Levels

Each storage defines two capacity values:

* **total capacity** – the theoretical maximum energy the storage can hold
* **reserved capacity** – the minimum energy level that must remain to protect storage health

Based on these values, the system distinguishes:

* **energy in storage** – the raw reported energy value
* **available energy in storage** – energy in storage minus reserved capacity

Important: If a storage device already subtracts the reserved capacity internally, configure the total capacity accordingly and set reserved capacity to zero.

### Power flow

#### Typical case

Separate power charge and power discharge parameters are the most common way in storages to determine total power flow, as these are intuitive to configure and unambiguous. The system uses the difference between them to present total power flow of a storage on a graph.

#### Ambiguous devices

But there are storages that supply only one value, and what is even worse, it does not always follow the same convention of direction of power flow.

In such cases, total power flow should be entered into one of these fields (leaving second one blank), and if the direction is incorrect on the graph, then you need to swap these fields.

Single phase readings for these parameters shouldn't be mixed with three phase readings.

## Screenshot (main form)

![](../.gitbook/assets/2026-07-10_Configuration_storage.png)

## Screenshot (control / States Map)

![](../.gitbook/assets/2026-07-10_Configuration_storage_control.png)
