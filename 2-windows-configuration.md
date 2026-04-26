# Setup guide for a development machine on Windows

This file contains the **Windows configuration** section of my [Setup guide for a development machine on Windows](https://github.com/EnduranceCode/windows-development-machine). The introduction to this guide as well as its full *Table of Contents* can be found on the [README.md](./README.md) file of this repository. The *Table of Contents* of this section is listed below.

## Table of Contents

2. [Windows configuration](#2-windows-configuration)
    1. [Advanced Windows Settings](#21-advanced-windows-settings)
    2. [Power Management](#22-power-management)
    3. [Custom Folders](#23-custom-folders)

## 2. Windows Configuration

### 2.1. Advanced Windows Settings

For details on the **Advanced Windows Settings**, refer to the [official Windows Advanced Settings documentation](https://learn.microsoft.com/en-us/windows/advanced-settings/).

#### 2.1.1. Enable Developer Mode

Developer Mode unlocks tools, settings, and features that are essential for many development tools. Enabling Developer Mode also allows you to create [symbolic links](https://blogs.windows.com/windowsdeveloper/2016/12/02/symlinks-windows-10/) without needing to run the Windows Command Prompt as an Administrator.

To enable *Windows Developer Mode*, follow the [official instructions](https://learn.microsoft.com/windows/apps/get-started/enable-your-device-for-development):

1. Open Windows Settings;
2. Go to **System > Advanced**, then scroll to the *For developers* section;
3. Toggle the *Developer Mode* setting, at the top of the *For developers* section (*Administrator* priviliges will be required);
4. Read the disclaimer. Click **Yes** to accept the change.

#### 2.1.2. Enable Long Paths

By default, Windows has a path limit of 260 characters. Modern development stacks (like Node.js with `node_modules`) often exceed this limit. You can remove this restriction via the **System** settings taking the following steps:

1. Open Windows Settings;
2. Go to **System > Advanced**, then scroll to the *File Explorer* section;
3. Toggle the *Enable long paths* setting (*Administrator* priviliges will be required).

The path limit can also be removed executing, on a PowerShell console with *Administrator* privileges, the following command:

```powershell
New-ItemProperty -Path "HKLM:\System\CurrentControlSet\Control\FileSystem" -Name "LongPathsEnabled" -Value 1 -PropertyType DWORD -Force
```

### 2.2. Power Management

Keeping the Laptop plugged after the battery is fully charged affect its health significantly, therefore its is recommended to keep the battery’s charge between 20% an 80%. On the Windows 10 **Power Management** we can setup an alarm/notification when the Laptop’s battery reaches a given low level. But there is no feature in Windows 10 to notify you when the battery reaches a given high level.

[John Howard](https://learn.microsoft.com/pt-pt/archive/blogs/jhoward/), Senior Program Manager in the Hyper-V team at Microsoft, [created a script](https://learn.microsoft.com/pt-pt/archive/blogs/jhoward/get-an-alert-when-my-battery-reaches-95) that gives an alert when the battery reaches 95%. I've adapted that script to give the alert when the the battery charges reaches 80% of it's capacity and I've stored on my [OneDrive](https://www.microsoft.com/microsoft-365/onedrive/online-cloud-storage), in my `dotfiles` folder.

If a [symlink](https://www.howtogeek.com/16226/complete-guide-to-symbolic-links-symlinks-on-windows-or-linux/) to the folder `%OneDriveCommercial%\dotfiles` isn't yet created the Windows `%USERPROFILE%`, create executing the below command from the Windows Command Line to be able to easily reference the `dotfiles` folder.

```cmd
mklink /J %USERPROFILE%\.dotfiles "%OneDriveCommercial%\dotfiles"
```

Then, to execute the above mentioned script on every Windows start up, inside the folder `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup`, create a *shortcut* pointing to the file `%USERPROFILE%\.dotfiles\scripts\FullBattery.vbs`.

### 2.3. Custom Folders

To easily access the custom folders referred in the below sections, you can pin it to *Quick Access*. It can be done taking the following steps:

1. Using the *File Explorer*, right-click on the new folder
2. Select **Pin to Quick Access**
3. The folder will appear in the left-hand sidebar of every File Explorer window

To customize the icon of the custom folders referred in the below sections, take the following steps:

1. Using the *File Explorer*, right-click on the new folder
2. Select **Properties**
3. Select the "Customize" tab on the shown pop-up window
4. Click the "Change Icon..." button
5. Select the desired icon on the new pop-up window and then click the "OK" button
6. Click the "Apply" button and then the "OK" button

#### 2.3.1. The `dev` folder

My preferred installation folder for all the developer tools that I use on Windows is `C:\dev`. This folder needs to be created, using the below command in a Windows Command Prompt:

```cmd
mkdir C:\dev
```

#### 2.3.2. The `code` folder

My preferred installation folder for all code repositories is `C:\code`. This folder needs to be created, using the below command in a Windows Command Prompt:

```cmd
mkdir C:\code
```

#### 2.3.3. The `Workspace` folder

Windows has a habit of treating the `Documents` folder like a digital junk drawer, where every game, printer driver, and random piece of software feels entitled to drop its configuration files. It clutters the `Documents` folder and I really hate it.

Therefore, I prefer to store all my personal work files in a folder, under the `Documents` folder, named `Workspace`. This folder needs to be created, using the below command in a Windows Command Prompt:

```cmd
mkdir %USERPROFILE%\Documents\Workspace
```
