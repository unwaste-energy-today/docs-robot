# Glossary

## "Boost" mode (devices)

One of [→ Device operating modes](Glossary.md#h-device-operating-mode)

In this mode, the device is encouraged to use as much energy as possible. This is typically done by storing energy for later use, for example by heating buffers above normal levels, but still within safe limits. This mode is used when energy prices are very low.

Important: Not all devices support "Boost" mode. It is available only on devices designed to store energy for later use, most commonly heat pumps.

***

## Circuit

Represents any part of your electrical installation. A main circuit is always created with a connection and cannot be removed. Sub-circuits may be added. Circuits and sub-circuits are used to model energy flows and attach production, storage, and devices.

When a circuit is connected to energy usage readings from a smart meter, it can be used to visualize energy flow within the installation.

In a local [Unwaste Robot,](Glossary.md#h-unwaste-robot) circuits and sub-circuits can be organized into a hierarchical structure, creating a clear energy flow diagram. The cloud [Unwaste Robot](Glossary.md#h-unwaste-robot) supports only a single main circuit.

***

## "Comfort" mode (devices)

One of [→ Device operating modes](Glossary.md#h-device-operating-mode)

In this mode, the device is allowed to use energy freely. This mode is activated when energy prices are low.

This does not force the device to consume energy; it only signals that energy is currently cheap. Devices that support variable power levels typically interpret this mode as a high or normal operating level (often referred to as "comfort mode").

***

## Connection

Represents a physical connection to the power grid and contains the definition of energy prices for that connection. Important: Prices and operating modes are calculated separately for each connection. Although multiple connections can be added, most installations have only one. Splitting parts of a single local installation into multiple connections is usually counterproductive.

***

## **Control**

see [→Device operating mode](Glossary.md#h-device-operating-mode), [→Storage control mode](Glossary.md#h-storage-control-mode).

The ability of the Unwaste Robot to send operating mode signals to a device or energy storage.

Control is only possible for elements that support and have control configured; otherwise, they remain in monitoring mode.

Control requires:

* device or storage support,
* correct configuration,
* and explicit enabling.

Control does not guarantee device behavior; the device decides how to react.

***

## "Default" mode (storages)

One of [→Storage operating modes](Glossary.md#h-storage-control-mode)

In Default mode, the storage operates according to its own internal rules.

In most cases, this means storing surplus energy from solar production (but not from the grid) and releasing it when needed. Exact behavior may vary depending on the storage device.

Please refer to your storage documentation and configuration for details.

***

## Design mode

see [→Design dashboard](Glossary.md#h-design-dashboard), [→Installation graph](Glossary.md#h-installation-graph)

A user interface mode in the Unwaste EMS where the structure of an electrical installation is created and modified. In Design mode, you add and organize connections, circuits, production sources, storage, and devices.

***

## Design dashboard

The main view within Design mode where all existing connections are listed and where new installations can be created. From the Design dashboard, you can enter the installation graph for each connection.

***

## Device

Any device connected to the [Unwaste Robot](Glossary.md#h-unwaste-robot) (either via cloud or locally) that can be monitored and managed.

Examples include electric vehicles, heat pumps, air conditioning units, and other compatible devices.

***

## Device control algorithm

Devices are managed by selecting a device operating mode every 15 minutes.

The algorithm works as follows:

* First, the current energy price is evaluated and a corresponding operating mode is selected.
* Next, any applicable schedule rules are checked. If present, they override the price-based mode.
* Finally, overrides are checked. Overrides take precedence over both schedules and price-based rules.

The resulting mode is then applied to the device.

***

## Device operating mode

A control signal sent by the Unwaste Robot, one of:

[→ "Unmanaged" mode ](Glossary.md#h-unmanaged-mode-devices-and-storages)[→ "Off" mode ](Glossary.md#h-off-mode-devices)[→ "Eco" mode ](Glossary.md#h-eco-mode-devices)[→ "Comfort" mode ](Glossary.md#h-comfort-mode-devices)[→ "Boost" mode](Glossary.md#h-boost-mode-devices)

Devices interpret these signals according to their capabilities and configuration.

Important notes:

**Note 1.** Not all devices support all modes. "Boost" mode is particularly rare. Devices with only ON/OFF control should map:

* "Off" and "Eco" → OFF
* "Comfort" and "Boost" → ON

**Note 2.** These modes are signals sent to devices. Each device ultimately decides whether and how to respond.

***

## "Eco" mode (devices)

One of [→ Device operating modes](Glossary.md#h-device-operating-mode)

In this mode, the device limits its energy usage. It is activated when energy prices are high.

Devices capable of operating at different power levels typically interpret this mode as a low-power or energy-saving state. For example, heat pumps, refrigerators, or air conditioning systems may continue operating at a reduced level to maintain temperature.

***

## Energy tariffs

Energy prices are one of the most important elements of the system. For each [→Connection](Glossary.md#h-connection), at least the following price must be defined:

* energy price – the cost of electricity purchased from the grid
* distribution price (optional) – used if distribution costs are not included in the energy price
* return price (optional) – the price paid for electricity exported back to the grid

Each price type can be:

* **dynamic** – directly linked to energy markets and may change every 15 minutes
* **static** – changes according to a predefined schedule
* **custom** – similar to static, but defined locally instead of downloaded from the cloud

For static and custom tariffs, only "Eco" and "Comfort" modes are used:

* prices equal to or below the daily average → "Comfort"
* prices above the daily average → "Eco"

***

## Energy usage forecast

Energy usage forecast consists of methods that estimate how much energy will be consumed each day.

Available methods:

* **daily average** – averages energy usage over the last 14 days
* **day-of-week average** – averages usage for the same weekday over the last 4 weeks
* (more methods to come)

Energy usage forecast is required for storage control. See [→Storage control algorithm](Glossary.md#h-storage-control-algorithm).

***

## "Force charge" mode (storages)

One of [→Storage operating modes](Glossary.md#h-storage-control-mode)

"Force charge" mode instructs the storage to charge from the grid when energy prices are low and an energy shortage is forecasted for the day.

For details, see [→Storage control algorithm](Glossary.md#h-storage-control-algorithm).

***

## **Installation**

A logical representation of a physical energy system configured in Unwaste.

An installation consists of one or more connections and their associated circuits, devices, production sources, and energy storage.

***

## **Installation graph**

see [→Connection](Glossary.md#h-connection), [→Circuit](Glossary.md#h-circuit), [→Device](Glossary.md#h-device), [→Production](Glossary.md#h-production), [→Storage](Glossary.md#h-storage)

A visual, tree-like representation of an electrical installation showing the hierarchical relationship between elements such as connections, circuits, production sources, energy storage, and devices. It reflects how energy flows and how elements are structurally organized for monitoring and control.

***

## Managed element

see [→Device](Glossary.md#h-storage), [→Storage](Glossary.md#h-device), [→Control](Glossary.md#h-control)

Any device or energy storage that is configured for control and can receive operating mode signals from the Unwaste Robot. Managed elements must be correctly configured in Home Assistant and support control actions to participate in optimization.

***

## Monitoring

The process of reading and reporting energy or power values from devices, circuits, or other elements without influencing their behavior. Monitoring provides insight into energy usage, production, and storage status.

***

## "Off" mode (devices)

One of [→ Device operating modes](Glossary.md#h-device-operating-mode)

Off mode means the device is instructed to stop normal operation to reduce energy usage when prices are high.

This does not always mean the device is completely powered off. For example, for heat pumps, "Off" typically means an anti-frost or protection mode.

***

## Override

An override forces a device to operate in a selected [→Device operating mode](Glossary.md#h-device-operating-mode) for a specific time period.

Overrides:

* are device-specific
* cannot be shared
* are not repeatable

Overrides have the highest priority and override both schedules and price-based rules.

Important: If multiple overrides overlap, the last override in the list takes precedence.

***

## Production

Any electricity-producing unit, including (but not limited to) solar panels, wind turbines, or generators.

The only requirement is that the [Unwaste Robot](Glossary.md#h-unwaste-robot) can read its data.

***

## Profile

A profile represents a predefined set of rules for common usage patterns.

Typical examples include:

* **default** – normal workday behavior
* **weekend** – adjusted rules for weekends
* **vacation** – minimal energy usage when nobody is present

Profiles can be freely defined as needed. There must always be at least one "default" profile.

Each device can have a separate [→schedule](Glossary.md#h-schedule) for each profile.

***

## Savings

Generating savings on your electricity bill is the main goal of the [Unwaste Robot](Glossary.md#h-unwaste-robot).

Unwaste calculates savings in three categories:

### 1. Self-use savings

Savings generated when solar energy is used immediately instead of being exported to the grid.

Unwaste increases these savings by scheduling devices to operate when local production is high.

Savings are calculated by valuing self-used energy at the current energy price.

***

### 2. Storage savings

Savings generated by storing surplus energy and using it later when prices are higher.

Calculated by multiplying the amount of energy taken from storage by the energy price at the time of use.

***

### 3. Unwaste savings

**Unwaste Robot control savings** (called **"Unwasted"** in the interface) – estimated savings from running controllable devices during cheaper energy periods; estimated because the system cannot know how the device would behave without control.

They are divided into:

* **device savings** – comparison between actual cost and average daily energy price
* **storage savings** – comparison between actual storage cost and average daily price

***

Important notes:

**Note 1.** Schedules and overrides may reduce optimal savings by limiting automatic optimization.

**Note 2.** The [Unwaste Robot](Glossary.md#h-unwaste-robot) only sends price-based signals. Final decisions are made by devices themselves, especially temperature-controlled devices such as heat pumps or air conditioning systems.

***

## Schedule

A schedule is a set of rules that override default device behavior (see [→Device control algorithm](Glossary.md#h-device-control-algorithm)).

Each rule defines:

* when it applies
* which [→Device operating mode](Glossary.md#h-device-operating-mode) is used

Each device can have one schedule per [→Profile](Glossary.md#h-profile).

Schedules define **when** operating modes are requested, but do not override device capability or safety logic.

***

## Solar production forecast

The system uses solar production forecasts compatible with Home Assistant's Energy Dashboard.

Common options include:

* **Forecast.Solar** – free, built into Home Assistant, lower accuracy
* **Open-Meteo Solar Forecast** – free, higher accuracy
* **Solcast** – highest accuracy, requires a paid API key

***

## Storage

An energy storage system that improves efficiency by storing surplus energy and releasing it when needed.

Both standalone storages and storages integrated with hybrid inverters are supported, provided the [Unwaste Robot](Glossary.md#h-unwaste-robot) can read and control them.

***

## Storage control algorithm

Storages are managed differently than devices.

The [Unwaste Robot](Glossary.md#h-unwaste-robot) may charge storage from the grid only when:

* energy prices are low, and
* solar production is forecasted to be insufficient

Prerequisites:

* storage supports [→"Force charge" mode](Glossary.md#h-force-charge-mode-storages)
* [→Solar production forecast](Glossary.md#h-solar-production-forecast) configured
* [→Energy usage forecast](Glossary.md#h-energy-usage-forecast) configured

The [Unwaste Robot](Glossary.md#h-unwaste-robot) checks:

* remaining forecasted production (RPr)
* remaining forecasted usage (RUs)
* available energy in storage (EAv)

If `RUs > (RPr + EAv)` and energy is cheap, "Force charge" mode is activated.

***

## Storage control mode

Possible storage states:

[→ "Unmanaged" mode ](Glossary.md#h-unmanaged-mode-devices-and-storages)[→ "Default mode" ](Glossary.md#h-default-mode-storages)[→ "Force charge"](Glossary.md#h-force-charge-mode-storages)

More modes may be added in the future.

Important: Many storages do not support any control beyond Default mode.

***

## Storage energy levels

Each storage defines:

* **total capacity** – theoretical maximum capacity
* **reserved capacity** – minimum energy that must remain to protect storage health

From these values, the system distinguishes:

* **energy in storage** – raw reading
* **available energy in storage** – energy minus reserved capacity

Important: If a storage already subtracts reserved capacity internally, configure total capacity accordingly and set reserved capacity to zero.

***

## Robot

See [→ Unwaste Robot](Glossary.md#h-unwaste-robot)

***

## "Unmanaged" mode (devices and storages)

One of [→ Device operating modes ](Glossary.md#h-device-operating-mode)and [→Storage operating modes](Glossary.md#h-storage-control-mode)

In this mode, the device or storage is not managed by the [Unwaste Robot](Glossary.md#h-unwaste-robot) and operates according to its own rules.

***

## Unwaste OS

An operating system built to provide a secure environment for Unwaste Robot.

It supports reliable updates and configuration of the robot's operating environment.

## Unwaste Robot

An entity that manages energy usage within the Unwaste EMS and aims to maximize savings.

Two types are available:

* **cloud robot** – no hardware required, suitable for small installations
* **local robot** – on-site hardware with extended capabilities for full installations
