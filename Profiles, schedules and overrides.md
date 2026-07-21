---
description: Understand how profiles, schedules, and overrides control device behavior.
---

# Device control introduction

## Profiles, schedules and overrides

## A bit of introduction

### How the Unwaste Robot controls devices

Price-based control is the **default control mechanism** used by the Unwaste Robot.

Every device that is set to **managed** is automatically controlled based on energy prices. The Unwaste Robot continuously evaluates whether energy is cheap or expensive and sends corresponding control signals to managed devices.

This default behavior applies to **all managed devices** unless it is modified by additional mechanisms described later in this article, such as profiles, schedules, overrides, or **Surplus mode** on the connection (for PV surplus — see [Connection](Configuration/Connection.md#surplus-mode)).

**Example**

If a user has a **two-zone electricity tariff** (for example, cheaper energy at night and more expensive during the day) and sets a device to **autoManage**, the device will **immediately start receiving control signals based on those prices**.

No additional configuration is required. The Unwaste Robot will automatically treat the low-price zone as "energy is cheap" and the high-price zone as "energy is expensive", and control the device accordingly.

### Use cases that need change of default behaviour

How to resolve situations when you know in advance that there is no need of heating home because all your family goes on the two week vacation? Or, that everyone will be outside home (in work for example) in every workday 8 am to 4pm and there is no need for air conditioning to run, despite energy being cheap in the middle of the day?

Or another example, you have just returned in a almost discharged car and need to charge it right now, not waiting for cheap electricity, because you know that in three hours you need to drive again?

These two types of situations:

* repeatable ones, that you know about in advance
* immediate ones, when you need to act "now"

need a method to address them, to change behaviour of the Unwaste Robot.

## Methods of changing default behaviour

There are two mechanisms to adjust default behavior: **repeatable adjustments** using profiles and schedules, and **immediate adjustments** using overrides.

For repeatable situations we give you a robust system of **profiles and scheduling**, allowing you to plan repeatable "exceptions" to the normal rules.

For immediate situations there is also a mechanism of **overrides**, which allows to set any mode you choose directly to the device for a given time.

### Priorities

These methods are not exclusive - you can use both schedule and override in the same device, with clear method of determining priority:

* Overrides have the highest priority. if there is an override active, it takes priority above any other option. If many override rules are active, the last one takes priority.
* Schedules are second on the priority list. If there is a schedule set for a device, and any rule matches current time, it is used. If many rules match, the last one is used.
* Default operation mode — the mode automatically determined by the Unwaste Robot based on electricity prices, and optionally **Surplus** when Surplus mode is enabled on the connection and export/import conditions are met. It is lowest on the priority list, and used only when there is no active override or schedule.

So, making it a short rule of thumb: \nOverrides > Schedules > Default (price + surplus)

### Timing behavior

These methods can behave quite differently when you look at expected moment the rules take effect, because **most of changes are not immediate**.

These changes take effect at the start of next control interval, that is, next full quarter of an hour (for example, making change at 10:02, takes effect only on 10:15):

* changing active profile
* editing a profile that is attached to current active profile
* attaching or detaching a profile to/from current active profile

These changes don't take effect until active profile is changed to relevant profile and next control interval starts:

* editing a schedule not attached to active profile
* attaching / detaching a schedule to/from not active profile

Overrides behave quite differently - they start:

* immediately - when defined without start date and time. **It is the only change that takes effect immediately**.
* at planned point in the future - when defined with start date and time set

### You are in control

These methods give you a full freedom of setting how devices would be controlled and responding to random events.

### A little warning about savings

There is one risk related to these mechanisms.

The Unwaste Robot can only generate savings when it has free hand at setting modes to the devices. When you force some modes via schedules or overrides, you in some situations can limit possibility to generate savings.

Some rules help generate savings (for example setting all devices to Eco or even Off for vacation), while others may derail savings completely - for example setting heating to Comfort in the exact hours when electricity is expensive.
