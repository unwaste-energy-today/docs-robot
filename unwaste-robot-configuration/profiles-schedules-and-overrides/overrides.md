---
description: Temporarily force a selected operating mode for an individual device.
---

# Overrides

## Overrides

## What is an override

An override is a way for you to force a device to work in any mode you want for a set period of time.

Overrides are intended for exceptional or temporary situations, not for regular daily control.

For example, it allows you to:

* force an unused device to Off for some time
* force charging a car (despite prices being high) whenever you cannot wait for it to charge when the prices would be low
* force a heat pump to operate in Comfort mode regardless of electricity prices.

When active, this replaces the automatic price-based decision for that period of time and any schedule set for this device.

Overrides > Schedules > Default (price based)

### Important notes

* Setting a mode to a device is only a signal for the device, and device itself decides if it obeys this signal. Internal logic of the devices may result in not changing mode as you request.

## **Timing behavior**

* Overrides are evaluated immediately after being created or modified.
* If an override has a defined start or end time, it becomes active or inactive at the next system evaluation interval.
* While an override is active, it always takes priority over schedules and default behavior.
* When an override ends, control automatically returns to schedules or default behavior.
* For more timing details, see _Timing behavior_ in the introduction.

_Note:_ Overrides do not permanently change schedules or profiles.

## Main differences between scheduling and overrides

### Overrides are one-device only

You cannot set the same override to many devices. They are not meant to be management tool for whole installation, but a method of controlling one device when necessary.

### Overrides are not repeating themselves

Overrides are set to a specific, period of time, and after this period passes, they are discarded, as they're not useful anymore.

### Overrides may work instantly

When you set an override rule, that covers this moment in time, it is applied **immediately.**

This is in contrast to schedules which are applied only at the beginning of a new control period (next full quarter of an hour)

Override rules that are designated in the future, start to be applied in planned time.

## Where to find overrides

Like schedules, overrides can be found on Schedules and Overrides tab accessible from a little panel under the box representing device.

![](../.gitbook/assets/Profiles, schedules and overrides_681a395b-7b97-46bc-a781-44c7cc3dc567_Screenshot_how_to_find_schedules.png " =208x174")

## Setting overrides

To add an override you simply add another rule on list of overrides set for a device.

### Rules

To define an override rule, you need to use "add" button on overrides list, then you have to define:

* From Date - date and time when the rule should start to be in force. It is optional parameter, leaving it empty means that this rule should be applied immediately.
* To Date - date and time and stop time when the rule should start to be in force. It is optional parameter, leaving it empty means that this rule should continue to be applied indefinitely, until it will be deleted.
* a mode - for this override to set on device.

#### Rules precedence

Similar to schedules, You can define many rules and you can freely change rules order (by dragging them up and down the list using 6-dot marker to the left of Mode).

Ordering of rules is important, because rules are evaluated in the order shown in the list. If multiple rules match, the one defined last in the list is applied.

You can think of it like the further up the list the rule is positioned, the more general rule it is, and the lower - the more specific, like an exception from the above rules. That's why the last matching rule is taken as **the most important**.

#### Example

![](../.gitbook/assets/Profiles, schedules and overrides_7888b8e1-4a60-4e0c-9f59-db6315445573_Screenshot_device_schedule_and_override.png " =1235x459")
