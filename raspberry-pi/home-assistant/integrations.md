# Integrations and Setup

[Home Assistant](README.md)

These examples bring together my tablet dashboard, connection helpers, scripts, recovery automation, and theme. All entity IDs are examples.

## UI Integrations

Add these under **Settings → Devices & services → Add integration**. They create entities used by the YAML; the files alone do not pair devices or establish the Proxmox connection.

| Integration | Setup | Example entities to map |
| --- | --- | --- |
| [Proxmox VE](https://www.home-assistant.io/integrations/proxmoxve/) | Use your own server and a dedicated API account. Enable the node readings and container status entities you need. | `sensor.proxmox_cpu_usage`, `sensor.proxmox_memory_usage_percentage`, `sensor.proxmox_uptime`, `binary_sensor.proxmox_status`, and each `binary_sensor.*_status` |
| [Govee lights local](https://www.home-assistant.io/integrations/govee_light_local/) | Enable LAN Control for your compatible light, then add the integration. | `light.govee_strip` |
| [HomeKit Device](https://www.home-assistant.io/integrations/homekit_controller/) | Pair the Nanoleaf locally with its private HomeKit code. This setup uses Bluetooth access from Home Assistant. | `light.nanoleaf_strip` |

Rename the resulting entities to match the examples, or replace their references consistently across all files. UI integration configuration and pairing data stay in your own Home Assistant installation.

The Proxmox monitoring account needs read permissions. The separate shutdown REST command needs an API token authorized for node shutdown; a monitoring-only token is not sufficient. Keep token values local.

## YAML Files

1. Merge `configuration.yaml` into your existing configuration. Keep existing definitions and combine matching top-level sections.
2. Copy the `dashboards/`, `scripts/`, `packages/`, and `themes/` folders alongside it, preserving their structure and merging existing files where needed.
3. Copy `secrets.example.yaml` to a local `secrets.yaml` and replace every example value. The address and hostname in the example are intentionally unusable for your network.
4. Map the UI integration entities across the dashboard, packages, scripts, and templates.
5. Check the configuration in Home Assistant before reloading or restarting. Open the **Homelab** dashboard from the sidebar afterward.

The package includes define `input_select.nanoleaf_connection` and `light.nanoleaf_controls`. The command-line sensors provide Pi memory, disk, and uptime readings plus `binary_sensor.proxmox_online`. The available-light sensor excludes the example light group and the Nanoleaf control wrapper.

Existing entity-registry entries may keep their old names. Match them to the dashboard rather than assuming a display-name change will rename an existing entity.

### How the Includes Work

The registered dashboard file is `dashboards/ui-lovelace.yaml`. It includes each file under `dashboards/views/` explicitly, keeping Home, Server, and System in that order. View paths are relative to the dashboard file.

The main configuration loads `scripts/` and `themes/` with `!include_dir_merge_named`. Each script file contains script names at its top level; the theme file contains the `Homelab` theme name. Keep those names unique across files.

These split files are intended for a YAML dashboard loaded from disk. To use the raw configuration editor instead, first combine the views into one dashboard configuration.

See [Home Assistant's configuration splitting guide](https://www.home-assistant.io/docs/configuration/splitting_configuration/) for include syntax.

## Local Secret Values

| Key | Local value |
| --- | --- |
| `proxmox_wake_mac` | The server network adapter's Wake-on-LAN MAC |
| `proxmox_broadcast_address` | Your network's broadcast address |
| `proxmox_reachability_command` | The example TCP check with your host substituted |
| `proxmox_shutdown_url` | Your Proxmox node status API endpoint |
| `proxmox_shutdown_authorization` | The complete API-token authorization header |
| `nanoleaf_config_entry_id` | The HomeKit Device integration entry for Nanoleaf |
| `proxmox_config_entry_id` | The Proxmox VE integration entry |

Use **Settings → Devices & services → the integration → Copy entry ID**, where available, for the integration entry IDs. These are integration identifiers, not entity IDs.

The shutdown REST example keeps TLS certificate verification enabled. Its hostname and certificate must be trusted by Home Assistant. It does not reuse the monitoring integration's TLS settings.

## Behavior

The Nanoleaf helper uses **Not checked**, **Connecting**, **Ready**, and **Connection error**. The guarded light and reconnect scripts use the same states. A reconnect attempt may send a real light command to check communication, using the previous state and brightness where available.

The recovery automation reloads the Proxmox integration when the host is reachable but its readings or node status have not recovered. It does not start or shut down the server.

The command-line system readings run inside Home Assistant's environment. In a container, disk usage refers to the filesystem containing `/config`; it is not a report of every disk attached to the Pi.

## Theme

`themes/homelab.yaml` contains the **Homelab** dark theme from my tablet setup. The dashboard selects it for each view.

## Validation

The examples are checked locally for YAML syntax, template syntax, file references, and matching helper and script names. They have been adapted for publication and have not been deployed or tested against a fresh Home Assistant instance.
