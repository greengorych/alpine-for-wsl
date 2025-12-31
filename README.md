# Alpine Linux for WSL

This project provides a ready-to-use Alpine Linux distribution for the Windows Subsystem for Linux (WSL).

> [!IMPORTANT]
> - The distribution is still under active development and testing and may have limited functionality.
> - The arm64 build has not yet been fully tested.

## Features

- Based on the official Alpine Linux mini root filesystem
- Designed for WSL 2
- OpenRC init system with automatic startup
- cloud-init configured with the WSL data source
- System logging (dmesg, OpenRC, syslog) with log rotation
- Built-in task scheduler (cron)

## Requirements

- Windows 10 version 1903 or newer, or Windows 11
- Windows Subsystem for Linux (WSL 2).

## Installation options

### Manual installation

Download the distribution for your architecture and install it by double-clicking the file.

### Manual installation with commands

Download the image for your architecture and install it with:

``` powershell
wsl --install --from-file C:\Users\<UserName>\Download\alpine-3.23.2-4-x86_64.wsl
```

### Using an additional WSL distributions list

You can also install Alpine from an unofficial community list of additional WSL distributions.

To register the list, run the following commands as Administrator.

Powershell:

``` powershell
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Lxss" `
  -Name DistributionListUrlAppend `
  -Value "https://raw.githubusercontent.com/greengorych/wsl-configs/main/distributions/distributions.json" `
  -Type String -Force
```

Command Prompt:

``` batch
reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Lxss" ^
/v "DistributionListUrlAppend" ^
/t REG_MULTI_SZ ^
/d "https://raw.githubusercontent.com/greengorych/wsl-configs/main/distributions/distributions.json" ^
/f
```

After adding the list, view available distributions:

``` powershell
wsl --list --online
```

If Alpine appears in the list, install it with:

``` powershell
wsl --install Alpine
```

> [!NOTE]
> More information about an additional WSL distribution list are available on this [page][Additional WSL distributions list].

### Contributing

Issues, bug reports, and improvement suggestions are welcome.

## Licensing

### Project License

The code and configuration in this repository are licensed under the [MIT license][MIT license].

### Alpine Linux and Third-Party Software

Alpine Linux consists of software distributed under various open-source licenses (GPL, LGPL, MIT, BSD, and others).

This project distributes Alpine Linux packages without modification.

[MIT license]: https://github.com/greengorych/alpine-wsl-test/blob/main/LICENSE-MIT.md
[Additional WSL distributions list]: https://greengorych.io/reference/distributions-list/
