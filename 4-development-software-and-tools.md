# Setup guide for a development machine on Windows

This file contains the **Development Software and Tools** section of my [Setup guide for a development machine on Windows](https://github.com/EnduranceCode/windows-development-machine). The introduction to this guide as well as its full *Table of Contents* can be found on the [README.md](./README.md) file of this repository. The *Table of Contents* of this section is listed below.

## Table of Contents

4. [Development Software & Tools](#4-development-software--tools)
    1. [Notepad++](#41-notepad)
    2. [Meld](#42-meld)
    3. [Command Line Fuzzy Finder](#43-command-line-fuzzy-finder)
    4. [Make](#44-make)
    5. [jq](#45-jq)
    6. [ripgrep](#46-ripgrep)
    7. [OpenCode](#47-opencode)
    8. [AWS CLI](#48-aws-cli)
    9. [Granted](#49-granted)
    10. [Docker](#410-docker)
    11. [kubectl](#411-kubectl)
    12. [kubectx](#12-kubectx)
    13. [K9s](#413-k9s)
    14. [Java](#414-java)
    15. [Apache Maven](#415-apache-maven)
    16. [Apache Tomcat](#416-apache-tomcat)
    17. [Quarkus CLI](#417-quarkus-cli)
    18. [Node.js](#418-nodejs)
    19. [Terraform](#419-terraform)
    20. [IntelliJ IDEA](#420-intellij-idea)
    21. [Visual Studio Code](#421-visual-studio-code)
    22. Eclipse
    23. [DBeaver](#423-dbeaver)
    24. [Postman](#424-postman)

## 4. Development Software & Tools

### 4.1 Notepad++

[**Notepad++**](https://notepad-plus-plus.org/) is a free and open-source text and source code editor for use with Microsoft Windows. It supports tabbed editing, which allows working with multiple open files in a single window.

#### 4.1.1. Installation

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**Notepad++**](https://notepad-plus-plus.org/), open a PowerShell console and execute the following commands:

```powershell
scoop bucket add extras
scoop install extras/notepadplusplus
```

#### 4.1.2. Configuration

On the menu option `Settings->Plugins Admin...`, install the plugins [**BetterMultiSelection**](https://github.com/dail8859/BetterMultiSelection), [**DSpellCheck**](https://github.com/Predelnik/DSpellCheck), [Json Tools](https://github.com/molsonkiko/JsonToolsNppPlugin) and [**XML Tools**](https://github.com/morbac/xmltools).

### 4.2 Meld

[**Meld**](https://meld.app/) is the visual diff and merge tool, targeted at developers. It allows users to compare two or three files or directories visually, color-coding the different lines.

[WinMerge](https://winmerge.org/) is an excellent alternative to [**Meld**](https://meld.app/) but there's only the [Windows](https://www.microsoft.com/en-us/windows) and [**Meld**](https://meld.app/) is multiplatform and that allows me to use the same software on every operating system that I work with.

#### 4.2.1. Installation

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**Meld**](https://meld.app/), open a PowerShell console and execute the following commands:

```powershell
scoop bucket add extras
scoop install extras/meld
```

### 4.3. Command Line Fuzzy Finder

The [**Command-line Fuzzy Finder | fzf**](https://github.com/junegunn/fzf) is a general-purpose command-line fuzzy finder. It's an interactive filter program for any kind of list; files, command history, processes, hostnames, bookmarks, git commits, etc. It implements a "fuzzy" matching algorithm, so you can quickly type in patterns with omitted characters and still get the results you want.

#### 4.3.1. Installation

##### 4.3.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

To install [**Command-line Fuzzy Finder | fzf**](https://github.com/junegunn/fzf) on the `WSL File System`, as recommended on the [official instructions](https://github.com/junegunn/fzf#linux-packages), execute the upcoming command on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
sudo apt install fzf
```

To verify if the [**fzf**](https://github.com/junegunn/fzf) installation was properly made, check the output of the following command:

```bash
fzf --version
fzf --help
```

Check the output of the previous command `fzf --help` to verify if the installed version supports [shell integration](https://github.com/junegunn/fzf#setting-up-shell-integration) and if it does, open the file `~/.bashrc` with the [Nano text editor](https://www.nano-editor.org/) and execute the following command:

```bash
nano ~/.bashrc
```

Then, add the upcoming snippet to the `~/.bashrc` file.

```bash
# Set up fzf key bindings and fuzzy completion
eval "$(fzf --bash)"
```

Save the changes with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`.

To enable the changes made, you will need to source the`~/.bashrc` file, executing the following command:

```bash
source ~/.bashrc
```

##### 4.3.2.1. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**fzf**](https://github.com/junegunn/fzf), open a PowerShell console and execute the following command:

```powershell
scoop install main/fzf
```

To verify if the [**fzf**](https://github.com/junegunn/fzf) installation was properly made, check the output of the following command:

```powershell
fzf --version
fzf --help
```

To set up shell integration with [Git Bash](https://git-scm.com/), open the file `~/.bashrc` with the [Nano text editor](https://www.nano-editor.org/), executing the below command on a [Git Bash](https://git-scm.com/) terminal.

```bash
nano ~/.bashrc
```

Then, add the upcoming snippet to the `~/.bashrc` file.

```bash
# Set up fzf key bindings and fuzzy completion
eval "$(fzf --bash)"
```

Save the changes with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`.

To enable the changes made, you will need to source the`~/.bashrc` file, executing the following command:

```bash
source ~/.bashrc
```

### 4.4. Make

[**GNU Make**](https://www.gnu.org/software/make/) is a tool which controls the generation of executables and other non-source files of a program from the program's source files.

#### 4.4.1. Installation

##### 4.4.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

To install [**GNU Make**](https://www.gnu.org/software/make/) on the `WSL File System`, execute the upcoming command on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
sudo apt install make
```

To verify if the [**GNU Make**](https://www.gnu.org/software/make/) installation was properly made, check the output of the following command:

```bash
make --version
```

##### 4.4.1.1. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**GNU Make**](https://www.gnu.org/software/make/) on the `Windows Native File System`, open a PowerShell console and execute the following command:

```powershell
scoop install main/make
```

To verify if the [**GNU Make**](https://www.gnu.org/software/make/) installation was properly made, check the output of the following command:

```powershell
make --version
```

### 4.5. jq

[**jq**](https://jqlang.org/) is a lightweight and flexible command-line JSON processor.

#### 4.5.1. Installation

##### 4.5.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

To install [**jq**](https://jqlang.org/) on the `WSL File System`, execute the upcoming command on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
sudo apt-get install jq
```

To verify if the [**jq**](https://jqlang.org/) installation was properly made, check the output of the following commands:

```bash
jq --version
jq --help
```

##### 4.5.1.1. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**jq**](https://jqlang.org/) on the `Windows Native File System`, open a PowerShell console and execute the following command:

```powershell
scoop install main/jq
```

To verify if the [**jq**](https://jqlang.org/) installation was properly made, check the output of the following commands:

```powershell
jq --version
jq --help
```

### 4.6. ripgrep

[**ripgrep**](https://github.com/BurntSushi/ripgrep) is a line-oriented search tool that recursively searches the current directory for a regex pattern.

#### 4.6.1. Installation

##### 4.6.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

To install [**ripgrep**](https://github.com/BurntSushi/ripgrep) on the `WSL File System`, following the [official instructions](https://github.com/BurntSushi/ripgrep#installation), replace the ***{LABEL}*** in the below commands as appropriate and then execute it on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
curl -LO https://github.com/BurntSushi/ripgrep/releases/download/{VERSION}/{DEBIAN_RELEASE_ASSET}
sudo dpkg -i {DEBIAN_RELEEASE_ASSET}
rm {DEBIAN_RELEEASE_ASSET}
```

> **Label Definition**
>
> + **{VERSION}**: The [latest release version](https://github.com/BurntSushi/ripgrep/releases), e.g. *15.1.0*
> + **{DEBIAN_RELEASE_ASSET}**: The [latest release Debian asset file name](https://github.com/BurntSushi/ripgrep/releases), e.g. *ripgrep_15.1.0-1_amd64.deb*

To verify if the [**ripgrep**](https://github.com/BurntSushi/ripgrep) installation was properly made, check the output of the following commands:

```bash
rg --version
rg --help
```

##### 4.6.1.1. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**ripgrep**](https://github.com/BurntSushi/ripgrep) on the `Windows Native File System`, open a PowerShell console and execute the following command:

```powershell
scoop install main/ripgrep
```

To verify if the [**ripgrep**](https://github.com/BurntSushi/ripgrep) installation was properly made, check the output of the following commands:

```powershell
rg --version
rg --help
```

### 4.7. OpenCode

[**OpenCode**](https://opencode.ai/) is an open source agent that helps you write code in your terminal, IDE, or desktop.

#### 4.7.1. Installation

##### 4.7.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

To install [**OpenCode**](https://opencode.ai/) on the `WSL File System`, following the [official instructions](https://opencode.ai/docs#install), execute the upcoming command on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
curl -fsSL https://opencode.ai/install | bash
```

Restart the *bash* section with the [following command](https://unix.stackexchange.com/a/217907):

```bash
exec "$SHELL"
```

To verify if the [**OpenCode**](https://opencode.ai/) installation was properly made, check the output of the following commands:

```bash
opencode --version
opencode --help
```

##### 4.7.1.1. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**OpenCode**](https://opencode.ai/) on the `Windows Native File System`, open a PowerShell console and execute the following command:

```powershell
scoop install main/opencode
```

To verify if the [**OpenCode**](https://opencode.ai/) installation was properly made, check the output of the following commands:

```powershell
opencode --version
opencode --help
```

### 4.8. AWS CLI

The [**AWS Command Line Interface (AWS CLI)**](https://aws.amazon.com/cli/) is a unified tool to manage your AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.

#### 4.8.1. Installation

##### 4.8.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

To install [**AWS CLI**](https://aws.amazon.com/cli/) on the `WSL File System`, take in consideration Linux's [AWS official instructions](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html) and execute the upcoming commands on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
curl https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip -o /tmp/awscliv2.zip
unzip /tmp/awscliv2.zip -d /tmp/
sudo /tmp/aws/install
```

To verify if the [**AWS CLI**](https://aws.amazon.com/cli/) installation was properly made, check the output of the following command:

```bash
aws --version
```

If the `aws` command cannot be found, you might need to restart your terminal or follow the troubleshooting in [Troubleshoot AWS CLI errors](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-troubleshooting.html).

[AWS](https://aws.amazon.com/) also provides a [Session Manager plugin](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html) that "enables you to establish secure connections to your Amazon Elastic Compute Cloud (EC2) instances, edge devices, on-premises servers, and virtual machines (VMs)". Follow the Debian and Ubuntu [official instructions](https://docs.aws.amazon.com/systems-manager/latest/userguide/install-plugin-debian-and-ubuntu.html) to install the [AWS Session Manager plugin](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html) on the `WSL File System` and download the `.deb` package executing the following command:

```bash
curl https://s3.amazonaws.com/session-manager-downloads/plugin/latest/ubuntu_64bit/session-manager-plugin.deb -o /tmp/session-manager-plugin.deb
```

To install the downloaded `.deb` package executing the following command:

```bash
sudo dpkg -i /tmp/session-manager-plugin.deb
```

Run the following commands to verify that the [AWS Session Manager plugin](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html) installed successfully.

```bash
session-manager-plugin
```

If the installation was successful, the following message is returned.

```bash
The Session Manager plugin is installed successfully. Use the AWS CLI to start a session.
```

##### 4.8.1.2. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**AWS CLI**](https://aws.amazon.com/cli/) on the `Windows Native File System`, open a PowerShell console and execute the following command:

```powershell
scoop install main/aws
```

To verify if the [**AWS CLI**](https://aws.amazon.com/cli/) installation was properly made, check the output of the following command:

```powershell
aws --version
```

If there's ant problem using the [**AWS CLI**](https://aws.amazon.com/cli/), follow the troubleshooting in [Troubleshoot AWS CLI errors](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-troubleshooting.html).

To install the [AWS Session Manager plugin](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html) on the `Windows Native File System`, open a PowerShell console and execute the following commands:

```powershell
scoop bucket add extras
scoop install extras/aws-session-manager-plugin
```

Run the following commands to verify that the [AWS Session Manager plugin](https://docs.aws.amazon.com/systems-manager/latest/userguide/session-manager.html) installed successfully.

```powershell
session-manager-plugin
```

If the installation was successful, the following message is returned.

```powershell
The Session Manager plugin is installed successfully. Use the AWS CLI to start a session.
```

### 4.9. Granted

[**Granted**](https://github.com/fwdcloudsec/granted) is a command line interface (CLI) application which simplifies access to cloud roles and allows multiple cloud accounts to be opened in your web browser simultaneously.

#### 4.9.1. Installation

##### 4.9.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

To install [**Granted**](https://github.com/fwdcloudsec/granted) on the `WSL File System`, take in consideration the [official Linux (APT) instructions](https://docs.commonfate.io/granted/getting-started) and execute the upcoming commands on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
sudo apt update
sudo apt install gpg wget ca-certificates
wget -O- https://apt.releases.commonfate.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/common-fate-linux.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/common-fate-linux.gpg] https://apt.releases.commonfate.io stable main" | sudo tee /etc/apt/sources.list.d/common-fate.list
sudo apt update
sudo apt install granted
```

To verify if the [**Granted**](https://github.com/fwdcloudsec/granted) installation was properly made, check the output of the following command:

```bash
granted --version
granted --help
```

To pin [**Granted**](https://github.com/fwdcloudsec/granted) backend to `file` execute the following commands:

```bash
mkdir -p ~/.granted/keyring
chmod 700 ~/.granted ~/.granted/keyring
granted settings set --setting Keyring.Backend --value file
granted settings set --setting Keyring.FileDir --value "${HOME}/.granted/keyring"
```
To set the browser opener unified to Windows default browser via the `XDG-OPEN` wrapper, execute the following commands:

```bash
granted settings set --setting DefaultBrowser --value CUSTOM
granted settings set --setting CustomBrowserPath --value "${HOME}/.local/bin/xdg-open"
granted settings set --setting CustomSSOBrowserPath --value "${HOME}/.local/bin/xdg-open"
```

To make [**Granted**](https://github.com/fwdcloudsec/granted) write SSO tokens to AWS’s standard cache location (`~/.aws/sso/cache`), which AWS CLI v2 reads, execute the following command:

```bash
granted settings set --setting ExportSSOToken --value true
```

To list all [**Granted**](https://github.com/fwdcloudsec/granted) settings execute the following command:

```bash
granted settings list
```

To set up [**Granted**](https://github.com/fwdcloudsec/granted) shell alias, open the file `~/.bashrc` with the [Nano text editor](https://www.nano-editor.org/), executing the following command:

```bash
nano ~/.bashrc
```

Then, add the upcoming snippet to the `~/.bashrc` file.

```bash
# Set Granted shell alias
#
# + https://docs.commonfate.io/granted/internals/shell-alias
# + https://docs.commonfate.io/granted/troubleshooting#manually-configuring-your-shell-profile
alias assume="source assume"
```

Save the changes with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`. To enable the changes made, you will need to source the `~/.bashrc` file, executing the following command:

```bash
source ~/.bashrc
```

Now, after running `assume <profile>`, you can run AWS CLI commands without `--profile` because the AWS environment variables are set in your current shell session. To confirm that `assume` is executed as expected, execute `assume <profile>` and then check the output of the following command:

```bash
aws configure list
```

##### 4.9.2.1. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**Granted**](https://github.com/fwdcloudsec/granted) on the `Windows Native File System`, open a PowerShell console and execute the following command:

```powershell
scoop install main/granted
```

To verify if the [**Granted**](https://github.com/fwdcloudsec/granted) installation was properly made, check the output of the following command:

```powershell
granted --version
granted --help
```

To pin [**Granted**](https://github.com/fwdcloudsec/granted) backend to `file` execute, on a [Git Bash](https://git-scm.com/) terminal, the following commands:

```bash
mkdir -p ~/.granted/keyring
chmod 700 ~/.granted ~/.granted/keyring
granted settings set --setting Keyring.Backend --value file
granted settings set --setting Keyring.FileDir --value "${HOME}/.granted/keyring"
```

To set the browser opener unified to Windows default browser via the `XDG-OPEN` wrapper, replace the ***{LABEL}*** in the below commands as appropriate and then execute it, on a [Git Bash](https://git-scm.com/) terminal.

```bash
granted settings set --setting DefaultBrowser --value FIREFOX
granted settings set --setting CustomSSOBrowserPath --value "{PATH_TO_DEFAULT_BROWSER}"
```

> **Label Definition**
>
> + **{PATH_TO_DEFAULT_BROWSER}**: The full path to the default browser executable file, e.g. *C:/Program Files/Mozilla Firefox/firefox.exe*

To make [**Granted**](https://github.com/fwdcloudsec/granted) write SSO tokens to AWS’s standard cache location (`~/.aws/sso/cache`), which AWS CLI v2 reads, execute, on a [Git Bash](https://git-scm.com/) terminal, the following command:

```bash
granted settings set --setting ExportSSOToken --value true
```

To list all [**Granted**](https://github.com/fwdcloudsec/granted) settings execute the following command:

```bash
granted settings list
```

To make `assume` behave in [Git Bash](https://git-scm.com/) like it does in PowerShell (i.e., set AWS environment variables in the current shell), add the following function to your `~/.bashrc`:

```bash
# Use Granted's bash wrapper so AWS_* variables persist in this bash session
assume() {
    local granted_folder="$HOME/scoop/apps/granted/current"

    # Temporarily add Granted's install folder to PATH so the bash wrapper can find `assumego.exe`
    # and source the Granted’s bash script so exports persist in the current shell.
    PATH="$granted_folder:$PATH" \
        . "$granted_folder/assume" "$@"
}
```

To enable the changes made, you will need to source the`~/.bashrc` file, executing the following command:

```bash
source ~/.bashrc
```

Now, after running `assume <profile>`, you can run AWS CLI commands without `--profile` because the AWS environment variables are set in your current [Git Bash](https://git-scm.com/) session. To confirm that `assume` is executed as expected, execute `assume <profile>` and then check the output of the following command:

```bash
aws configure list
```

### 4.10. Docker

[**Docker**](https://www.docker.com/) is an open-source containerization platform. It enables developers to package applications into containers, which are standardized, executable components combining application source code with the operating system libraries and dependencies required to run that code in any environment.

[**Docker**](https://www.docker.com/) updated its [Docker Desktop License Agreement](https://docs.docker.com/subscription/?ref=paulsblog.dev#docker-desktop-license-agreement) and this change means that on companies with more than 250 employees or more than $10 million in annual revenue you will not be able to use [Docker Desktop](https://www.docker.com/products/docker-desktop/) without a paid subscription. A possible alternative is [Rancher Desktop](https://rancherdesktop.io/) but, as the license update is only related to [Docker Desktop](https://www.docker.com/products/docker-desktop/), it's also possible to utilize [WSL](https://learn.microsoft.com/windows/wsl/) to run [**Docker**](https://www.docker.com/) or the [Docker Engine](https://docs.docker.com/engine/).

If you're going to do your development work on the Windows native file system, you should choose [Rancher Desktop](https://rancherdesktop.io/) to replace [Docker Desktop](https://www.docker.com/products/docker-desktop/). But if you're planning to do all you development work on the [WSL](https://learn.microsoft.com/windows/wsl/) file system (taking advantage of the Linux tools), you should utilize [WSL](https://learn.microsoft.com/windows/wsl/) to run [**Docker**](https://www.docker.com/) or the [Docker Engine](https://docs.docker.com/engine/).

#### 4.10.1. Pre-Installation requirements

To avoid future conflicts between the ports reserved by ***Hyper-V*** and the ports used by the [**Docker**](https://www.docker.com/) containers, you should [reset the "*TCP Dynamic Port Range*"](https://medium.com/@sevenall/completely-solve-the-problem-of-docker-containers-not-starting-or-running-on-windows-10-due-to-port-57f16ed6143). That is achieved executing the upcoming commands from a PowerShell console with *Administrator* privileges:

```powershell
netsh int ipv4 set dynamic tcp start=49152 num=16384
netsh int ipv6 set dynamic tcp start=49152 num=16384
```

Following the execution of the above commands, reboot the computer to apply the changes made.

After restarting the computer, check the output of the following command:

```powershell
netsh int ipv4 show dynamicport tcp
```

The above command should now show that "*TCP Dynamic Port Range*" has been changed to 49152–65535. Now only the ports in this range may be reserved by ***Hyper-V***.

#### 4.10.2. Installation

##### 4.10.2.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

This section describes the necessary steps to install [**Docker**](https://www.docker.com/) and [Docker Engine](https://docs.docker.com/engine/) on a [WSL](https://learn.microsoft.com/windows/wsl/) [Ubuntu](https://ubuntu.com/) distribution. The following steps are based on the [official documentation for installing Docker on Ubuntu](https://docs.docker.com/engine/install/ubuntu/) with some adaptations provided by [Paul Knulst](https://www.paulsblog.dev/how-to-install-docker-without-docker-desktop-on-windows/).

As per [**Docker**](https://www.docker.com/) [documentation](https://docs.docker.com/engine/install/ubuntu/#uninstall-old-versions), before you can install Docker Engine, you need to uninstall any conflicting packages. Do it executing the following command:

```bash
sudo apt remove docker.io docker-compose docker-compose-v2 docker-doc podman-docker containerd runc
sudo apt autoremove
```

On your [Ubuntu](https://ubuntu.com/) submodule of [WSL](https://learn.microsoft.com/windows/wsl/), install the required dependencies with the following commands:

```bash
sudo apt update
sudo apt install ca-certificates curl
```

To add the [**Docker**](https://www.docker.com/) stable repository, execute the following commands:

```bash
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Architectures: $(dpkg --print-architecture)
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
```

Install the latest version of the [**Docker**](https://www.docker.com/)'s packages with the following command:

```bash
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

Add you user to the `docker` group with the following command

```bash
sudo usermod -aG docker $USER
```

Log out and log back in so that your group membership is re-evaluated, or run the following command to activate the changes to groups:

```bash
newgrp docker
```

Check the installed versions using the following commands

```bash
docker --version
dockerd --version
docker compose version
docker info
```

On a standard [Ubuntu](https://ubuntu.com/) install, Docker is started by `systemd` automatically after installation. On [WSL](https://learn.microsoft.com/windows/wsl/), this depends on `systemd=true` being enabled (as in `/etc/wsl.conf`) and on the [WSL](https://learn.microsoft.com/windows/wsl/) distro session actually starting `systemd`.

```bash
sudo systemctl status docker.service
sudo systemctl status containerd.service
```

If [**Docker**](https://www.docker.com/) isn’t running, start it manually with the following commands:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

The default `iptables` frontend on [Ubuntu](https://ubuntu.com/) is usually `iptables-nft`. [**Docker**](https://www.docker.com/) works with `iptables-nft` and `iptables-legacy`, but if you experience Docker networking issues (for example, containers can’t reach the internet, port publishing doesn’t work, or firewall rules look wrong), you can try switching to the legacy backend as a troubleshooting step:

```bash
sudo update-alternatives --config iptables
sudo update-alternatives --config ip6tables
sudo systemctl restart docker.service
```

Then, verify if everything is running properly by checking the output of the following commands:

```bash
sudo systemctl status docker.service
sudo systemctl status containerd.service
docker run hello-world
```

When you run `docker login`, [**Docker**](https://www.docker.com/) may use a credential helper to store credentials. On Linux, `secretservice` requires a running DBus session *and* a Secret Service provider (commonly GNOME Keyring or KWallet). On a headless [WSL](https://learn.microsoft.com/windows/wsl/) [Ubuntu](https://ubuntu.com/) (no desktop environment), this is often not available, so using [`pass`](https://www.passwordstore.org/) is a practical alternative, which can be installed with the following command:

```bash
sudo apt install pass
```

When it's necessary to manage credentials with [**Docker**](https://www.docker.com/), [`pass`](https://www.passwordstore.org/) requires a GPG key to encrypt passwords and it can be created with the following command:

```bash
gpg --full-generate-key
```

Following the above command, when prompted, set the following options:

```bash
Kind of key:    {KEY_TYPE}
Key expiration: {KEY_EXPIRATION}
Real name:      {REAL_NAME}
Email address:  {EMAIL}
Passphrase:     {PASSPHRASE}
```

> **Label Definition**
>
> + **{KEY_TYPE}**: The cryptographic algorithm and usage for your keypair. Recommended for `pass`: `RSA and RSA` (creates a primary key for signing/certifying + a subkey for encryption).
> + **{KEY_SIZE}**: The size of the RSA key, in bits (security vs performance trade-off). Common choices: `3072` (good default) or `4096` (stronger, slightly slower).
> + **{KEY_EXPIRATION}**: When the key should expire. Examples: `0` (never expires), `1y` (expires in one year), `2y`, `6m`, etc.  
> + **{REAL_NAME}**: A human-readable name embedded in the key’s user ID (UID).
> + **{EMAIL}**: The email address embedded in the key’s UID. It does not have to be “real” for cryptographic purposes, but you should use something you’ll recognize.
> + **{PASSPHRASE}**: The passphrase that protects your private key on disk, if you forget it, you effectively lose the ability to decrypt previously stored secrets.

After generating the key, you can discover the Key ID with the following command:

```bash
gpg --list-secret-keys --keyid-format=long
```

Once the GPG key is created, replace the ***{LABEL}*** in the below command as appropriate and then execute it to initialize [`pass`](https://www.passwordstore.org/) with the GPG identity you want to use:

```bash
pass init {GPG_IDENTITY}
```

> **Label Definition**
>
> + **{GPG_IDENTITY}** : The email used when generating the key, or the key ID

Upon success of the GPG key initialization, edit the [**Docker**](https://www.docker.com/) configuration to use the [`pass`](https://www.passwordstore.org/) credentials helper executing the following commands:

```bash
mkdir -p ~/.docker
echo '{
    "credsStore": "pass"
}' > ~/.docker/config.json
```

##### 4.10.2.1. Installation on the Windows Native File System with Rancher Desktop

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

[**Rancher Desktop**](https://rancherdesktop.io/) is an app that provides container management and Kubernetes on the desktop. It is available for Mac (both on Intel and Apple Silicon), Windows, and Linux.

[**Rancher Desktop**](https://rancherdesktop.io/) installation is only necessary if you're going to do your development work on the Windows Native File System because, if you're going to do all you development work on the [WSL](https://learn.microsoft.com/windows/wsl/) file system, you should utilize [WSL](https://learn.microsoft.com/windows/wsl/) to run [**Docker**](https://www.docker.com/) or the [Docker Engine](https://docs.docker.com/engine/).

[Windows Linux Subsystem (WSL)](https://learn.microsoft.com/en-us/windows/wsl/) is required to run [**Rancher Desktop**](https://rancherdesktop.io/). If it isn't installed, follow the [instructions on this repository](./1-fundamental-software.md#13-windows-subsystem-for-linux) to install it.

To install [**Rancher Desktop**](https://rancherdesktop.io/), take the following steps:

1. **Download:** Get the latest version from the [releases page on GitHub](https://github.com/rancher-sandbox/rancher-desktop/releases) and execute the installer.
2. **Install:** When prompted, choose *Install for all users of this machine* (accept the elevated permissions prompt).
3. **Finish:** When the installation is finished, uncheck *Run Rancher Desktop* and click **Finish**.
4. **Launch:** Start Rancher Desktop from the Windows Start Menu.
5. **Configure:** On the welcome screen, uncheck `Enable Kubernetes` and select `dockerd` as the Container Engine.

Once the installation is completed, go through [**Rancher Desktop**](https://rancherdesktop.io/) preferences and set it as desired. It is recommended to enable *Automatically start at login* and also *Start in the background*.

To verify that the installation was successful, make sure [**Rancher Desktop**](https://rancherdesktop.io/) is running, then open a new PowerShell console and execute:

```powershell
wsl --list --verbose
```

You should see the [**Rancher Desktop**](https://rancherdesktop.io/) distros running. Next, test if the `docker` command is fully functional for your user:

```powershell
docker info
```

If you see detailed information about the Docker installation, you are done! No further action is necessary.

If `docker info` returns a permission error (e.g., "Access is denied"), your Windows user lacks the privileges to interact with the Docker socket. You will need to add your user to the `docker-users` group and that can be done taking the following steps:

1. On a PowerShell console, check if the group exists and your membership by running:

```powershell
net localgroup docker-users
```

2. If the `docker-users` group doesn't exists yet, open a PowerShell console with *Administrator* privileges and [create it](https://stackoverflow.com/a/64293327) with the following commands:

```powershell
New-LocalGroup -Name 'docker-users' -Description 'docker Users Group'
```

3. On a PowerShell console with *Administrator* privileges, add your Windows user to the group (replace `{YOUR_USER_ID}` with your exact Windows username, found by looking at the folder name under `C:\Users\`):

```powershell
net localgroup docker-users "{YOUR_USER_ID}" /ADD
```

> **Security Note: Avoid the "Administrator" Workaround**
>
> You might find older tutorials or StackOverflow answers (like the one linked above) suggesting you run `Add-LocalGroupMember -Group 'Administrators' -Member ('docker-users')` to fix this issue. Do not do this. Adding the docker-users group to the Windows Administrators group is a severe security risk that grants full system control to anyone in the group.
>
> How it actually works: The Docker/Rancher background service runs with elevated privileges and listens for commands via a Windows "Named Pipe" (`//./pipe/docker_engine`). By default, the service is programmed to look for a local group called exactly `docker-users`. If this group exists, the service explicitly allows members of that group to send commands through the pipe.
>
> By simply creating the group, adding your user, and logging out/in (which refreshes your Windows security token), the Docker service will securely grant your user access to the pipe without needing to compromise your entire machine's security.

4. Log out of Windows and log back in to apply the group membership changes.

     + Click the Start button;
     + Click your User Profile Icon;
     + Select Sign out;
     + Log back into Windows.

5. Confirm that everything is correct, executing on a [Git Bash](https://git-scm.com/) terminal the following commands:

```bash
docker info
docker --version
kubectl version --client
```

The [**Rancher Desktop**](https://rancherdesktop.io/) installation and usage files are stored in the following folder:

+ `%USERPROFILE%\AppData\Local\rancher-desktop` contains the distribution data, container images, logs, etc;

### 4.11. kubectl

[**kubectl**](https://kubernetes.io/docs/reference/kubectl/) is the command line tool for controlling Kubernetes clusters. It allows you to deploy applications, inspect and manage cluster resources, and view logs.

#### 4.11.1. Installation

##### 4.11.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

Following the [official instructions](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/#install-using-native-package-management), install the [**kubectl**](https://kubernetes.io/docs/reference/kubectl/) dependencies with the following commands:

```bash
sudo apt update
sudo apt install apt-transport-https ca-certificates curl gnupg
```

Download the public signing key for the [Kubernetes](https://kubernetes.io/) package repositories. The same signing key is used for all repositories so you can disregard the version in the URL:

```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.35/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
sudo chmod 644 /etc/apt/keyrings/kubernetes-apt-keyring.gpg
```

Add the appropriate Kubernetes apt repository. If you want to use Kubernetes version different than *v1.35*, replace *v1.35* with the desired version (check the [official instructions](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/#install-using-native-package-management)) in the command below:

```bash
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.35/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
```

Install [**kubectl**](https://kubernetes.io/docs/reference/kubectl/) with the following command:

```bash
sudo apt update
sudo apt install kubectl
```

Verify the installation:

```bash
kubectl version --client
```

> **Note**
>
> If you want to prevent [**kubectl**](https://kubernetes.io/docs/reference/kubectl/) from being automatically updated by `apt upgrade`, you can hold the package:
>
> ```bash
> sudo apt-mark hold kubectl
> ```

> **Note**
>
> To upgrade [**kubectl**](https://kubernetes.io/docs/reference/kubectl/) to another minor release, you'll need to bump the version in `/etc/apt/sources.list.d/kubernetes.list` before running `apt update` and `apt-get upgrade`. This procedure is described in more detail in [Changing The Kubernetes Package Repository](https://kubernetes.io/docs/tasks/administer-cluster/kubeadm/change-package-repository/).

### 4.12. kubectx

[**kubectx**](https://github.com/ahmetb/kubectx/) is a tool to switch between contexts (clusters) on `kubectl` faster. It also includes`kubens`, which is a tool to switch between Kubernetes namespaces (and configure them for `kubectl`) easily.

#### 4.12.1. Installation

##### 4.12.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

To install [**kubectx**](https://github.com/ahmetb/kubectx/) on the `WSL File System`, as recommended on the [official instructions](https://github.com/ahmetb/kubectx/#installation), execute the upcoming command on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
sudo apt install kubectx
```

To verify if the [**kubectx**](https://github.com/ahmetb/kubectx/) installation was properly made, check the output of the following command:

```bash
kubectx --version
kubectx --help
```

##### 4.12.2.1. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**kubectx**](https://github.com/ahmetb/kubectx/) on the `Windows Native File System`, open a PowerShell console and execute the following command:

```powershell
scoop install main/kubectx
```

To verify if the [**kubectx**](https://github.com/ahmetb/kubectx/) installation was properly made, check the output of the following command:

```powershell
kubectx --version
kubectx --help
```

### 4.13. K9s

[**K9s**](https://github.com/derailed/k9s) provides a terminal UI to interact with your Kubernetes clusters. The aim of the project is to make it easier to navigate, observe and manage your applications in the wild. [**K9s**](https://github.com/derailed/k9s) continually watches Kubernetes for changes and offers subsequent commands to interact with your observed resources.

#### 4.13.1. Installation

##### 4.13.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

To install [**K9s**](https://github.com/derailed/k9s)) on the `WSL File System`, as recommended on the [official instructions](https://github.com/derailed/k9s#installation), execute the upcoming commands on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
wget -P /tmp https://github.com/derailed/k9s/releases/latest/download/k9s_linux_amd64.deb
sudo apt install /tmp/k9s_linux_amd64.deb
rm /tmp/k9s_linux_amd64.deb
```

To verify if the [**K9s**](https://github.com/derailed/k9s) installation was properly made, check the output of the following commands:

```bash
k9s version
k9s info
k9s help
```

If the command `k9s info` shows a warning/error stating "*ERROR Unable to reads k9s config file*", that's because it was just installed and haven't actually been launched yet. By design, [**K9s**](https://github.com/derailed/k9s) does not create its configuration files or folders during the apt install process. Instead, it generates them dynamically the very first time you start the program. All you need to do is launch [**K9s**](https://github.com/derailed/k9s) once to initialize your environment.

##### 4.13.2.1. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**K9s**](https://github.com/derailed/k9s) on the `Windows Native File System`, open a PowerShell console and execute the following command:

```powershell
scoop install main/k9s
```

To verify if the [**K9s**](https://github.com/derailed/k9s) installation was properly made, check the output of the following commands:

```powershell
k9s version
k9s info
k9s help
```

### 4.14. Java

[**Java**](https://openjdk.org/) is a high-level, class-based, object-oriented programming language that is designed to have as few implementation dependencies as possible. It is a general-purpose programming language intended to let programmers write once, run anywhere, meaning that compiled Java code can run on all platforms that support Java without the need to recompile.

#### 4.14.1. Installation

##### 4.14.1.1. Installation the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

The easiest way to install and manage multiple versions of [**Java**](https://openjdk.org/) on the `WSL File System` is to use [SDKMAN](https://sdkman.io/). This is a free, lightweight, open-source utility written in [Bash](https://www.gnu.org/software/bash/) that provides a convenient command line interface to manage multiple versions of [**Java**](https://openjdk.org/) and also takes care of setting the necessary environment variables.

Following the [official instructions](https://sdkman.io/install), install [SDKMAN](https://sdkman.io/) and the necessary dependencies executing the upcoming commands on a [Ubuntu](https://ubuntu.com/) terminal:

```bash
sudo apt update
sudo apt install zip unzip
curl -s "https://get.sdkman.io" | bash
```

After completing the installation process, open a new terminal or run the following command in the same shell:

```bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
```

To confirm the installation's success, execute the following command:

```bash
sdk version
```

To list the available [**Java**](https://openjdk.org/) versions, execute the following command:

```bash
sdk list java
```

To install a specific version of [**Java**](https://openjdk.org/), replace the **{LABEL}** in the upcoming command as appropriate and then execute it:

```bash
sdk install java {IDENTIFIER}
```

> **Label Definition**
>
> + **{IDENTIFIER}** : Identifier of the desired [**Java**](https://openjdk.org/) version as shown in the output of the command `sdk list java`, e.g. *21.ea.35-open*

To set a specific version of [**Java**](https://openjdk.org/) as the default, replace the **{LABEL}** in the upcoming command as appropriate and then execute it:

```bash
sdk default java {IDENTIFIER}
```

> **Label Definition**
>
> + **{IDENTIFIER}** : Identifier of the desired [**Java**](https://openjdk.org/) version as shown in the output of the command `sdk list java`, e.g. *21.ea.35-open*

Restart the *bash* section with the [following command](https://unix.stackexchange.com/a/217907):

```bash
exec "$SHELL"
```

To check if the `JAVA_HOME` value was properly set, check the output of the following command:

```bash
echo $JAVA_HOME
```

To check if the Windows `PATH` value was properly set, check the output of the following command:

```bash
echo $PATH
```

To check if [**Java**](https://openjdk.org/) was properly installed, check the output of the following command:

```bash
java -version
```

If everything is correct, the above command will output **Java Runtime Environment** version.

Finally, to check if the **Java Compiler** was properly installed, check the output of the following command:

```bash
javac -version
```

If everything is correct, the above command will output the **Java Compiler** version.

When using applications like [Zscaler](https://www.zscaler.com/), it might be necessary to import security certificate to the [**Java**](https://openjdk.org/) Keystore. Do it by replacing the **{LABELS}** in the upcoming command as appropriate and then execute it:

```bash
keytool -importcert -trustcacerts -alias {CERTIFICATE_ALIAS} -file {PATH_TO_DER_CERTIFICATE} -keystore $JAVA_HOME/lib/security/cacerts -storepass changeit -noprompt
```

> **Label Definition**
>
> + **{PATH_TO_DER_CERTIFICATE}** : Path to the `.der` certificate file
> + **{CERTIFICATE_ALIAS}**       : The chosen certificate alias

To confirm that the certificate was added to the JRE keystore, replace the **{LABELS}** in the upcoming command as appropriate and then execute it:

```bash
keytool -v -list -keystore $JAVA_HOME/lib/security/cacerts -alias {CERTIFICATE_ALIAS} -storepass changeit -noprompt
```

> **Label Definition**
>
> + **{CERTIFICATE_ALIAS}** : The chosen certificate alias

##### 4.14.1.2. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

The instructions shown here describe how to manually install [**Java**](https://openjdk.org/) on the `Windows Native File System` for the current *user account*.

Start by creating the folder where [**Java**](https://openjdk.org/) will be installed, executing, on a **Git Bash** terminal the following commands:

```bash
mkdir -p /c/dev/java/candidates
```

Download the *.zip* option of the desired [JDK version and vendor](https://javaalmanac.io/). Then, unpack it to a folder inside `C:\dev\java\candidates`. Rename the extracted folder taking in consideration the following structure:

    {VENDOR}-{VERSION}-{PROJECT}

The different parts in the above name structure, shall be replaced as explained next:

> + **{VENDOR}** : The Java vendor's name, e.g. *oracle*
> + **{VERSION}** : The Java version number, including the string *jdk*, e.g. *jdk1.8.0.231*
> + **{PROJECT}** : The name of the project where this version of Java will be used, e.g. *sa3*
>
> With the above examples, the JDK folder name would be *oracle-jdk1.8.0.231-sa3*

To have more control over [**Java**](https://openjdk.org/) versions and updates, you will create a symbolic link named`current` that will target the desired [**Java**](https://openjdk.org/) candidate folder. But, to be able to do so without Administrator priviliges, you need to enable Windows **Developer Mode** which can be done following the [Advanced Windows Settings](./2-windows-configuration.md#21-advanced-windows-settings) of this guide.

With **Developer Mode** enabled, replace the **{LABEL}** in the upcoming command as appropriate and then execute it, on a Windows Command Prompt, to create a symbolic link named `current` that targets the the desired [**Java**](https://openjdk.org/) candidate folder:

```cmd
mklink /J C:\dev\java\candidates\{JAVA_CANDIDATE} C:\dev\java\current
```

> + **{JAVA_CANDIDATE}** : The folder's name that contains the desired Java candidate, e.g. *oracle-jdk1.8.0.231-sa3*

Check the output of the upcoming commands to confirm that the the symlink was created as desired:

```cmd
dir C:\dev\java\candidates\
dir C:\dev\java\candidates\current\
```

Later if you want to upgrade and/or change the [**Java**](https://openjdk.org/) version in use, you can simply unpack the newer version and change the symlink to point to the latest version.

```cmd
del C:\dev\java\candidates\current
mklink /J C:\dev\java\candidates\{JAVA_CANDIDATE} C:\dev\java\current
```

To set `JAVA_HOME` as environment variable for the current *user account*, press `WIN + R`, type `rundll32.exe sysdm.cpl,EditEnvironmentVariables` and then press `Enter`.

On the ***User variables*** section, click the **New** button and fill the *Variable name* input box with `JAVA_HOME` and *Variable value* input box with the path `C:\dev\java\current` . If a `JAVA_HOME` already exists, select it and click the **Edit** button, then fill the *Variable value* input box with the path `C:\dev\java\current`.

Still on the ***User variables*** section, select the `Path` variable and click the **Edit** button. Then, click the **New** button and fill the input box with the following value:

  %JAVA_HOME%\bin

Click the **OK** button to close the window used to edit the `PATH` variable and then click the **OK** button on the *environment variables* window to close it.

To check if the Windows `JAVA_HOME` value was properly set, open a Windows Command Prompt and check the output of the following command:

```cmd
echo %JAVA_HOME%
```

To check if the Windows `PATH` value was properly set, on the same Windows Command Prompt, check the output of the following command:

```cmd
echo %PATH%
```

To check if [**Java**](https://openjdk.org/) was properly installed, on the same Windows Command Prompt, check the output of the following command:

```cmd
java -version
```

If everything is correct, the above command will output **Java Runtime Environment** version.

Finally, to check if the **Java Compiler** was properly installed, on the same Windows Command Prompt, check the output of the following command:

```cmd
javac -version
```

If everything is correct, the above command will output the **Java Compiler** version.

When using applications like [Zscaler](https://www.zscaler.com/), it might be necessary to import security certificate to the [**Java**](https://openjdk.org/) Keystore. On a **Git Bash** terminal, replace the **{LABELS}** in the upcoming command as appropriate and then execute it:

```bash
keytool -importcert -trustcacerts -alias {CERTIFICATE_ALIAS} -file {PATH_TO_DER_CERTIFICATE} -keystore $JAVA_HOME/lib/security/cacerts -storepass changeit -noprompt
```

> **Label Definition**
>
> + **{PATH_TO_DER_CERTIFICATE}** : Path to the `.der` certificate file
> + **{CERTIFICATE_ALIAS}**       : The chosen certificate alias

To confirm that the certificate was added to the JRE keystore, replace the **{LABELS}** in the upcoming command as appropriate and then execute it:

```bash
keytool -v -list -keystore $JAVA_HOME/lib/security/cacerts -alias {CERTIFICATE_ALIAS} -storepass changeit -noprompt
```

> **Label Definition**
>
> + **{CERTIFICATE_ALIAS}** : The chosen certificate alias

### 4.15. Apache Maven

[**Apache Maven**](https://maven.apache.org/) is a build automation tool used primarily for Java projects. It can also be used to build and manage projects written in C#, Ruby, Scala, and other languages and it is hosted by the [Apache Software Foundation](https://en.wikipedia.org/wiki/Apache_Software_Foundation).

#### 4.15.1. Installation

##### 4.15.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

To be able to install a specific [**Apache Maven**](https://maven.apache.org/) version on the `WSL File System`, I like to follow a procedure inspired by the [Linuxiz Blog](https://linuxize.com/post/how-to-install-apache-maven-on-ubuntu-18-04/).

Start by creating the folder where [**Apache Maven**](https://maven.apache.org/) will be installed, executing the following commands:

```bash
sudo mkdir -p /opt/maven/candidates
sudo chown -R $USER:$USER /opt/maven/
```

Check the output of the upcoming command to confirm that the folder was created as desired:

```bash
ls -la --group-directories-first /opt
```

To download the desired [**Apache Maven**](https://maven.apache.org/) version in the `/tmp` directory, replace the **{LABEL}** in the upcoming command as appropriate and then execute it:

```bash
wget {DOWNLOAD_LINK} -P /tmp
```

> **Label Definition**
>
> + **{DOWNLOAD_LINK}** : Download link to the binary `tar.gz` archive take from the official [download page](https://maven.apache.org/download.cgi)

Once the download is completed, extract the archive in the `/opt/candidates` directory with the following command:

```bash
tar xf /tmp/apache-maven-*.tar.gz -C /opt/maven/candidates/
```

Check the output of the upcoming command to confirm that the folder was created as desired:

```bash
ls -la --group-directories-first /opt/maven/candidates
```

Then, rename the extracted folder taking in consideration the following structure:

```bash
apache-maven-{VERSION}-{PROJECT}
```

The different parts in the above name structure, shall be replaced as explained next:

> + **{VERSION}** : The Maven version number, e.g. *3.8.6*
> + **{PROJECT}** : The name of the project where this instance of Maven will be used, e.g. *sa3*
>
> With the above examples, the Maven folder name would be *apache-maven-3.8.6-sa3*

Check the output of the upcoming command to confirm that the folder was renamed as desired:

```bash
ls -la --group-directories-first /opt/maven/candidates
```

To have more control over [**Apache Maven**](https://maven.apache.org/) versions and updates, replace the **{LABEL}** in the upcoming command as appropriate and then execute it to create a symbolic link `current` that will point to the [**Apache Maven**](https://maven.apache.org/) installation folder:

```bash
ln -s /opt/maven/candidates/{MAVEN_FOLDER} /opt/maven/current
```

> + **{MAVEN_FOLDER}** : The folder's name that contains the desired version, e.g. *apache-maven-3.8.6-sa3*

Check the output of the upcoming commands to confirm that the the symlink was created as desired:

```bash
ls -la --group-directories-first /opt/maven/
ls -la --group-directories-first /opt/maven/current/
```

Later if you want to upgrade your [**Apache Maven**](https://maven.apache.org/) installation you can simply unpack the newer version and change the symlink to point to the latest version.

To set the `MAVEN_HOME` environment variable for your [WSL](https://learn.microsoft.com/windows/wsl/) user, open the file `~/.bashrc` with the [Nano text editor](https://www.nano-editor.org/), executing the below command on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
nano ~/.bashrc
```

Then, add the upcoming snippet to the `~/.bashrc` immediately before sourcing the file to customize the bash prompt.

```bash
# User's environment variables
export MAVEN_HOME=/opt/maven/current

# User's path customization
export PATH=${MAVEN_HOME}/bin:${PATH}
```

Save the changes with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`.

To enable the changes made, you will need to source the`~/.bashrc` file, executing the following command:

```bash
source ~/.bashrc
```

To check if the `MAVEN_HOME` environment variable was properly set, check the output of the following command:

```bash
echo $MAVEN_HOME
```

To check if the users's `PATH` was properly set, check the output of the following command:

```bash
echo $PATH
```

To check if **Apache Maven** was properly installed, check the output of the following command:

```bash
mvn -version
```

If everything is correct, the above command will output the **Apache Maven** version.

##### 4.15.1.2. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**Apache Maven**](https://maven.apache.org/), download the desired [Binary zip archive](https://maven.apache.org/download.cgi) and unpack it to the folder `C:\dev\apache-maven\candidates`. Rename the extracted folder taking in consideration the following structure:

    apache-maven-{VERSION}-{PROJECT}

The different parts in the above name structure, shall be replaced as explained next:

> + **{VERSION}** : The Maven version number, e.g. *3.8.6*
> + **{PROJECT}** : The name of the project where this instance of Maven will be used, e.g. *sa3*
>
> With the above examples, the Maven folder name would be *apache-maven-3.8.6-sa3*

To have more control over [**Apache Maven**](https://maven.apache.org/) versions and updates, you will create a symbolic link named `current` that will target the desired [**Apache Maven**](https://maven.apache.org/) candidate folder. But, to be able to do so without Administrator priviliges, you need to enable Windows **Developer Mode** which can be done following the [Advanced Windows Settings](./2-windows-configuration.md#21-advanced-windows-settings) of this guide.

With **Developer Mode** enabled, replace the **{LABEL}** in the upcoming command as appropriate and then execute it, on a Windows Command Prompt, to create a symbolic link named `current` that targets the the desired [**Apache Maven**](https://maven.apache.org/) candidate folder:

```cmd
mklink /J C:\dev\maven\candidates\{MAVEN_CANDIDATE} C:\dev\maven\current
```

> + **{MAVEN_CANDIDATE}** : The folder's name that contains the desired Maven candidate, e.g. *apache-maven-3.8.6-sa3*

Check the output of the upcoming commands to confirm that the the symlink was created as desired:

```cmd
dir C:\dev\maven\candidates\
dir C:\dev\maven\candidates\current\
```

Later if you want to upgrade and/or change the [**Apache Maven**](https://maven.apache.org/) version in use, you can simply unpack the newer version and change the symlink to point to the desired candidate.

```cmd
del C:\dev\maven\candidates\current
mklink /J C:\dev\maven\candidates\{MAVEN_CANDIDATE} C:\dev\maven\current
```

To set the `MAVEN_HOME` environment variable for the current *user account*, press `WIN + R`, type `rundll32.exe sysdm.cpl,EditEnvironmentVariables` and then press `Enter`.

On the ***User variables*** section, click the **New** button and fill the *Variable name* input box with **MAVEN_HOME** and the *Variable value* input box with the path to the **Apache Maven** folder. If a `MAVEN_HOME` already exists, select it and click the **Edit** button, then fill the *Variable value* input box with the path to the **Apache Maven** installation folder.

Still on the ***User variables*** section, select the `Path` variable and click the **Edit** button. Then, click the **New** button and fill the input box with the following value:

    %MAVEN_HOME%\bin

Click the **OK** button to close the window used to edit the `PATH` variable and then click the **OK** button on the *environment variables* window to close it.

To check if the Windows `MAVEN_HOME` value was properly set, open a Windows Command Prompt and check the output of the following command:

```cmd
echo %MAVEN_HOME%
```

To check if the Windows `PATH` value was properly set, on the same Windows Command Prompt, check the output of the following command:

```cmd
echo %PATH%
```

To check if **Apache Maven** was properly installed, on the same Windows Command Prompt, check the output of the following command:

```cmd
mvn -version
```

If everything is correct, the above command will output the **Apache Maven** version.

#### 4.15.2. Configuration

The default location for the user's settings file and for the *Maven Local Repository* is the `.m2` folder at the user's *Home Folder*. Check it it already exists and if it doesn't create it with the upcoming command. If [**Apache Maven**](https://maven.apache.org/) is installed on the `WSL File System`, use a [Ubuntu](https://ubuntu.com/) terminal and if it is installed on the `Windows Native File System` use a  [Git Bash](https://git-scm.com/) terminal.

```bash
mkdir -p ~/.m2
```

The development environment will better contained if a *Maven Local Repository* is set for each project. Therefore, replace the **{LABEL}** in the upcoming command as appropriate and execute it. If [**Apache Maven**](https://maven.apache.org/) is installed on the `WSL File System`, use a [Ubuntu](https://ubuntu.com/) terminal and if it is installed on the `Windows Native File System` use a [Git Bash](https://git-scm.com/) terminal.

```bash
mkdir -p ~/.m2/repository-{PROJECT}
```

> **Label Definition**
>
> + **{PROJECT}** : The label that identifies the project name

To set the folder created with the above command as the custom location for the *Maven Local Repository*, edit the file `settings.xml` located at the `conf` folder of the **Apache Maven** installation folder, first replace the **{LABEL}** in the below snippet as appropriate and then insert the it immediately after the *localRepository* comment section.

    <localRepository>${user.home}/.m2/repository-{PROJECT}</localRepository>

> **Label Definition**
>
> + **{PROJECT}** : The label that identifies the project name

#### 4.15.11. Usage & Maintenance

To maintain a transparent development environment, each project version uses a dedicated settings file. These are linked to the default Maven location (`~/.m2/settings.xml`) using **Symbolic Links** (Windows Developer mode must be enabled). This allows IDEs and the CLI to work without additional flags or admin permissions, while providing a clear visual indication of which configuration is currently active.

Every project configuration must be stored in `~/.m2/` using following naming structure:

    settings-{PROJECT}-{DATE}.xml

The different parts in the above name structure, shall be replaced as explained next:

> + **{PROJECT}** : The name of the project where the settings.xml file was used with, e.g. *sa3*
> + **{DATE}** : The date of the change on the format yyyymmdd, e.g. *20200321*
>
> With the above examples, the settings.xml backup file name would be *settings-sa3-20200321.xml*

If a project requires no specific configuration, create an "empty" settings file containing only the basic `<settings>` tags to ensure Maven remains functional:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns="http://maven.apache.org/SETTINGS/1.2.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.2.0 https://maven.apache.org/xsd/settings-1.2.0.xsd">
</settings>
```

To switch to a different project or update to a new version, you must first delete the existing `~/.m2/settings.xml` symlink and then create the new one. If [**Apache Maven**](https://maven.apache.org/) is installed on the `WSL File System`, replace the placeholders in the below command as necessary and then execute it on a [Ubuntu](https://ubuntu.com/) terminal to get it done.

```bash
rm ~/.m2/settings.xml
ln ~/.m2/settings-{PROJECT}-{DATE}.xml ~/.m2/settings.xml
```

When [**Apache Maven**](https://maven.apache.org/) is installed on the `Windows Native File System`, to delete the existing `~/.m2/settings.xml` symlink and then create the new one when switching to a different project or update to a new version, replace the placeholders in the below command as necessary and then execute it on a Windows Command Prompt.

```cmd
del %USERPROFILE%\.m2\settings.xml
mklink %USERPROFILE%\.m2\settings.xml %USERPROFILE%\.m2\settings-{PROJECT}-{DATE}.xml
```

### 4.16. Apache Tomcat

[**Apache Tomcat**](http://tomcat.apache.org/) is an open source implementation of the [Jakarta Servlet](https://projects.eclipse.org/projects/ee4j.servlet), [Jakarta Server Pages](https://projects.eclipse.org/projects/ee4j.jsp), [Jakarta Expression Language](https://projects.eclipse.org/projects/ee4j.el), [Jakarta WebSocket](https://projects.eclipse.org/projects/ee4j.websocket), [Jakarta Annotations](https://projects.eclipse.org/projects/ee4j.cahttps://projects.eclipse.org/projects/ee4j.authentication) specifications. These specifications are part of the [Jakarta EE platform](https://projects.eclipse.org/projects/ee4j.jakartaee-platform).

#### 4.16.1. Installation

##### 4.16.1.1. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**Apache Tomcat**](http://tomcat.apache.org/) application server on the `Windows Native File System`, download the desired [release zip archive](http://tomcat.apache.org/) and unpack it to the folder `C:\dev\apache-tomcat\candidates`. Rename the extracted folder taking in consideration the following structure:

    tomcat-{VERSION}-{PROJECT}

The different parts in the above name structure, shall be replaced as explained next:

> + **{VERSION}** : The Tomcat version number, e.g. *8.5.82*
> + **{PROJECT}** : The name of the project where this instance of Tomcat will be used, e.g. *sa3*
>
> With the above examples, the Tomcat folder name would be *tomcat-8.5.82-sa3*

### 4.17. Quarkus CLI

The [**Quarkus CLI**](https://quarkus.io/guides/cli-tooling) lets you create Quarkus projects, manage extensions and do essential build and development tasks using the underlying project build tool.

#### 4.17.1. Installation

##### 4.17.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

To install [**Quarkus CLI**](https://quarkus.io/guides/cli-tooling) on the `WSL File System`, as recommended on the [Quarkus documentation](https://quarkus.io/guides/cli-tooling), use [SDKMAN](https://sdkman.io/), execute the upcoming command on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
sdk install quarkus
```

To verify if the [**Quarkus CLI**](https://quarkus.io/guides/cli-tooling) installation was properly made, check the output of the following command:

```bash
quarkus --version
```

##### 4.17.1.2. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**Quarkus CLI**](https://quarkus.io/guides/cli-tooling), open a PowerShell console and execute the following command:

```powershell
scoop install main/quarkus-cli
```

To verify if the [**Quarkus CLI**](https://quarkus.io/guides/cli-tooling) installation was properly made, check the output of the following command:

```powershell
quarkus --version
```

### 4.18. Node.js

[**Node.js**](https://nodejs.org/) is a cross-platform, open-source JavaScript runtime environment that runs on the V8 JavaScript engine, and executes JavaScript code outside a web browser.

#### 4.18.1. Installation

The most pratical way to install [**Node.js**](https://nodejs.org/) is via a Node version manager because it allows you to easily install and switch between numerous versions of [**Node.js**](https://nodejs.org/). This is useful when a project you’re working on requires a different version of [**Node.js**](https://nodejs.org/) than what you currently have installed.

##### 4.18.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

The Node version manager that I use on Linux is [`nvm`](https://github.com/nvm-sh/nvm), which cam also be used  on the `WSL File System`. [`nvm`](https://github.com/nvm-sh/nvm) is a version manager for [**Node.js**](https://nodejs.org/), designed to be installed per-user, and invoked per-shell. It works on any POSIX-compliant shell (sh, dash, ksh, zsh, bash), in particular on these platforms: unix, macOS, and [WSL](https://github.com/nvm-sh/nvm#important-notes). [`nvm`](https://github.com/nvm-sh/nvm) is also recommended on [`npm`](https://www.npmjs.com/)'s [Official Documentation](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm).

Make sure that you have the `build-essentials` package already installed and then, to install [`nvm`](https://github.com/nvm-sh/nvm), replace the **{LABEL}** in the upcoming command as appropriate and execute it from an [Ubuntu](https://ubuntu.com/) terminal.

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/{VERSION_NUMBER}/install.sh | bash
```

> **Label Definition**
>
> + **{VERSION_NUMBER}** : The latest version number found on [Installing and Updating](https://github.com/nvm-sh/nvm?tab=readme-ov-file#installing-and-updating) section of the project’s home repository

Running the above command downloads a script and runs it. The script clones the [`nvm`](https://github.com/nvm-sh/nvm) repository to `~/.nvm` and adds a code snippet to the end of the `~/.bashrc` file. To add proper context to this new code snippet, start editing the `~/.bashrc` file, execute the following command to be able to edit with the [Nano text editor](https://www.nano-editor.org/).

```bash
nano ~/.bashrc
```

and add the below comments above the mentioned new code snippet.

```bash
# Sets the environment for nvm (Node Version Manager)
```

After completing the edition of the `.bashrc file`, save and close it. In order for the changes to take effect, run the following command:

```bash
source ~/.bashrc
```

To check that [`nvm`](https://github.com/nvm-sh/nvm) is properly installed, run the following command:

```bash
nvm --version
```

To have a list of default global packages installed with every new version of [**Node.js**](https://nodejs.org/), start editing the file `~/.config/nvm/default-packages` with the below command.

```bash
nano ~/.config/nvm/default-packages
```

and add the desired packages names, one per line, to the file. After completing the edition of the file `~/.config/nvm/default-packages`, save and close it.

To check if the edition of the file was successful, run the following command:

```bash
cat ~/.config/nvm/default-packages
```

To install the latest available LTS version of [**Node.js**](https://nodejs.org/), run the following command:

```bash
nvm install --lts
```

To check if node is correctly installed, run the following command

```bash
node --version
```

When [**Node.js**](https://nodejs.org/) is installed, [`npm`](https://www.npmjs.com/) is automatically installed with it. However, according to [`npm`](https://www.npmjs.com/)'s documentation [`npm`](https://www.npmjs.com/) is released more frequently than[**Node.js**](https://nodejs.org/), so to install the latest stable version of [`npm`](https://www.npmjs.com/), run the following command:

```bash
nvm install-latest-npm
```

##### 4.18.1.2. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

My go to Node version manager on on the `Windows Native File System` used to be [NVS](https://github.com/jasongin/nvs) but, it has seen very little activity recently, with the last major release being in 2023. Therefore, I'm now starting to use [fnm (Fast Node Manager)](https://github.com/Schniz/fnm).

###### 4.18.1.2.1. fnm (Fast Node Manager)

[fnm](https://github.com/Schniz/fnm) can be installed with [scoop](https://scoop.sh/) executing, on PowerShell console, the following command:

```powershell
scoop install main/fnm
```

Before you can use [fnm](https://github.com/Schniz/fnm), you have to first set up your shell.

To be able to use [fnm](https://github.com/Schniz/fnm) with Git Bash, edit the `~/.bashrc` file and add the bellow snippet.

```bash
# fnm shel setup
eval "$(fnm env --use-on-cd --shell bash --version-file-strategy=recursive)"
```

Check out also the [Official Configuration](https://github.com/Schniz/fnm/blob/master/docs/configuration.md) section to enable other highly recommended features.

To enable the changes made, you will need to source the`~/.bashrc` file, executing the following command:

```bash
source ~/.bashrc
```

At this stage, you will probably be prompt to install the default [**Node.js**](https://nodejs.org/) version and you should refuse to install it. To check if [fnm](https://github.com/Schniz/fnm) was properly installed, execute the following commands:

```bash
fnm -V
fnm -h
```

To install and use the latest [**Node.js**](https://nodejs.org/) LTS version, on Git Bash, execute the following command:

```bash
fnm install --lts
fnm use lts-latest
fnm list
```

To be able to use [fnm](https://github.com/Schniz/fnm) with PowerShell, you will need add the bellow snippet to you profile file.

```powershel
# fnm shel setup
fnm env --use-on-cd --shell powershell --version-file-strategy=recursive | Out-String | Invoke-Expression
```

To create a PowerShell profile, if it doesn't exists yet, execute the below command on a PowerShell console.

```powershell
if (-not (Test-Path $profile)) { New-Item $profile -Force }
```

To edit you PowerShell profile, execute, on a PowerShell console, the following command:

```powershell
Invoke-Item $profile
```

To check if [fnm](https://github.com/Schniz/fnm) was properly installed, execute the following commands:

```powershell
fnm -V
fnm -h
```

To install and use the latest [**Node.js**](https://nodejs.org/) LTS version, on PowerShell, execute the following command:

```powershell
fnm install --lts
fnm use lts-latest
fnm list
```

For an extended usage documentation, check the [official documentation](https://github.com/Schniz/fnm/blob/master/docs/commands.md)

From now on, the latest [**Node.js**](https://nodejs.org/) LTS version will be available on Git Bash and PowerShell. To set up other shells, check the [official documentation](https://github.com/Schniz/fnm?tab=readme-ov-file#shell-setup). To confirm that everything is properly set, check the output of the below commands executed from a from a PowerShell console and from a [Git Bash](https://git-scm.com/) terminal.

```powershell
node --version
npm --version
```

If everything is correct, the above commands will output the **node** version and the **npm** version.

###### 4.18.1.2.2. NVS (Node Version Switcher)

Although I'm now using [fnm](https://github.com/Schniz/fnm) as my preferred Node Version Manager, I'm keeping here, for historical reference, my guide to install [NVS](https://github.com/jasongin/nvs).

The instructions to install [NVS](https://github.com/jasongin/nvs) shown here are following the official instructions for the [manual setup from a Command Prompt](https://github.com/jasongin/nvs/blob/master/doc/SETUP.md#manual-setup---command-prompt).

To set `NVS_HOME` as environment variable for the current *user account*, press `WIN + R`, type `rundll32.exe sysdm.cpl,EditEnvironmentVariables` and then press `Enter`.

On the ***User variables*** section, click the **New** button and fill the *Variable name* input box with `NVS_HOME` and the *Variable value* input box with `%LOCALAPPDATA%\nvs`.

Click the **OK** button to close the window used to create the new environment variable and then click the **OK** button on the *environment variables* window to close it.

To check if the Windows `NVS_HOME` value was properly set, open a Windows Command Prompt and check the output of the following command:

```cmd
echo %NVS_HOME%
```

On the same Windows Command Prompt, clone the [nvs repository](https://github.com/jasongin/nvs) with the following command:

    git clone https://github.com/jasongin/nvs "%NVS_HOME%"

Then, on the same Windows Command Prompt, install the application executing the following command:

```cmd
"%NVS_HOME%\nvs.cmd" install
```

To check if the folder `%LOCALAPPDATA%\nvs` was properly added to the current *user account* path variable, press `WIN + R`, type `rundll32.exe sysdm.cpl,EditEnvironmentVariables` and then press `Enter`.

On the ***User variables*** section, select the `Path` variable and click the **Edit** button. Then check if the folder `%LOCALAPPDATA%\nvs` is one of the `Path` variable entries. If it isn't, edit or create it.

Click the **OK** button to close the window used to edit the `PATH` variable and then click the **OK** button on the *environment variables* window to close it.

To check if [NVS](https://github.com/jasongin/nvs) was properly installed, on the same Windows Command Prompt, check the output of the following command:

```cmd
nvs --version
```

To be able to use [NVS](https://github.com/jasongin/nvs) with [Git Bash](https://github.com/jasongin/nvs/blob/master/doc/SETUP.md#git-bash-on-windows), open a [Git Bash](https://git-scm.com/) terminal and execute the below command to source the `install` command:

```bash
. "$NVS_HOME/nvs.sh" install
```

The `install` command adds a snippet to the `~/.bashrc` file to source `nvs.sh`, so that the `nvs` function is available in future shells. The `nvs.sh` script adds an `nvs` shell function to the environment.

Edit the `~/.bashrc` file and add the bellow comment above the code added by the `install` command.

```bash
# Adds an nvs shell function to the environment to enable the tool to be invoked as just nvs without any path
```

After adding the above snippet, the new code on the `~/.bashrc` will be similar to the following snippet:

```bash
# Adds an nvs shell function to the environment to enable the tool to be invoked as just nvs without any path
function setupNvs {
    export NVS_HOME="$HOME\AppData\Local\nvs";
    [ -s "$NVS_HOME/nvs.sh" ] && source "$NVS_HOME/nvs.sh" >> /dev/null;
    return 0;
}
setupNvs
```

To add the latest version of **node** run the below command from a Windows Command Prompt.

```cmd
nvs add lts
```

Then execute the bellow command to add a version of node to PATH for the current shell:

```cmd
nvs use lts
```

The above command will **only** set the **node** version in use for the current shell/terminal and it will **not** be permanent. To add it to PATH permanently, execute the following command:

```cmd
nvs link lts
```

To check if the folder `%LOCALAPPDATA%\nvs\default` was properly added to the current *user account* path variable, press `WIN + R`, type `rundll32.exe sysdm.cpl,EditEnvironmentVariables` and then press `Enter`.

On the ***User variables*** section, select the `Path` variable and click the **Edit** button. Then check if the folder `%LOCALAPPDATA%\nvs\default` is one of the `Path` variable entries. If it isn't, edit or create it.

Click the **OK** button to close the window used to edit the `PATH` variable and then click the **OK** button on the *environment variables* window to close it.

From now on, the latest **node** lts version will be available on all shells of the system. To confirm that everything is properly set, check the output of the below commands executed from a Windows Command Prompt, from a PowerShell console and from a [Git Bash](https://git-scm.com/) terminal.

```bash
node --version
npm --version
```

If everything is correct, the above commands will output the **node** version and the **npm** version.

### 4.19. Terraform

[**Terraform**](https://www.terraform.io/) is a tool for building, changing, and versioning infrastructure safely and efficiently.

#### 4.19.1. Installation

##### 4.19.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

The easiest way to install and manage multiple versions of [**Terraform**](https://www.terraform.io/) on the `WSL File System` is to use [TFSwitch](https://tfswitch.warrensbox.com/). This is a command line tool that lets you switch between different versions of [**Terraform**](https://www.terraform.io/).

Create a folder to [store the user's binaries](https://unix.stackexchange.com/a/36874) executing the following command:

```bash
mkdir -p ~/.local/bin
```

It's necessary that the folder `~/.local/bin` is included on the `PATH` and, on [Ubuntu](https://ubuntu.com/), that is normally done by the `~/.profile` script. Close the terminal and on a new [Ubuntu](https://ubuntu.com/) terminal and then check the output of the following command to confirm that `~/.local/bin` is included on the `PATH`.

```bash
echo $PATH
```

Following the [official instructions](https://tfswitch.warrensbox.com/Install/), download [TFSwitch](https://tfswitch.warrensbox.com/) installation script to the folder `/tmp` executing the upcoming commands on a [Ubuntu](https://ubuntu.com/) terminal:

```bash
wget https://raw.githubusercontent.com/warrensbox/terraform-switcher/release/install.sh -P /tmp
```

Make the [TFSwitch](https://tfswitch.warrensbox.com/) installation script executable with the following command:

```bash
chmod 755 /tmp/install.sh
```

Install [TFSwitch](https://tfswitch.warrensbox.com/) on the `~/.local/bin` executing the following command:

```bash
/tmp/install.sh -b ~/.local/bin/
```

To verify if the [TFSwitch](https://tfswitch.warrensbox.com/) installation was properly made, check the output of the following command:

```bash
tfswitch --version
```

To install a specific [**Terraform**](https://www.terraform.io/) on the `WSL File System`, replace the ***{LABEL}*** in the below command as appropriate and then execute it on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
tfswitch -b ~/.local/bin/terraform {VERSION}
```

> **Label Definition**
>
> + **{VERSION}** : The desired [**Terraform**](https://www.terraform.io/) version

To verify if the [**Terraform**](https://www.terraform.io/) installation was properly made, check the output of the following command:

```bash
terraform --version
```

##### 4.19.1.2. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**Terraform**](https://www.terraform.io/) on the `Windows Native File System`, open a PowerShell console and execute the following command:

```powershell
scoop install main/terraform
```

Using [Scoop](https://scoop.sh/), it's possible to [install a specific version](https://github.com/ScoopInstaller/Scoop/wiki/FAQ#how-do-i-install-a-specific-version-of-an-app) of an app. To do that for [**Terraform**](https://www.terraform.io/), replace the ***{LABEL}*** in the below command as appropriate and then execute it on a PowerShell console.

```powershell
scoop install terraform@ {VERSION}
```

> **Label Definition**
>
> + **{VERSION}** : The desired [**Terraform**](https://www.terraform.io/) version

To verify if the [**Terraform**](https://www.terraform.io/) installation was properly made, check the output of the following command:

```powershell
terraform --version
```

### 4.20. IntelliJ IDEA

[**IntelliJ IDEA**](https://www.jetbrains.com/idea/) is an integrated development environment written in Java for developing computer software written in Java, Kotlin, Groovy, and other JVM-based languages. It is developed by JetBrains and is available as an Apache 2 Licensed community edition, and in a proprietary commercial edition.

#### 4.20.1. Installation

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

The [**JetBrains Toolbox App**](https://www.jetbrains.com/toolbox-app/) is the [recommended process](https://www.jetbrains.com/help/idea/installation-guide.html#toolbox) to install JetBrain products. Download the latest installation file from the [official download page](https://www.jetbrains.com/toolbox-app/). Then, execute the downloaded file to install [**JetBrains Toolbox App**](https://www.jetbrains.com/toolbox-app/).

Execute the [**JetBrains Toolbox App**](https://www.jetbrains.com/toolbox-app/) and then login in the JetBrains account. Then, on the `Toolbox App Menu`choose the `Settings` option and uncheck the checkbox `Launch Toolbox App at system startup`.  

To install [**IntelliJ IDEA**](https://www.jetbrains.com/idea/), launch the [**JetBrains Toolbox App**](https://www.jetbrains.com/toolbox-app/) and then choose the desired [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) version to install and follow the instructions prompted.

Some antivirus software can interfere with the IDE build process, [causing builds to run dramatically slower](https://intellij-support.jetbrains.com/hc/en-us/articles/360006298560). To prevent this, the folders where the IDE writes a lot of files should be excluded from the antivirus software real-time scanning. That can be done following the following steps:

+ Click the Start button and search for “Windows Security”;
+ Start the *Windows Security* application;
+ Click on “Virus and threat protection”;
+ Click on “Manage settings” under “Virus & threat protection settings”;
+ Scroll down if needed, and then click on “Add or remove exclusions” (there will be a prompt for elevated permissions that must be accepted);
+ Click the button `+ Add an exclusion`, choose `Folder` from the dropdown list and then add all (one by one) the following folders:
  + `C:\code`
  + `%APPDATA%\JetBrains\`
  + `%LOCALAPPDATA%\JetBrains\`

It is also recommend to [exclude the IDE process from the antivirus](https://intellij-support.jetbrains.com/hc/en-us/articles/360005028939-Slow-startup-on-Windows-splash-screen-appears-in-more-than-20-seconds) to improve the startup performance. To do that exclusion, on the on “Add or remove exclusions”, Click the button `+ Add an exclusion`, choose `Process` from the dropdown list and then add all (one by one) the following processes:

+ `idea64.exe`
+ `fsnotifier.exe`

#### 4.20.2. Install plugins

##### 4.20.2.1. Install SonarQube plugin

[SonarQube](https://plugins.jetbrains.com/plugin/7973-sonarqube-for-ide) is an IDE extension that helps to detect and fix quality issues as the code is written. To install it, choose `Plugins` from the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) welcome screen and then, on the `Marketplace` tab search for "SonarQube". Within the listed plugins, click "Install" on the right one and follow the "Wizard" instructions to install it.

##### 4.20.2.2. Install JPA Buddy

[JPA Buddy](https://plugins.jetbrains.com/plugin/15075-jpa-buddy) is an IDE extension that helps developers work efficiently with Hibernate, EclipseLink, Spring Data JPA, Flyway, Liquibase, Lombok, MapStruct, and other related technologies in both Java and Kotlin. To install it, choose `Plugins` from the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) welcome screen and then, on the `Marketplace` tab search for "JPA Buddy". Within the listed plugins, click "Install" on the right one and follow the "Wizard" instructions to install it.

#### 4.20.3. Set code formatters

##### 4.20.3.1. Java

[Google Java Style Guide](https://google.github.io/styleguide/javaguide.html) seems to be the most popular **Code Style Guide** for [Java](https://www.java.com/en/). This style guide is licensed under the [CC-By 3.0 License](https://creativecommons.org/licenses/by/3.0/) and a there's a [repository](https://github.com/google/styleguide) where a formatter configuration file for [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) is available.

To add the above mentioned Code Style Formatter settings, on the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) welcome screen, choose `All Settings` from the `Customize` tab. Then choose the tab `Editor->Code Style->Java`. On this tab, click the `settings` icon choose `Import Scheme/IntelliJ IDEA code style XML` and pick the file(s) with the desired settings.

#### 4.20.4. Configure Version Control

##### 4.20.4.1. Commit

Modern IntelliJ IDEA versions uses a **non-modal Commit tool window** (accessible via `Alt + 0` or the checkmark icon on the left sidebar). The **Shelf** tab is contextual; it only appears in the Commit tool window when you have at least one shelved change. To manage your shelf:

1.  Open the **Commit** tool window.
2.  If you have shelved items, the **Shelf** tab will appear next to the **Changes** tab header.
3.  If you do not see the tab, it means your shelf is currently empty.

To move changes to the shelf instead of committing them, take the following steps:

1.  In the **Commit** tool window, right-click the files or the "Changes" changelist.
2.  Select **Shelf Changes...** from the context menu.
3.  Provide a name for the shelf and click **Shelf Changes**. The **Shelf** tab will now become visible.

#### 4.20.5. Configure Build Tools

##### 4.20.5.1. Maven

To customize *Maven*, on the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) welcome screen, choose `All Settings` from the `Customize` tab. Then choose the tab `Build, Execution, Deployment->Build Tools->Maven`. On this tab, change the input boxes listed below as described:

+ **Maven home path** : The path to the chosen [system *Maven* instance](#451-installation);
+ **User setting file** : Check the `Override` checkbox and point to the [custom project's *Maven Local Repository*](#452-configuration);
+ **Local repository** : Check the `Override` checkbox and point to the [custom project's *Maven Local Repository*](#452-configuration);

Beware that you must choose the [Apache Maven](https://maven.apache.org/) according to the file system you're working on (`WSL File System` or the `Windows Native File System`). This is a per project setting, therefore it might be necessary to set it for every project when opened with [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) for the first time.

#### 4.20.6. Configure Tools

##### 4.20.6.1. Terminal

To customize the *Terminal* in use with [**IntelliJ IDEA**](https://www.jetbrains.com/idea/), on the application welcome screen, choose `All Settings` from the `Customize` tab. Then choose the tab `Tools->Terminal`. On this tab, take in consideration the file system you're working on and change the input boxes listed below as described:

+ `WSL File System`
  + **Shell path** : `wsl.exe`
  + **Default Tab name** : `Terminal`;
+ `Windows Native File System`
  + **Shell path** : `C:\Users\{USER}\AppData\Local\Programs\Git\bin\bash.exe --login -i`
  + **Default Tab name** : `Terminal`;

> **Label Definition**
>
> + **{USER}** : Windows username

This settings will only take effect when starting a new terminal. Therefore, create/add/open a new terminal window and terminate the old one.

This is a per project setting, therefore it might be necessary to set it for every project when opened with [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) for the first time.

#### 4.20.7. Run/Debug Configurations

When `networkingMode=mirrored` is not enabled the Windows firewall configuration needs to be adapted to ensure the building of a project on the `WSL File System` [works properly](https://www.jetbrains.com/help/idea/how-to-use-wsl-development-environment-in-product.html#debugging_system_settings). Open a PowerShell console with *Administrator* privileges and execute the following command to get the exact network interface name:

```powershell
Get-NetAdapter
```

Replace the **{LABEL}** in the upcoming command as appropriate and execute it from an a PowerShell console with *Administrator* privileges to allow connections using WSL.

```powershel
New-NetFirewallRule -DisplayName "WSL" -Direction Inbound  -InterfaceAlias "{ADAPTER_NAME}"  -Action Allow
```

> **Label Definition**
>
> + **{ADAPTER_NAME}** : The Hyper-V Virtual Ethernet Adapter for WSL name obtained with the Powershell command `Get-NetAdapter`

Then, to renew the firewall rules, execute the following command:

```powershel
Get-NetFirewallProfile -Name Public | Get-NetFirewallRule | where DisplayName -ILike "IntelliJ IDEA*" | Disable-NetFirewallRule
```

After starting a debugger session, the Windows Firewall popup might appears and them, select the *Public networks* checkbox and click the `Allow access` button.

##### 4.20.7.1 Shorten command line method

To avoid the error "*Command line is too long*" when running tests it's necessary to set the "*Shorten command line*" method in the Run/Debug configuration to "*JAR manifest*". That can be done for the specific method or class, but it's better to [set it as default](https://stackoverflow.com/a/47927544) on [run/debug configuration templates](https://www.jetbrains.com/help/idea/run-debug-configuration.html#templates).

From the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) main menu, select `Run->Edit Configurations...`. On the screen that pop-up, click `Edit configuration templates...` (bottom left corner of the pop-up screen). On the following pop-up screen, select the `JUnit` tab.

[Then](https://stackoverflow.com/a/65639857), click on the `Modify options` link (`ALT+M`) and set/select the `Shorten command line` option. Back on the `JUnit` tab, there will be a new dropdown input box named `Shorten command line`. In this new dropdown, choose the *Jar manifest* option. Click the button `OK` (once to close the `Select configuration templates` pop up and again to close the  `Run->Edit Configurations` pop up screen) and from now on all the new `JUnit` Run/Debug configurations will use this template.

### 4.21. Visual Studio Code

[**Visual Studio Code**](https://code.visualstudio.com/), also commonly referred to as **VS Code**, is a source-code editor made by Microsoft with the Electron Framework, for Windows, Linux and macOS. Features include support for debugging, syntax highlighting, intelligent code completion, snippets, code refactoring, and embedded Git.

#### 4.21.1. Installation

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

Download the [**Visual Studio Code**](https://code.visualstudio.com) *User Installer* file from the [official download page](https://code.visualstudio.com/download). Then, execute the downloaded file to install [**Visual Studio Code**](https://code.visualstudio.com).

Execute [**Visual Studio Code**](https://code.visualstudio.com) and to enable the [`Settings Sync`](https://code.visualstudio.com/docs/editor/settings-sync) option, click on te gear menu (on the bottom left of the application screen) and select the [`Setting Sync...`](https://code.visualstudio.com/docs/editor/settings-sync) option. When asked to sign in, choose the *GitHub* option and then insert the needed credentials. When asked what preferences to sync, select the checkboxes listed next:

+ Settings;
+ Keyboard Shortcuts for each platform;
+ User Snippets;
+ Extensions
+ UI State

#### 4.21.2. Install extensions

With the [`Settings Sync`](https://code.visualstudio.com/docs/editor/settings-sync) option on, [**Visual Studio Code**](https://code.visualstudio.com) will installed all the synced extensions. Wait for while to allow the full synchronization and then check if all of the following extensions were properly installed:

+ [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag);
+ [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments);
+ [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker);
+ [Data Workspace](https://marketplace.visualstudio.com/items?itemName=ms-mssql.data-workspace-vscode);
+ [Debugger for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-debug);
+ [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
+ [Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)
+ [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig);
+ [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint);
+ [Extension Pack for java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-pack);
+ [GitHub Copilot](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot);
+ [GitHub Copilot Chat](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat);
+ [Gradle for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-gradle);
+ [IntelliSense for CSS class names in HTML](https://marketplace.visualstudio.com/items?itemName=Zignd.html-css-class-completion);
+ [Language Support for Java(TM) by Red Hat](https://marketplace.visualstudio.com/items?itemName=redhat.java);
+ [lit-plugin](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin);
+ [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint);
+ [Maven for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-maven);
+ [MySQL Shell for VS Code](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint);
+ [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense);
+ [PHP Debug](https://marketplace.visualstudio.com/items?itemName=xdebug.php-debug);
+ [PHP Extension Pack](https://marketplace.visualstudio.com/items?itemName=xdebug.php-pack);
+ [PHP Intelliphense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client);
+ [Prettier - Code Formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
+ [Project Manager for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-dependency);
+ [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance)
+ [Python](https://marketplace.visualstudio.com/items?itemName=ms-python.python)
+ [Python Debugger](https://marketplace.visualstudio.com/items?itemName=ms-python.debugpy)
+ [Rainbow CSV](https://marketplace.visualstudio.com/items?itemName=mechatroner.rainbow-csv)
+ [Smarty](https://marketplace.visualstudio.com/items?itemName=imperez.smarty);
+ [SonarQube for IDE](https://marketplace.visualstudio.com/items?itemName=SonarSource.sonarlint-vscode);
+ [SQL Bindings](https://marketplace.visualstudio.com/items?itemName=ms-mssql.sql-bindings-vscode);
+ [SQL Database Projects](https://marketplace.visualstudio.com/items?itemName=ms-mssql.sql-database-projects-vscode);
+ [SQL Server (mssql)](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql):
+ [Test Runner for Java)](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-test);
+ [WSL](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl);
+ [XML Tools](https://marketplace.visualstudio.com/items?itemName=DotJoshJohnson.xml).

### 4.22. Eclipse

TODO

### 4.23. DBeaver

[**DBeaver**](https://dbeaver.io/) is free and open source universal database tool for developers and database administrators.

#### 4.23.1. Installation

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

Download [**DBeaver**](https://dbeaver.io/) installer latest version from [official downloads page](https://dbeaver.io/download/). Then, execute the downloaded file and when prompted, choose to install [**DBeaver**](https://dbeaver.io/) only for the current user. When asked to select the components to install, check the following checkboxes:

+ DBeaver Community;
+ Include Java
+ Associate .SQL files

[**DBeaver**](https://dbeaver.io/) will store the drivers it uses in the folder `%USERPROFILE%\AppData\Roaming\DBeaverData\drivers`.

When using applications like [Zscaler](https://www.zscaler.com/), it might be necessary to import security certificate to the [**DBeaver**](https://dbeaver.io/) JRE Keystore. On a **Git Bash** terminal, navigate to the folder `%USERPROFILE%\AppData\Local\DBeaver\jre\lib\security`, replace the **{LABELS}** in the upcoming command as appropriate and then execute it:

```bash
keytool -importcert -trustcacerts -alias {CERTIFICATE_ALIAS} -file {PATH_TO_DER_CERTIFICATE} -keystore cacerts -storepass changeit -noprompt
```

> **Label Definition**
>
> + **{PATH_TO_DER_CERTIFICATE}** : Path to the `.der` certificate file
> + **{CERTIFICATE_ALIAS}**       : The chosen certificate alias

To confirm that the certificate was added to the JRE keystore, replace the **{LABELS}** in the upcoming command as appropriate and then execute it:

```bash
keytool -v -list -keystore cacerts -alias {CERTIFICATE_ALIAS} -storepass changeit -noprompt
```

> **Label Definition**
>
> + **{CERTIFICATE_ALIAS}** : The chosen certificate alias

### 4.24. Postman

[**Postman**](https://www.postman.com/) helps you be more efficient while working with APIs. Using Postman, you can construct complex HTTP requests quickly, organize them in collections.

#### 4.24.1. Installation

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

Download [**Postman**](https://www.postman.com/) installer latest version from [official downloads page](https://www.postman.com/downloads/). Then, execute the downloaded file and when prompted, sign in into the [**Postman**](https://www.postman.com/) account.
