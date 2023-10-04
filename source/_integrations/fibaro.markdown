---
title: Fibaro
description: Instructions on how to setup Fibaro Home Center and Yubii Home within Home Assistant.
ha_category:
  - Binary Sensor
  - Climate
  - Cover
  - Hub
  - Light
  - Lock
  - Scene
  - Sensor
  - Switch
ha_release: 0.83
ha_iot_class: Local Push
ha_domain: fibaro
ha_platforms:
  - binary_sensor
  - climate
  - cover
  - light
  - lock
  - scene
  - sensor
  - switch
ha_codeowners:
  - '@rappenze'
ha_config_flow: true
ha_integration_type: hub
---

The Fibaro integration allows you to connect Home Assistant to a Fibaro Home Center or a Yubii Home hub so that you can control and monitor the connected devices and run scenes. Home Assistant uses a local connection to connect to the Fibaro hub.

## Supported hub models

Fibaro Home Center 2, Home Center Lite, Home Center 3, Home Center 3 Lite, and Yubii Home.

## Features

1. Control devices connected to the hub and synchronize the state of the devices (see platforms for supported devices and capabilities).
2. Entities are automatically added when configuring the Fibaro integration and upon restart of Home Assistant when changed in the Fibaro hub.
3. Support for multiple hubs.
4. Activate scenes defined in the Fibaro hub.

{% include integrations/config_flow.md %} 

<div class='note'>

It is recommended to assign a static IP address to your Fibaro controller. This ensures that it won't change its IP address, so you won't have to change the `url` if the controller reboots and comes up with a different IP address. See your router's manual for details on how to set this up. If you need the MAC address of your Fibaro, check the label on the bottom.

</div>

## Supported platforms

- Binary Sensor
- Climate
- Cover
- Light
- Lock
- Scene
- Sensor
- Switch
