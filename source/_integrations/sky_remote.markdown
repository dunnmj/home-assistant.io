---
title: Sky Remote
description: The Sky Remote integration allows you to control a Sky box with Home Assistant.
ha_category:
  - Remote
ha_release: 2024.12
ha_domain: sky_remote
ha_config_flow: true
ha_codeowners:
  - "@dunnmj"
  - "@saty9"
ha_iot_class: Assumed State
ha_platforms:
  - remote
ha_integration_type: device
related:
  - docs: /docs/configuration/
    title: Configuration file
---

The **Sky Remote** {% term integration %} lets you control a [Sky](https://www.sky.com/) box using Home Assistant.

## Supported models

This integration is intended to control all Sky satellite receiver boxes with a LAN port. It will not control Sky stream pucks.

## Configuration

{% include integrations/config_flow.md %}

{% configuration_basic %}
host:
  description: "Hostname or IP address of your Sky device."
  required: true
  type: string
{% endconfiguration_basic %}

## Remote

The Sky Remote platform will create a [Remote](/integrations/remote/) entity for the device. This entity allows you to send the following commands via the `remote.send_command` action.

`power`

`sky`

`tvguide` `boxoffice` `services` `interactive`

`up` `down` `left` `right`

`select` `backup`

`channelup` `channeldown`

`i` `text` `help`

`red` `green` `yellow` `blue`

`0` `1` `2` `3` `4` `5` `6` `7` `8` `9`

`play` `pause` `stop` `record` `fastforward` `rewind`

`sidebar`
`dismiss`
`search`
`home`

### Action `remote.send_command`

Send a single command or a set of commands to one Sky box.

| Data attribute | Optional | Description                                         |
| ---------------------- | -------- | --------------------------------------------------- |
| `entity_id`            | no       | Entity ID to target.                                |
| `command`              | no       | A single command or a list of commands to send.     |


A typical action for sending several commands looks like this:

```yaml
action: remote.send_command
target:
  entity_id: remote.192_168_1_250
data:
  command:
    - sky
    - tvguide
```

