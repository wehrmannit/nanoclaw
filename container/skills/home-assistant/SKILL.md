---
name: home-assistant
description: Control and query Home Assistant smart home devices — check states, call services, view history, and automate. Use whenever the user asks about their home, devices, lights, temperature, or anything smart-home related.
allowed-tools: Bash(home-assistant:*)
---

# Home Assistant Integration

Query and control smart home devices via the Home Assistant REST API.

## Quick start

```bash
home-assistant status                            # Check connectivity
home-assistant states                            # All entity states
home-assistant states light                      # All lights
home-assistant state sensor.temperature          # Specific entity
```

## Commands

### Query

```bash
home-assistant states [domain]                   # List states (light, sensor, switch, etc.)
home-assistant state <entity_id>                 # Detailed state with attributes
home-assistant entities [domain]                 # List entity IDs
home-assistant history <entity_id> [hours]       # State history (default: 24h)
home-assistant services [domain]                 # Available services
```

### Control

```bash
home-assistant call <domain> <service> [entity_id] [json_data]
```

Examples:
```bash
home-assistant call light turn_on light.living_room
home-assistant call light turn_off light.bedroom
home-assistant call switch toggle switch.fan
home-assistant call climate set_temperature climate.thermostat '{"temperature": 21}'
home-assistant call cover open_cover cover.garage
home-assistant call media_player media_play media_player.speaker
home-assistant call scene turn_on scene.movie_night
```

### Advanced

```bash
home-assistant event <event_type> [json]         # Fire custom event
home-assistant template '<jinja2>'               # Render HA template
```

## Common domains

| Domain | Description | Common services |
|--------|-------------|-----------------|
| light | Lights | turn_on, turn_off, toggle |
| switch | Switches/plugs | turn_on, turn_off, toggle |
| climate | Thermostats/HVAC | set_temperature, set_hvac_mode |
| cover | Blinds/garage | open_cover, close_cover, stop_cover |
| media_player | Speakers/TVs | media_play, media_pause, volume_set |
| scene | Scenes | turn_on |
| automation | Automations | trigger, turn_on, turn_off |
| sensor | Sensors (read-only) | — |
| binary_sensor | On/off sensors | — |

## Example: Check and control lights

```bash
home-assistant states light                      # See all light states
home-assistant call light turn_on light.kitchen '{"brightness": 200, "color_temp": 350}'
home-assistant state light.kitchen               # Verify change
```

## Example: Temperature monitoring

```bash
home-assistant entities sensor                   # Find temperature sensors
home-assistant state sensor.living_room_temperature
home-assistant history sensor.living_room_temperature 48  # Last 48 hours
```
