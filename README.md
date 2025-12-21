# Alpine Linux for WSL

This project provides an Alpine Linux distribution for the Windows Subsystem for Linux (WSL).

> [!IMPORTANT]
> - This distribution is in the development and testing stage and has limited functionality.
> - The arm64 distribution has not been tested.

## Features

- Based on the official Alpine Linux mini root filesystem.
- Designed for WSL 2.

## Requirements

- Windows 10 (version 1903 or later) or Windows 11.
- Windows Subsystem for Linux (WSL 2).

## Installation options

### Manual installation

Download the distribution of the required architecture and install it by double-clicking.

### Manual installation with commands

Download the distribution of the required architecture and install it using the command:

``` powershell
wsl --install --from-file C:\Users\<UserName>\Download\alpine-3.23.2-1-x86_64.wsl
```

### Using an additional WSL distribution list

An unofficial, ready-to-use list provides additional WSL distributions that are not included in the official list.

To register the list, use the following commands.

Powershell (as Administrator):

``` powershell
Set-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Lxss" `
  -Name DistributionListUrlAppend `
  -Value "https://raw.githubusercontent.com/greengorych/wsl-configs/main/distributions/distributions.json" `
  -Type String -Force
```

Command Prompt (as Administrator):

``` batch
reg add "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Lxss" ^
/v "DistributionListUrlAppend" ^
/t REG_MULTI_SZ ^
/d "https://raw.githubusercontent.com/greengorych/wsl-configs/main/distributions/distributions.json" ^
/f
```

After registering, the distributions available for installation can be checked using the command:

``` powershell
wsl --list --online
```

If Alpine appears in the output, install it using the command:

``` powershell
wsl --install Alpine
```

> [!NOTE]
> More information about an additional WSL distribution list are available on this [page][Additional WSL distributions list].

### Contributing

Feel free to open issues and suggest improvements.

## Licensing

### Project License

The code and configuration files in this repository are licensed under the [MIT license][MIT license].

### Alpine Linux and Third-Party Software

Alpine Linux is a Linux distribution composed of software licensed under
various open source licenses, including GPL, LGPL, MIT, BSD, and others.

This project distributes Alpine Linux packages without modification.

[MIT license]: https://github.com/greengorych/alpine-wsl-test/blob/main/LICENSE-MIT.md
[Additional WSL distributions list]: https://greengorych.io/reference/distributions-list/
