# Introduction

## System Architecture

Unwaste EMS is built around a unique architecture designed to combine local reliability with cloud convenience.

### The Local Robot Concept

At the heart of Unwaste EMS is the **Unwaste Local Robot** - a controller that runs close to your energy infrastructure, directly monitoring and controlling your devices. The Local Robot operates on-site (at your home, business, or facility) using hardware that meets our [hardware requirements](Installation/Hardware%20requirements.md) and runs on [Home Assistant](Installation/Software%20requirements.md).

**Key advantages of local operation:**

* **Real-time responsiveness** - Control decisions are made locally without depending on internet latency
* **Privacy and security** - Your energy data stays on your premises
* **Independent operation** - The system continues working even during internet outages
* **Direct device control** - Communicates directly with your devices through the local network

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

Learn more about cloud benefits in [Cloud Account Benefits](../Cloud%20Account/Benefits%20of%20Cloud%20Account.md).

## Getting Started

To begin using Unwaste EMS:

1. Review [System editions and licensing models](System%20editions%20and%20licensing%20models.md) to understand your options
2. Check [Hardware Requirements](../Installation/Hardware%20requirements.md) to choose your platform
3. Review [Software Requirements](../Installation/Software%20requirements.md) for Home Assistant setup
4. Follow the [Installation](../Installation/Local%20installation.md) guide
5. Complete [Configuration](../Configuration/Designing%20your%20electrical%20installation.md) of your electrical installation
6. Optionally, connect to [Unwaste Cloud](../Cloud%20Account/Creating%20account%20in%20Unwaste%20Cloud.md) for enhanced features

The modular design means you can start with basic local operation and expand capabilities as your needs grow.
