# Proxmox Server

[Home](../README.md) · [Service index](services/README.md) · [Home Assistant](../raspberry-pi/home-assistant/README.md)

My custom-built server runs Proxmox VE and hosts the virtualized services in this homelab. It provides a place to experiment with self-hosting and service administration.

## Services

The server hosts the following services in Proxmox containers.

| Service | Documentation |
| --- | --- |
| Dashy | [Dashboard](services/dashy.md) |
| Pelican Panel and Wings | [Game server management](services/pelican.md) |
| VS Code | [Development tools](services/vscode.md) |
| Nginx Proxy Manager | [Reverse proxy management](services/nginx-proxy-manager.md) |
| cloudflared | [Connectivity infrastructure](services/cloudflared.md) |

## Connection to Home Assistant

Home Assistant runs on the [separate Raspberry Pi](../raspberry-pi/README.md) and connects the server to the tablet dashboard:

- CPU, memory, uptime, and container status in the tablet dashboard.
- Wake-on-LAN configured to request server startup from the Pi.
- A shutdown control with a confirmation prompt.
- Resource displays hidden when the server or its measurements are unavailable.
