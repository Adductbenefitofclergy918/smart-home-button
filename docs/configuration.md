# Configuration Guide

## 1. Secrets

Copy the example secrets file:

```bash
cp secrets.example.yaml secrets.yaml
```

Fill in your Wi-Fi and ESPHome credentials. `secrets.yaml` is intentionally ignored by Git. The example API key is a public dummy value for config checks only; generate your own before flashing.

## 2. Home Assistant Entities

Edit `src/main/entities.yaml` and replace the placeholders:

```yaml
substitutions:
  weather_entity: weather.your_location
  climate_entity: climate.your_ac
  music_player_entity: media_player.your_player
```

Find these IDs in Home Assistant under Developer Tools -> States.

## 3. Music Player Selection

Choose the entity that actually plays audio, not the Dial entity itself. A good target usually exposes:

- `state`: `playing` or `paused`
- `volume_level`
- `media_title`
- `media_artist`
- `media_duration`
- `media_position`
- `entity_picture`

If the entity is `unavailable`, Home Assistant will disable controls and the Dial cannot sync it.

## 4. Timezone

The default timezone is `Asia/Shanghai`. Change it in `src/pages/main.yaml` if you use another timezone.
