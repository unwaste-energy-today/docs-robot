---
description: Create profiles that define device behavior for different usage scenarios.
---

# Profiles

## Profiles

## What is a profile

A profile is a way to group different schedules into a kind of "meta-mode" for your installation.

You can think about profiles as a way to change many schedules at once.

## Where to look for profiles

Profiles are accessible through settings link in UI, they have a separate tab.

![](../.gitbook/assets/Profiles, schedules and overrides_d077d93e-9add-4299-8db5-98a85b6f6bd6_Screenshot_lista_profili.png " =758x319")

## Managing profiles

Profiles are simple entities, consisting of name and description only.

You can add, edit and delete them (with one exception as needed - default profile cannot be deleted).

Important! For a profile to have any effect, you need also to attach schedules to devices for this profile (see Attaching schedules part of Schedules section). A profile alone does not control devices; it only serves to group schedules.

## Changing active profile

On the same tab you can select Active profile in the bar above list.

Changing active profile makes Unwaste Robot to look at different schedules (attached to this new profile) at the nearest moment when device modes will be calculated.

So, profile itself changes immediately, but effects of this change will manifest at the nearest full quarter of a hour.

### **Important notes.**

* A profile does not control any device on its own.
* If no schedules are assigned to a profile, switching to it may have no effect, or may disable schedules previously attached.
* For timing details, see _Timing behavior_ in the introduction.
