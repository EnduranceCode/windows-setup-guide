# Setup guide for a development machine on Windows

This file contains the **Development Software and Tools** section of my [Setup guide for a development machine on Windows](https://github.com/EnduranceCode/windows-development-machine). The introduction to this guide as well as its full *Table of Contents* can be found on the [README.md](./README.md) file of this repository. The *Table of Contents* of this section is listed below.

## Table of Contents

4. [Development Software & Tools](#4-development-software--tools)
    1. [Docker](#41-docker)
    2. [Notepadd++](#42-notepad)
    3. [Meld](#43-meld)
    4. [Git & Git Bash](#44-git--git-bash)
    5. [Java](#45-java)
    6. [Apache Maven](#46-apache-maven)
    7. [Apache Tomcat](#47-apache-tomcat)
    8. [Quarkus CLI](#48-quarkus-cli)
    9. [AWS CLI](#49-aws-cli)
    10. [Make](#410-make)
    11. [Rancher Desktop](#411-rancher-desktop)
    12. [Terraform](#412-terraform)
    13. [NVS (Node Version Switcher)](#413-nvs-node-version-switcher)
    14. [IntelliJ IDEA](#414-intellij-idea)
    15. [Visual Studio Code](#415-visual-studio-code)
    16. Eclipse
    17. [DBeaver](#417-dbeaver)
    18. [Postman](#418-postman)

## 4. Development Software & Tools

### 4.1 Docker

[**Docker**](https://www.docker.com/) is an open-source containerization platform. It enables developers to package applications into containers, which are standardized, executable components combining application source code with the operating system libraries and dependencies required to run that code in any environment.

[**Docker**](https://www.docker.com/) updated its [Docker Desktop License Agreement](https://docs.docker.com/subscription/?ref=paulsblog.dev#docker-desktop-license-agreement) and this change means that on companies with more than 250 employees or more than $10 million in annual revenue you will not be able to use [Docker Desktop](https://www.docker.com/products/docker-desktop/) without a paid subscription. A possible alternative is [Rancher Desktop](https://rancherdesktop.io/) but, as the license update is only related to [Docker Desktop](https://www.docker.com/products/docker-desktop/), it's also possible to utilize [WSL](https://learn.microsoft.com/windows/wsl/) to run [**Docker**](https://www.docker.com/) or the [Docker Engine](https://docs.docker.com/engine/).

If you're going to do your development work on the Windows native file system, you should choose [Rancher Desktop](https://rancherdesktop.io/) to replace [Docker Desktop](https://www.docker.com/products/docker-desktop/). But if you're planning to do all you development work on the [WSL](https://learn.microsoft.com/windows/wsl/) file system (taking advantage of the Linux tools), you should utilize [WSL](https://learn.microsoft.com/windows/wsl/) to run [**Docker**](https://www.docker.com/) or the [Docker Engine](https://docs.docker.com/engine/).

This section describes the necessary steps to install [**Docker**](https://www.docker.com/) and [Docker Engine](https://docs.docker.com/engine/) on a [WSL](https://learn.microsoft.com/windows/wsl/) [Ubuntu](https://ubuntu.com/) distribuition. The following steps are based on the [official documentation for installing Docker on Ubuntu](https://docs.docker.com/engine/install/ubuntu/) with some adaptations provided by [Paul Knulst](https://www.paulsblog.dev/how-to-install-docker-without-docker-desktop-on-windows/).

On your [Ubuntu](https://ubuntu.com/) submodule of [WSL](https://learn.microsoft.com/windows/wsl/), install the required dependencies with the following commands:

    sudo apt update
    sudo apt -y install apt-transport-https ca-certificates curl gnupg lsb-release

Then, add [**Docker**](https://www.docker.com/)'s official GPG key with the following commands:

    sudo install -m 0755 -d /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    sudo chmod a+r /etc/apt/keyrings/docker.gpg

To add the [**Docker**](https://www.docker.com/) stable repository, execute the following command:

    echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt update

Install the latetst version of the [**Docker**](https://www.docker.com/)'s packages with the following command:

    sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

Add you user to the `docker` group with the following command

    sudo usermod -aG docker $USER

Log out and log back in so that your group membership is re-evaluated, or run the following command to activate the changes to groups:

    newgrp docker

Check the installed versions using the following commands

    docker --version
    dockerd --version
    docker compose version

On [Ubuntu](https://ubuntu.com/), the Docker service starts on boot by default, therefore, it won't be necessary to enable it. To verify that `docker` and `containerd` were started bu *systemd*, run the following commands:

    sudo systemctl status docker.service
    sudo systemctl status containerd.service

The `iptables` used by [Ubuntu](https://ubuntu.com/) is the `nftables` version and this might stop [**Docker**](https://www.docker.com/)'s interaction with the firewall because using `nftables` natively requires Linux Kernel 5.8 but the latest Kernel version for the [WSL](https://learn.microsoft.com/windows/wsl/) is 5.4. Luckily, [Ubuntu](https://ubuntu.com/) still has the possibility to use a legacy version of `iptables` by simply executing upcoming command and choosing, when prompted, the option `1`.

    sudo update-alternatives --config iptables

After updating the `iptables` just restart the Docker daemon with the following command:

    sudo systemctl restart docker.service

Then, verify if everything is running properly by checking the output of the following commands:

    sudo systemctl status docker.service
    sudo systemctl status containerd.service
    docker run hello-world

### 4.2 Notepad++

[**Notepad++**](https://notepad-plus-plus.org/) is a free and open-source text and source code editor for use with Microsoft Windows. It supports tabbed editing, which allows working with multiple open files in a single window.

#### 4.2.1. Installation

[Download](https://notepad-plus-plus.org/downloads/) the latest portable version of [**Notepad++**](https://notepad-plus-plus.org/). Then extract the downloaded archive to the `%USERPROFILE%\AppData\Local\` folder (`%LOCALAPPDATA%`). Rename the new folder to `Notepad++`.

Inside the folder `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Development`, create a *shortcut* pointing to the file `%USERPROFILE%\AppData\Local\KeepassXC\KeePassXC.exe` and name it (the *shortcut*) `KeepassXC`. Then, edit the *shortcut* and point its icon to the main icon available on the file `%USERPROFILE%\AppData\Local\Notepad++\notepad++.exe`.

#### 4.2.2. Configuration

To replicate on [**Notepad++**](https://notepad-plus-plus.org/) the standard *Quit* Linux keyboard shortcut, select the menu option `Settings->Shortcut Mapper...`, change the existing shortcut *CTRL+Q* to *CTRL+W* and then change the previous existing shortcut *CTRL+W* to *CTRL+Q*. Repeat the process for the existing shortcuts *CTRL+SHIFT+Q* and *CTRL+SHIFT+W*.

On the menu option `Settings->Plugins Admin...`, install the plugins [**BetterMultiSelection**](https://github.com/dail8859/BetterMultiSelection), [**DSpellCheck**](https://github.com/Predelnik/DSpellCheck), [Json Tools](https://github.com/molsonkiko/JsonToolsNppPlugin) and [**XML Tools**](https://github.com/morbac/xmltools).

### 4.3 Meld

[**Meld**](https://meld.app/) is the visual diff and merge tool, targeted at developers. It allows users to compare two or three files or directories visually, color-coding the different lines.

[WinMerge](https://winmerge.org/) is an excellent alternative to [**Meld**](https://meld.app/) but there's only the [Windows](https://www.microsoft.com/en-us/windows) and [**Meld**](https://meld.app/) is multiplatform and that allows me to use the same software on every operating system that I work with.

#### 4.3.1. Installation

To install [**Meld**](https://meld.app/), download the latest version from [official downloads page](https://meld.app/). Then, execute the downloaded file (there will be a prompt for elevated permissions that must be accepted).

Move the [**Meld**](https://meld.app/) *Start Menu* *shortcut* to the `%PROGRAMDATA%\Microsoft\Windows\Start Menu\Programs\Development` folder (Create the `Development` folder if it doesn't exits).

### 4.4 Git & Git Bash

[**Git**](https://git-scm.com/) is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

#### 4.4.1. Installation

#### 4..4.1.1. Installation on the WSL File System

[**Git**](https://git-scm.com/) is included on the [Ubuntu](https://ubuntu.com/) submodule of [WSL](https://learn.microsoft.com/windows/wsl/), therefore, it's not necessary to install it on the `WSL File System`.

#### 4..4.1.2. Installation on the Windows Native File System

**Git Bash** comes included as part of the [Git's Windows package](https://git-scm.com/download/win) and is an application for Microsoft Windows environments which provides an emulation layer for a [**Git**](https://git-scm.com/) command line experience.

To install [**Git**](https://git-scm.com/) on the `Windows Native File System`, use a PowerShell console with *Administrator* privileges and execute the following command:

    choco install git /NoGuiHereIntegration /Symlinks

The parameters used on the above command are personal choices, the list of available parameters (and its definitions) can be found at [Git Package Parameters documentation page](https://github.com/chocolatey-community/chocolatey-packages/blob/master/automatic/git.install/ARGUMENTS.md).

#### 4.4.2. Bash prompt customization

#### 4.4.2.1. Bash prompt customization on the WSL File System

The customization of the bash prompt is very personal and the files used to accomplish my personal customization on the `WSL File System` are stored at the folder `%OneDriveCommercial%\dotfiles\bash-wsl`. To make use of the mentioned files on the bash prompt customization, replace the **{LABEL}** in the upcoming command as appropriate and then execute it from an [Ubuntu](https://ubuntu.com/) terminal.

    mkdir -p ~/.bash_"$USER" && cp -r {ONEDRIVE_COMMERCIAL_PATH}/dotfiles/bash-wsl ~/.bash_"$USER"

> **Label Definition**
>
> + **{ONEDRIVE_COMMERCIAL_PATH}** : Path to the folder `%OneDriveCommercial%`

Replace the **{LABEL}** in the upcoming snippet as appropriate and the add it to the file `~/.bashrc`.

    # Source the file ~/.bash_{USER}/bashrc_{USER}.sh to customize the bash shell
    #
    if [ -f ~/.bash_{USER}/bashrc_{USER}.sh ]; then
        . ~/.bash_{USER}/bashrc_{USER}.sh
    fi

> **Label Definition**
>
> + **{USER}** : Output of the command `echo "$USER"`

After applying the above mentioned changes, save and close the file `~/.bashrc`. To make the changes effective, execute, from the [Ubuntu](https://ubuntu.com/) terminal, the following command:

    source ~/.bashrc

#### 4.4.2.2. Bash prompt customization on the Windows Native File System

The files used to accomplish my personal customization on the `Windows Native File System` are stored at the folder `%OneDriveCommercial%\dotfiles\bash-win`. If a [symlink](https://www.howtogeek.com/16226/complete-guide-to-symbolic-links-symlinks-on-windows-or-linux/) to the folder `%OneDriveCommercial%\dotfiles` isn't yet created the Windows `%USERPROFILE%`, create executing the below command from the Windows Command Line.

    mklink /J %USERPROFILE%\.dotfiles "%OneDriveCommercial%\dotfiles"

Replace the **{LABEL}** in the upcoming snippet as appropriate and the add it to the file `~/.bashrc`.

    # Source the file ~/.dotfiles/bash-win/bashrc_{USER}.sh to customize the bash shell
    #
    if [ -f ~/.dotfiles/bash-win/bashrc_{USER}.sh ]; then
        . ~/.dotfiles/bash-win/bashrc_{USER}.sh
    fi

> **Label Definition**
>
> + **{USER}** : Output of the command `echo "$USER"`

After applying the above mentioned changes, save and close the file `~/.bashrc`. To make the changes effective, execute, from a bash terminal, the following command:

    source ~/.bashrc

#### 4.4.3. Git configuration

To set [Git's global configuration](https://www.learnenough.com/git-tutorial#sec-installation_and_setup), replace the **{LABELS}** in the below commands as appropriate and then execute it in an [Git Bash](https://git-scm.com/) terminal window.

    git config --global user.name "{USER_NAME}"
    git config --global user.email {USER_EMAIL}
    git config --global core.editor nano
    git config --global pull.rebase true
    git config --list

> **Label Definition**
>
> + **{USER_NAME}** : The name of the user
> + **{USER_EMAIL}** : The e-mail of the user

Instructions for a more detailed Git global configuration can be found in the [Git's Official Documentation](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup).

#### 4.4.4. SSH Keys

The [SSH Protocol](https://en.wikipedia.org/wiki/Secure_Shell) is very useful to connect and authenticate to remote servers and services. The creation and setup of the SSH keys described here follows the instructions at [GitHub](https://help.github.com/en/articles/connecting-to-github-with-ssh).

##### 4.4.4.1. Checking for existing SSH keys

To check if the system already has an SSH key set, type the following command:

    ls -al ~/.ssh

If the output of the above command contains a list of files (by default, the filenames of the public keys are *id_dsa.pub*, *id_ecdsa.pub*, *id_ed25519.pub* or *id_rsa.pub*), the system already has a SSH key and it can be used.

##### 4.4.4.2. Generating a new SSH key

To create a new SSH key, replace the **{LABEL}** in the below command as appropriate and then execute it in an [Git Bash](https://git-scm.com/) terminal window.

    ssh-keygen -t rsa -b 4096 -C "{EMAIL_ADDRESS}"

> **Label Definition**
>
> + **{EMAIL_ADDRESS}** : The e-mail address to be used as label for the SSH key

The above command creates a new SSH key, using the provided email as a label.

    > Generating public/private rsa key pair.

When  prompted to "Enter a file in which to save the key," press Enter to accept the default file location.

    > Enter a file in which to save the key (/home/you/.ssh/id_rsa): [Press enter]

Type a secure passphrase when prompted. GitHub has further instructions on [working with SSH key passphrases](https://help.github.com/en/articles/working-with-ssh-key-passphrases).

    > Enter passphrase (empty for no passphrase): [Type a passphrase]
    > Enter same passphrase again: [Type passphrase again]

##### 4.4.4.3. Adding the SSH key to the ssh-agent

To add the new SSH key to the `ssh-agent`, start it in the background with the command below.

    eval "$(ssh-agent -s)"

The command below will add the private key to the `ssh-agent`.

    ssh-add ~/.ssh/id_rsa

##### 4.4.4.4. Adding a new SSH key to the remote servers

To be able to copy the public SSH key to the clipboard, display it in a bash terminal window with the following command:

    cat ~/.ssh/id_rsa.pub

Copy the output of the above command and then add the public SSH key to the remote servers in use ([GitHub](https://github.com/settings/keys), [Bitbucket](https://bitbucket.org/account/user/ssh-keys), etc.).

### 4.5. Java

[**Java**](https://openjdk.org/) is a high-level, class-based, object-oriented programming language that is designed to have as few implementation dependencies as possible. It is a general-purpose programming language intended to let programmers write once, run anywhere, meaning that compiled Java code can run on all platforms that support Java without the need to recompile.

#### 4.5.1. Installation

##### 4.5.1.1. Installation the WSL File System

The easiest way to install and manage multiple versions of [**Java**](https://openjdk.org/) on the `WSL File System` is to use [SDKMAN](https://sdkman.io/). This is a free, lightweight, open-source utility written in [Bash](https://www.gnu.org/software/bash/) that provides a convenient command line interface to manage multiple versions of [**Java**](https://openjdk.org/) and also takes care of setting the necessary environment variables.

Following the [official instructions](https://sdkman.io/install), install [SDKMAN](https://sdkman.io/) and the necessary dependencies executing the upcomming commands on a [Ubuntu](https://ubuntu.com/) terminal:

    sudo apt update
    sudo apt install zip unzip
    curl -s "https://get.sdkman.io" | bash

After completing the installation process, open a new terminal or run the following command in the same shell:

    source "$HOME/.sdkman/bin/sdkman-init.sh"

To confirm the installation's success, execute the following command:

    sdk version

To list the available [**Java**](https://openjdk.org/) versions, execute the following command:

    sdk list java

To install a specific version of [**Java**](https://openjdk.org/), replace the **{LABEL}** in the upcoming command as appropriate and then execute it:

    sdk install java {IDENTIFIER}

> **Label Definition**
>
> + **{IDENTIFIER}** : Identifier of the desired [**Java**](https://openjdk.org/) version as shown in the output of the command `sdk list java`, e.g. *21.ea.35-open*

To set a specific version of [**Java**](https://openjdk.org/) as the default, replace the **{LABEL}** in the upcoming command as appropriate and then execute it:

    sdk default java {IDENTIFIER}

> **Label Definition**
>
> + **{IDENTIFIER}** : Identifier of the desired [**Java**](https://openjdk.org/) version as shown in the output of the command `sdk list java`, e.g. *21.ea.35-open*

To check if the `JAVA_HOME` value was properly set, check the output of the following command:

    echo $JAVA_HOME

To check if the Windows `PATH` value was properly set, check the output of the following command:

    echo $PATH

To check if **Java** was properly installed, check the output of the following command:

    java -version

If everything is correct, the above command will output **Java Runtime Environment** version.

Finally, to check if the **Java Compiler** was properly installed, check the output of the following command:

    javac -version

If everything is correct, the above command will output the **Java Compiler** version.

##### 4.5.1.2. Installation on the Windows Native File System

The instructions shown here describe how to manually install [**Java**](https://openjdk.org/) on the `Windows Native File System` for the current *user account*.

Download the *.zip* option of the desired JDK version and and unpack it to a folder inside `C:\DEV\java`. Rename the extracted folder taking in consideration the following structure:

    {VENDOR}-{VERSION}-{PROJECT}

The different parts in the above name structure, shall be replaced as explained next:

> + **{VENDOR}** : The Java vendor's name, e.g. *oracle*
> + **{VERSION}** : The Java version number, including the string *jdk*, e.g. *jdk1.8.0.231*
> + **{PROJECT}** : The name of the project where this version of Java will be used, e.g. *sa3*
>
> With the above examples, the JDK folder name would be *oracle-jdk1.8.0.231-sa3*

To set `JAVA_HOME` as environment variable for the current *user account*, go to `Control Panel -> User Accounts` and choose the option ***Change my environment variables***.

On the ***User variables*** section, click the **New** button and fill the *Variable name* input box with `JAVA_HOME` and *Variable value* input box with the path to the JDK folder. If a `JAVA_HOME` already exists, select it and click the **Edit** button, then fill the *Variable value* input box with the path to the desired JDK folder.

Still on the ***User variables*** section, select the `Path` variable and click the **Edit** button. Then, click the **New** button and fill the input box with the following value:

    %JAVA_HOME%\bin

Click the **OK** button to close the window used to edit the `PATH` variable and then click the **OK** button on the *environment variables* window to close it.

To check if the Windows `JAVA_HOME` value was properly set, open a Windows Command Prompt and check the output of the following command:

    echo %JAVA_HOME%

To check if the Windows `PATH` value was properly set, on the same Windows Command Prompt, check the output of the following command:

    echo %PATH%

To check if **Java** was properly installed, on the same Windows Command Prompt, check the output of the following command:

    java -version

If everything is correct, the above command will output **Java Runtime Environment** version.

Finally, to check if the **Java Compiler** was properly installed, on the same Windows Command Prompt, check the output of the following command:

    javac -version

If everything is correct, the above command will output the **Java Compiler** version.

### 4.6. Apache Maven

[**Apache Maven**](https://maven.apache.org/) is a build automation tool used primarily for Java projects. It can also be used to build and manage projects written in C#, Ruby, Scala, and other languages and it is hosted by the [Apache Software Foundation](https://en.wikipedia.org/wiki/Apache_Software_Foundation).

#### 4.6.1. Installation

##### 4.6.1.1. Installation on the WSL File System

To be able to install a specific [**Apache Maven**](https://maven.apache.org/) version on the `WSL Fily System`, I like to follow a procedure inspired by the [Linuxiz Blog](https://linuxize.com/post/how-to-install-apache-maven-on-ubuntu-18-04/).

Start by creating the folder where [**Apache Maven**](https://maven.apache.org/) will be installed, executing the following commands:

    sudo mkdir -p /opt/maven/candidates
    sudo chown -R $USER:$USER /opt/maven/

Check the output of the upcoming command to confirm that the folder was created as desired:

    ls -la --group-directories-first /opt

To download the desired [**Apache Maven**](https://maven.apache.org/) version in the `/tmp` directory, replace the **{LABEL}** in the upcoming command as appropriate and then execute it:

    wget {DOWNLOAD_LINK} -P /tmp

> **Label Definition**
>
> + **{DOWNLOAD_LINK}** : Download link to the binary `tar.gz` archive take from the official [download page](https://maven.apache.org/download.cgi)

Once the download is completed, extract the archive in the `/opt/candidates` directory with the following command:

    tar xf /tmp/apache-maven-*.tar.gz -C /opt/maven/candidates/

Check the output of the upcoming command to confirm that the folder was created as desired:

    ls -la --group-directories-first /opt/maven/candidates

Then, rename the extracted folder taking in consideration the following structure:

    apache-maven-{VERSION}-{PROJECT}

The different parts in the above name structure, shall be replaced as explained next:

> + **{VERSION}** : The Maven version number, e.g. *3.8.6*
> + **{PROJECT}** : The name of the project where this instance of Maven will be used, e.g. *sa3*
>
> With the above examples, the Maven folder name would be *apache-maven-3.8.6-sa3*

Check the output of the upcoming command to confirm that the folder was renamed as desired:

    ls -la --group-directories-first /opt/maven/candidates

To have more control over [**Apache Maven**](https://maven.apache.org/) versions and updates, replace the **{LABEL}** in the upcoming command as appropriate and then execute it to create a symbolic link `current` that will point to the [**Apache Maven**](https://maven.apache.org/) installation folder:

    ln -s /opt/maven/candidates/{MAVEN_FOLDER} /opt/maven/current

> + **{MAVEN_FOLDER}** : The folder's name that contains the desired version, e.g. *apache-maven-3.8.6-sa3*

Check the output of the upcoming commands to confirm that the the symlinnk was created as desired:

    ls -la --group-directories-first /opt/maven/
    ls -la --group-directories-first /opt/maven/current/

Later if you want to upgrade your [**Apache Maven**](https://maven.apache.org/) installation you can simply unpack the newer version and change the symlink to point to the latest version.

To set the `MAVEN_HOME` environment variable for your [WSL](https://learn.microsoft.com/windows/wsl/) user, open the file `~/.bashrc` with the [nano text editor](https://www.nano-editor.org/), executing the below command on a [Ubuntu](https://ubuntu.com/) terminal.

    nano ~/.bashrc

Then, add the upcoming snippet to the `~/.bashrc` imediatly before sourcing the file to customize the bash prompt.

    # User's environmnent variables
    export export MAVEN_HOME=/opt/maven/current

    # User's path customization
    export PATH=${MAVEN_HOME}/bin:${PATH}

Save the changes with the command `CTRL + O` and then exit the [nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`.

To enable the changes made, you will need to source the`~/.bashrc` file, executing the following command:

    source ~/.bashrc

To check if the `MAVEN_HOME` environment variable was properly set, check the output of the following command:

    echo $MAVEN_HOME

To check if the users's `PATH` was properly set, check the output of the following command:

    echo $PATH

To check if **Apache Maven** was properly installed, check the output of the following command:

    mvn -version

If everything is correct, the above command will output the **Apache Maven** version.

##### 4.6.1.2. Installation on the Windows Native File System

To install [**Apache Maven**](https://maven.apache.org/), download the desired [Binary zip archive](https://maven.apache.org/download.cgi) and unpack it to the folder `C:\DEV\apache-maven`. Rename the extracted folder taking in consideration the following structure:

    apache-maven-{VERSION}-{PROJECT}

The different parts in the above name structure, shall be replaced as explained next:

> + **{VERSION}** : The Maven version number, e.g. *3.8.6*
> + **{PROJECT}** : The name of the project where this instance of Maven will be used, e.g. *sa3*
>
> With the above examples, the Maven folder name would be *apache-maven-3.8.6-sa3*

To set the `MAVEN_HOME` environment variable for the current *user account* go to `Control Panel -> User Accounts` and choose the option ***Change my environment variables***.

On the ***User variables*** section, click the **New** button and fill the *Variable name* input box with **MAVEN_HOME** and the *Variable value* input box with the path to the **Apache Maven** folder. If a `MAVEN_HOME` already exists, select it and click the **Edit** button, then fill the *Variable value* input box with the path to the **Apache Maven** installation folder.

Still on the ***User variables*** section, select the `Path` variable and click the **Edit** button. Then, click the **New** button and fill the input box with the following value:

    %MAVEN_HOME%\bin

Click the **OK** button to close the window used to edit the `PATH` variable and then click the **OK** button on the *environment variables* window to close it.

To check if the Windows `MAVEN_HOME` value was properly set, open a Windows Command Prompt and check the output of the following command:

    echo %MAVEN_HOME%

To check if the Windows `PATH` value was properly set, on the same Windows Command Prompt, check the output of the following command:

    echo %PATH%

To check if **Apache Maven** was properly installed, on the same Windows Command Prompt, check the output of the following command:

    mvn -version

If everything is correct, the above command will output the **Apache Maven** version.

#### 4.6.2. Configuration

The default location for the user's settings file and for the *Maven Local Repository* is the `.m2` folder at the user's *Home Folder*. Check it it already exists and if it doesn't create it with the upcoming command. If [**Apache Maven**](https://maven.apache.org/) is installed on the `WSL File System`, use a [Ubuntu](https://ubuntu.com/) terminal and if it is installed on the `Windows Native File System`. use a  [Git Bash](https://git-scm.com/) terminal.

    mkdir -p ~/.m2

The development environment will better contained if a *Maven Local Repository* is set for each project. Therefore, replace the **{LABEL}** in the upcoming command as appropriate and execute it. If [**Apache Maven**](https://maven.apache.org/) is installed on the `WSL File System`, use a [Ubuntu](https://ubuntu.com/) terminal and if it is installed on the `Windows Native File System`. use a [Git Bash](https://git-scm.com/) terminal.

    mkdir -p ~/.m2/repository-{PROJECT}

> **Label Definition**
>
> + **{PROJECT}** : The label that identifies the project name

To set the folder created with the above command as the custom location for the *Maven Local Repository*, edit the file `settings.xml` located at the `conf` folder of the **Apache Maven** installation folder, first replace the **{LABEL}** in the below snippet as appropriate and then insert the it immediately after the *localRepository* comment section.

    <localRepository>${user.home}/.m2/repository-{PROJECT}</localRepository>

> **Label Definition**
>
> + **{PROJECT}** : The label that identifies the project name

#### 4.6.3. Usage & Maintenance

For each change of the user's `settings.xml` file, placed on the folder `~/.m2`, a copy of the file that is replaced should be made and named with the following naming structure

    settings-{PROJECT}-{DATE}.xml

The different parts in the above name structure, shall be replaced as explained next:

> + **{PROJECT}** : The name of the project where the settings.xml file was used with, e.g. *sa3*
> + **{DATE}** : The date of the change on the format yyyy-mm-dd, e.g. *2020-03-21*
>
> With the above examples, the settings.xml backup file name would be *settings-sa3-2020-03-21.xml*

If there's no need to have a user's `settings.xml` file, the last one in use should be backuped as explain above and then deleted.

A `README.md` file must be stored on the folder `~/.m2` with a list a of all existing `settings.xml` file backups. This list must include the context of each bacuped file usage.

### 4.7. Apache Tomcat

[**Apache Tomcat**](http://tomcat.apache.org/) is an open source implementation of the [Jakarta Servlet](https://projects.eclipse.org/projects/ee4j.servlet), [Jakarta Server Pages](https://projects.eclipse.org/projects/ee4j.jsp), [Jakarta Expression Language](https://projects.eclipse.org/projects/ee4j.el), [Jakarta WebSocket](https://projects.eclipse.org/projects/ee4j.websocket), [Jakarta Annotations](https://projects.eclipse.org/projects/ee4j.cahttps://projects.eclipse.org/projects/ee4j.authentication) specifications. These specifications are part of the [Jakarta EE platform](https://projects.eclipse.org/projects/ee4j.jakartaee-platform).

#### 4.7.1. Installation

To install [**Apache Tomcat**](http://tomcat.apache.org/) application server, download the desired [release zip archive](http://tomcat.apache.org/) and unpack it to the folder `C:\DEV\apache-tomcat`. Rename the extracted folder taking in consideration the following structure:

    tomcat-{VERSION}-{PROJECT}

The different parts in the above name structure, shall be replaced as explained next:

> + **{VERSION}** : The Tomcat version number, e.g. *8.5.82*
> + **{PROJECT}** : The name of the project where this instance of Tomcat will be used, e.g. *sa3*
>
> With the above examples, the Tomcat folder name would be *tomcat-8.5.82-sa3*

### 4.8 Quarkus CLI

The [**Quarkus CLI**](https://quarkus.io/guides/cli-tooling) lets you create Quarkus projects, manage extensions and do essential build and development tasks using the underlying project build tool.

#### 4.8.1. Installation

##### 4.8.1.1. Installation on the WSL File System

To install [**Quarkus CLI**](https://quarkus.io/guides/cli-tooling) on the `WSL File System`, as recomended on the [Quarkus documentation](https://quarkus.io/guides/cli-tooling), use [SDKMAN](https://sdkman.io/), execute the upcomming command on a [Ubuntu](https://ubuntu.com/) terminal.

    sdk install quarkus

To verify if the [**Quarkus CLI**](https://quarkus.io/guides/cli-tooling) installation was properly made, check the output of the following command:

    quarkus --version

##### 4.8.1.2. Installation on the Windows Native File System

To install [**Quarkus CLI**](https://quarkus.io/guides/cli-tooling), use a PowerShell console with *Administrator* privileges and execute the following command:

    choco install quarkus

To verify if the [**Quarkus CLI**](https://quarkus.io/guides/cli-tooling) installation was properly made, check the output of the following command:

    quarkus --version

### 4.9 AWS CLI

The [**AWS Command Line Interface (AWS CLI)**](https://aws.amazon.com/cli/) is a unified tool to manage your AWS services. With just one tool to download and configure, you can control multiple AWS services from the command line and automate them through scripts.

#### 4.9.1. Installation

To install [**AWS CLI**](https://aws.amazon.com/cli/), download the latest version from [official downloads page](https://aws.amazon.com/cli/). Then, execute the downloaded file (there will be a prompt for elevated permissions that must be accepted).

### 4.10 Make

[**GNU Make**](https://www.gnu.org/software/make/) is a tool which controls the generation of executables and other non-source files of a program from the program's source files.

#### 4.10.1. Installation

To install [**GNU Make**](https://www.gnu.org/software/make/), use a PowerShell console with *Administrator* privileges and execute the following command:

    choco install make

### 4.11. Rancher Desktop

[**Rancher Desktop**](https://rancherdesktop.io/) is an app that provides container management and Kubernetes on the desktop. It is available for Mac (both on Intel and Apple Silicon), Windows, and Linux.

#### 4.11.1. Installation

[Windows Linux Subsystem (WSL)](https://learn.microsoft.com/en-us/windows/wsl/) is required to run [**Rancher Desktop**](https://rancherdesktop.io/). If it isn't installed, follow the [instructions on this repository](./1-fundamental-software.md#13-windows-subsystem-for-linux) to install it.

To [install](https://docs.rancherdesktop.io/getting-started/installation/) the software [Rancher Desktop](https://rancherdesktop.io/), download the latest version from the [releases page on GitHub](https://github.com/rancher-sandbox/rancher-desktop/releases) and then execute the downloaded executable.

When prompted, choose the option *Install for all users of this machine* (there will be a prompt for elevated permissions that must be accepted) and when the installation is finished, click Finish to close the installation wizard and run the [Rancher Desktop](https://rancherdesktop.io/) application.

On the [**Rancher Desktop**](https://rancherdesktop.io/) welcome screen, uncheck the option `Enable Kubernetes` and select `dockerd` as the *Container Engine*.

It's now necessary to re-start Windows to enable all the previous changes.

Make sure that [**Rancher Desktop**](https://rancherdesktop.io/) is running (launch it if necessary) and, on a PowerShell console, execute the following command:

    wsl --list --verbose

If everything is correct, the output of the previous command will show the **rancher-desktop** distros running on [WSL](https://learn.microsoft.com/windows/wsl/).

The [**Rancher Desktop**](https://rancherdesktop.io/) installation and usage files are [stored in the local](https://github.com/rancher-sandbox/rancher-desktop/discussions/1551#discussioncomment-2137434) in the following folders:

+ `%USERPROFILE%\AppData\Local\rancher-desktop` contains the distribution data, container images, logs, etc;
+ `%USERPROFILE%\AppData\Roaming\rancher-desktop` contains preferences;
+ `%USERPROFILE%\AppData\Local\Programs\Rancher Desktop` is the folder where the application is installed.

To be able to run the `docker` command on the terminal, it's necessary to add your Windows user to the `docker-users` group. On a PowerShell console, execute the below command to check if the `docker-users` group exists and if your user belongs to it.

    net localgroup docker-users

If the `docker-users` group doesn't exists yet, open a PowerShell console as **Administrator** and [create it](https://stackoverflow.com/a/64293327) with the following commands:

    New-LocalGroup -Name 'docker-users' -Description 'docker Users Group'
    Add-LocalGroupMember -Group 'Administrators' -Member ('docker-users') -Verbose
    Add-LocalGroupMember -Group 'docker-users' -Member ('Username','Administrators') -Verbose

To add your Windows user to the `docker-users` group, open a PowerShell console as **Administrator**, replace the ***{LABEL}*** in the below command as appropriate and then execute it.

    net localgroup docker-users "{YOUR_USER_ID}" /ADD

> **Label Definition**
>
> + **{YOUR_USER_ID}** : Your local Windows user name that can be determines by looking at the folder name under `C:\Users\`.

If, successful, the output of the previous command will be `The command completed successfully`.

It's now necessary to re-start Windows to enable all the previous changes.

To confirm that everything is correct, execute the below commands on a [Git Bash](https://git-scm.com/) terminal and check its output.

    net localgroup docker-users
    docker --version
    kubectl version

### 4.12 Terraform

[**Terraform**](https://www.terraform.io/) is a tool for building, changing, and versioning infrastructure safely and efficiently.

#### 4.12.1. Installation

To install [**Terraform**](https://www.terraform.io/), use a PowerShell console with *Administrator* privileges and execute the following command:

    choco install terraform

### 4.13. NVS (Node Version Switcher)

[**NVS**](https://github.com/jasongin/nvs) is a cross-platform utility for switching between different versions and forks of Node.js. [**NVS**](https://github.com/jasongin/nvs) is itself written in node JavaScript.

#### 4.13.1. Installation

The instructions to install [**NVS**](https://github.com/jasongin/nvs) shown here are following the official instructions for the [manual setup from a Command Prompt](https://github.com/jasongin/nvs/blob/master/doc/SETUP.md#manual-setup---command-prompt).

To set `NVS_HOME` as environment variable for the current *user account* go to `Control Panel -> User Accounts` and choose the option ***Change my environment variables***.

On the ***User variables*** section, click the **New** button and fill the *Variable name* input box with `NVS_HOME` and the *Variable value* input box with `%LOCALAPPDATA%\nvs`.

Click the **OK** button to close the window used to create the new environment variable and then click the **OK** button on the *environment variables* window to close it.

To check if the Windows `NVS_HOME` value was properly set, open a Windows Command Prompt and check the output of the following command:

    echo %NVS_HOME%

On the same Windows Command Prompt, clone the [nvs repository](https://github.com/jasongin/nvs) with the following command:

    git clone https://github.com/jasongin/nvs "%NVS_HOME%"

Then, on the same Windows Command Prompt, install the application executing the following command:

    "%NVS_HOME%\nvs.cmd" install

To check if the folder `%LOCALAPPDATA%\nvs` was properly added to the current *user account* path variable, go to `Control Panel -> User Accounts` and choose the option ***Change my environment variables***.

On the ***User variables*** section, select the `Path` variable and click the **Edit** button. Then check if the folder `%LOCALAPPDATA%\nvs` is one of the `Path` variable entries. If it isn't, edit or create it.

Click the **OK** button to close the window used to edit the `PATH` variable and then click the **OK** button on the *environment variables* window to close it.

To check if [**NVS**](https://github.com/jasongin/nvs) was properly installed, on the same Windows Command Prompt, check the output of the following command:

    nvs --version

To be able to use [**NVS**](https://github.com/jasongin/nvs) with [Git Bash](https://github.com/jasongin/nvs/blob/master/doc/SETUP.md#git-bash-on-windows), open a [Git Bash](https://git-scm.com/) terminal and execute the below command to source the `install` command:

    . "$NVS_HOME/nvs.sh" install

The `install` command adds a snippet to the `~/.bashrc` file to source `nvs.sh`, so that the `nvs` function is available in future shells. The `nvs.sh` script adds an `nvs` shell function to the environment.

Edit the `~/.bashrc` file and add the bellow comment above the code added by the `install` command.

    # Adds an nvs shell function to the environment to enable the tool to be invoked as just nvs without any path

After adding the above snippet, the new code on the `~/.bashrc` will be similar to the following snippet:

    # Adds an nvs shell function to the environment to enable the tool to be invoked as just nvs without any path
    function setupNvs {
            export NVS_HOME="$HOME\AppData\Local\nvs";
            [ -s "$NVS_HOME/nvs.sh" ] && source "$NVS_HOME/nvs.sh" >> /dev/null;
            return 0;
    }
    setupNvs

To add the latest version of **node** run the below command from a Windows Command Prompt.

    nvs add lts

Then execute the bellow command to add a version of node to PATH for the current shell:

    nvs use lts

The above command will **only** set the **node** version in use for the current shell/terminal and it will **not** be permanent. To add it to PATH permanently, execute the following command:

    nvs link lts

To check if the folder `%LOCALAPPDATA%\nvs\default` was properly added to the current *user account* path variable, go to `Control Panel -> User Accounts` and choose the option ***Change my environment variables***.

On the ***User variables*** section, select the `Path` variable and click the **Edit** button. Then check if the folder `%LOCALAPPDATA%\nvs\default` is one of the `Path` variable entries. If it isn't, edit or create it.

Click the **OK** button to close the window used to edit the `PATH` variable and then click the **OK** button on the *environment variables* window to close it.

From now on, the latest **node** lts version will be available on all shells of the system. To confirm that everything is properly set, check the output of the below commands executed from a Windows Command Prompt, from a PowerShell console and from a [Git Bash](https://git-scm.com/) terminal.

    node --version
    npm --version

If everything is correct, the above commands will output the **node** version and the **npm** version.

### 4.14. IntelliJ IDEA

[**IntelliJ IDEA**](https://www.jetbrains.com/idea/) is an integrated development environment written in Java for developing computer software written in Java, Kotlin, Groovy, and other JVM-based languages. It is developed by JetBrains and is available as an Apache 2 Licensed community edition, and in a proprietary commercial edition.

#### 4.14.1. Installation

The [**JetBrains Toolbox App**](https://www.jetbrains.com/toolbox-app/) is the [recommended way](https://www.jetbrains.com/help/idea/installation-guide.html#toolbox) to install JetBrain products. Download the latest installation file from the [official download page](https://www.jetbrains.com/toolbox-app/). Then, execute the downloaded file to install [**JetBrains Toolbox App**](https://www.jetbrains.com/toolbox-app/).

Move the [**JetBrains Toolbox App**](https://www.jetbrains.com/toolbox-app/) *Start Menu* *shortcut* to the `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Development` folder (Create the `Development` folder if it doesn't exits). Then delete the folder `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\JetBrains Toolbox` that was created by the [**JetBrains Toolbox App**](https://www.jetbrains.com/toolbox-app/) installer.

Execute the [**JetBrains Toolbox App**](https://www.jetbrains.com/toolbox-app/) and then login in the JetBrains account. Then, on the `Toolbox App Menu`choose the `Settings` option and uncheck the checkbox `Launch Toolbox App at system startup`.  

To install [**IntelliJ IDEA**](https://www.jetbrains.com/idea/), on the [**JetBrains Toolbox App**](https://www.jetbrains.com/toolbox-app/) and then choose the desired *IntelliJ IDEA* version to install and follow the instructions prompted.

Move the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) *Start Menu* *shortcut* to the `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Development` folder. Then delete the folder `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\JetBrains Toolbox` that was created by the installer.

Some antivirus software can interfere with the IDE build process, [causing builds to run dramatically slower](https://intellij-support.jetbrains.com/hc/en-us/articles/360006298560). To prevent this, the folders where the IDE writes a lot of files should be excluded from the antivirus software real-time scanning. That can be done following the following steps:

+ Click the Start button and search for “Windows Security”;
+ Start the *Windows Security* application;
+ Click on “Virus and threat protection”;
+ Click on “Manage settings” under “Virus & threat protection settings”;
+ Scroll down if needed, and then click on “Add or remove exclusions” (there will be a prompt for elevated permissions that must be accepted);
+ Click the button `+ Add an exclusion`, choose `Folder` from the dropdown list and then add all (one by one) the following folders:
  + `C:\CODE`
  + `%APPDATA%\JetBrains`
  + `%LOCALAPPDATA%\JetBrains\`

We also recommend [excluding the IDE process from the antivirus](https://intellij-support.jetbrains.com/hc/en-us/articles/360005028939-Slow-startup-on-Windows-splash-screen-appears-in-more-than-20-seconds) to improve the startup performance. To do that exclusion, on the on “Add or remove exclusions”, Click the button `+ Add an exclusion`, choose `Process` from the dropdown list and then add all (one by one) the following processes:

+ `idea64.exe`
+ `fsnotifier.exe`
+ `fsnotifier64.exe`

Execute the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) chosen version and follow the instructions prompted. On the welcome screen, click the button `Enable New UI`.

#### 4.14.2. Install plugins

##### 4.14.2.1. Install SonarLint plugin

[SonarLint](https://plugins.jetbrains.com/plugin/7973-sonarlint) is an IDE extension that helps to detect and fix quality issues as the code is written. To install it, choose `Plugins` from the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) welcome screen and then, on the `Marketplace` tab search for "SonarLint". Within the listed plugins, click "Install" on the right one and follow the "Wizard" instructions to install it.

##### 4.14.2.2. Install Markdown plugin

[Markdown](https://plugins.jetbrains.com/plugin/7793-markdown) is an IDE extension that provides the capability to edit Markdown files within the IDE and see the rendered HTML in a live preview. To install it, choose `Plugins` from the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) welcome screen and then, on the `Marketplace` tab search for "Markdown". Within the listed plugins, click "Install" on the right one and follow the "Wizard" instructions to install it.

#### 4.14.3. Set code formatters

##### 4.14.3.1. Java

[Google Java Style Guide](https://google.github.io/styleguide/javaguide.html) seems to be the most popular **Code Style Guide** for [Java](https://www.java.com/en/). This style guide is licensed under the [CC-By 3.0 License](https://creativecommons.org/licenses/by/3.0/) and a there's a [repository](https://github.com/google/styleguide) where a formatter configuration file for [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) is available.

To add the above mentioned Code Style Formatter settings, on the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) welcome screen, choose `All Settings` from the `Customize` tab. Then choose the tab `Editor->Code Style->Java`. On this tab, click the `settings` icon choose `Import Scheme/IntelliJ IDEA code style XML` and pick the file(s) with the desired settings.

#### 4.14.4. Configure Version Control

##### 4.14.4.1. Commit

On the **Version Control**, the *Local Changes* and the *Shelf* tabs are very useful on my workflow. To enable those tabs it's necessary to make a small [change on the default settings](https://intellij-support.jetbrains.com/hc/en-us/community/posts/4412759255698-2021-2-3-Git-Local-Changes-view-in-VCS-is-gone).

To make the necessary change, on the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) welcome screen, choose `All Settings` from the `Customize` tab. Then choose the tab `Version Control->Commit`.  On this tab, uncheck the `Use non-modal commit interface` checkbox.

#### 4.14.5. Configure Build Tools

##### 4.14.5.1. Maven

To customize *Maven*, on the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) welcome screen, choose `All Settings` from the `Customize` tab. Then choose the tab `Build, Execution, Deployment->Build Tools->Maven`. On this tab, change the input boxes listed below as described:

+ **Maven home path** : The path to the chosen [system *Maven* instance](#451-installation);
+ **User setting file** : Check the `Override` checkbox and point to the [custom project's *Maven Local Repository*](#452-configuration);
+ **Local repository** : Check the `Override` checkbox and point to the [custom project's *Maven Local Repository*](#452-configuration);

This is a per project setting, therefore it might be necessary to set it for every project when opened with [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) for the first time.

#### 4.14.6. Configure Tools

##### 4.14.6.1. Terminal

To customize the *Terminal* in use with [**IntelliJ IDEA**](https://www.jetbrains.com/idea/), on the application welcome screen, choose `All Settings` from the `Customize` tab. Then choose the tab `Tools->Terminak`. On this tab, change the input boxes listed below as described:

+ **Shell path** : `C:\Program Files\Git\bin\sh.exe --login --i`
+ **Default Tab name** : `Terminal`;

This settings will only take effect when starting a new terminal. Therefore, create/add/open a new terminal window and terminate the old one.

This is a per project setting, therefore it might be necessary to set it for every project when opened with [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) for the first time.

#### 4.14.7. Run/Debug Configurations

##### 4.14.7.1 Shorten command line method

To avoid the error "*Command line is too long*" when running tests it's necessary to set the "*Shorten command line*" method in the Run/Debug configuration to "*JAR manifest*". That can be done for the specific method or class, but it's better to [set it as default](https://stackoverflow.com/a/47927544) on [run/debug configuration templates](https://www.jetbrains.com/help/idea/run-debug-configuration.html#templates).

From the [**IntelliJ IDEA**](https://www.jetbrains.com/idea/) main menu, select `Run->Edit Configurations...`. On the screen that pop-up, click `Select configuration templates...` (bottom left corner of the pop-up screen). On the following pop-up screen, select the `JUnit` tab.

[Then](https://stackoverflow.com/a/65639857), click on the `Modify options` link (`ALT+M`) and set/select the `Shorten command line` option. Back on the `JUnit` tab, there will be a new dropdown input box named `Shorten command line`. In this new dropdown, choose the *Jar manifest* option. Click the button `OK` (once to close the `Select configuration templates` pop up and again to close the  `Run->Edit Configurations` pop up screen) and from now on all the new `JUnit` Run/Debug configurations will use this template.

### 4.15. Visual Studio Code

[**Visual Studio Code**](https://code.visualstudio.com/), also commonly referred to as **VS Code**, is a source-code editor made by Microsoft with the Electron Framework, for Windows, Linux and macOS. Features include support for debugging, syntax highlighting, intelligent code completion, snippets, code refactoring, and embedded Git.

#### 4.15.1. Installation

Download the [**Visual Studio Code**](https://code.visualstudio.com) *User Installer* file from the [official download page](https://code.visualstudio.com/download). Then, execute the downloaded file to install [**Visual Studio Code**](https://code.visualstudio.com).

Move the [**Visual Studio Code**](https://code.visualstudio.com) *Start Menu* *shortcut* to the `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Development` folder (Create the `Development` folder if it doesn't exits). Then delete the folder `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Visual Studio Code` that was created by the installer.

Execute [**Visual Studio Code**](https://code.visualstudio.com) and on the `Manage` gear menu (on the bottom left of the application screen). select the [`Turn on Setting Sync...` option](https://code.visualstudio.com/docs/editor/settings-sync). When asked to sign in, choose the *GitHub* option and then insert the needed credentials. When asked what preferences to sync, select the checkboxes listed next:

+ Settings;
+ Keyboard Shortcuts for each platform;
+ User Snippets;
+ Extensions
+ UI State

#### 4.15.2. Install extensions

With the `Settings Sync` turned on, [**Visual Studio Code**](https://code.visualstudio.com) will installed all the synced extensions. Wait for while to allow the full synchronization and then check if all of the following extensions were properly installed:

+ [Auto Rename Tag](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag);
+ [Better Comments](https://marketplace.visualstudio.com/items?itemName=aaron-bond.better-comments);
+ [Data Workspace](https://marketplace.visualstudio.com/items?itemName=ms-mssql.data-workspace-vscode);
+ [Debugger for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-debug);
+ [EditorConfig for VS Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig);
+ [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint);
+ [Extension Pack for java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-pack);
+ [IntelliSense for CSS class names in HTML](https://marketplace.visualstudio.com/items?itemName=Zignd.html-css-class-completion);
+ [Language Support for Java(TM) by Red Hat](https://marketplace.visualstudio.com/items?itemName=redhat.java);
+ [lit-html](https://marketplace.visualstudio.com/items?itemName=bierner.lit-html);
+ [lit-plugin](https://marketplace.visualstudio.com/items?itemName=runem.lit-plugin);
+ [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint);
+ [Maven for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-maven);
+ [MySQL Shell for VS Code](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint);
+ [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense);
+ [PHP Debug](https://marketplace.visualstudio.com/items?itemName=xdebug.php-debug);
+ [PHP Extension Pack](https://marketplace.visualstudio.com/items?itemName=xdebug.php-pack);
+ [PHP Intelliphense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client);
+ [Project Manager for Java](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-dependency);
+ [Smarty](https://marketplace.visualstudio.com/items?itemName=imperez.smarty);
+ [SonarLint](https://marketplace.visualstudio.com/items?itemName=SonarSource.sonarlint-vscode);
+ [Spell Right](https://marketplace.visualstudio.com/items?itemName=ban.spellright);
+ [SQL Bindings](https://marketplace.visualstudio.com/items?itemName=ms-mssql.sql-bindings-vscode);
+ [SQL Database Projects](https://marketplace.visualstudio.com/items?itemName=ms-mssql.sql-database-projects-vscode);
+ [SQL Server (mssql)](https://marketplace.visualstudio.com/items?itemName=ms-mssql.mssql):
+ [Test Runner for Java)](https://marketplace.visualstudio.com/items?itemName=vscjava.vscode-java-test);
+ [WSL)](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl);
+ [XML Tools](https://marketplace.visualstudio.com/items?itemName=DotJoshJohnson.xml).

### 4.16. Eclipse

TODO

### 4.17. DBeaver

[**DBeaver**](https://dbeaver.io/) is free and open source universal database tool for developers and database administrators.

#### 4.17.1. Installation

Download [**DBeaver**](https://dbeaver.io/) installer latest version from [official downloads page](https://dbeaver.io/download/). Then, execute the downloaded file and when prompted, choose to install [**DBeaver**](https://dbeaver.io/) only for the current user. When asked to select the components to install, check the following checkboxes:

+ DBeaver Community;
+ Include Java
+ Associate .SQL files

Move the [**DBeaver**](https://dbeaver.io/) *Start Menu* *shortcut* to the `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Development` folder (Create the `Development` folder if it doesn't exits). Then delete the folder `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\DBeaver Community` that was created by the installer.

### 4.18. Postman

[**Postman**](https://www.postman.com/) helps you be more efficient while working with APIs. Using Postman, you can construct complex HTTP requests quickly, organize them in collections.

#### 4.18.1. Installation

Download [**Postman**](https://www.postman.com/) installer latest version from [official downloads page](https://www.postman.com/downloads/). Then, execute the downloaded file and when prompted, sign in into the [**Postman**](https://www.postman.com/) account.

Move the [**Postman**](https://www.postman.com/) *Start Menu* *shortcut* to the `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Tools` folder (Create the `Tools` folder if it doesn't exits). Then delete the folder `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Postman` that was created by the installer.
