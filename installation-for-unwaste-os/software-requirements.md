# Software requirements

## Overview

Unwaste EMS runs as an add-on within Home Assistant. Before installing Unwaste EMS, you must have a working Home Assistant installation.

## Required Software

### Home Assistant

**Minimum Version:** Home Assistant 2024.1 or newer

**Recommended Installation Method:**

* **Home Assistant Operating System (HAOS)** - Provides the easiest setup, automatic updates, and most reliable experience

**Alternative Installation Methods:**

* Home Assistant Container (Docker)
* Home Assistant Core (Python virtual environment)
* Home Assistant Supervised

{% hint style="warning" %}
While all installation methods are supported, **Home Assistant Operating System (HAOS)** is strongly recommended for production use. Other methods require more technical knowledge and manual maintenance.
{% endhint %}

## Virtualization Support

Home Assistant (and therefore Unwaste EMS) can run in virtualized environments. Supported hypervisors include:

* **Proxmox VE** - Popular choice for home labs and small businesses
* **VMware ESXi / vSphere** - Enterprise virtualization platform
* **Microsoft Hyper-V** - Windows Server virtualization
* **VirtualBox** - Desktop virtualization (testing only, not recommended for production)
* **KVM/QEMU** - Linux native virtualization

{% hint style="info" %}
Virtualized installations require the host system to meet or exceed the recommended hardware specifications. Ensure adequate CPU, memory, and storage resources are allocated to the virtual machine.
{% endhint %}

### Virtualization Best Practices

* Allocate at least 2 CPU cores and 4GB RAM to the Home Assistant VM
* Use SSD storage for the virtual disk
* Enable CPU passthrough if available
* Configure network bridge for stable connectivity
* Set VM to auto-start with the host system

## Additional Software Components

### Required Home Assistant Integrations

Unwaste EMS requires certain Home Assistant integrations to function:

* **Energy Dashboard** - For energy flow visualization
* **Device integrations** - Specific to your controllable devices (e.g., Modbus, MQTT, proprietary integrations)

### Optional but Recommended

* **Forecast.Solar** or **Solcast** - For solar production forecasting
* **Open-Meteo** - For weather data and energy predictions
* **InfluxDB / Grafana** (optional) - For advanced data analysis and custom dashboards

## Internet Connectivity

{% hint style="info" %}
**Internet connection is required** for:

* Downloading Unwaste EMS updates
* Accessing dynamic energy price data
* Solar and weather forecasting
* Remote access (if Cloud Account is used)
{% endhint %}

Local operation continues even if internet connection is temporarily lost, but features requiring real-time data (price updates, forecasts) will be unavailable during outages.

## Browser Requirements

For accessing the Home Assistant and Unwaste EMS web interface:

* **Modern web browser** - Chrome, Firefox, Safari, or Edge (latest versions)
* **JavaScript enabled**
* **Minimum screen resolution:** 1280x720 (1920x1080 recommended for optimal experience)

## Updates and Maintenance

* **Home Assistant updates:** Follow Home Assistant's update schedule
* **Unwaste EMS updates:** Delivered through Home Assistant's add-on system
* **Backup strategy:** Regular backups recommended (Home Assistant includes built-in backup features)

***

With proper software configuration, Unwaste EMS seamlessly integrates with your Home Assistant installation to provide intelligent energy management capabilities.
