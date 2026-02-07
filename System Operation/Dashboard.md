# Dashboard

### What the Dashboard is

The Dashboard provides a daily summary of system performance.

Each **connection** is presented as a separate block because connections may differ in:

* tariffs and pricing currency,
* consumption model and forecasting,
* production and storage setup.

For this reason, some metrics (especially percentages) are not safely "summable" across connections.

 ![](../.gitbook/assets/System Operation_f51c7be0-4ad2-4dda-bd4c-29422befb411_Screenshot_dashboard.png " =862x515")


---

### Dashboard metrics

All Dashboard metrics show **today's totals** (midnight to now), but only for periods when the system was **STARTED**.

**Note: STARTED vs STOPPED**\nIf the Unwaste Robot was **STOPPED** for part of today, the Dashboard totals include only the time when it was **STARTED**. Time spent STOPPED is not recorded and cannot be reconstructed later.\nSee **System operation → Starting and stopping the Unwaste Robot**.


Per connection, the Dashboard shows:

* **Produced (Wh, kWh)**\nTotal electrical energy produced locally (for example, by a PV inverter) since midnight.
* **Used (Wh, kWh)**\nShows the **total energy consumed** since midnight **by all devices in the installation**.

  This value represents the sum of energy used by all loads, **regardless of the energy source**. It includes energy drawn from the power grid, produced by solar panels, or supplied from an energy storage
* **Self Sufficiency (%)**\nHow much of the consumed energy was covered by local production (directly or indirectly).\nThis uses standard industry definitions. For precise computation, see *Inner workings → Self-use calculation*.
* **Self Use (%)**\nHow much of produced energy was used locally instead of being exported.\nThis uses standard industry definitions. For precise computation, see *Inner workings → Self-use calculation*.
* **Energy Price (currency)**\nThe **current tariff price** for the connection.\nThe displayed currency symbol is taken from connection configuration.\n**Important:** The system does not perform currency conversion. Having tariffs in different currencies is not supported.
* **Unwasted (currency)**\nTotal monetary value of savings attributed to the Unwaste Robot.\nSee *Inner workings → Savings calculation*.

### Alerts

The Dashboard includes an **Alerts panel** for abnormal situations that the user should be informed about.

 ![](../.gitbook/assets/System Operation_b6d9ec2a-5e4d-4388-add6-229ed3d3d601_Screenshot_dashboard_alerts.png " =837x675")

 ![](../.gitbook/assets/System Operation_ca4ef992-87b5-4061-8c98-9dbabe5e2371_Screenshot_Alert.png " =2028x240")



---

#### What alerts are

Alerts represent operational issues such as:

* failure to read from a device (missing sensor data),
* failure to set an operating mode on a controlled device,
* data failure (impossible or abnormal readings),
* internet connection failures,
* failures when reading **dynamic tariffs** (important because pricing directly affects cost optimisation).

Alerts are meant to be actionable: they indicate that a part of the system may not be working correctly, or that optimisation decisions may be less accurate.


---

#### Aggregation and muting

To avoid repeated spam-like notifications:

* Alerts are **aggregated**:
  * repeated occurrences of the same alert type are grouped,
  * the system reports the situation without producing a large number of identical messages.
* Alerts can be **muted**:
  * a muted alert does not generate a notification,
  * it can still remain visible in the list for review.

**Note:**\nA future mobile application may deliver alerts as **push notifications**.


---

### Details button

The **DETAILS** button opens the detailed views for the selected connection (starting with **Energy Usage**).