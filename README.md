<h1 align="center">
  <br>
  <a href="https://github.com/chanhpng/vlbe_ui"><img src="./images/resticity-logo.svg" alt="Resticity" width="100"></a>
  <br>
  Resticity
  <br>
</h1>

<h4 align="center">A beautiful cross-platform UI for <a href="https://restic.readthedocs.io/en/stable/" target="_blank">restic</a>, built with <a href="https://wails.io" target="_blank">Wails</a>.</h4>

![screenshot](./images/resticity_screenshot.png)

## Status

![release](https://github.com/chanhpng/vlbe_ui/actions/workflows/build.yml/badge.svg?branch=)
![aur](https://github.com/chanhpng/vlbe_ui/actions/workflows/aur.yml/badge.svg?branch=)
![container](https://github.com/chanhpng/vlbe_ui/actions/workflows/container.yml/badge.svg?branch=)
![flatpak](https://github.com/chanhpng/vlbe_ui/actions/workflows/flatpak.yml/badge.svg?branch=)
[![Version](https://img.shields.io/github/release/chanhpng/vlbe_ui.svg?style=flat)]()
[![GitHub stars](https://img.shields.io/github/stars/chanhpng/vlbe_ui.svg?style=social&label=Star)]()
[![GitHub watchers](https://img.shields.io/github/watchers/chanhpng/vlbe_ui.svg?style=social&label=Watch)]()
[![GitHub forks](https://img.shields.io/github/forks/chanhpng/vlbe_ui.svg?style=social&label=Fork)]()

> [!CAUTION]  
> I'm still working on the Windows and macOS version. They're not ready yet.

## Key Features

- Easy to use
- Light/Dark mode
- Cross platform
  - Linux
  - Windows
  - MacOS
- Docker image to run on self-hosted servers
- Scheduled backups
- Supports local and remote repositories
  - Local folder or mounted network drive
  - AWS
  - Backblaze
  - Azure
  - Google
- System tray support
- Desktop Notifications
  - when a schedule starts
  - when a schedule finishes sucessfully or with errors
- Hooks
  - when a schedule starts
  - when a schedule finishes sucessfully or with errors

## How To Use

### Desktop

```bash
# Run in GUI mode
$ resticity

# Run in background mode (useful for autostart)
$ resticity --background

# Run with custom configuration path
$ resticity --config /path/to/config.json
```

### Docker

> [!NOTE]  
> Make sure to set the hostname for the container since it gets changed after each restart.

```bash
# Run within Docker
# Add the paths that you want resticity to grant access to
$ docker run -d --name resticity -h myHostnameChangeMe -p 11278:11278 -v /path/to/config.json:/config.json -v /mnt:/mnt -v /home:/home ghcr.io/chanhpng/vlbe_ui
```

#### Docker compose

```yaml
version: "3"
services:
  reseticity:
  image: ghcr.io/chanhpng/vlbe_ui
  container_name: resticity
  hostname: myHostnameChangeMe
  ports:
    - 11278:11278
  volumes:
    - /mnt:/mnt # Add the paths that you want resticity to grant access to
    - /home:/home
    - /path/to/config.json:/config.json # changeMe
```

## Configuration

Resticity looks for a configuration file in the following order:

1. Custom file location with the `--config path/to/config.json` flag
2. `RESTICITY_SETTINGS_FILE` environment variable
3. `$XDG_CONFIG_HOME/resticity/config.json`

## Troubleshooting

Set `RESTICITY_LOG_LEVEL=debug` as environment variable for detailed debug messages (and log files).

> [!WARNING]  
> This produces larger log files, so it is advised not to run it in production.

## Installation

### Linux

```bash
# Arch Linux
paru -S resticity
```

### Windows

- install [restic](https://restic.readthedocs.io/en/latest/020_installation.html#windows) and [rclone](https://rclone.org/downloads/) on your system
- Download the Resticity binary for Windows from the latest [release](https://github.com/chanhpng/vlbe_ui/releases)

## Build yourself

```bash
# Clone this repo
$ git clone https://github.com/chanhpng/vlbe_ui

# Install wails
$ go install github.com/wailsapp/wails/v2/cmd/wails@latest

# cd into resticity
$ cd resticity

# Run as dev
$ ./build.sh dev

# Build desktop
$ ./build.sh desktop
# run
$ ./build/bin/resticity
```

## TODOs

- [ ] Packaging for different platforms

---

> [adisdurakovic.com](https://adisdurakovic.com) &nbsp;&middot;&nbsp;
> GitHub [@ad-on-is](https://github.com/ad-on-is)
