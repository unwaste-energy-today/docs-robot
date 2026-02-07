# Determining what controls a device

# Why it is needed

Sometimes it might be needed to determine what element is now in force (that is, if the mode is determined by schedules or overrides or by default mechanism.

That's why we show this information directly in dashboard, because it could be useful for "debugging" your installation, where this rule comes from. 

It is only a way to see this information, you cannot change it here.

# Devices

In dashboard, on the graph, each device is labeled with two important pieces of information:

* what mode it operates on
* what is the source of this mode


Mode, as usual, takes one of these values:

* Disabled
* Unmanaged
* Off
* Eco
* Comfort
* Boost

Mode source can take one of three possible values:

* Tariff - that means the algorithm determined this mode looking at the price of electricity
* Schedule - that means a schedule has determined this mode
* Override - that means that override forced this mode

Unmanaged indicates the device is not under tariff, schedule, or override control.

Mode source is not shown for Disabled or Unmanaged modes.

## Examples for devices

It can look like in these examples of the same device:

 ![](../.gitbook/assets/Profiles, schedules and overrides_2bea1b35-535b-4922-a269-7e69a30af326_Screenshot_tryby.png " =853x127")

# Storages

Storages are controlled by quite different algorithm, so they don't have a mode source parameter - they show only their current mode, and it is one of valid storage operating modes:

* Disabled
* Unmanaged
* Default
* Force charge


\

\