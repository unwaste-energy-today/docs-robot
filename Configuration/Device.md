# Device

# Device

## What is a device

A **device** in Unwaste EMS is any electrical appliance that consumes energy to perform work.

Devices are the main objects that the **Unwaste Robot** can:

* **monitor** (observe energy usage), and/or
* **control** (send operating mode signals).

Monitoring and control are **independent** capabilities:

* A device may be monitored without being controlled.
* A device may be controlled even if no energy readings are available.

In practice, not all devices provide built-in energy consumption readings. If monitoring is required, this can often be added by installing an external smart meter on the device's circuit or wall socket.

Control is also optional and depends on both device and installation capabilities.

### Which devices should be controlled

Devices best suited for control are:

* **Smart-grid ready devices**, which expose predefined operating modes (for example Off / Eco / Comfort / Boost).
* **Time-agnostic devices**, which can operate at any time and do not require immediate availability.

Devices that **should not be controlled** include those that:

* must always be ready for immediate use, or
* must operate at strictly defined times.

Controlling such devices may lead to situations where the device is unavailable when urgently needed.


---

## Device types

Unwaste EMS supports multiple device types. Some types belong to a dedicated **heating subtype**, which has additional configuration options.

When adding a device to the installation graph, you can choose:

* **Generic**
* **EV Charger**
* **Air Conditioner**
* **Fridge**
* **Freezer**
* **Dish Washer**
* **Wash Machine**
* **Cloth Dryer**
* **Heat Pump** (heating subtype)
* **Heating** (heating subtype — other electric heating)
* **DHW Heater** (heating subtype)

All devices share the same control logic. Differences between types relate mainly to available readings and additional configuration sections.

Choosing an incorrect device type does not damage the system, but may limit optimization or disable subtype-specific features.


## Optional entities

Many devices have only optional entities. Leaving optional sections empty is safe. The device will still appear in the system and can be monitored or controlled later.

Especially, monitoring and control of the devices are independent of each other.

* you can configure only control, and leave all optional entries blank - the device will be controlled normally but not monitored,
* you can configure only monitoring options (all or some), but not control - the Unwaste Robot will monitor configured parameters on the device, but will not control it
* you can configure both of these - and it will be both controlled and monitored

Optional monitoring and additional readings are described in [Optional monitoring](Optional%20monitoring.md) and [Additional readings](Additional%20readings.md).

## Screenshot (device type selection)

 ![](../.gitbook/assets/2026-07-10_Configuration_adding_new_device_select_type.png " =821x400")
