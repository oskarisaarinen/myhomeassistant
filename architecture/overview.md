# System Overview

This document provides a detailed overview of my Home Assistant smart home system,
its architecture, and the key components that make it work reliably and securely.

---

## 1. Architecture Summary

The system is designed with **local-first automation, security, and maintainability** in mind.
Home Assistant runs as a virtual machine on a Proxmox hypervisor hosted on a dedicated mini PC.
This setup allows isolation of services, easy snapshots, and flexible future expansion.

Key design principles:

- **Local-only control:** Core automations run without cloud dependency.
- **Security-first:** No public exposure of critical services.
- **Scalable architecture:** New devices and services can be added without disrupting the system.

---

## 2. System Components

### Host & Virtualization
- **Mini PC**: dedicated host for all smart home services
- **Proxmox VE**: hypervisor managing virtual machines
- **HAOS VM**: Home Assistant operating system, fully isolated from host

### Communication & Protocols
- **MQTT**: primary messaging protocol for devices
- **Zigbee**: for sensors, switches, lights
- **Wi-Fi**: for devices that do not support Zigbee
- **REST APIs**: for integration with cloud or local services when required

### Core Integrations & Services
- **Heating & Climate Control:** Smart thermostat automations
- **Lighting:** Scenes, schedules, adaptive lighting
- **Presence Detection:** Device trackers, occupancy-based automations
- **Security:** Smart locks, cameras, motion alerts
- **Robot Vacuums:** Scheduled and presence-aware cleaning
- **Energy Monitoring:** Real-time electricity consumption tracking
- **Network-wide Ad Blocking:** DNS-level filtering for all connected devices

---

## 3. Data Flow & Interaction

Below is a simplified flow of how the system components interact:

```mermaid
graph TD
    User --> HA[Home Assistant VM]
    HA --> Devices[Smart Devices]
    HA --> Automations[Automations & Scripts]
    Devices --> HA
    HA --> MQTTBroker[MQTT Broker]
    HA --> AdBlock[Network-wide Ad Blocking]

