# Configuration

## What configuration means in Unwaste

**Configuration** is the process of describing your real electrical installation to the Unwaste system so that the **Unwaste Robot** can correctly:

* understand how energy flows through your installation,
* monitor energy production, consumption, and storage,
* send meaningful control signals to selected devices.

Configuration does **not** change how your electrical installation works physically.\nIt creates a **logical model** that reflects what already exists in reality.

The quality of configuration directly affects:

* correctness of energy calculations,
* accuracy of statistics and savings,
* effectiveness and safety of device control.


---

## How configuration is structured

Configuration in Unwaste is built in **layers**, from the most general to the most specific:


1. **Connection** – your connection to the power grid
2. **Circuits** – how energy flows inside your installation
3. **Energy sources and storage** – where energy is produced or stored
4. **Devices** – what consumes energy and what can be controlled

Each layer depends on the previous one and should be configured in order.


---

## Step 1: Configure the connection

The **connection** represents your physical connection to the power grid.

Here you define:

* number of phases (single-phase or three-phase),
* location (used for forecasts and solar calculations),
* tariff-related information,
* consumption forecast method (required if energy storage is used).

This step establishes the **global context** for all further configuration.

> Note: Most installations have exactly one connection.


---

## Step 2: Define circuits (electrical structure)

**Circuits** describe how energy flows through your installation.

They form a tree structure:

* the **main circuit** represents the entire installation,
* **sub-circuits** represent branches (for example: heating, sockets, EV charger),
* devices and meters are attached to circuits.

Circuits are essential for:

* correct energy flow calculations,
* separating different types of consumption,
* assigning meters, devices, and production sources correctly.

> Important: The main circuit is mandatory.\nOther circuits are optional but strongly recommended.


---

## Step 3: Add energy production and storage

At this stage you describe where energy comes from and where it can be stored.

This may include:

* solar inverters (energy production),
* batteries or other energy storage systems.

Configuration defines:

* how much energy is produced or stored,
* how the Unwaste Robot can read data from these devices,
* whether the Unwaste Robot can send control signals to them.

> Important:\nControl signals are advisory. Devices and inverters may accept, limit, or ignore them based on their own logic and safety rules.


---

## Step 4: Configure devices

A **device** is any appliance that consumes energy.

For each device you decide independently:

* whether it is **monitored** (energy usage is measured),
* whether it is **controlled** (receives Eco / Comfort / Boost / Off signals).

Monitoring and control are separate:

* a device can be controlled without being monitored,
* a device can be monitored without being controlled.

Devices are attached to circuits to ensure their energy usage is counted correctly.


---

## Configuration vs control

Configuration only describes **what exists** and **what is possible**.

Actual behavior (when devices run, which mode is active) is determined later by:

* price-based logic (default),
* profiles,
* schedules,
* overrides.

These mechanisms are described in separate sections of the documentation and build on top of a correct configuration.


---

## Typical configuration workflow

A recommended workflow for a new installation:


1. Configure the **connection**
2. Create the **main circuit**
3. Add important **sub-circuits**
4. Attach **meters** to circuits
5. Configure **production sources** (for example PV)
6. Configure **energy storage** (if present)
7. Add and assign **devices**
8. Enable control where appropriate

You can return to configuration at any time to refine or extend it.


---

## Important notes

* Configuration should reflect the **real physical installation**, not desired behavior.
* Incorrect circuit structure leads to incorrect energy statistics.
* Device control depends on **device capability** and **installation capability**, not only on configuration.
* Some advanced features require additional hardware (meters, buffers, mixing valves).