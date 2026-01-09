# Home Assistant Smart Home – Documentation

This repository documents my personal Home Assistant smart home system.
The system is designed with a strong focus on local-only control, security and reliability.

All core automations run locally without cloud dependency.
External cloud services are used only when explicitly required and never for critical functionality.

See examples/automation_example.yaml for a sample automation.

## System Overview

The system is hosted on a dedicated mini PC running Proxmox VE.
Home Assistant runs as a virtualized service, allowing separation of concerns,
easy backups and future scalability.

### Infrastructure

- **Host:** Mini PC
- **Hypervisor:** Proxmox VE
- **Home Assistant:** Virtual Machine running HAOS
- **Storage:** Local SSD and NAS 
- **Networking:** Bridged networking

## Technologies

### Platform & Infrastructure
- Home Assistant
- Proxmox VE

### Communication & Protocols
- MQTT
- Zigbee
- Wi-Fi
- REST APIs

### Configuration
- YAML

## Key Features
- Smart heating control and scheduling
- Smart locks and access control
- Camera surveillance and motion detection
- Real-time electricity and energy consumption monitoring
- Smart lighting (scenes, schedules and adaptive lighting)
- Presence-based automations
- Robot vacuum cleaners integration and automation
- Security alerts and notifications
- Network-wide ad blocking


## Lessons Learned
- Local-first architecture significantly improves reliability and privacy
- Virtualization makes backups, testing and recovery straightforward
- Clear separation of services reduces maintenance effort

