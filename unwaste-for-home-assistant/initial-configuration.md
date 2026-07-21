---
description: >-
  Complete the first-run setup for your Unwaste Robot and electrical
  installation.
---

# Initial configuration

## Initial configuration

## First Run

After installing and starting the Unwaste Home Assistant application (add-on), open it from the sidebar.

The first time you open Unwaste EMS, an **onboarding wizard** guides you through basic setup.

***

### Onboarding

You will be asked for:

* **Robot name** and optional description
* **Location** (latitude and longitude)
* **Timezone**, **country**, and **currency**
* **Language** and display preferences (for example whether prices include VAT)

These settings are described in [Robot settings](../unwaste-robot-configuration/robot-settings.md).

Accept the terms of use to continue.

***

### After Onboarding

Once onboarding is complete:

1. You enter **Design mode** automatically (or select **Design** from the top navigation).
2. Add your first **connection** and configure tariffs and forecasts. See [Connection](../unwaste-robot-configuration/connection.md).
3. Open the **installation graph** for that connection. The **main circuit** is created automatically — configure energy import (and return, if you have PV). See [Circuit](../unwaste-robot-configuration/circuit.md).
4. Add production, storage, and devices as needed. See [Designing your electrical installation](../unwaste-robot-configuration/designing-your-electrical-installation.md).

Before adding elements in Unwaste, ensure sensors and integrations exist in Home Assistant. See [Connecting devices](connecting-devices.md).

***

### Starting the Robot

Configuration changes are made while the robot is **STOPPED**.

When your installation graph and readings are configured:

1. Review configuration using **reload and validate** if available.
2. **Start** the Unwaste Robot from the system state control.
3. Use the **Dashboard** and operational views to verify data collection.

See [System Operation](../unwaste-robot-operation/system-operation.md).
