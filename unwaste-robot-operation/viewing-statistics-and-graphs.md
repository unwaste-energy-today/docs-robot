---
description: Explore historical statistics, graphs, and energy performance data.
---

# Viewing statistics and graphs

### How to open graphs

Graphs are opened using the **Statistics** button available on most components.

![](../.gitbook/assets/System Operation_bd89b27c-16e5-4ba4-ab56-8e8d444c417e_Screenshot_stats_button.png " =200x195")

**Important:** Statistics are available for all components except **connections**, because a connection does not have its own direct readings. Readings are taken from the **main circuit**.

***

### Detailed view

The **Detailed view** lets you choose which data series to display as graphs.

![](../.gitbook/assets/2026-07-10_Operation_graphs_initial.png)

Use the **Today** and **Historical** tabs to switch time range.

In the **Select data** field, pick one or more metrics. Available options depend on what readings are configured for that element (including [Optional monitoring](../unwaste-robot-configuration/optional-monitoring/) and [Additional readings](../unwaste-robot-configuration/optional-monitoring/additional-readings.md)).

![](../.gitbook/assets/2026-07-10_Operation_graphs_selection.png)

Examples include total energy production, energy usage, average voltage on a phase, and other aggregated series.

![](../.gitbook/assets/2026-07-10_Operation_graphs_viewing.png)

***

### What graphs can show

The set of available graphs depends on:

* the type of object (device vs storage vs inverter vs circuit),
* and the readings configured for that object.

In general:

* each configured reading can have its own graph,
* some calculated values may also have graphs.

***

### Today and Historical graphs

For Energy Usage and Power Flow statistics:

* "Today" uses 15-minute aggregated periods.
* "Historical" also uses 15-minute periods but allows selecting a single past day.
* If the system was STOPPED for part of a day, those periods appear as **zero** values to keep the timeline continuous.

**Note:** STOPPED periods appear as zeros in "Today" and "Historical" graphs to keep the timeline continuous. This does not mean "zero consumption", it means the system was not collecting data. See **System operation → Starting and stopping the Unwaste Robot**.

***

### Aggregated Energy graphs and grouping

In Aggregated Energy statistics:

* the time range is inherited from the selected date span in the Aggregated Energy view,
* the user can change the grouping interval:
  * 1 hour, 2 hours, 4 hours, 6 hours, 12 hours, 1 day.

![](../.gitbook/assets/System Operation_7ada579a-de8f-41ce-a4ac-ba259d8b257e_Screenshot_graphs_for_aggregated.png " =1240x608")

***

### Important limitations

* All graphs show **aggregated values**, never raw 5-second samples.
* The system collects 5-second readings, but stores only 15-minute (or higher) aggregates for history.
