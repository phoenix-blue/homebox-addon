# Changelog

## 0.23.1.3-dev1

- Add automatic Homebox API authentication via username/password fallback
- Keep manual token support as first authentication method
- Improve sync logging for Homebox API HTTP status and auth mode

## 0.23.1.2-dev1

- Add Homebox item to Home Assistant entity sync (MVP, no MQTT)
- Add configurable sync options (item ID, API token, target entity, interval)
- Add `jq` dependency for JSON parsing inside add-on runtime

## 0.23.1.1-dev1

- Enable Home Assistant Core API access in add-on config
- Add optional startup check to Home Assistant Core API via SUPERVISOR_TOKEN

## 0.23.1.0

- Initial release based on Homebox v0.23.1
