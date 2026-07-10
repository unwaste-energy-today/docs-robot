# Other devices

# Other device types

## Configuration

The **Generic** device type is used when no dedicated device type matches your appliance. Other types such as Fridge, Freezer, Dish Washer, Wash Machine, and Cloth Dryer use the same form layout as Generic.


---

### Energy consumed

Optional. Select one to three Home Assistant entities representing total energy consumption.

For a three-phase device, you can provide:

* one sensor for summed energy (leaving the rest empty) - it must be specified in the L1 field
* three sensors, each corresponding to one phase - L1, L2, L3.

For a single-phase device in a three-phase installation, only one field is used. It should correspond to the phase of the circuit the device is connected to.


---

### Energy return

Optional. Select one to three Home Assistant entities representing energy exported from the device (if applicable).

The same L1 / L2 / L3 rules apply as for Energy consumed.


---

### Power flow

Optional. Instantaneous power is configured in **Optional monitoring**. See [Optional monitoring](../Optional%20monitoring.md).


---

## Control

Control configuration is identical to other devices. See [Device control](Device%20control.md).

**Important**

* Generic and similar device types have no subtype-specific behaviour beyond readings and control.
* All control logic relies on modes calculated by the Unwaste Robot and configured entities and States Map values.


---

# Screenshot

 ![](../.gitbook/assets/2026-07-10_Configuration_device_generic.png " =811x655")

