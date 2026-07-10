# Robot settings

# Global Settings

When you first open the Unwaste EMS after installing the Home Assistant add-on, an **onboarding wizard** collects basic settings for your **Unwaste Robot**.

You can change most of these later under **Settings**.

Typical global settings include:

* **Robot name** — display name in the interface
* **Description** — optional free text
* **Location** — latitude and longitude (used for weather and solar forecasts)
* **Timezone** — local time zone for schedules and tariffs
* **Country** — used when selecting tariffs
* **Currency** — how prices and savings are displayed
* **Language** — interface language
* **Include VAT** — whether prices include value-added tax


---

# Connection Location

The **connection** form also has latitude and longitude fields.

In most installations these match the global robot location. They define the reference point for forecasts tied to that grid connection.


---

# After Onboarding

Once onboarding is complete:

1. Open **Design mode** to build your installation graph.
2. Configure the **connection** (tariffs, forecasts, optional Surplus mode).
3. Set up circuits, production, storage, and devices as described in the Configuration section.

See [Initial configuration](../Installation/Initial%20configuration.md) for the first-run workflow.


---

# Home Assistant Add-on Options

Outside the Unwaste web interface, the add-on has optional settings in Home Assistant:

* **Use external database** — when enabled, connect to an external PostgreSQL/TimescaleDB instead of the built-in database
* **Server address, port, user, password, database name, SSL** — connection details for the external database (only when external database is enabled)

When **Use external database** is off, leave the database fields empty.

See [Local installation](../Installation/Local%20installation.md) for add-on installation steps.

