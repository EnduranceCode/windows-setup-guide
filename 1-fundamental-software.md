# Setup guide for a development machine on Windows

This file contains the **Fundamental Software** section of my [Setup guide for a development machine on Windows](https://github.com/EnduranceCode/windows-development-machine). The introduction to this guide as well as its full *Table of Contents* can be found on the [README.md](./README.md) file of this repository. The *Table of Contents* of this section is listed below.

## Table of Contents

1. [Fundamental Software](#1-fundamental-software)
    1. [Google Chrome](#11-google-chrome)
    2. [KeePassXC](#12-keepassxc)
    3. [Windows Subsystem for Linux](#13-windows-subsystem-for-linux)
    4. [Windows Terminal](#14-windows-terminal)
    5. [Package Manager](#15-package-manager)

## 1. Fundamental Software

[**Google Chrome**](https://www.google.com/chrome/) is a cross-platform web browser developed by [Google](https://en.wikipedia.org/wiki/Google). With [Lubuntu](https://lubuntu.me) I normally choose [Firefox](https://www.mozilla.org/firefox/new/) but on Windows I normally use [**Google Chrome**](https://www.google.com/chrome/).

### 1.1. Google Chrome

[**Google Chrome**](https://www.google.com/chrome/) is a cross-platform web browser developed by [Google](https://en.wikipedia.org/wiki/Google).

#### 1.1.1. Installation

To install [**Google Chrome**](https://www.google.com/chrome/), start by downloading the latest version from [official downloads page](https://www.google.com/chrome/). Then, execute the downloaded file (there will be a prompt for elevated permissions that must be accepted).

#### 1.1.2. Configuration

Set [**Google Chrome**](https://www.google.com/chrome/) preferences as desired and then install the following extensions:

+ [AWS Extend Switch Roles](https://chrome.google.com/webstore/detail/aws-extend-switch-roles/jpmkfafbacpgapdghgdpembnojdlgkdl)
+ [JSON Formatter](https://chrome.google.com/webstore/detail/json-formatter/bcjindcccaagfpapjjmafapmmgkkhgoa)
+ [KeePassXC-Browser](https://chrome.google.com/webstore/detail/keepassxc-browser/oboonakemofpalcgghocfoadofidjkkk)
+ [Omnivore](https://chromewebstore.google.com/detail/omnivore/blkggjdmcfjdbmmmlfcpplkchpeaiiab)
+ [Proxy SwitchyOmega](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif)
+ [Raindrop.io](https://chromewebstore.google.com/detail/raindropio/ldgfbffkinooeloadekpmfoklnobpien)
+ [Tab Session Manager](https://chrome.google.com/webstore/detail/tab-session-manager/iaiomicjabeggjcfkbimgmglanimpnae)

Set the options of all the above extensions. Use the extensions settings backups/exports stored in the folder `%OneDriveCommercial%\dotfiles\chrome\extensions` to better customize the relevant extension.

### 1.2. KeePassXC

[**KeePassXC**](https://keepassxc.org/) is a cross-platform community-driven port of the Windows application [Keepass Password Safe](https://keepass.info/) that I choose to use precisely because it's cross-platform and it allows me to use it on every operating system that I work with.

#### 1.2.1. Installation

[Download](https://keepassxc.org/download/) the latest portable version of [**KeePassXC**](https://keepassxc.org/). Then extract the downloaded archive to the `%USERPROFILE%\AppData\Local\` folder (`%LOCALAPPDATA%`). Rename the new folder to `KeepassXC`.

Inside the folder `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Tools`, create a *shortcut* pointing to the file `%USERPROFILE%\AppData\Local\KeepassXC\KeePassXC.exe` and name it (the *shortcut*) `KeepassXC`. Then, edit the *shortcut* and point its icon to the main icon available on the file `%USERPROFILE%\AppData\Local\KeepassXC\KeePassXC.exe`.

#### 1.2.2. Configuration

Set [**KeePassXC**](https://keepassxc.org/) preferences (`Tools->Settings`) as desired but make sure to enable the `Browser Integrations`. Then, setup [KeePassXC-Browser](https://chrome.google.com/webstore/detail/keepassxc-browser/oboonakemofpalcgghocfoadofidjkkk) extension to integrate it with the machine's installation of [**KeePassXC**](https://keepassxc.org/).

#### 1.2.3. Upgrade

To upgrade [**KeepassXC**](https://keepassxc.org/), delete all files and folders inside the folder `%USERPROFILE%\AppData\Local\KeepassXC`, **EXCEPT** the folder `config`, and then extract the content of the archive of the new version to that `KeepassXC` folder.

### 1.3. Windows Subsystem for Linux

[Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/windows/wsl/) lets developers run a GNU/Linux environment directly on Windows.

#### 1.3.1. Installation

Follow the [Official instructions](https://learn.microsoft.com/windows/wsl/install-manual) to manually [enable](https://learn.microsoft.com/windows/wsl/install-manual#step-1---enable-the-windows-subsystem-for-linux) the [**WSL**](https://learn.microsoft.com/windows/wsl/), executing the upcoming command on a PowerShell console with *administrator privileges*.

    dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

Before restarting the machine, execute the below command on the same PowerShell console to [enable the Virtual Machine feature](https://learn.microsoft.com/windows/wsl/install-manual#step-3---enable-virtual-machine-feature).

    dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

Reboot the machine to be able to proceed with the [**WSL**](https://learn.microsoft.com/windows/wsl/) installation.

After rebooting your machine, set [**WSL 2**](https://learn.microsoft.com/windows/wsl/basic-commands#set-wsl-version-to-1-or-2) as your default version. executing the below command on a standard PowerShell console.

    wsl --set-default-version 2

[List all available Linux distributions](https://learn.microsoft.com/windows/wsl/basic-commands#list-available-linux-distributions) executing the bellow command on a standard PowerShell console.

    wsl --list --online

From the output of the above command, get the latest available [Ubuntu LTS version](https://ubuntu.com/about/release-cycle) and use it to replace the label **{DISTRO_NAME}** in the upcoming command. Then, execute it on a standard PowerShell console to set the [default distribuition](https://learn.microsoft.com/windows/wsl/basic-commands#set-default-linux-distribution).

    wsl --set-default {DISTRO_NAME}

Replace the label **{DISTRO_NAME}**, in the upcoming command, with the name of the latest available [Ubuntu LTS version](https://ubuntu.com/about/release-cycle) and then execute it on a standard PowerShell console to [install](https://learn.microsoft.com/windows/wsl/install#install-wsl-command) the latest available [Ubuntu LTS version](https://ubuntu.com/about/release-cycle).

    wsl --install -d {DISTRO_NAME}

The execution of the above command will [require elevation](https://learn.microsoft.com/windows/security/application-security/application-control/user-account-control/how-it-works), and therefore, Windows will prompt you to [elevate](https://learn.microsoft.com/windows/security/application-security/application-control/user-account-control/how-it-works#the-uac-user-experience). If you choose not to [elevate](https://learn.microsoft.com/windows/security/application-security/application-control/user-account-control/how-it-works#the-uac-user-experience), the [**WSL**](https://learn.microsoft.com/windows/wsl/) installation will fail.

To [update](https://learn.microsoft.com/windows/wsl/troubleshooting#updating-wsl) the [**WSL**](https://learn.microsoft.com/windows/wsl/) installation, execute the following command on a standard PowerShell console.

    wsl --update

On a regular PowerShell console, execute the below command to list the installed Linux distributions and check if everything is correct:

    wsl --list --verbose

If [Ubuntu](https://ubuntu.com/) is not running with [**WSL 2**](https://learn.microsoft.com/windows/wsl/), replace the **{LABEL}** in the below command as appropriate and execute it on a standard PowerShell console.

    wsl --set-version {DISTRO_NAME} 2

> **Label Definition**
>
> + **{DISTRO_NAME}** : Name of the Linux distribution to be executed with WSL 2

#### 1.3.2. Configuration

Once the process of installing [Ubuntu](https://ubuntu.com/) on [**WSL**](https://learn.microsoft.com/windows/wsl/) is complete, open the distribution using the *Start Menu*. You will be asked to [create a User and Password](https://learn.microsoft.com/windows/wsl/setup/environment#set-up-your-linux-username-and-password) for your [Ubuntu](https://ubuntu.com/) installation.

Configure the settings for your [Ubuntu](https://ubuntu.com/) installation, by using the `wsl.conf` file that is stored on `/etc` folder of every [**WSL**](https://learn.microsoft.com/windows/wsl/) distribuition. Open the file `/etc/wsl.conf` with the [nano text editor](https://www.nano-editor.org/), executing the below command on a [Ubuntu](https://ubuntu.com/) terminal.

    nano /etc/wsl.conf

To change the [default mount location](https://learn.microsoft.com/windows/wsl/wsl-config#automount-settings) of the Windows `C:\` drive from the default `/mnt/c` to `/c`, add the upcoming code snippet to the `/etc/wsl.conf` file.

    [automount]
    root=/

Then, to [enable systemd support](https://learn.microsoft.com/windows/wsl/wsl-config#systemd-support), add the upcoming code snippet to the same `/etc/wsl.conf` file.

    [boot]
    systemd=true

Save the changes with the command `CTRL + O` and then exit the [nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`.

To enable the changes made on the `wsl.conf` file, youl will need to to restart your [**WSL**](https://learn.microsoft.com/windows/wsl/) instances. It can be done with the execution of the bellow command on a standard PowerShell console.

    wsl.exe --shutdown

 Once [Ubuntu](https://ubuntu.com/) restarts, *systemd* should be running. You can confirm executing the below command on a [Ubuntu](https://ubuntu.com/) terminal, which will show the status of your services.

    systemctl list-unit-files --type=service

The article [Set up a WSL development environment](https://learn.microsoft.com/windows/wsl/setup/environment) has some good optional advices to setup a development environment with  [**WSL**](https://learn.microsoft.com/windows/wsl/), but one that is almost mandatory is the installation of the [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701).

#### 1.3.3. Update, upgrade and install additional packages

It's recommended to regularly update and upgrade your packages using [Ubuntu](https://ubuntu.com/)'s package manager. This is done with the following command:

    sudo apt update && sudo apt full-upgrade

Aditional sofware can be installed using [Ubuntu](https://ubuntu.com/)'s package manager, exactly as in any other [Ubuntu](https://ubuntu.com/) installation.

To be able to install software from its source code, you need to make sure your system has a C++ compiler. The `build-essentials` packages are meta-packages that include all the necessary tools for compiling software. You can install it with the following command:

    sudo apt install build-essential

To verify if the `build-essentials` installation was properly made, check the output of the following command:

    gcc --version

### 1.4. Windows Terminal

The [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701) is a terminal application for users of command-line tools and shells like Command Prompt, PowerShell, and WSL. Its main features include multiple tabs, panes, Unicode and UTF-8 character support, a GPU accelerated text rendering engine, and custom themes, styles, and configurations.

#### 1.4.1. Installation

Open the [Microsoft Store](https://aka.ms/wslstore) and install the [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701).

### 1.5. Package Manager

A package manager is a software that easily automates the installation, upgradation, and configuration of third-party software or dependencies. [**Chocolatey**](https://chocolatey.org/) and [**winget**](https://github.com/microsoft/winget-cli) are both package managers for Windows software. Nowadays, I prefer [**winget**](https://github.com/microsoft/winget-cli) over [**Chocolatey**](https://chocolatey.org/) because [**winget**](https://github.com/microsoft/winget-cli) can be used to install software from the [Microsoft Store](https://apps.microsoft.com/home).

#### 1.5.1. Install winget

Windows Package Manager [**winget**](https://github.com/microsoft/winget-cli) command-line tool is available on Windows 11 and modern versions of Windows 10 as a part of the [App Installer](https://apps.microsoft.com/detail/9NBLGGH4NNS1). To check if [**winget**](https://github.com/microsoft/winget-cli) is available, open a PowerShell console and execute the following command:

    winget --version

If [**winget**](https://github.com/microsoft/winget-cli) is already available on your system, the current version of the software will be displayed and now you should make sure it is updated with the latest version.

If you need to install [**winget**](https://github.com/microsoft/winget-cli), open the [Microsoft Store](https://aka.ms/wslstore) and install the [App Installer](https://apps.microsoft.com/detail/9NBLGGH4NNS1) because that's how [**winget**](https://github.com/microsoft/winget-cli) is distribuited.

Upgrading applications with [**winget**](https://github.com/microsoft/winget-cli) is very easy. To identify which apps are in need of an update, open a PowerShell console and execute the following command:

    winget upgrade

The above command will output a list of which app (if any) have an available update. To upgrade all applications with an available update, open a PowerShell console and execute the following command:

    winget upgrade --all

When running [**winget**](https://github.com/microsoft/winget-cli) without administrator privileges, some applications may [require elevation](https://learn.microsoft.com/windows/security/application-security/application-control/user-account-control/how-it-works) to install. On those cases, Windows will prompt you to elevate. If you choose not to elevate, the application will fail to install/upgrade.

Check the [official documentation](https://learn.microsoft.com/windows/package-manager/winget/) to know the full potential of [**winget**](https://github.com/microsoft/winget-cli).

#### 1.5.2. Install Chocolatey

If you are going to do your development work on the `Windows Native File System` (instead of doing it exclusively on the `WSL File System`) you should also install [**Chocolatey**](https://chocolatey.org/).

Before proceeding with the installation of [**Chocolatey**](https://chocolatey.org/), you must ensure **Get-ExecutionPolicy** is not ***Restricted***. The upcoming command, executed on a PowerShell console with *Administrator* priviliges. will output the current [execution policy](https://go.microsoft.com/fwlink/?LinkID=135170).

    Get-ExecutionPolicy

If the output of the above command shows ***Restricted***, then run the following command on the same PowerShell console:

    Set-ExecutionPolicy Bypass -Scope Process

Or the upcoming command, for quite a [bit more security](https://chocolatey.org/install).

    Set-ExecutionPolicy AllSigned

Then, on the same PowerShell console, execute the below command to install [**Chocolatey**](https://chocolatey.org/).

    Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

To list the installed chocolatey packages, execute the following command on a PowerShell console:

    choco list
