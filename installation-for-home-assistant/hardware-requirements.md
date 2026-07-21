---
description: >-
  Review supported hardware and recommended specifications for Home Assistant
  deployments.
---

# Hardware requirements

## Overview

Unwaste EMS operates as an add-on to Home Assistant, leveraging its robust platform for device integration and automation. The hardware requirements below ensure reliable, 24/7 operation of both Home Assistant and the Unwaste Robot.

## Hardware Options

You have two options for running Unwaste EMS:

### Option 1: Our Tested and Recommended Hardware - reComputer R1125-10

**reComputer R1125-10** - Our officially recommended and tested platform

{% hint style="success" %}
The **reComputer R1125-10** is tested and validated in our laboratory with Unwaste EMS software. This device is based on Raspberry Pi Compute Module 4 (CM4) and provides a reliable, production-ready solution.
{% endhint %}

**Why choose reComputer R1125-10:**

* Tested and validated with Unwaste EMS in our lab
* Industrial-grade reliability with metal case and efficient cooling
* Built-in eMMC or NVMe storage (no microSD card issues)
* Multiple connectivity options (Ethernet, Wi-Fi, USB)
* Expandable with additional I/O interfaces
* Production-ready out of the box

If you want a hassle-free setup with hardware we know works perfectly with our software, the reComputer R1125-10 is the best choice.

### Option 2: Use Your Own Hardware

You can run Unwaste EMS on your own hardware with Home Assistant already installed, provided it meets the requirements specified below. This gives you flexibility to use existing equipment or choose your preferred platform.

## Minimum Hardware Requirements

To run Home Assistant with Unwaste EMS, your system must meet these minimum specifications:

* **Processor (CPU):** 1.5 GHz single-core processor (64-bit required)
* **RAM:** 2 GB minimum (4 GB or more recommended)
* **Storage:** 16 GB or more (SSD strongly recommended for reliability and speed)
* **Network:** Ethernet connection (recommended for stability) or reliable Wi-Fi
* **System Type:** UEFI boot capability (for x86-64 systems)

{% hint style="warning" %}
While these minimum specifications will work, they may result in slower performance during peak operations or when managing many devices.
{% endhint %}

## Recommended Hardware (2025-2026 Standards)

For optimal performance and long-term reliability, we recommend:

### Recommended Platforms

If using your own hardware (Option 2), we recommend:

**Primary Recommendations:**

* **Raspberry Pi 4** (4GB RAM model) or **Raspberry Pi 5**
* Devices based on **Compute Module 4 (CM4)** or **Compute Module 5 (CM5)**

**Alternative Options:**

* **Mini PC** - Intel NUC, Dell Wyse 5070, or similar
* **Processor** - Intel Celeron, i3, or i5
* **RAM** - 4GB minimum, 8GB preferred

### Storage Recommendations

* **Capacity:** 128 GB or larger
* **Type:** NVMe or SATA SSD
* **Important:** SSD is strongly preferred over microSD cards to prevent database corruption and system failures

### Power Supply

* **For Raspberry Pi:** High-quality 5V/3A power supply (official Raspberry Pi power supply recommended)
* **For other systems:** Stable power supply with UPS backup recommended for critical installations

### Network Connection

* **Ethernet** (strongly recommended for stability and reliability)
* **Wi-Fi** - Acceptable for simple installations, but may cause connection issues in complex setups

## Key Considerations

### Storage Media Warning

{% hint style="danger" %}
**Avoid low-quality microSD cards for production use.** They frequently fail under the constant read/write operations required by the Home Assistant database. Use an SSD whenever possible.
{% endhint %}

### Power Consumption

For 24/7 operation, consider systems with:

* **Idle power consumption:** Less than 15W
* **Raspberry Pi 4/5:** Excellent choice for low power consumption (typically 5-8W under normal load)

### Reliability Factors

* **Temperature:** Ensure adequate cooling and ventilation
* **SD card vs SSD:** SSDs provide significantly better reliability and performance
* **Network stability:** Wired Ethernet eliminates Wi-Fi-related connection drops
* **Power stability:** UPS recommended to prevent corruption during power outages

## Enterprise and Industrial Installations

For mission-critical industrial or business environments where continuous operation is essential, we recommend enterprise-grade hardware:

### High-Availability Server Infrastructure

{% hint style="info" %}
For large-scale industrial facilities, commercial buildings, or business environments where system downtime is unacceptable, consider deploying Unwaste EMS on enterprise-grade server hardware.
{% endhint %}

**Recommended Enterprise Features:**

* **Redundant Power Supplies** - Dual or multiple power supplies ensure operation continues even if one fails
* **RAID Storage** - RAID 1 (mirroring) or RAID 10 for data redundancy and protection against disk failure
* **ECC Memory** - Error-correcting code memory for improved data integrity
* **Hot-swappable Components** - Replace failed components without system shutdown
* **Enterprise-grade Network** - Redundant network interfaces with failover capability
* **Hardware Monitoring** - IPMI/iLO/iDRAC for remote management and health monitoring
* **Backup Power** - UPS with sufficient capacity for extended operation and graceful shutdown

### Platform Options for Enterprise

* **Dell PowerEdge** servers (R340, R440, or similar)
* **HPE ProLiant** servers (DL20, DL360, or similar)
* **Lenovo ThinkSystem** servers
* **Virtualized infrastructure** on VMware vSphere, Proxmox VE, or Microsoft Hyper-V with high-availability clustering

### When to Choose Enterprise Hardware

Consider enterprise-grade infrastructure when:

* Managing energy systems for industrial facilities with 24/7 operations
* Controlling critical infrastructure where downtime impacts production
* Operating in environments requiring compliance with uptime SLAs
* Managing multiple installations from a centralized location
* Integration with existing enterprise IT infrastructure is required

Enterprise deployments typically use virtualization with clustering and live migration capabilities to ensure zero-downtime maintenance and automatic failover in case of hardware failure.

## Safety and Reliability First

We recognize that energy is a critical, essential resource for your home, business, or industrial facility. The security and uninterrupted availability of your energy management system is paramount.

**Unwaste EMS is fundamentally built with safety and reliability as core principles:**

* **Safe by design** - The system is designed to never compromise the safety of your electrical installation
* **Fail-safe operation** - If the Unwaste Robot becomes unavailable, your devices continue operating safely using their built-in controls
* **Advisory control** - All control signals are advisory; final decisions remain with individual devices and their safety systems
* **Continuous monitoring** - Real-time validation of system health and data integrity
* **Graceful degradation** - System continues operating with reduced functionality if components fail

The hardware requirements outlined in this document ensure that your Unwaste EMS installation operates reliably 24/7, providing consistent energy optimization while maintaining the safety and security your critical energy infrastructure demands.
