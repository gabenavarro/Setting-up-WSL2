# Setting Up WSL2

This is a guide to setting up a new Windows 10 machine with wsl2 using ubuntu 20 + zsh + oh-my-zsh + powerline9k

## Requirements

* Windows 10, version 20H2 or greater
* [Ubuntu 20.04 LTS](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6?activetab=pivot:overviewtab&atc=true)
* [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab&atc=true&rtc=1)

## Table of content

1. Installing WSL2 and Windows Terminal

2. Configuring Windows Terminal

3. Setting up zsh and oh-my-zsh

## 1. Installing WSL2 and Windows Terminal

As of today, best instructions on installing wsl2 and windows terminal is directly from [Microsofts documentation](https://docs.microsoft.com/en-us/windows/wsl/install-win10). This section will cover a curtailed abridged version. Run all of the following commands in PowerShell with administrator previlages.

### 1.1 Enable wsl for you windows machine.

> ```powershell
> ism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
> ```

### 1.2 Enable virtual machines on your PC

> ```powershell
> dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
> ```

### 1.3 Linux kernal update for wsl

This might change in the future.  As of 2020 November 27th, downloand and install the [wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) from Microsoft.

### 1.4 Set wsl2 as your default

> ```powershell
> wsl --set-default-version 2
> ```

### 1.5 Install the Linux OS of your choice in the [Microsoft Store](https://aka.ms/wslstore)

For this tutorial we will be using [Ubuntu 20.04 LTS](https://www.microsoft.com/store/apps/9n6svws3rx71) from the Microsoft Store. While other Ubuntu flavors could work, to get the exact results in this tutorial, use Ubuntu 20.04 LTS.

Launch your Ubuntu 20.04 and setup your account.

### 1.6 Install Windows Terminal

In order to have a the latest terminal for your Windows 10 PC, install [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab&atc=true&rtc=1) from the Microsoft Store. It has a straightfoward configuration json file and allows for multiple tabs to be open.

## 2. Configure your Windows Terminal

The following section covers how to confingure your Windows Terminal in order to have a beautiful display for Powerlevel9k.

### 2.1 Install DejaVu Sans Mono Nerd Font

While there are many fonts to choose from at the Nerd Font website, I recommend [DejaVu Sans Mono Nerd Font](https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/DejaVuSansMono/Regular/complete/DejaVu%20Sans%20Mono%20Nerd%20Font%20Complete.ttf) from Ryan and Daniel's git repo. You can find the ttf file directly from the gitrepo, alternatively, you can find it in the bin folder from this repo.  

### 2.2 Adjusting your Windows Terminal settings

Open your Windows Terminal settings and adjust the values for your Ubuntu profile to the following:

> ```json
> {
>     "guid": "{2c4de342-38b7-51cf-b940-2309a097f518}",
>     "hidden": false,
>     "name": "Ubuntu",
>     "fontFace": "DejaVuSansMono Nerd Font",
>     "colorScheme": "One Half Dark",
>     "fontSize": 8,
>     "source": "Windows.Terminal.Wsl"
> }
> ```

The most important setting is `"fontFace"` and `"colorScheme"`. Adjust `"fontSize"` to your preference depending on your monitor size and resolution.

## 3. Setting up zsh and oh-my-zsh

The following section goes over setting up your bash shell with zsh and oh-my-zsh.  Its  compilation of various tutorials, in particular I heavily adapt configurations from [William](https://twasa.ml/post/wsl/) and [Nikcy's](https://nickymeuleman.netlify.app/blog/linux-on-windows-wsl2-zsh-docker) tutorials.

### 3.1 Update your Linux tools

> ```zsh
> sudo apt update
> sudo apt upgrade
> ```

### 3.2 Install and configure git

Install git with the following command

> ```zsh
> sudo apt install git
> ```

Configure your git account

> ```zsh
> git config --global user.name "User Name"
> git config --global user.email "juan@doe.com"
> git config --global core.autocrlf input
> ```

### 3.3 Install Node and NPM

Fist isntall nvm with the following command.

> ```zsh
> curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
> ```

Restart your bash script, and confirm installation successful:

> ```zsh
> command -v nvm
> ```

It should return ```nvm```.  If successful, install node.

> ```zsh
> nvm install node
> nvm use node
> ```

Afterwords, install yarn.

> ```zsh
> npm install -g yarn
> ```

There are more instructions [here](https://yarnpkg.com/getting-started/install) on how to install and maintain yarn projects.

### 3.4 Install zsh and oh-my-zsh

> ```zsh
> sudo apt install zsh
> ```

Select option 2 to populate your .zshrc file with recommended settings.

Set zsh as the default linux bash shell.

> ```zsh
> chsh -s $(which zsh)
> ```

Lastly, install Oh-My-Zsh with the following command.

> ```zsh
> sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
>

### 3.5 Install useful Oh-My-Zsh extensions

At this point, you want to install a few extentension to make your shell experience more enjoyable (based entirely on a non quantitative personal experience).

First, install powerlevel9k. You will need later to re

> ```zsh
> git clone https://github.com/bhilburn/powerlevel9k.git ~/.oh-my-zsh/custom/themes/powerlevel9k
> ```

We will configure this in the next section. For the time being install the following exentions.

> ```zsh
> git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
> git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
> ```

You can find more information about [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md) and [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md) in their respective git repo.  In the next section, we will configure your .zshrc file to auto-start all of these downloaeded extensions.

### 3.6 Configure Oh-My-Zsh

To configure your theme, open your .zshrc file

> ```zsh
> nano ~/.zshrc
> ```

Add the following lines.

> ```vi
> ZSH_THEME="powerlevel9k/powerlevel9k"
> POWERLEVEL9K_MODE='nerdfont-complete'
> POWERLEVEL9K_LEFT_PROMPT_ELEMENTS=(context dir dir_writable vcs vi_mode)
> POWERLEVEL9K_RIGHT_PROMPT_ELEMENTS=(status)
> POWERLEVEL9K_PROMPT_ON_NEWLINE=true
> ```

If there was a previous `ZSH_THEME`, you can comment it out or delete it.

Next, add zsh-autosuggestions and zsh-syntax-highlighting extensions by editing the plugins list in your .zshrc file.

> ```vi
> plugins=(
>   git,
>   zsh-autosuggestions,
>   zsh-syntax-highlighting
> )
> ```
