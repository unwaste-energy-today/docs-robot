---
description: Understand the electrical network calculations used by Unwaste EMS.
---

# Electrical Network Calculations

## Electrical Network Calculations

### Assumptions

* Electrical network calculations are performed **per connection**. Connections are separate from each other (there should be no energy flows between connections) and are often geographically separated, so they are a sensible boundary for both calculations and database partitioning.
* For a given connection, the electrical installation is modeled as a **tree of circuits**.
* Circuits can be **metered** or **unmetered**:
  * A **metered circuit** has its own energy meter and can calculate both **total consumption** and **residual consumption**.
  * An **unmetered circuit** has no meter. It cannot measure bidirectional energy flow, so its `energyImported` / `energyReturned` must be handled by assumptions described below.
* In the current model, the system **does not track phases** (L1/L2/L3) for calculations. If values are collected per phase, they are summed into a single value.

***

### Elements in the circuit tree

#### Circuit

A circuit is the structural element of the tree. A circuit can have **child circuits** and can also have leaf elements connected directly under it (production, storage, devices).

**Metered circuit readings**

A **metered circuit** provides two energy readings (as shown in the diagram):

* `energyImported` \[Wh] — energy entering this circuit from its parent circuit
* `energyReturned` \[Wh] — energy flowing from this circuit back to its parent circuit

These two values are read **directly from this circuit's own meter**.

**Unmetered circuit assumptions**

An **unmetered circuit** has no meter, so the system cannot measure how much energy flowed in both directions.

For unmetered circuits the model assumes:

* `energyReturned = 0`
* `energyImported = energyUsedChildren`

This means: an unmetered circuit is treated as if all energy needed by its children is "imported" from the parent, and none is "returned" upward (because it cannot be measured).

`energyUsedChildren` for a circuit is defined in the calculation section below.

***

#### Production

Production is an element connected under a circuit (a leaf element). It represents any source that injects energy into the installation, for example solar PV inverters or wind turbines.

Production provides:

* `energyProduced` \[Wh] — total energy generated

(Use `energyProduced` consistently; avoid `energyProduction`.)

***

#### Storage

Storage is an element connected under a circuit (a leaf element). It represents a device that can both absorb and return electrical energy (currently: a battery).

Storage provides:

* `energyStored` \[Wh] — energy charged into storage
* `energyRetrieved` \[Wh] — energy discharged from storage
* `chargeLevel` \[%] — state of charge
* `freeStorage` \[Wh] — remaining "free space", calculated from `chargeLevel` and configured storage capacity

***

#### Devices

Devices are elements connected under a circuit (leaf elements). They represent controllable loads (execution units).

A device may provide:

* `energyConsumption` \[Wh] — device energy use

***

## Calculations for a single circuit

This section explains how calculations are performed **for one circuit**, and how child circuits affect the result.

A key rule used throughout:

* When a circuit needs a "sum below it", it sums only its **direct children** (child circuits and directly connected leaf elements).\nValues for deeper levels are already included inside each child circuit's totals.

***

### Step 1: Calculate `energyUsedChildren` for a circuit

For each circuit, define:

`energyUsedChildren = (sum of energyUsedChildren of all child circuits) + (sum of energyConsumption of devices connected directly to this circuit)`

Notes:

* **Child circuits** contribute via their `energyUsedTotal` (their own subtree totals).
* **Devices connected directly** to this circuit contribute via their `energyConsumption`.
* Production and storage are _not_ part of `energyUsedChildren` directly, because they affect the energy balance via `energyProduced`, `energyStored`, and `energyRetrieved` in Step 2.

This definition is also what an **unmetered circuit** uses as its assumed import:

* `energyImported = energyUsedChildren`
* `energyReturned = 0`

***

### Step 2: Calculate subtree totals for production and storage

For a circuit, define these subtree totals as sums of **direct children**:

* `energyProduced` = sum of `energyProduced` from:
  * production elements connected directly to this circuit, and
  * child circuits' own `energyProduced` totals (already including their deeper levels)
* `energyStored` = sum of `energyStored` from:
  * storage elements connected directly to this circuit, and
  * child circuits' `energyStored` totals
* `energyRetrieved` = sum of `energyRetrieved` from:
  * storage elements connected directly to this circuit, and
  * child circuits' `energyRetrieved` totals

This matches the idea in the diagram: production and retrieved energy "flow into" the circuit balance, while stored and returned energy "flow out".

Important clarification:

* `energyImported` and `energyReturned` are **never summed from child circuits**. They are **meter readings (or assumptions) for the circuit being calculated**.

***

### Step 3: Total energy consumption for a circuit (`energyUsedTotal`)

![](<../.gitbook/assets/Inner Workings_9d18a379-deff-4f9c-849c-9060c5912e2c_węzeł.png>)

Based on the **law of conservation of energy**, the total energy flowing **into** a circuit (from import, local production, and storage discharge) must equal the total energy flowing **out of** that circuit (to export/return, storage charging) plus the energy **consumed** within the circuit and its subtree—so the circuit energy balance can be written as an 'inflows − outflows = consumption' equation.

`energyConsumption = energyImported + energyProduced + energyRetrieved - energyReturned - energyStored`

Where:

* `energyImported`, `energyReturned` are:
  * **meter readings** for metered circuits, or
  * **assumed values** for unmetered circuits (as described above).
* `energyProduced`, `energyRetrieved`, `energyStored` are the **subtree totals** computed in Step 2.

***

### Step 4: Residual consumption for a metered circuit (`energyUsedThisLevel`)

Residual consumption means: consumption that happens "at this circuit level", that is **not separately metered** in any part below it.

For a **metered circuit**:

`energyUsedThisLevel = energyUsedTotal - energyUsedChildren`

![](<../.gitbook/assets/Inner Workings_2947b528-b993-4138-a023-4bb51941d03a_węzeł2.png>)

Explanation (diagram):

* `energyUsedTotal` covers the full subtree.
* If child circuits exist, their `energyUsedTotal` represents consumption that can be attributed to those child branches.
* What remains is the residual consumption for this circuit level (`energyUsedThisLevel`).

By definition, if a metered circuit has no child circuits:

* `energyUsedThisLevel == energyUsedTotal`

For an **unmetered circuit**, `energyUsedThisLevel` is typically not meaningful in the same way, because it has no own meter-based balance. In this model, residual consumption is primarily a feature of **metered circuits**.
