# Setting Up WSL2

This is a guide to setting up a new Windows 10 machine with wsl2 using ubuntu 20 + zsh + oh-my-zsh + powerline9k

## Requirements

* Windows 10, version 20H2 or greater
* [Ubuntu 20.04 LTS](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6?activetab=pivot:overviewtab&atc=true)
* [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab&atc=true&rtc=1)

## Table of content

1. Installing WSL2 and Windows Terminal

2. Setting up zsh and oh-my-zsh

3. Configuring Windows Terminal for Powerline9K

4. Configuring Git

## 1. Installing WSL2 and Windows Terminal

As of today, best instructions on installing wsl2 and windows terminal is directly from [Microsofts documentation](https://docs.microsoft.com/en-us/windows/wsl/install-win10). This section will cover a curtailed abridged version. Run all of the following commands in PowerShell with administrator previlages.

1.1 Enable wsl for you windows machine.

> ```powershell
> ism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
> ```

1.2 Enable virtual machines on your PC

> ```powershell
> dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
> ```

1.3 Linux kernal update for wsl

This might change in the future.  As of 2020 November 27th, downloand and install the [wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) from Microsoft.

1.4 Set wsl2 as your default

> ```powershell
> wsl --set-default-version 2
> ```

1.5 Install the Ubuntu OS of your choice in the [Microsoft Store](https://aka.ms/wslstore)

For this tutorial we will be using [Ubuntu 20.04 LTS](https://www.microsoft.com/store/apps/9n6svws3rx71) from the Microsoft Store. While other Ubuntu flavors could work, to get the exact results in this tutorial, use Ubuntu 20.04 LTS.

Launch your Ubuntu 20.0
