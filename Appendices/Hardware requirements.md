# Hardware requirements

## Home Assistant add-on (supported installation)

This document describes hardware requirements for the **Unwaste EMS Home Assistant add-on** — the supported installation path described in [Installation](../Installation.md).

### Minimum requirements

* **Host:** Home Assistant with Supervisor (Home Assistant OS or supervised installation)
* **Architecture:** aarch64 or x86_64
* **RAM:** 2 GB minimum recommended for the host running Home Assistant and the add-on
* **Storage:** Sufficient free space on the host for Home Assistant, the add-on, and the built-in database (exact needs depend on retention and installation size)
* **Network:** Network connectivity for Home Assistant and, when used, Unwaste Cloud (tariffs, dynamic prices)

### Recommended

* **RAM:** 4 GB or more on the host if Home Assistant runs many integrations alongside Unwaste
* **Storage:** SSD-based storage on the host for smoother database performance
* **Network:** Stable Ethernet connection to the local network

See [Local installation](../Installation/Local%20installation.md) for add-on setup steps.

---

## Other deployment options

Requirements for **Unwaste OS** and other deployment models are not covered in this manual until those options are generally available. See [Cloud deployment](../Installation/Cloud%20deployment.md).
