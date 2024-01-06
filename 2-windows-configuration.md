# Setup guide for a development machine on Windows

This file contains the **Windows configuration** section of my [Setup guide for a development machine on Windows](https://github.com/EnduranceCode/windows-development-machine). The introduction to this guide as well as its full *Table of Contents* can be found on the [README.md](./README.md) file of this repository. The *Table of Contents* of this section is listed below.

## Table of Contents

2. [Windows configuration](#2-windows-configuration)
    1. [Keyboard and Mouse Software](#21-keyboard-and-mouse-software)
    2. [Windows Start Menu](#22-windows-start-menu)

## 2. Windows Configuration

### 2.1. Keyboard and Mouse Software

[**Mouse and Keyboard Center**](https://support.microsoft.com/topic/mouse-and-keyboard-center-download-f5b10905-7887-eedb-2f1c-d0737a36a3b2) is an application that helps you personalize and customize how you work on your PC with your keyboard and mouse. Off course that this application shall only be installed on systems that use one of the [supported devices](https://support.microsoft.com/en-us/topic/which-devices-are-supported-by-microsoft-mouse-and-keyboard-center-61ac6d03-9cc1-d7c6-ca9b-c9c8ce4cb303).

#### 2.1.1. Installation

To install [**Mouse and Keyboard Center**](https://support.microsoft.com/topic/mouse-and-keyboard-center-download-f5b10905-7887-eedb-2f1c-d0737a36a3b2), download the latest version from [official downloads page](https://support.microsoft.com/topic/mouse-and-keyboard-center-download-f5b10905-7887-eedb-2f1c-d0737a36a3b2). Then, execute the downloaded file (there will be a prompt for elevated permissions that must be accepted).

Move the application shortcut to the `%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\Tools` folder (Create the `Tools` folder if it doesn't exits).

### 2.2. Windows Start Menu

To have the Windows **Start Menu** with a [strtucture similar](https://specifications.freedesktop.org/menu-spec/latest/apa.html) to the one that have on my [Lubuntu](https://lubuntu.me) machines, the following folders must be created:

+ Audio & Video;
+ Development;
+ Graphics;
+ Network
+ Office
+ Utility

To create the above listed folders on the system wide **Start Menu**, open a PowerShell console with *Administrator* privileges and execute the following commands:

    mkdir "%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\Audio & Video"
    mkdir "%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\Development"
    mkdir "%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\Graphics"
    mkdir "%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\Network"
    mkdir "%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\Office"
    mkdir "%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\Utility"

On the same PowerShell console, move all the Office shortcuts to the folder `%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\Office`.

To create the above listed folders on the system wide **Start Menu**, open a regular PowerShell console and execute the following commands:

    mkdir "%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Audio & Video"
    mkdir "%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Development"
    mkdir "%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Graphics"
    mkdir "%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Network"
    mkdir "%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Office"
    mkdir "%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Utility"
