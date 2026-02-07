# Inner Workings

**What is "Inner workings"**

* This section explains how the Unwaste Robot calculates energy flows, costs, savings, and how it stores and interprets time-based data.
* It is primarily useful for advanced users, installers, and troubleshooting.

**How to use this section**

* If you only want to configure your system, you can skip this section.
* If your charts or power flow views look inconsistent, start here to understand what the system can and cannot infer.

**What is covered (short summaries + links)**

* **Time model and data storage**: how time intervals are handled; what gaps mean.
* **Energy flow calculation and balancing**: how the system balances measured flows into a consistent picture.
* **Electrical network calculations**: how circuits and phases influence computed flows.
* **Self-use calculation**: how local production consumption is estimated.
* **Savings calculation**: how tariffs and measured flows become savings numbers.
* **What the Unwaste Robot does not know**: explicit limits and assumptions.

**Notes / Important**

* Important: These calculations depend on sensor availability and installation topology. Incorrect meter placement or missing measurements can produce misleading results.This section explains how Unwaste derives energy flows, self-use, and savings from raw readings.\nIt is intended for users who want deeper understanding or need to validate results.