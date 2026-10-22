# Proxmox Server

[Home](../README.md) · [Service index](services/README.md) · [Home Assistant](../raspberry-pi/home-assistant/README.md)

My custom-built server runs Proxmox VE and hosts the virtualized services in this homelab. It provides a place to experiment with self-hosting and service administration.

## Hardware

| Component | Specification |
| --- | --- |
| CPU | AMD Ryzen 9 5900X · 12 cores / 24 threads |
| Virtualization | AMD-V |
| Motherboard | MSI A320M-A PRO (MS-7C51) |
| Memory | 32 GB DDR4 · 2 × 16 GB DIMMs, configured at 2133 MT/s |
| Graphics | NVIDIA GeForce GTX 750 Ti |
| Network | Realtek RTL8111/8168/8211/8411 family Gigabit Ethernet controller |

## Storage

The SATA SSD holds Proxmox, the root filesystem, and LVM-thin storage. Three SATA hard drives form a single ZFS RAIDZ1 pool.

| Drive | Model | Capacity | Role |
| --- | --- | --- | --- |
| SATA SSD | Samsung MZ7TE256HMHP-000L7 | 238.5 GiB | System and LVM-thin storage |
| SATA HDD | Western Digital WD10JPVX-22JC3T0 | 931.5 GiB | ZFS RAIDZ1 member |
| SATA HDD | Seagate ST1000LM035-1RK172 | 931.5 GiB | ZFS RAIDZ1 member |
| SATA HDD | ST1000LM024 HN-M101MBB | 931.5 GiB | ZFS RAIDZ1 member |

*Capacities are per-drive values reported by the operating system, not the usable capacity of the ZFS pool.*


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
