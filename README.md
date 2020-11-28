# Setting Up WSL2

This is a guide to setting up a new Windows 10 machine with wsl2 using ubuntu 20 + zsh + oh-my-zsh + powerline9k

**Requirements**
* Windows 10, version 20H2 or greater
* [Ubuntu 20.04 LTS](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6?activetab=pivot:overviewtab&atc=true)
* [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab&atc=true&rtc=1)

## Table of content

1. Installing WSL2 and Windows Terminal

2. Setting up zsh and oh-my-zsh

3. Configuring Windows Terminal for Powerline9K

4. Configuring Git

## 1. Installing WSL2 and Windows Terminal

As of today, best instructions on installing wsl2 and windows terminal is directly from [Microsofts documentation](https://docs.microsoft.com/en-us/windows/wsl/install-win10). This section will cover a curtailed abridged version.

1.1 Enable wsl for you windows machine



> ```powershell
> ism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
> ```


1.2 Enable virtual machines on your PC

 
> ```powershell
> dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
> ``` 

1.3 Linux kernal update for wsl

This might change in the future.  As of 2020 November 27th, downloand and install the [wsl_update_x64.msi](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) from Microsoft. 

1.4


<div class="codeHeader" id="code-try-1" data-bi-name="code-header"><span class="language">PowerShell</span><button type="button" class="action is-relative" data-bi-name="copy" aria-label="Copy code">
<span class="icon">
<span class="docon docon-edit-copy" role="presentation"></span>
</span>
<span>Copy</span>
<div class="successful-copy-alert is-absolute has-right-zero has-top-zero has-left-zero has-bottom-zero is-flex has-flex-align-items-center has-flex-justify-content-center has-text-success-invert has-background-success is-transparent" aria-hidden="true">
<span class="icon is-size-large">
<span class="docon docon-check-mark" role="presentation"></span>
</span>
</div>
</button></div>
<pre tabindex="0" class="has-inner-focus"><code class="lang-powershell" data-author-content="dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
"><span>dism.exe /online /<span class="hljs-pscommand">enable-feature</span> /featurename:VirtualMachinePlatform /all /norestart
</span></code></pre>