# Introduction

## System Architecture

Unwaste EMS is built around a unique architecture designed to combine local reliability with cloud convenience.

### The Local Robot Concept

The **Unwaste Robot** is the on-site controller for your energy infrastructure. It monitors and controls devices directly on your local network. Deploy it at a home, business, or facility using supported [hardware](../unwaste-for-home-assistant/hardware-requirements.md) running [Home Assistant](../unwaste-for-home-assistant/software-requirements.md) or using Unwaste OS.

The **Unwaste Robot** is the core controller of Unwaste EMS. It runs locally, close to your energy infrastructure. It monitors and controls devices directly.

The Local Robot operates on-site at your home, business, or facility. It runs within Home Assistant or on Unwaste OS. See [Installation options](../getting-started/installation-options.md) for details.

The Local Robot is available through your local LAN. Connect it to [Unwaste Cloud](https://app.gitbook.com/s/Wf3M0a04WuhvfEbAgXFl/unwaste-cloud) to manage multiple Unwaste Robots from anywhere. Use the [web portal](https://cloud.unwaste.energy/) or mobile app.

**Key advantages of local operation:**

* **Responsive control** — Decisions remain local and avoid internet latency.
* **Privacy and security** — Energy data stays on your premises.
* **Independent operation** — The system continues during internet outages.
* **Direct device control** — The robot communicates through the local network.

### Local-First with Cloud Enhancement

The Unwaste Local Robot can **operate independently** without cloud connectivity. Core functionality works locally:

* Energy monitoring and flow calculations
* Device control and optimization
* Storage management
* Historical data and statistics
* Custom tariff-based optimization (manually configured)

{% hint style="info" %}
**Note:** Some features require connection to Unwaste Cloud services, including energy tariffs (both static and dynamic). Without cloud connectivity, you can only use manually configured custom tariffs.
{% endhint %}

**Cloud connectivity adds valuable features:**

While the Local Robot works standalone, connecting to **Unwaste Cloud** unlocks additional capabilities:

* **Automatic tariff updates** - Dynamic and static energy prices downloaded automatically from our API
* **Remote access** - Control and monitor your installation from anywhere in the world
* **Multi-installation management** - Manage multiple Local Robots from a single account
* **Access sharing** - Grant temporary access to installers or family members
* **Future enhancements** - Advanced analytics, forecasting, and optimization features

Learn more about cloud benefits in [Cloud Account Benefits](../unwaste-cloud/benefits-of-cloud-account.md).

## Getting Started

To begin using Unwaste EMS:

1. Review [System editions and licensing models](<System editions and licensing models.md>) to understand your options
2. Check [Installation options](../getting-started/installation-options.md)
3. Review software and hardware requirements
4. Follow the installation guide
5. Complete [Configuration](../unwaste-robot-configuration/designing-your-electrical-installation.md) of your electrical installation
6. Optionally, connect to [Unwaste Cloud](../unwaste-cloud/web-interface/creating-account-in-unwaste-cloud.md) for enhanced features

The modular design means you can start with basic local operation and expand capabilities as your needs grow.
