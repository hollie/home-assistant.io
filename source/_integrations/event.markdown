---
title: Event
description: Instructions on how to use event entities in Home Assistant.
ha_category:
  - Event
ha_release: 2023.8
ha_quality_scale: internal
ha_domain: event
ha_codeowners:
  - '@home-assistant/core'
ha_integration_type: entity
---

Events are signals that are emitted when something happens, for example, when a user presses a physical button like a doorbell or when a button on a remote control is pressed.

These events are stateless. For example, a doorbell does not have a state like being "on" or "off" but instead is momentarily pressed. Some events can have variations in the type of event that is emitted. For example, maybe your remote control is capable of emitting a single press, a double press, or a long press.

The event entity can capture these events in the physical world and makes them available in Home Assistant as an entity.

Please note, the event integration cannot be directly used; you cannot create your own event entities using this integration. This integration is a building block for other integrations to use, enabling them to create event entities for you.

## The state of an event entity

The event entity is stateless, as in, it cannot have a state like the `on` or `off` state that, for example, a normal switch or light entity has.

Therefore, every event entity keeps track of the timestamp when the emitted event has last been detected.

Because the state of an event entity in Home Assistant is a timestamp, it means we can use it in our automations. For example:

```yaml
trigger:
  - platform: state
    entity_id: event.doorbell
action:
  - service: notify.frenck
    data:
      message: "Ding Dong! Someone is at the door!"
```

## Event types

Besides the timestamp of the last event, the event entity also keeps track of the event type that has last been emitted. This can be used in automations to trigger different actions based on the type of event.

This allows you, for example, to trigger a different action when the button on a remote control is pressed once or twice, if your remote control is capable of emitting these different types of events.

When combining that with the [choose action](/docs/scripts/#choose-a-group-of-actions) script, you can assign multiple different actions to a single event entity. In the following example, short- or long-pressing the button on the remote will trigger a different scene:

```yaml
trigger:
  - platform: state
    entity_id: event.hue_remote_control
action:
  - alias: "Choose an action based on the type of event"
    choose:
      - conditions:
        - alias: "Normal evening scene if the button was pressed"
          condition: state
          entity_id: event.hue_remote_control_on_button
          attribute: "event_type"
          state: "short_release"
        sequence:
          - scene: scene.living_room_evening
      - conditions:
        - alias: "Scene for watching a movie if the button was long-pressed"
          condition: state
          entity_id: event.hue_remote_control_on_button
          attribute: "event_type"
          state: "long_release"
        sequence:
          - scene: scene.living_room_movie
```

When creating automations in the automation editor in the UI, the event types are available as a dropdown list, depending on the event entity you are using. This means you don't have to remember the different event types and can easily select them.

## Device classes

The following device classes are supported by event entities:

- **None**: Generic event. This is the default and doesn't need to be set.
- **button**: For remote control buttons.
- **doorbell**: Specifically for buttons that are used as a doorbell.
- **motion**: For motion events detected by a motion sensor.
