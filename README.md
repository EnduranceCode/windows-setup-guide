# Setup guide for a development machine on Windows

## Introduction

My [operating system (OS)](https://en.wikipedia.org/wiki/Operating_system) of choice is [Linux](https://en.wikipedia.org/wiki/Linux) and the distribution that I like to use is [Lubuntu](https://lubuntu.me). But, the majority of my professional work is done on [Windows](https://www.microsoft.com/en-us/windows) and I often need to setup a new machine or setup my machine to work on a new project. Therefore, I've created this guide to help me every time I need to perform such task.

This is my personal guide to setup a development machine on Windows. Although this is a very opinionated guide, I've decided to share it because it might be useful to somebody and, maybe, there will be someone out there that might be willing to help me improve the methodology that I normally follow. Please feel free to use this guide and make a [pull request](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) to suggest any improvement that you find important.

## Table of Contents

1. [Fundamental Software](./1-fundamental-software.md)
    1. [Browser](./1-fundamental-software.md#11-browser)
    2. [Windows Subsystem for Linux](./1-fundamental-software.md#12-windows-subsystem-for-linux)
    3. [Windows Terminal](./1-fundamental-software.md#13-windows-terminal)
    4. [Package Manager](./1-fundamental-software.md#14-package-manager)
    5. [Git & Git Bash](./1-fundamental-software.md#15-git--git-bash)
    6. [KeePassXC](./1-fundamental-software.md#16-keepassxc)
2. [Windows Configuration](./2-windows-configuration.md)
    1. [Advanced Windows Settings](./2-windows-configuration.md#21-advanced-windows-settings)
    2. [Power Management](./2-windows-configuration.md#22-power-management)
    3. [Custom Folders](./2-windows-configuration.md#23-custom-folders)
3. [Desktop Software](./3-desktop-software.md)
    1. [Autenticação.gov](./3-desktop-software.md#31-autenticaçãogov)
    2. [GIMP](./3-desktop-software.md#32-gimp)
    3. [Inkscape](./3-desktop-software.md#33-inkscape)
    4. [PDFsam](./3-desktop-software.md#34-pdfsam)
    5. [SpeedCrunch](./3-desktop-software.md#35-speedcrunch)
    6. [Spotify](./3-desktop-software.md#36-spotify)
    7. [VLC](./3-desktop-software.md#37-vlc)
4. [Development Software & Tools](./4-development-software-and-tools.md)
    1. [Notepad++](./4-development-software-and-tools.md#41-notepad)
    2. [Meld](./4-development-software-and-tools.md#42-meld)
    3. [Command Line Fuzzy Finder](./4-development-software-and-tools.md#43-command-line-fuzzy-finder)
    4. [Make](./4-development-software-and-tools.md#44-make)
    5. [jq](./4-development-software-and-tools.md#45-jq)
    6. [ripgrep](./4-development-software-and-tools.md#46-ripgrep)
    7. [OpenCode](./4-development-software-and-tools.md#47-opencode)
    8. [AWS CLI](./4-development-software-and-tools.md#48-aws-cli)
    9. [Granted](./4-development-software-and-tools.md#49-granted)
    10. [Docker](./4-development-software-and-tools.md#410-docker)
    11. [kubectl](./4-development-software-and-tools.md#411-kubectl)
    12. [kubectx](./4-development-software-and-tools.md#412-kubectx)
    13. [K9s](./4-development-software-and-tools.md#413-k9s)
    14. [Java](./4-development-software-and-tools.md#414-java)
    15. [Apache Maven](./4-development-software-and-tools.md#415-apache-maven)
    16. [Apache Tomcat](./4-development-software-and-tools.md#416-apache-tomcat)
    17. [Quarkus CLI](./4-development-software-and-tools.md#417-quarkus-cli)
    18. [Node.js](./4-development-software-and-tools.md#418-nodejs)
    19. [Terraform](./4-development-software-and-tools.md#419-terraform)
    20. [IntelliJ IDEA](./4-development-software-and-tools.md#420-intellij-idea)
    21. [Visual Studio Code](./4-development-software-and-tools.md#421-visual-studio-code)
    22. [Zed](./4-development-software-and-tools.md#422-zed)
    23. [DBeaver](./4-development-software-and-tools.md#423-dbeaver)
    24. [Postman](./4-development-software-and-tools.md#424-postman)
