<div align=center>
    <h1 style="font-size: 4em; color: red">SystemD Scripts</h1>
</div>

## Description

Custom systemd service scripts for vm and stand-alone systems like the Raspberry Pi, for more and set and forget system that is required for basic home lab setups.

This started out as a couple of scripts for my Raspberry Pi 3b that I used for a time as a [Pi-Hole](https://pi-hole.net/) server, but I have since moved on to a [Proxmox](https://www.proxmox.com/en/) container and now us the Pi has my [Cloudflared](https://www.cloudflare.com) Tunnel server.

### List of scripts

<!-- This is set in a table -->

| Script Name                | Description                                                | type                | Status              |
| :------------------------- | :--------------------------------------------------------- | :------------------ | :------------------ |
| **pihole-framework**       | Keeps Pi-hole framework updated (Not supported by Pi-hole) | **Timer & Service** | Active (Timer Only) |
| **pihole-gravity**         | Update DNS Gravity for Pi-hole                             | **Timer & Service** | Active (Timer Only) |
| **unbound-hints**          | Keeps the unbound root hints file updated                  | **Timer & Service** | Active (Timer Only) |
| **clean-apt-cache**        | Cleans the apt cache on a daily bases                      | **Timer & Service** | Active (Timer Only) |
| **unbound-log2ram**        | Recreate the unbound log file if log2ram is installed.     | **Service Only**    | Active              |
| **starship-prompt**        | Updates the starship prompt to the latest version          | **Timer & Service** | Active (Timer Only) |
| **vaultwarden-pod-update** | Updates the vaultwarden docker container                   | **Timer & Service** | Active (Timer Only) |

## Installation

Installing is easy, just clone the repo and copy the desired scripts to `/usr/lib/systemd/system/`. Then enable the scripts with `systemctl enable --now <script-name>.service` and `systemctl enable --now <script-name>.timer`.

For services that rely on the timer do not enable the service since the timer will start the service when it is triggered.

## [License](COPYING)

This project is licensed under the MIT License - see the [LICENSE](COPYING) file for details.
