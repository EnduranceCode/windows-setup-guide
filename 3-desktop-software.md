# Setup guide for a development machine on Windows

This file contains the **Desktop Software** section of my [Setup guide for a development machine on Windows](https://github.com/EnduranceCode/windows-development-machine). The introduction to this guide as well as its full *Table of Contents* can be found on the [README.md](./README.md) file of this repository. The *Table of Contents* of this section is listed below.

## Table of Contents

3. [Desktop Software](#3-desktop-software)
    1. [Autenticação.gov](#31-autenticaçãogov)
    2. [GIMP](#32-gimp)
    3. [Inkscape](#33-inkscape)
    4. [PDFsam](#34-pdfsam)
    5. [SpeedCrunch](#35-speedcrunch)
    6. [Spotify](#36-spotify)
    7. [VLC](#37-vlc)

## 3. Desktop Software

### 3.1. Autenticação.gov

[**Autenticação.gov App**](https://www.autenticacao.gov.pt/) application allows the Portuguese citizens to take advantage of the electronic features of their Citizen Card.

#### 3.1.1. Installation

Download the [**Autenticação.gov App**](https://www.autenticacao.gov.pt/) from the [official downloads page](https://www.autenticacao.gov.pt/web/guest/cc-aplicacao).
Then, execute the downloaded file (there will be a prompt for elevated permissions that must be accepted).

It will, probably, be necessary to restart the machine to complete the [**Autenticação.gov App**](https://www.autenticacao.gov.pt/) installation.

Download the [**Autenticação.gov Plugin**](https://autenticacao.gov.pt/fa/ajuda/autenticacaogovpt.aspx) from the [official downloads page](https://autenticacao.gov.pt/fa/ajuda/autenticacaogovpt.aspx). Then, execute the downloaded file (there will be a prompt for elevated permissions that must be accepted).

#### 3.1.2. Configuration

Go through the [**Autenticação.gov App**](https://www.autenticacao.gov.pt/) configuration options and set it as desired, but make sure that the auto start is disabled. Do the same with the [**Autenticação.gov Plugin**](https://autenticacao.gov.pt/fa/ajuda/autenticacaogovpt.aspx).

### 3.2. GIMP

[**GIMP**](https://www.gimp.org/), an acronym for GNU Image Manipulation Program, is a multi-platform photo manipulation tool.

#### 3.2.1. Installation

To install [**GIMP**](https://www.gimp.org/), open a PowerShell console and execute the upcoming command to execute the installation from the [Microsoft Store](https://apps.microsoft.com/detail/XPDM27W10192Q0).

    scoop bucket add extras
    scoop install extras/gimp

### 3.3. Inkscape

[**Inkscape**](https://inkscape.org/) is a Free and open source vector graphics multi-platform editor that uses the standardized SVG file format as its main format, which is supported by many other applications including web browsers.

#### 3.3.1. Installation

To install [**Inkscape**](https://inkscape.org/), open a PowerShell console and execute the following command:

    scoop bucket add extras
    scoop install extras/inkscape

### 3.4. PDFsam

[**PDFsam Basic**](https://pdfsam.org/pdfsam-basic/) is a free and open-source cross-platform desktop application to split, merge, extract pages, rotate and mix PDF documents.

#### 3.4.1. Installation

To install [**PDFsam Basic**](https://pdfsam.org/pdfsam-basic/), execute the upcoming commands on a PowerShell console.

    scoop bucket add extras
    scoop install extras/pdfsam

### 3.5. SpeedCrunch

[**SpeedCrunch**](http://www.speedcrunch.org) is a high-precision scientific calculator featuring a fast, keyboard-driven user interface. It is free and open-source software, licensed under the GPL.

#### 3.5.1. Installation

To install [**SpeedCrunch**](http://www.speedcrunch.org), execute the upcoming commands on a PowerShell console.

    scoop bucket add extras
    scoop install extras/speedcrunch

### 3.6. Spotify

[**Spotify**](https://open.spotify.com/) is an application for the corresponding audio streaming and media service provider.

#### 3.6.1. Installation

To install [**Spotify**](https://open.spotify.com/), open a PowerShell console and execute the following commands:

    scoop bucket add extras
    scoop install extras/spotify

### 3.7. VLC

VLC is a free and open source cross-platform multimedia player and framework that plays most multimedia files as well as DVDs, Audio CDs, VCDs, and various streaming protocols.

#### 3.7.1. Installation

To install [**VLC**](https://www.videolan.org/), open a PowerShell console and execute the following commands:

    scoop bucket add extras
    scoop install extras/vlc
