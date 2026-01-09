```mermaid
%% Home Assistant Smart Home System Overview

graph TD
    %% Keskus
    HA[Home Assistant VM]:::vm

    %% Host & Virtualization
    Proxmox[Proxmox VE Hypervisor]:::host
    MiniPC[Dedicated Mini PC Host]:::host

    %% Services
    MQTT[MQTT Broker]:::service
    AdBlock[AdGuard]:::service

    %% Devices
    ZigbeeDevices["Zigbee Devices\n(Sensors, Lights)"]:::device
    WifiDevices["Wi-Fi Devices\n(Smart Plugs, Lights, Shelly switches)"]:::device
    RobotVacuum["Robot Vacuum Cleaners"]:::device
    SmartLocks["Smart Locks"]:::device
    Cameras["Cameras & Motion Sensors"]:::device

    %% Automations
    Automations["Automations & Scripts"]:::automation

    %% Connections
    MiniPC --> Proxmox
    Proxmox --> HA
    HA --> MQTT
    HA --> AdBlock

    HA --> ZigbeeDevices
    HA --> WifiDevices
    HA --> RobotVacuum
    HA --> SmartLocks
    HA --> Cameras
    HA --> Automations

    ZigbeeDevices --> HA
    WifiDevices --> HA
    RobotVacuum --> HA
    SmartLocks --> HA
    Cameras --> HA

    Automations --> ZigbeeDevices
    Automations --> WifiDevices
    Automations --> RobotVacuum
    Automations --> SmartLocks
    Automations --> Cameras

    %% Class definitions for colors
    classDef vm fill:#1f77b4,stroke:#000,stroke-width:1px,color:#fff;
    classDef host fill:#2ca02c,stroke:#000,stroke-width:1px,color:#fff;
    classDef service fill:#ff7f0e,stroke:#000,stroke-width:1px,color:#fff;
    classDef device fill:#d62728,stroke:#000,stroke-width:1px,color:#fff;
    classDef automation fill:#9467bd,stroke:#000,stroke-width:1px,color:#fff;
