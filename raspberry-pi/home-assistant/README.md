# Home Assistant

[Home](../../README.md) · [Raspberry Pi](../README.md) · [Proxmox server](../../proxmox/README.md)

Home Assistant brings home controls and server information into one tablet interface. It runs in Docker on the Raspberry Pi, separately from the Proxmox host.

## Tablet Dashboard

The Samsung Galaxy Tab S6 Lite uses the Home Assistant Companion app as a control panel. Android was retained; rooting or flashing the tablet was not required.

The dashboard has home, server, and system views, with controls and status information grouped by purpose.

## Proxmox Integration

The server integration brings these controls and readings to the tablet:

- CPU, memory, uptime, and container status displays.
- Wake-on-LAN configured for server startup.
- A shutdown control with a confirmation prompt.
- A power button whose action follows the reported server state.
- Resource displays shown only when the server is reachable and measurements are available.

## Lighting

| Device | Connection | Controls |
| --- | --- | --- |
| Govee light strip | Local LAN control | Brightness |
| Nanoleaf light strip | HomeKit over Bluetooth | Switching and dimming |

Govee uses the local LAN integration. The Nanoleaf controls include a reconnect button and connection feedback.

## Configuration Backups

Home Assistant configuration backups are stored on both the Pi and PC. They contain private configuration and integration data and stay outside this repository.
