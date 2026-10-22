# My Homelab

Welcome to my homelab! I'm building a personal environment for self-hosted services, home automation, and hands-on learning.

This repository documents how the pieces fit together, the decisions behind them, and what I learn along the way.

## Overview

A custom-built Proxmox server hosts my virtualized services. A separate Raspberry Pi runs Home Assistant, with a repurposed Samsung tablet as its dashboard. Keeping home automation on the Pi allows it to operate independently of the main server.

![Hand-drawn overview of my homelab, showing the tablet dashboard, Raspberry Pi, Proxmox server, and lighting](homelab-overview.png)

*My hand-drawn functional overview. Connections are simplified and do not represent the complete network topology.*

## Explore the Setup

- **[Proxmox server](proxmox/README.md):** virtualization, services, monitoring, and power controls.
- **[Raspberry Pi](raspberry-pi/README.md):** the separate home automation controller.
- **[Home Assistant](raspberry-pi/home-assistant/README.md):** the tablet dashboard, lighting, and server integration.

## Hardware

| Device | Role |
| --- | --- |
| [Custom-built server](proxmox/README.md#hardware) | Ryzen 9 5900X · 32 GB DDR4 · Proxmox VE |
| Raspberry Pi 3 Model B | Home Assistant and local device integrations |
| Samsung Galaxy Tab S6 Lite | Dashboard for home controls and server monitoring |
| Govee and Nanoleaf light strips | Connected lighting |

## Services

These are the services that make up my homelab.

| Service | Area |
| --- | --- |
| [Home Assistant](raspberry-pi/home-assistant/README.md) | Home automation and dashboard |
| [Dashy](proxmox/services/dashy.md) | Dashboard |
| [Pelican Panel and Wings](proxmox/services/pelican.md) | Game server management |
| [VS Code](proxmox/services/vscode.md) | Development tools |
| [Nginx Proxy Manager](proxmox/services/nginx-proxy-manager.md) | Reverse proxy management |
| [cloudflared](proxmox/services/cloudflared.md) | Connectivity infrastructure |

See the [Proxmox service index](proxmox/services/README.md) for a closer look at each service.

## Progress and Learning

The setup brings together a tablet dashboard, Proxmox monitoring, server power controls, and local lighting. Building it has helped me learn about virtualization, device integration, dashboard design, and troubleshooting.

## About This Documentation

This is a personal project that grows as I experiment and learn.

Public diagrams and descriptions are simplified. Credentials, real device addresses, deployment domains, tunnel mappings, private configurations, and backups are excluded.
