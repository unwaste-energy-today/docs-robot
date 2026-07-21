# Installation

## Option 1 (Part of Home Assistant)

This document describes installation of the **Unwaste EMS Home Assistant application (add-on)**.

Unwaste OS and other deployment options are not covered here.

#### System Requirements

* Home Assistant with Supervisor (Home Assistant OS or supervised installation)
* aarch64 or x86\_64 architecture
* Minimum 2 GB RAM recommended
* Network connectivity

See [Hardware requirements](hardware-requirements.md) for details.

***

### Installation Steps

1. **Install the add-on** — Follow [Local installation](local-installation.md).
2. **Initial configuration** — Complete onboarding and [Robot settings](<../Configuration/Robot settings.md>). See [Initial configuration](initial-configuration.md).
3. **Connect devices in Home Assistant** — Integrate meters and controllable devices before configuring Unwaste. See [Connecting devices](connecting-devices.md).
4. **Configure the installation** — Use Design mode to build your installation graph. See [Configuration](../Configuration.md).

***

### Post-Installation

After the add-on is running:

1. Finish onboarding (robot name, location, timezone, tariffs).
2. Open **Design mode** and configure your connection, circuits, production, storage, and devices.
3. **Start** the Unwaste Robot when configuration is complete to begin data collection and control.

See [System Operation](<../System Operation.md>) for starting and stopping the robot.

## Option 2 for Pro users (Part of Unwaste OS)

This option installs Unwaste Robot on a dedicated Unwaste OS system.

Unwaste OS is prepared specifically to run Unwaste Robot. It provides a more secure and reliable deployment than a general-purpose operating system.

This installation method is intended for professional users.
