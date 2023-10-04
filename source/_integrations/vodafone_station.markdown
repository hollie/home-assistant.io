---
title: Vodafone Station
description: Instructions on how to integrate Vodafone Station routers into Home Assistant.
ha_category:
  - Presence Detection
ha_release: 2023.9
ha_domain: vodafone_station
ha_config_flow: true
ha_codeowners:
  - '@paoloantinori'
  - '@chemelli74'
ha_iot_class: Local Polling
ha_platforms:
  - device_tracker
ha_integration_type: integration
---

The Vodafone Station integration allows you to control your [Vodafone Station](https://www.vodafone.it/privati/area-supporto/assistenza-dispositivi/vodafone-station.html) based router.

There is support for the following platform types within Home Assistant:

- **Device tracker** - presence detection by looking at connected devices.
{% include integrations/config_flow.md %}

## Configuration

The configuration in the UI asks for a a few information: host, username, password and SSL.
Depending on the model of the router, the login URL can be based on http:// or https://.
The default username is `vodafone`.


## Integration options

It is possible to change some behaviors through the integration options.
To change the settings, go to {% my integrations title="**Settings** > **Devices & Services**" %}. On the **Vodafone Station** integration, select the cogwheel. Then select **Configure**.

- **Consider home**: Number of seconds that must elapse before considering a disconnected device "not at home".

## Additional info

### Device Tracker

**Note**: If you don't want to automatically track newly detected devices, disable the integration system option `Enable new added entities`.


### Tested models

This integartion was tested against the following models:

  - Vodafone Power Station 
  - Vodafone WiFi 6 Station
