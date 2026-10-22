# My Homelab

Welcome to my homelab! I'm building a personal environment for self-hosted services, home automation, and hands-on learning.

This repository documents how the pieces fit together, the decisions behind them, and what I learn along the way.

## Overview

The setup combines a custom-built Proxmox server, a Raspberry Pi running Home Assistant, and a repurposed Samsung tablet as a dashboard.

Home Assistant runs separately from the main server, keeping home controls available when the Proxmox host is switched off.

![Hand-drawn overview of my homelab, showing the tablet dashboard, Raspberry Pi, Proxmox server, and lighting](homelab-overview.png)

*This is a simplified functional overview, rather than a complete network map.*

## Hardware

| Device | Role |
| --- | --- |
| Custom-built server | Proxmox VE host for virtualized services |
| Raspberry Pi 3 Model B | Home Assistant and local device integrations |
| Samsung Galaxy Tab S6 Lite | Dashboard for home controls and server monitoring |
| Govee and Nanoleaf light strips | Connected lighting |

## Services

The following services were recorded in my latest documented setup. Individual documentation and current status checks are being added.

| Service | Area |
| --- | --- |
| Home Assistant | Home automation and dashboard |
| Dashy | Dashboard |
| Pelican Panel and Wings | Game server management |
| VS Code | Development tools |
| Nginx Proxy Manager | Reverse proxy management |
| cloudflared | Connectivity infrastructure |

## Features and Progress

- Tablet dashboard combining home controls and server monitoring.
- Proxmox resource and container status displays.
- Wake-on-LAN and shutdown controls configured.
- Local lighting control through LAN and Bluetooth integrations.
- Connection status feedback and a manual reconnect control for Nanoleaf.
- Home Assistant configuration backups stored on the Pi and PC.

A complete server shutdown-and-wake cycle still needs final verification. Bluetooth reliability is also an ongoing improvement area.

## What I'm Learning

- Running and maintaining self-hosted services.
- Working with Proxmox and containers.
- Integrating devices into Home Assistant.
- Designing useful dashboards.
- Troubleshooting connectivity and keeping configuration backups.

## Next Steps

- [ ] Document each service and how I use it.
- [ ] Expand the hardware overview.
- [ ] Verify the complete server power cycle.
- [ ] Improve Bluetooth reliability.
- [ ] Refine dashboards and automations.
- [ ] Explore a smart mirror as an additional display.

## About This Documentation

This is a growing personal project. Some parts are working, while others are still being tested or planned.

Public diagrams and examples are simplified. Credentials, real addresses, domains, and detailed access configurations are intentionally omitted.
