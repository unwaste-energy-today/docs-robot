---
description: Review Unwaste OS software, virtualization, network, and browser requirements.
---

# Software requirements

## Bare metal

Unwaste OS runs directly on physical hardware. This is the recommended deployment method.

Running on bare metal avoids virtualization overhead and resource contention. It provides more predictable performance and higher reliability.

Energy infrastructure control may require near-real-time behavior. A dedicated system helps maintain responsive and consistent operation.

## Virtualization Support

Unwaste Robot can run in virtualized environments. Supported hypervisors include:

* **Proxmox VE** - Popular choice for home labs and small businesses
* **VMware ESXi / vSphere** - Enterprise virtualization platform
* **Microsoft Hyper-V** - Windows Server virtualization
* **VirtualBox** - Desktop virtualization (testing only, not recommended for production)
* **KVM/QEMU** - Linux native virtualization

{% hint style="info" %}
Virtualized installations require the host system to meet or exceed the recommended hardware specifications. Ensure adequate CPU, memory, and storage resources are allocated to the virtual machine.
{% endhint %}

### Virtualization Best Practices

* Allocate at least 2 CPU cores and 4GB RAM&#x20;
* Use SSD storage for the virtual disk
* Enable CPU passthrough if available
* Configure network bridge for stable connectivity
* Set VM to auto-start with the host system

## Internet Connectivity

{% hint style="info" %}
**Internet connection is required** for:

* Downloading Unwaste Robot updates
* Accessing dynamic energy price data
* Solar and weather forecasting
* Remote access (if Unwaste Cloud is used)
{% endhint %}

Unwaste Robot is designed to continue operating during a temporary internet outage. The outage does not interrupt local control.

However, weather forecasts and dynamic energy prices are unavailable without internet access. Their absence can affect system decisions and energy optimization.

## Browser Requirements

For accessing the Unwaste Robot web interface:

* **Modern web browser** - Chrome, Firefox, Safari, or Edge (latest versions)
* **JavaScript enabled**
* **Minimum screen resolution:** 1280x720 (1920x1080 recommended for optimal experience)

## Updates and Maintenance

* **Unwaste Robot updates:** Delivered through web management interface
* **Backup strategy:** Regular backups recommended
