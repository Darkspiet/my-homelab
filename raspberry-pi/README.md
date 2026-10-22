# Raspberry Pi

[Home](../README.md) · [Home Assistant](home-assistant/README.md) · [Proxmox server](../proxmox/README.md)

The Raspberry Pi is the separate controller for my home automation setup. It connects the tablet dashboard with lighting devices and the main server.

## Setup

| Component | Setup |
| --- | --- |
| Hardware | Raspberry Pi 3 Model B |
| Operating system | 64-bit Debian 13 |
| Application | Home Assistant running in a Docker container |
| Display and controls | Samsung Galaxy Tab S6 Lite using the Home Assistant Companion app |

## Why a Separate Controller?

Keeping Home Assistant on the Pi allows home controls to remain available independently of the Proxmox server. The Pi can also send a Wake-on-LAN request when the main server is off.

## Home Automation

See the [Home Assistant documentation](home-assistant/README.md) for dashboard behavior, lighting integrations, monitoring, and known limitations.

Home Assistant configuration backups are stored on the Pi and PC. Private configuration files and backup archives stay outside this repository.
