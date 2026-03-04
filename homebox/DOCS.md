# Homebox Add-on Documentation

[Homebox](https://homebox.software) is an inventory and organization system built for the home user. It allows you to track and manage all of your belongings with a clean, intuitive web UI.

## Installation

1. Add this repository to your Home Assistant add-on store.
2. Install the **Homebox** add-on.
3. Configure the options (see below).
4. Start the add-on.
5. Open the Web UI and create your first account.

> **Tip:** After creating your first account, disable **Allow registration** in the add-on configuration to prevent other users from signing up.

## Configuration

### Option: `log_level`

Sets the verbosity of the Homebox logs. Options: `trace`, `debug`, `info`, `warn`, `error`, `fatal`, `panic`.

Default: `info`

### Option: `allow_registration`

When `true`, anyone who can reach the web UI can create a new account.

Set to `false` after creating your first account.

Default: `true`

### Option: `max_upload_size`

The maximum size (in MB) for file uploads such as item photos and attachments.

Default: `10`

### Option: `ha_api_startup_check`

When `true`, the add-on performs a startup connectivity check to the Home Assistant Core API using the Supervisor token and logs the result.

Default: `true`

### Option: `homebox_sync_enabled`

Enables periodic sync of one Homebox item to one Home Assistant entity.

Default: `false`

### Option: `homebox_url`

Base URL of Homebox API. For this add-on on the same host, `http://127.0.0.1:7745` usually works.

Default: `http://127.0.0.1:7745`

### Option: `homebox_api_token`

Homebox API bearer token used to fetch the selected item.

If this is empty, the add-on can try login with `homebox_username` and `homebox_password`.

### Option: `homebox_username`

Homebox username (or email) used to obtain an API token automatically when no manual token is set.

### Option: `homebox_password`

Homebox password used to obtain an API token automatically when no manual token is set.

### Option: `homebox_item_id`

The Homebox item UUID to sync to Home Assistant.

### Option: `ha_target_entity_id`

Entity ID in Home Assistant that will be updated by the sync process (for example `sensor.homebox_selected_item`).

Default: `sensor.homebox_selected_item`

### Option: `homebox_sync_interval_seconds`

Sync interval in seconds.

Default: `60`

## Homebox → Home Assistant sync (MVP)

This add-on can sync one selected Homebox item to one Home Assistant entity using the Supervisor token. The entity state is set to the item name, and attributes include fields like price, currency, location and item URL.

Authentication priority for Homebox API:
1. `homebox_api_token` when provided
2. automatic login using `homebox_username` + `homebox_password`

This is an MVP implementation and does not add a Home Assistant device picker inside the Homebox UI yet.

## Data Storage

All Homebox data (SQLite database, uploaded images and attachments) is stored in the add-on's persistent `/data` directory. This directory is included in Home Assistant backups automatically.

The database file is located at `/data/homebox.db`.

## Port

Homebox listens on port `7745` by default. You can change the external port mapping in the add-on **Network** configuration tab.

## Support

- [Homebox documentation](https://homebox.software/en/)
- [Homebox GitHub](https://github.com/sysadminsmedia/homebox)
- [Add-on GitHub](https://github.com/Crafter-Y/homebox-addon)
