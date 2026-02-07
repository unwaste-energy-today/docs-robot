# Device control

## "What device control means"

When control is enabled, the **Unwaste Robot sends control signals** to a device. These signals request a specific operating mode.

The Unwaste Robot **does not directly enforce behavior**. It only sends a signal, and the device decides whether and how to follow a signal. Actual behavior depends on device firmware, manufacturer implementation, and installation configuration. Especially:

* the Unwaste Robot does not replace manufacturer safety logic,
* the Unwaste Robot does not override thermostats or vehicle BMS,
* due to these limitations, the Unwaste Robot does not guarantee comfort or readiness.


It operates like this:

* Every 15 minutes, the Unwaste Robot analyzes prices and determines if electricity is cheap or expensive at the moment.
  * For static tariffs (which are usually two-tiered) it simply sets Eco for higher price tier and Comfort for lower price tier, Off and Boost modes are unused
  * For dynamic prices (which vary greatly) it calculates which mode to use (using all four: Off/Eco/Comfort/Boost) with our internal algorithm that ensures there would be at least some hours when energy would be marked as Comfort
* The Unwaste Robot then decides which mode to request to each device, taking into account:
  * electricity price
  * schedule set for this device
  * if there are overrides present
* The Unwaste Robot sends appropriate signal to the device. 
* The device decides how (or if) it reacts. 
* The installation limits what is physically possible - for example, it is not possible to heat whole home or charge a car completely in timespan of couple of minutes.

There is no guaranteed outcome of sending this signal to device, but Unwaste Robot does its best.

Exact outcomes cannot be guaranteed. The Unwaste Robot optimizes based on available information, but final behavior depends on the device.


---

## How device control works

Device control is based on defining **named controllable parameters** and assigning **mode-specific values** for them. The configuration consists of two main steps:


1. **Define controllable parameters** — tell the system what aspects of the device can be controlled and assign a user-friendly name to each.
2. **Assign values for each operating mode** — decide what values each parameter should receive in Eco, Comfort, Boost, and Off.


---

## Enabling Control (prerequisite

Before any parameters or modes can be configured, **control must be enabled** for the device.

Without enabled control, the device remains in *Unmanaged* mode and is only monitored.

When enabling control, you must select the **type of control**:

* "None" - no control is available for this device. This means control is not applicable; it does not count as disabled.
* "State" - device is controlled via setting states for each mode. Control entities must be selected, and finally values must be defined for each entity and for each supported control mode (or disabled for specific modes if required).

The selected control type determines whether the **States Map** section is available for configuration.


Note: "None" and "Disabled" are separate concepts and serve different purposes.

"None" tells us that there is no control available at all, which is useful, as empty "State" form would complain for missing values.

"Disabled" allows to temporarily disable control, without losing all the configuration stored in "State" form.


---

## Step 1: Define controllable parameters

In this step, you define **which parts of the device can be controlled**. Each controllable parameter consists of:

* a **Home Assistant entity** (for example a switch or select entity), and
* a **name** assigned by the user.

The name serves as a reference when assigning values per operating mode. No values are sent to the device in this step; you are only telling the Unwaste Robot what can potentially be controlled.

Think of this as *creating named control channels*.

### Examples of entity types

* **Switch** entities accept simple on/off values.
* **Select** entities allow choosing one value from a predefined list (for example an operating state supported by the device).


---

### **Note: selecting Home Assistant entities**

* The Unwaste Robot integrates with Home Assistant, and the correct entity to use depends on the specific device integration.
* Because entity naming and capabilities vary between manufacturers and integrations, this documentation does not provide a universal "entity selection guide".
* If you are unsure which entity to use, verify in Home Assistant whether it supports the required action (for example switching modes or turning on/off).

**Planned improvement**

* A simplified configuration mechanism for selected supported devices is planned. In most supported cases, users will not need to select entities manually.
* This mechanism is not available in this release.


---

## Step 2: Assign values for each operating mode

After parameters are defined and named, assign **values for each operating mode**:

* Disabled
* Unmanaged
* Off
* Eco
* Comfort
* Boost

For each mode, you must:

* enable or disable the mode (if supported), and
* define what value each control entity receives, or disable specific parameters for that mode.

When a mode becomes active, all enabled control entities for that mode are set simultaneously.

**Important notes about modes:**

* Each state must have **at least one enabled entity** configured.
* If a device does not support a specific mode, approximate configuration may be applied (for example, mapping Boost to Comfort).
* If Eco or Comfort mode is missing, the device may not be smart-grid ready and should be mapped to simple on/off semantics:
  * Disabled, Off and Eco modes should be mapped to Turn Off state 
  * Unmanaged, Comfort and Boost should be mapped to Turn On state


---

## Device Control Modes

A device can operate in one of the following modes:

* **Disabled mode**  – the device is temporarily disabled by user or the Unwaste Robot
* **Unmanaged mode** – the device is not controlled by the Unwaste Robot
* **Off mode** – the device is instructed to turn off or use only the minimum possible energy
* **Eco mode** – the device is instructed to operate in a low energy consumption mode
* **Comfort mode** – the device is allowed to operate with higher energy consumption
* **Boost mode** – the device is instructed to use as much energy as possible, and store it if the device supports for example overheating

## Screenshot

 ![](../.gitbook/assets/Configuration_Device_79c04140-71c0-408e-be9c-ecdaef279a5d_Screenshot_storage_control.png " =770x1008")