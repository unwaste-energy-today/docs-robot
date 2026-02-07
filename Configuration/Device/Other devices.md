# Other devices

# Other device types

## Configuration

Other device types are configured the same way as generic device (which are used when no dedicated device type exists).


---

### Energy consumed

Optional. Select one to three Home Assistant entities representing total energy consumption.

For a three-phase device, you can provide:

* one sensor for summed energy (leaving the rest empty) - it must be specified in the L1 field
* three sensors, each corresponding to one phase - L1, L2, L3.

For a single-phase device in a three-phase installation, only one field is used. It should correspond to the phase of the circuit the device is connected to.


---

### Power flow

Optional. Select one to three Home Assistant entities representing instantaneous charging power.

For a three-phase device, you can provide:

* one sensor for summed power (leaving the rest empty) - it must be specified in the L1 field
* three sensors, each corresponding to one phase - L1, L2, L3.

For a single-phase device in a three-phase installation, only one field is used. It should correspond to the phase of the circuit the device is connected to.


---

## Control

Control configuration is identical to other devices.

**Important**

* All device types other than EV chargers and heating devices have no subtype-specific behavior.
* All control logic relies solely on modes calculated by the Unwaste Robot and configured entities and modes.


---

# Screenshot

 ![](../.gitbook/assets/Configuration_Device_c6d52989-b2c8-46ea-b381-8663b290121a_Screenshot_Generic.png " =811x655")