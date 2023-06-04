<img src="https://github.com/geertmeersman/robonect/raw/main/images/brand/logo.png"
     alt="Robonect"
     align="right"
     style="width: 200px;margin-right: 10px;" />

# Robonect for Home Assistant

A Home Assistant integration to monitor Robonect

### Features

- MQTT listener
- REST API client
- All Robonect sensors (if MQTT enabled priority to MQTT sensors)
- Automower vacuum entity
- Buttons (change mode, start, stop, return home, ...)
- Service calls to Robonect actions, like scheduling a job

---

<!-- [START BADGES] -->
<!-- Please keep comment here to allow auto update -->

[![maintainer](https://img.shields.io/badge/maintainer-Geert%20Meersman-green?style=for-the-badge&logo=github)](https://github.com/geertmeersman)
[![buyme_coffee](https://img.shields.io/badge/Buy%20me%20a%20Duvel-donate-yellow?style=for-the-badge&logo=buymeacoffee)](https://www.buymeacoffee.com/geertmeersman)
[![discord](https://img.shields.io/discord/1104706338111627385?style=for-the-badge&logo=discord)](https://discord.gg/wZHsA4aGvS)

[![MIT License](https://img.shields.io/github/license/geertmeersman/robonect?style=flat-square)](https://github.com/geertmeersman/robonect/blob/master/LICENSE)
[![hacs_badge](https://img.shields.io/badge/HACS-Default-41BDF5.svg?style=flat-square)](https://github.com/hacs/integration)

[![Open your Home Assistant instance and open the repository inside the Home Assistant Community Store.](https://my.home-assistant.io/badges/hacs_repository.svg?style=flat-square)](https://my.home-assistant.io/redirect/hacs_repository/?owner=geertmeersman&repository=robonect&category=integration)

[![GitHub issues](https://img.shields.io/github/issues/geertmeersman/robonect)](https://github.com/geertmeersman/robonect/issues)
[![Average time to resolve an issue](http://isitmaintained.com/badge/resolution/geertmeersman/robonect.svg)](http://isitmaintained.com/project/geertmeersman/robonect)
[![Percentage of issues still open](http://isitmaintained.com/badge/open/geertmeersman/robonect.svg)](http://isitmaintained.com/project/geertmeersman/robonect)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-brightgreen.svg)](https://github.com/geertmeersman/robonect/pulls)

[![Hacs and Hassfest validation](https://github.com/geertmeersman/robonect/actions/workflows/validate.yml/badge.svg)](https://github.com/geertmeersman/robonect/actions/workflows/validate.yml)
[![Python](https://img.shields.io/badge/Python-FFD43B?logo=python)](https://github.com/geertmeersman/robonect/search?l=python)

[![manifest version](https://img.shields.io/github/manifest-json/v/geertmeersman/robonect/master?filename=custom_components%2Frobonect%2Fmanifest.json)](https://github.com/geertmeersman/robonect)
[![github release](https://img.shields.io/github/v/release/geertmeersman/robonect?logo=github)](https://github.com/geertmeersman/robonect/releases)
[![github release date](https://img.shields.io/github/release-date/geertmeersman/robonect)](https://github.com/geertmeersman/robonect/releases)
[![github last-commit](https://img.shields.io/github/last-commit/geertmeersman/robonect)](https://github.com/geertmeersman/robonect/commits)
[![github contributors](https://img.shields.io/github/contributors/geertmeersman/robonect)](https://github.com/geertmeersman/robonect/graphs/contributors)
[![github commit activity](https://img.shields.io/github/commit-activity/y/geertmeersman/robonect?logo=github)](https://github.com/geertmeersman/robonect/commits/main)

<!-- [END BADGES] -->

## Installation

The Pull request is still pending merge for the hacs-default repository. So until that time, add my repository as a custom repository in hacs and the integration will show up.

Explanation: https://hacs.xyz/docs/faq/custom_repositories/

```
Repository: geertmeersman/robonect
Category: Integration
```

### Using [HACS](https://hacs.xyz/) (recommended)

1. Simply search for `Robonect` in HACS and install it easily.
2. Restart Home Assistant
3. Add the 'Robonect' integration via HA Settings > 'Devices and Services' > 'Integrations'
4. Provide your Robonect username and password

### Manual

1. Copy the `custom_components/robonect` directory of this repository as `config/custom_components/robonect` in your Home Assistant instalation.
2. Restart Home Assistant
3. Add the 'robonect' integration via HA Settings > 'Devices and Services' > 'Integrations'
4. Provide your robonect username and password

This integration will set up the following platforms.

| Platform   | Description                           |
| ---------- | ------------------------------------- |
| `robonect` | Home Assistant component for Robonect |

## Contributions are welcome!

If you want to contribute to this please read the [Contribution guidelines](CONTRIBUTING.md)

## Troubleshooting

### ENABLING DEBUG LOGGING

To enable debug logging, go to Settings -> Devices & Services and then click the triple dots for the Robonect integration and click Enable Debug Logging.

![enable-debug-logging](https://raw.githubusercontent.com/geertmeersman/robonect/main/images/screenshots/enable-debug-logging.gif)

### DISABLE DEBUG LOGGING AND DOWNLOAD LOGS

Once you enable debug logging, you ideally need to make the error happen. Run your automation, change up your device or whatever was giving you an error and then come back and disable Debug Logging. Disabling debug logging is the same as enabling, but now you will see Disable Debug Logging. After you disable debug logging, it will automatically prompt you to download your log file. Please provide this logfile.

![disable-debug-logging](https://raw.githubusercontent.com/geertmeersman/robonect/main/images/screenshots/disable-debug-logging.gif)

## Lovelace examples

### Mower card with some nice buttons

![Lovelace mower card](https://raw.githubusercontent.com/geertmeersman/robonect/main/images/screenshots/lovelace_card.png)

<details><summary>Show markdown code</summary>

The example uses the following custom lovelace cards:

- custom:button-card: https://github.com/custom-cards/button-card
- custom:mini-graph-card: https://github.com/kalkih/mini-graph-card
- custom:stack-in-card: https://github.com/custom-cards/stack-in-card

```
type: custom:stack-in-card
mode: vertical
keep:
  border_radius: true
cards:
  - type: horizontal-stack
    cards:
      - entity: sensor.automower_mower_status_duration
        show_entity_picture: true
        show_name: false
        font-size: 11px
        show_state: true
        show_label: true
        styles:
          card:
            - height: 40px
            - padding: 5px
            - margin-top: 10px
            - border-top: 1px solid var(--state-icon-color)
            - border: 0px solid var(--primary-background-color)
            - font-size: 11px
        type: custom:button-card
      - entity: sensor.automower_mower_blades_quality
        show_entity_picture: true
        show_name: false
        font-size: 11px
        show_state: true
        show_label: true
        styles:
          card:
            - height: 40px
            - padding: 5px
            - margin-top: 10px
            - border-top: 1px solid var(--state-icon-color)
            - border: 0px solid var(--primary-background-color)
            - font-size: 11px
        type: custom:button-card
      - entity: binary_sensor.automower_health_alarm
        show_entity_picture: true
        show_name: false
        font-size: 11px
        show_state: true
        show_label: true
        styles:
          card:
            - height: 40px
            - padding: 5px
            - margin-top: 10px
            - border-top: 1px solid var(--state-icon-color)
            - border: 0px solid var(--primary-background-color)
            - font-size: 11px
        type: custom:button-card
      - entity: sensor.automower_mower_distance
        show_entity_picture: true
        show_name: false
        font-size: 11px
        show_state: true
        show_label: true
        styles:
          card:
            - height: 40px
            - padding: 5px
            - margin-top: 10px
            - border-top: 1px solid var(--state-icon-color)
            - border: 0px solid var(--primary-background-color)
            - font-size: 11px
        type: custom:button-card
      - entity: sensor.automower_wlan_rssi
        show_entity_picture: true
        show_name: false
        font-size: 11px
        show_state: true
        show_label: true
        styles:
          card:
            - height: 40px
            - padding: 5px
            - margin-top: 10px
            - border-top: 1px solid var(--state-icon-color)
            - border: 0px solid var(--primary-background-color)
            - font-size: 11px
        type: custom:button-card
      - entity: sensor.automower_health_climate_temperature
        show_entity_picture: true
        show_name: false
        font-size: 11px
        show_state: true
        show_label: true
        styles:
          card:
            - height: 40px
            - padding: 5px
            - margin-top: 10px
            - border-top: 1px solid var(--state-icon-color)
            - border: 0px solid var(--primary-background-color)
            - font-size: 11px
        type: custom:button-card
      - entity: sensor.automower_health_climate_humidity
        show_entity_picture: true
        show_name: false
        font-size: 11px
        show_state: true
        show_label: true
        styles:
          card:
            - height: 40px
            - padding: 5px
            - margin-top: 10px
            - border-top: 1px solid var(--state-icon-color)
            - border: 0px solid var(--primary-background-color)
            - font-size: 11px
        type: custom:button-card
  - type: conditional
    conditions:
      - entity: sensor.automower_mower_timer_next_unix
        state_not: Unknown
    card:
      type: markdown
      content: >
        {% set time =
        states.sensor.automower_mower_timer_next_unix.state|as_datetime %} {%
        set day = as_timestamp(time)|timestamp_custom('%d', true)|int %} {% set
        weekday = as_timestamp(time)|timestamp_custom('%w', true)|int %} {% set
        month = as_timestamp(time)|timestamp_custom('%m', true)|int -1 %} {% set
        weekday = ["zondag",
        "maandag","dinsdag","woensdag","donderdag","vrijdag","zaterdag"][weekday]
        %} {% set month = ["januari",
        "februari","maart","april","mei","juni","juli","augustus","september","oktober","november","december"][month]
        %} Volgende start gepland op {{weekday}} {{day}} {{month}} {{
        as_timestamp(time)|timestamp_custom('om %H:%M', true) }}
      card_mod:
        style: |
          ha-card {
            border-width: 0;
            text-align: center;
          }
  - type: tile
    entity: vacuum.automower_robonect
    show_entity_picture: true
    vertical: true
    features:
      - type: vacuum-commands
        commands:
          - start_pause
          - stop
          - return_home
    card_mod:
      style: |
        ha-card {
          border-width: 0;
        }
  - type: horizontal-stack
    style: |
      ha-card {
        margin-left: 10px;
      }
    cards:
      - show_name: false
        show_icon: true
        type: custom:button-card
        tap_action:
          action: call-service
          service: button.press
          service_data:
            entity_id: button.automower_auto
        entity: button.automower_auto
        styles:
          card:
            - height: 40px
            - border: 0px solid var(--primary-background-color)
            - background: |
                [[[
                  if (states['sensor.automower_mower_mode'].state == '0' )
                    return 'var(--state-vacuum-17-color, var(--state-vacuum-active-color, var(--state-active-color)))'
                  return ''
                ]]]
            - font-size: 11px
            - border-radius: 10px
            - '--keep-background': 'true'
      - show_name: false
        show_icon: true
        type: custom:button-card
        entity: button.automower_man
        tap_action:
          action: call-service
          service: button.press
          service_data:
            entity_id: button.automower_man
        styles:
          card:
            - height: 40px
            - border: 0px solid var(--primary-background-color)
            - background: |
                [[[
                  if (states['sensor.automower_mower_mode'].state == '1' )
                    return 'var(--state-vacuum-17-color, var(--state-vacuum-active-color, var(--state-active-color)))'
                  return ''
                ]]]
            - font-size: 11px
            - '--keep-background': 'true'
      - show_name: false
        show_icon: true
        type: custom:button-card
        tap_action:
          action: call-service
          service: button.press
          service_data:
            entity_id: button.automower_eod
        entity: button.automower_eod
        styles:
          card:
            - height: 40px
            - border: 0px solid var(--primary-background-color)
            - background: |
                [[[
                  if (states['sensor.automower_mower_mode'].state == '98' )
                    return 'var(--state-vacuum-17-color, var(--state-vacuum-active-color, var(--state-active-color)))'
                  return ''
                ]]]
            - font-size: 11px
            - '--keep-background': 'true'
  - type: horizontal-stack
    cards:
      - entities:
          - entity: sensor.automower_battery_0
            attribute: voltage
            unit: V
            index: 0
        show:
          icon: false
        font_size: 80
        name: Batt Volt
        decimals: 1
        animate: true
        color_thresholds:
          - value: 0
            color: red
          - value: 17
            color: orange
          - value: 19.3
            color: green
        type: custom:mini-graph-card
        card_mod:
          style: |
            ha-card {
              border-width: 0;
              border-radius: 0
            }
      - entities:
          - entity: sensor.automower_battery_0
            attribute: current
            unit: mA
            index: 0
        show:
          icon: false
        font_size: 80
        name: Batt Curr
        decimals: 1
        animate: true
        color_thresholds:
          - value: -2500
            color: red
          - value: -1000
            color: orange
          - value: 0
            color: green
        type: custom:mini-graph-card
        card_mod:
          style: |
            ha-card {
              border-width: 0;
              border-radius: 0
            }
      - entities:
          - entity: sensor.automower_battery_0
            attribute: temperature
            unit: °C
            index: 0
        show:
          state: true
          icon: false
        font_size: 80
        name: Batt Temp
        decimals: 1
        animate: true
        color_thresholds:
          - value: 0
            color: red
          - value: 10
            color: green
          - value: 30
            color: red
        type: custom:mini-graph-card
        card_mod:
          style: |
            ha-card {
              border-width: 0;
              border-radius: 0
            }
      - aggregate_func: max
        name: Maaitijd
        entities:
          - entity: sensor.maaitijd
        group_by: date
        hour24: true
        hours_to_show: 360
        line_color: green
        show:
          graph: bar
          icon: false
        type: custom:mini-graph-card
        card_mod:
          style: |
            ha-card {
              border-width: 0;
              border-radius: 0
            }

```

</details>

## Screenshots

### Integration page

![Integration device](https://raw.githubusercontent.com/geertmeersman/robonect/main/images/screenshots/integration_device.png)

![Diagnostic](https://raw.githubusercontent.com/geertmeersman/robonect/main/images/screenshots/diagnostic_1.png)
![Diagnostic](https://raw.githubusercontent.com/geertmeersman/robonect/main/images/screenshots/diagnostic_2.png)
![Diagnostic](https://raw.githubusercontent.com/geertmeersman/robonect/main/images/screenshots/diagnostic_3.png)

### Mowing job

![Mowing job](https://raw.githubusercontent.com/geertmeersman/robonect/main/images/screenshots/mowing_job.png)
