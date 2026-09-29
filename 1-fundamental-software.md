# Setup guide for a development machine on Windows

This file contains the **Fundamental Software** section of my [Setup guide for a development machine on Windows](https://github.com/EnduranceCode/windows-development-machine). The introduction to this guide as well as its full *Table of Contents* can be found on the [README.md](./README.md) file of this repository. The *Table of Contents* of this section is shown below.

## Table of Contents

1. [Fundamental Software](#1-fundamental-software)
    1. [Browser](#11-browser)
    2. [Windows Subsystem for Linux](#12-windows-subsystem-for-linux)
    3. [Windows Terminal](#13-windows-terminal)
    4. [Package Manager](#14-package-manager)
    5. [Git & Git Bash](#15-git--git-bash)
    6. [KeePassXC](#16-keepassxc)

## 1. Fundamental Software

### 1.1. Browser

With [Lubuntu](https://lubuntu.me) I use [Firefox](https://www.mozilla.org/firefox/new/) as my default browser and on Windows I used to choose [**Google Chrome**](https://www.google.com/chrome/). At the moment, I'm also using [Firefox](https://www.mozilla.org/firefox/new/) on Windows, mainly due to Firefox's [Multi-Account Containers](https://addons.mozilla.org/en-US/firefox/addon/multi-account-containers/) extension.

#### 1.1.1. Firefox

[**Firefox**](https://www.mozilla.org/firefox/new/) is a cross-platform web browser developed by [Mozilla](https://en.wikipedia.org/wiki/Mozilla).

##### 1.1.1.1. Installation

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**Firefox**](https://www.mozilla.org/firefox/new/), download the latest version from the [official downloads page](https://www.mozilla.org/firefox/new/). Then, execute the downloaded file (there will be a prompt for elevated permissions that must be accepted).

##### 1.1.1.2. Configuration

Set [**Firefox**](https://www.mozilla.org/firefox/new/) preferences as desired and then install the following extensions:

+ [AWS Extend Switch Roles](https://addons.mozilla.org/firefox/addon/aws-extend-switch-roles3/)
+ [ColorZilla](https://addons.mozilla.org/firefox/addon/colorzilla/)
+ [Firefox Facebook Container](https://addons.mozilla.org/en-US/firefox/addon/facebook-container/)
+ [Firefox Multi-Account Containers](https://addons.mozilla.org/firefox/addon/multi-account-containers/)
+ [FoxyProxy Standard](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/)
+ [KeePassXC-Browser](https://addons.mozilla.org/firefox/addon/keepassxc-browser/)
+ [Linkding](https://addons.mozilla.org/en-US/firefox/addon/linkding-extension/)
+ [Markdown Viewer](https://addons.mozilla.org/en-US/firefox/addon/markdown-viewer-chrome/)
+ [Raindrop.io](https://addons.mozilla.org/firefox/addon/raindropio/)
+ [Search by Image](https://addons.mozilla.org/en-US/firefox/addon/search_by_image/)
+ [Tab Session Manager](https://addons.mozilla.org/firefox/addon/tab-session-manager/)
+ [Wapplyzer](https://addons.mozilla.org/firefox/addon/wappalyzer/)

Set the desired options for all the above extensions. The folder `root/home/user/browser/extensions` in the [**system-configuration-files**](https://github.com/EnduranceCode/system-configuration-files) repository contains settings that can be imported to the browser extensions that support it.

#### 1.1.2. Google Chrome

[**Google Chrome**](https://www.google.com/chrome/) is a cross-platform web browser developed by [Google](https://en.wikipedia.org/wiki/Google).

##### 1.1.2.1. Installation

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**Google Chrome**](https://www.google.com/chrome/), download the latest version from the [official downloads page](https://www.google.com/chrome/). Then, execute the downloaded file (there will be a prompt for elevated permissions that must be accepted).

##### 1.1.2.2. Configuration

Set [**Google Chrome**](https://www.google.com/chrome/) preferences as desired and then install the following extensions:

+ [AWS Extend Switch Roles](https://chrome.google.com/webstore/detail/aws-extend-switch-roles/jpmkfafbacpgapdghgdpembnojdlgkdl)
+ [ColorZilla](https://chromewebstore.google.com/detail/colorzilla/bhlhnicpbhignbdhedgjhgdocnmhomnp)
+ [JSON Formatter](https://chrome.google.com/webstore/detail/json-formatter/bcjindcccaagfpapjjmafapmmgkkhgoa)
+ [KeePassXC-Browser](https://chrome.google.com/webstore/detail/keepassxc-browser/oboonakemofpalcgghocfoadofidjkkk)
+ [Linkding](https://chromewebstore.google.com/detail/linkding-extension/beakmhbijpdhipnjhnclmhgjlddhidpe)
+ [Proxy SwitchyOmega](https://chrome.google.com/webstore/detail/proxy-switchyomega/padekgcemlokbadohgkifijomclgjgif)
+ [Raindrop.io](https://chromewebstore.google.com/detail/raindropio/ldgfbffkinooeloadekpmfoklnobpien)
+ [Tab Session Manager](https://chrome.google.com/webstore/detail/tab-session-manager/iaiomicjabeggjcfkbimgmglanimpnae)
+ [Wapplyzer](https://chromewebstore.google.com/detail/wappalyzer-technology-pro/gppongmhjkpfnbhagpmjfkannfbllamg)

Set the desired options for all the above extensions. The folder `root/home/user/browser/extensions` in the [**system-configuration-files**](https://github.com/EnduranceCode/system-configuration-files) repository contains settings that can be imported to the browser extensions that support it.

### 1.2. Windows Subsystem for Linux

[Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/windows/wsl/) lets developers run a GNU/Linux environment directly on Windows.

#### 1.2.1. Installation

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue) ![WSL](https://img.shields.io/badge/WSL-purple)

Follow the [official instructions](https://learn.microsoft.com/windows/wsl/install) to [install](https://learn.microsoft.com/windows/wsl/install#install-wsl-command) [**WSL**](https://learn.microsoft.com/windows/wsl/), executing the following command on a PowerShell console with *administrator privileges*.

```powershell
wsl --install
```

Reboot the machine to be able to proceed with the [**WSL**](https://learn.microsoft.com/windows/wsl/) installation.

After rebooting your machine, set [**WSL 2**](https://learn.microsoft.com/windows/wsl/basic-commands#set-wsl-version-to-1-or-2) as your default version, executing the following command on a standard PowerShell console.

```powershell
wsl --set-default-version 2
```

To [update](https://learn.microsoft.com/windows/wsl/troubleshooting#updating-wsl) the [**WSL**](https://learn.microsoft.com/windows/wsl/) installation, execute the following command on a standard PowerShell console. The execution of this command will [require elevation](https://learn.microsoft.com/windows/security/application-security/application-control/user-account-control/how-it-works). If you choose not to [elevate](https://learn.microsoft.com/windows/security/application-security/application-control/user-account-control/how-it-works#the-uac-user-experience), the [**WSL**](https://learn.microsoft.com/windows/wsl/) update will fail.

```powershell
wsl --update
```

#### 1.2.2. Configuration

As per [Microsoft official documentation](https://learn.microsoft.com/windows/wsl/wsl-config#wslconfig) it is recommended to modify WSL configurations directly in **WSL Settings**, rather than manually editing the `.wslconfig` file. **WSL Settings** can be found in the Windows *Start menu* and is a graphical application that comes with WSL, allowing you to manage general settings that apply to all WSL 2 instances. It is analogous to the `.wslconfig` file.

On the **WSL Settings** *Memory and processor* tab check, and if necessary, adjust the following parameters:

+ **Processor Count** - Total available logical processors can be obtained with the Powershell command `Get-Ciminstance Win32_Processor | Select NumberOfLogicalProcessors`
+ **Memory Size**
+ **Swap Size**

On the *File System* tab check, and if necessary, adjust the following parameter:

+ **Default VHD Size**

On the *Networking* tab check, and if necessary, adjust the following parameters:

+ **Networking mode**: Set to `mirrored`
+ **Auto Proxy enabled**: Set to `On`
+ **DNS Proxy enabled**: Set to `On`

On the *Optional Features* tab check, and if necessary, adjust the following parameter:

+ **Auto memory reclaim**: Set to `DropCache`

By default, the `.wslconfig` file does not exist, and it will be created by the **WSL Settings** app if any of the default parameters are modified. After adjusting the general settings for all WSL 2 instances, the content of the `.wslconfig` file might be similar to the following snippet:

```txt
[wsl2]
processors=12
memory=32490MB
swap=8192MB

networkingMode=mirrored
autoProxy=true
dnsTunneling=true

autoMemoryReclaim=dropcache
```

Beware that the ideal values for **Processor Count**, **Memory Size** and **Swap Size** are hardware dependent.

For changes to apply, you may need to run `wsl --shutdown` from PowerShell to shut down the WSL 2 VM. Then "you must wait until the subsystem running your Linux distribution completely stops running and restarts for configuration setting updates to appear. This typically takes about 8 seconds after closing ALL instances of the distribution shell".

#### 1.2.3. WSL distribution installation & configuration

[List all available Linux distributions](https://learn.microsoft.com/windows/wsl/basic-commands#list-available-linux-distributions) executing the following command on a standard PowerShell console.

```powershell
wsl --list --online
```

[Ubuntu](https://ubuntu.com/) will be one of the distributions displayed on the output of the above command. To install [Ubuntu](https://ubuntu.com/) on [**WSL**](https://learn.microsoft.com/windows/wsl/), execute the following command on a standard PowerShell console.

```powershell
wsl --install -d Ubuntu
```

The distro named "**Ubuntu**" is [Canonical](https://canonical.com/)’s flagship/default **Ubuntu** distro for [**WSL**](https://learn.microsoft.com/windows/wsl/). It is intended to track the latest stable [Ubuntu LTS](https://ubuntu.com/about/release-cycle) available for [**WSL**](https://learn.microsoft.com/windows/wsl/). When a new LTS comes out, this "**Ubuntu**" distro can be upgraded to it (typically once Canonical considers upgrades ready—commonly after the first point release).

If a *version-pinned* distro is required, replace "**Ubuntu**" in the above command with the the desired [Ubuntu LTS](https://ubuntu.com/about/release-cycle) version. The *version-pinned* will only be updated if you explicitly enable/do a release upgrade. By default, *version-pinned* releases do not auto-upgrade to the next LTS.

With the execution of the command to install a [**WSL**](https://learn.microsoft.com/windows/wsl/) distro, you will be prompted to create a default Unix user account and to set a password for this user.

Replace the label **{DISTRO_NAME}**, in the following command, as appropriate and execute it on a standard PowerShell console to set the [default distribution](https://learn.microsoft.com/windows/wsl/basic-commands#set-default-linux-distribution).

```powershell
wsl --set-default {DISTRO_NAME}
```

On a regular PowerShell console, execute the following command to list the installed Linux distributions and check if everything is correct:

```powershell
wsl --list --verbose
```

If [Ubuntu](https://ubuntu.com/) is not running with [**WSL 2**](https://learn.microsoft.com/windows/wsl/), replace the **{LABEL}** in the following command as appropriate and execute it on a standard PowerShell console.

```powershell
wsl --set-version {DISTRO_NAME} 2
```

> **Label Definition**
>
> + **{DISTRO_NAME}** : Name of the Linux distribution to be executed with WSL 2

Once the process of installing [Ubuntu](https://ubuntu.com/) on [**WSL**](https://learn.microsoft.com/windows/wsl/) is complete, open the distribution using the *Start Menu*.

Configure the settings for your [Ubuntu](https://ubuntu.com/) installation by using the `wsl.conf` file that is stored on `/etc` folder of every [**WSL**](https://learn.microsoft.com/windows/wsl/) distribution. Open the file `/etc/wsl.conf` with the [Nano text editor](https://www.nano-editor.org/), executing the following command on a [Ubuntu](https://ubuntu.com/) terminal.

```bash
sudo nano /etc/wsl.conf
```

To change the [default mount location](https://learn.microsoft.com/windows/wsl/wsl-config#automount-settings) of the Windows `C:\` drive from the default `/mnt/c` to `/c`, add the following code snippet to the `/etc/wsl.conf` file.

```txt
[automount]
root=/
options="metadata,umask=22,fmask=11"
```

Then, to [enable systemd support](https://learn.microsoft.com/windows/wsl/wsl-config#systemd-support), add the following code snippet to the same `/etc/wsl.conf` file.

```txt
[boot]
systemd=true
```

Then, for the [interop settings](https://learn.microsoft.com/en-us/windows/wsl/wsl-config#interop-settings), add the following code snippet to the same `/etc/wsl.conf` file.

```txt
[interop]
enabled=true
appendWindowsPath=false
```

Finally, for the [network settings](https://learn.microsoft.com/windows/wsl/wsl-config#network-settings), add the following code snippet to the same `/etc/wsl.conf` file.

```txt
[network]
generateHosts=true
generateResolvConf=true
```

Save the changes with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`.

To enable the changes made, you will need to restart your [**WSL**](https://learn.microsoft.com/windows/wsl/) instances. It can be done with the execution of the following command on a standard PowerShell console.

```powershell
wsl --shutdown
```

 You must wait until the subsystem running your Linux distribution completely stops running and restarts for configuration setting updates to appear. This typically takes about 8 seconds after closing ALL instances of the distribution shell. Once [Ubuntu](https://ubuntu.com/) restarts, *systemd* should be running. You can confirm executing the following command on a [Ubuntu](https://ubuntu.com/) terminal, which will show the status of your services.

```bash
systemctl list-unit-files --type=service
```

Further WSL configurations can be found on the Microsoft article [Advanced settings configuration in WSL](https://learn.microsoft.com/windows/wsl/wsl-config).

By default, the [**WSL**](https://learn.microsoft.com/windows/wsl/) [Ubuntu](https://ubuntu.com/) environment doesn't naturally know how to talk to the Windows browser because the `BROWSER` environment variable isn't set, and the `xdg-open` command doesn't have a default handler. The cleanest way to solve this is to use the built-in ***PowerShell interop**. Windows allows you to call `.exe` files directly from the Linux terminal.

Since we've set `appendWindowsPath=false`, the WSL environment is isolated from the Windows System32 folder where `powershell.exe` lives. Instead of re-enabling the entire Windows `PATH`, replace the **{LABEL}** in the following command as appropriate and then execute it to create a specific symbolic link to PowerShell. This keeps your path clean but gives you the one tool you need.

```bash
mkdir -p ~/.local/bin
ln -s {PATH_TO_POWERSHELL}/powershell.exe ~/.local/bin/pwsh
```

> **Label Definition**
>
> + **{PATH_TO_POWERSHELL}** : Path to the Windows PowerShell executable folder obtained by executing `$PSHOME`

Ensure your `.local/bin` folder is in your `PATH` by checking your `~/.bashrc` and make sure this line exists:

```bash
# Add the ~/.local/bin to the PATH
export PATH="$HOME/.local/bin:$PATH"
```

To create a real `xdg-open` executable wrapper, execute the following command:

```bash
nano ~/.local/bin/xdg-open
```

Then, paste the following snippet on the newly created file.

```bash
#!/usr/bin/env bash
set -euo pipefail

target="${1:-}"
if [[ -z "$target" ]]; then
  echo "Usage: xdg-open <url-or-path>" >&2
  exit 2
fi

# If it's a Linux absolute path, convert it to a Windows path for Start.
if [[ "$target" == /* ]]; then
  target="$(wslpath -w "$target")"
fi

# Use Windows PowerShell (through the pwsh symlink) to open the target
# Start-Process handles URLs and file paths.
pwsh -NoProfile -Command "Start-Process '$target'" >/dev/null 2>&1
```

Save the changes with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`. Then make the `xdg-open` wrapper executable with the following commands:

```bash
chmod +x ~/.local/bin/xdg-open
hash -r
```

Check if the `xdg-open` wrapper is working as expected with the following commands:

```bash
which xdg-open
xdg-open "https://example.com"
```

To complete the process, it's necessary to edit the file `.bashrc` located in the home folder and add the following line to set the `BROWSER` environment variable.

```bash
export BROWSER="$HOME/.local/bin/xdg-open"
```

Open the file `.bashrc` with the [Nano text editor](https://www.nano-editor.org/) executing the following command:

```bash
nano ~/.bashrc
```

After adding the necessary modifications, save the file with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`. Make the changes effective with the following command:

```bash
source ~/.bashrc
```

The article [Set up a WSL development environment](https://learn.microsoft.com/windows/wsl/setup/environment) has some good optional advices to setup a development environment with  [**WSL**](https://learn.microsoft.com/windows/wsl/), but one that is almost mandatory is the installation of the [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701).

#### 1.2.3.1. Update, upgrade and install additional packages

It's recommended to regularly update and upgrade your packages using [Ubuntu](https://ubuntu.com/)'s package manager. This is done with the following command:

```bash
sudo apt update && sudo apt full-upgrade
```

Additional software can be installed using [Ubuntu](https://ubuntu.com/)'s package manager, exactly as in any other [Ubuntu](https://ubuntu.com/) installation.

To be able to install software from its source code, you need to make sure your system has a C++ compiler. The `build-essentials` packages are meta-packages that include all the necessary tools for compiling software. You can install it with the following command:

```bash
sudo apt install build-essential
```

To verify if the `build-essentials` installation was properly made, check the output of the following command:

```bash
gcc --version
```

#### 1.2.3.2. Secret storage on the WSL File System

Many command line tools can store their credentials (e.g. a **Personal Access Token**), but they usually delegate this task to an operating system credential store. On the `Windows Native File System`, the [Windows Credential Manager](https://learn.microsoft.com/windows/win32/secauthncredentialmanager) is available for that purpose. On the `WSL File System` there's no such service available by default: the desktop environment is absent, so there's no Secret Service provider (`GNOME Keyring` or `KWallet`) for the tools to talk to. Most of the tools then fall back to writing the secret in **plain text** inside a configuration file in your home folder, which can be read by any process running as your user and is included in backups of your home folder.

This section documents two ways to store secrets securely on the `WSL File System`. The recommended one is [`pass`](https://www.passwordstore.org/), which stores each secret as a [GnuPG](https://gnupg.org/) encrypted file and is available on a headless distribution; the optional one is [`GNOME Keyring`](https://wiki.gnome.org/Projects/GNOMEKeyring), which integrates with the Secret Service API but requires a working D-Bus session.

**Installation of `pass`**

To install [`pass`](https://www.passwordstore.org/) and its dependencies on a [Ubuntu](https://ubuntu.com/) terminal, execute the following commands:

```bash
sudo apt update
sudo apt install pass gnupg pinentry-curses
```

The package `pinentry-curses` provides the passphrase prompt, which is required every time the [GnuPG](https://gnupg.org/) agent needs to decrypt a secret.

**Creation of the GPG key**

[`pass`](https://www.passwordstore.org/) requires a [GnuPG](https://gnupg.org/) key pair to encrypt and decrypt secrets. Create it executing the following command:

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

The output lists one entry per key in the key pair, as the recommended `RSA and RSA` creates a **primary** key for signing and certifying and a **subkey** for encryption:

```text
sec   rsa3072/{PRIMARY_KEY_ID} {CREATION_DATE} [SC] [expires: {KEY_EXPIRATION_DATE}]
      {PRIMARY_KEY_FINGERPRINT}
uid                 [ultimate] {REAL_NAME} <{EMAIL}>
ssb   rsa3072/{SUBKEY_ID} {CREATION_DATE} [E] [expires: {KEY_EXPIRATION_DATE}]
```

> **Label Definition**
>
> + **{PRIMARY_KEY_ID}** : The 16 hexadecimal characters identifier of the **primary** key, displayed in the `sec` line after the algorithm
> + **{PRIMARY_KEY_FINGERPRINT}** : The full 40 hexadecimal characters identifier of the **primary** key, displayed on the line below the `sec` line. It's the extended form of the **{PRIMARY_KEY_ID}**, which it ends with, not a separate key
> + **{SUBKEY_ID}** : The 16 hexadecimal characters identifier of the **encryption** subkey, displayed in the `ssb` line
> + **{CREATION_DATE}** : The date the key was created
> + **{KEY_EXPIRATION_DATE}** : The date the key expires

The option `--keyid-format=long` is what makes [GnuPG](https://gnupg.org/) display the 16 characters identifiers instead of the 8 characters ones used by default. The letters in brackets are the key capabilities: `[SC]` on the `sec` line means **S**igning and **C**ertifying and `[E]` on the `ssb` line means **E**ncryption only. The primary key never handles the secrets themselves, which are encrypted with the subkey, so compromising the signing capability doesn't expose the ability to decrypt anything.

To use the identifiers on the commands below, replace the ***{LABEL}*** with the **{PRIMARY_KEY_ID}**, with the **{PRIMARY_KEY_FINGERPRINT}** or with the ***{EMAIL}***, but never with the **{SUBKEY_ID}**, as the commands that renew the expiration date operate on the primary key.

If you forget the passphrase, the secrets encrypted with that key can't be recovered, so store it on a password manager that doesn't depend on this [WSL](https://learn.microsoft.com/windows/wsl/) distribution, such as the [KeePassXC](#16-keepassxc) section of this guide or any other [KeePassXC](https://keepassxc.org/) database.

The label **{KEY_EXPIRATION}** refers to the expiration of the **key**, not to the passphrase: the passphrase itself doesn't expire and can be changed at any time with the command `gpg --passwd {GPG_IDENTITY}`. When the expiration date of the key is reached, the secrets already stored can still be decrypted (the command `pass show` only reports that the key has expired), but new secrets can no longer be added: the commands `pass insert`, `pass edit` and `pass generate` fail with an `encryption failed: unusable public key` error, because [GnuPG](https://gnupg.org/) refuses to encrypt to an expired key. The store then becomes read-only, which means that a secret can't be rotated until the expiration date is renewed.

Check the expiration date of the keys with the following command:

```bash
gpg --list-keys
```

The expiration date of a key is displayed as `[expires: YYYY-MM-DD]`, or as `[expired: YYYY-MM-DD]` when the date has already passed.

To renew the expiration date of the key, replace the ***{LABEL}*** in the below command as appropriate and then execute it (you'll be asked for the passphrase of the key):

```bash
gpg --quick-set-expire {GPG_IDENTITY} 3y '*'
```

> **Label Definition**
>
> + **{GPG_IDENTITY}** : The email used when generating the key, the key ID or the fingerprint

The expiration date of the primary key can be renewed at any time, even after it has expired. The third argument `'*'` sets the new expiration date on all non-revoked subkeys that **haven't expired yet**, so a subkey that has already expired keeps the old date. In that case, renew it individually by its fingerprint or create a new encryption subkey, executing the following command:

```bash
gpg --quick-add-key {GPG_IDENTITY} rsa{KEY_SIZE} encr 3y
```

> **Label Definition**
>
> + **{GPG_IDENTITY}** : The email used when generating the key, the key ID or the fingerprint
> + **{KEY_SIZE}**: The size of the RSA key, in bits (security vs performance trade-off). Common choices: `3072` (good default) or `4096` (stronger, slightly slower).

To remove the expiration date of the key, replace `3y` with `0` on the above commands. The tradeoff of both options: a key that doesn't expire requires no periodic maintenance, while a key with an expiration date forces you to review and renew it periodically, so that the store doesn't silently become read-only.

**Configuration of the GPG agent**

To avoid being asked for the passphrase on every single secret, configure the [GnuPG](https://gnupg.org/) agent to cache it.

Create the file `~/.gnupg/gpg-agent.conf` with the upcoming content, using the folder `~/.gnupg` that [GnuPG](https://gnupg.org/) created automatically when the key pair was generated. Open the file with the [Nano text editor](https://www.nano-editor.org/), executing the following command:

```bash
nano ~/.gnupg/gpg-agent.conf
```

Add the upcoming content to the file:

```text
pinentry-program /usr/bin/pinentry-curses
default-cache-ttl 43200
max-cache-ttl 43200
```

Save the changes with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`. Restart the agent to load the new configuration, by executing the following command:

```bash
gpgconf --kill gpg-agent
```

The option `pinentry-program` states explicitly which program draws the passphrase prompt. Without it, [GnuPG](https://gnupg.org/) falls back to reading the terminal device directly, which fails with a `gpg: can't open '/dev/tty'` error on some [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701) and terminal multiplexer configurations.

The options `default-cache-ttl 43200` and `max-cache-ttl 43200` define how long the passphrase stays cached in memory, in seconds (12 hours for both). They cover the two different limits of the cache: `default-cache-ttl` is the time an entry stays valid and its timer is reset every time the entry is accessed, while `max-cache-ttl` is the absolute limit after which the entry expires regardless of how recently it was used. As both are set to the same value, the passphrase is requested once and then reused for as long as the secrets are used, up to 12 hours.

There is no maximum supported by [GnuPG](https://gnupg.org/) for these options, so `86400` (24 hours) or even `0` (no limit) are valid values, but a longer cache widens the window in which any process running as your user can use the agent without knowing the passphrase. On a shared machine, prefer shorter values or don't cache it at all, as any process running as your user can use the agent while the passphrase is cached.

The cache is kept in memory by the [gpg-agent](https://gnupg.org/) daemon, whose socket is created in the folder `/run/user/{UID}`, a `tmpfs` filesystem that is discarded when the [WSL](https://learn.microsoft.com/windows/wsl/) distribution is shut down. As a consequence, terminating the distribution with the command `wsl --shutdown` discards the cached passphrase and the next use of [`pass`](https://www.passwordstore.org/) asks for it again, regardless of the configured cache time.

To verify if the agent is properly configured, check the output of the following command:

```bash
gpg-connect-agent 'getinfo version' /bye
```

**Initialization of `pass`**

Replace the ***{LABEL}*** in the below command as appropriate and then execute it to initialize [`pass`](https://www.passwordstore.org/) with the GPG identity you want to use:

```bash
pass init {GPG_IDENTITY}
```

> **Label Definition**
>
> + **{GPG_IDENTITY}** : The email used when generating the key, or the key ID

Upon success of the [`pass`](https://www.passwordstore.org/) initialization, check the output of the following commands:

```bash
pass show
pass ls
```

The command `pass show` must print a folder named `Password Store` and the command `pass ls` must print an empty list of entries.

**Verification of the installation**

Store a throwaway secret to confirm that the whole setup works end to end, by executing the following command:

```bash
pass insert test/hello-world
```

Following the above command, type `hello-world` on the prompt `Enter password for test/hello-world:` and then type it again on the prompt `Retype password for test/hello-world:`. The terminal doesn't echo the input, so nothing is displayed while typing.

To confirm that the secret was stored and that it decrypts correctly, check the output of the following commands:

```bash
pass ls
pass show test/hello-world
```

The command `pass ls` must list the entry `test/hello-world` and the command `pass show test/hello-world` must print `hello-world`. The first time the secret is decrypted, the [GnuPG](https://gnupg.org/) agent asks for the passphrase of your key (unless it's still cached, see the previous step).

To confirm that the secret is stored **encrypted** at rest and not in plain text, check the output of the following commands:

```bash
ls -l ~/.password-store/test/
file ~/.password-store/test/hello-world.gpg
cat ~/.password-store/test/hello-world.gpg
```

The file `~/.password-store/test/hello-world.gpg` must exist and the command `file` must report it as *GPG encrypted data*. The command `cat` must print binary content and **must not** contain the text `hello-world`.

When the verification is complete, remove the throwaway secret by executing the following command and confirming the removal on the prompt:

```bash
pass rm test/hello-world
```

The command `pass rm` only removes the local entry. The command `pass show test/hello-world` must then fail with a `test/hello-world is not in the password store` error.

**Usage of `pass`**

Store a secret executing the following command:

```bash
pass insert services/my-service
```

The command `pass insert` reads the secret from the terminal with the keyboard echo disabled and asks for it twice, for confirmation. The entry name is the path inside the `~/.password-store` folder, so you can group your secrets by service and the folder creation is automatic.

When the secret has multiple lines (e.g. a configuration file or a private key), use the option `--multiline`, which reads the input until `CTRL + D` is pressed:

```bash
pass insert --multiline settings/my-config
```

To edit an existing entry, execute the following command, which opens the current (decrypted) content on the editor set on the `EDITOR` environment variable:

```bash
pass edit services/my-service
```

To let [`pass`](https://www.passwordstore.org/) generate the secret instead of typing it, execute the following command:

```bash
pass generate services/my-token 32
```

The command `pass generate` creates the secret and prints it, so it's better suited to generate passwords than to store tokens that are issued by an external service.

Retrieve a secret by executing the following command:

```bash
pass show services/my-service
```

The command `pass show services/my-service` **prints** the secret on the terminal and it's included in the terminal scrollback, so don't use it in scripts or on a shared screen. When the secret is consumed by a command line tool, it's preferable to pipe the output of `pass show` into that tool, either directly or through a wrapper function that decrypts the secret on a subshell. Each tool that needs a secret documents that wrapper on its own section of this guide. If a secret is printed by mistake, rotate it on the service that issued it.

Remove a secret by executing the following command:

```bash
pass rm services/my-service
```

`pass rm` deletes the file, but a copy of a secret may still be present in the encrypted backups mentioned below and in the `git` history of the folder, if `~/.password-store` was version controlled at any point. When removing a secret, rotate it on the service that issued it.

**Backup and recovery**

The `~/.password-store` folder contains all your secrets, encrypted, and the `~/.gnupg` folder contains the key pair needed to decrypt them. A backup of the first folder is useless without the private key of the second one, so back up **both** folders. An export of the secret store and of the private key can be created executing the following commands:

```bash
tar czf password-store-backup.tgz ~/.password-store
```

```bash
gpg --armor --export-secret-keys {GPG_IDENTITY} > gpg-private-keys-backup.asc
```

> **Label Definition**
>
> + **{GPG_IDENTITY}** : The email used when generating the key, or the key ID

The file `gpg-private-keys-backup.asc` holds the **unencrypted private key**, so store it in an encrypted location and never in a repository. On a new machine, restore the two folders by extracting the archive and by executing the following command:

```bash
gpg --armor --import gpg-private-keys-backup.asc
```

Test the backup periodically by decrypting an entry with it (`pass show services/my-service`). A backup that was never verified is not a backup.

**Optional: Secret storage with GNOME Keyring**

[`GNOME Keyring`](https://wiki.gnome.org/Projects/GNOMEKeyring) stores the secrets encrypted in the `~/.local/share/keyrings` folder and exposes them through the Secret Service API, which is the interface expected by the command line tools that support this credential store. As it requires a D-Bus session, it's only practical on a [WSL](https://learn.microsoft.com/windows/wsl/) distribution with a desktop environment; on a headless distribution, prefer [`pass`](https://www.passwordstore.org/) as documented above.

To install the required packages on a [Ubuntu](https://ubuntu.com/) terminal, execute the following command:

```bash
sudo apt install gnome-keyring libsecret-tools dbus-x11
```

Create the folder of the keyrings, if it doesn't exist yet, and make sure the D-Bus session is started on every new terminal. Start by creating the file `~/.profile.d/`:

```bash
mkdir -p ~/.profile.d
```

Create the file `~/.profile.d/wsl-gnome-keyring.sh` with the [Nano text editor](https://www.nano-editor.org/), executing the following command:

```bash
nano ~/.profile.d/wsl-gnome-keyring.sh
```

Then, add the upcoming content to the file:

```bash
if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]; then
    eval "$(dbus-launch --sh-syntax)"
fi
```

Save the changes with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`. Then, open the file `~/.profile` with the [Nano text editor](https://www.nano-editor.org/), executing the following command:

```bash
nano ~/.profile
```

Then, add the upcoming line to the `~/.profile` file, before the line that sources `~/.bashrc` (the snippet is only executed on a new login shell, which is what every [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701) tab is):

```bash
if [ -f "$HOME/.profile.d/wsl-gnome-keyring.sh" ]; then
    . "$HOME/.profile.d/wsl-gnome-keyring.sh"
fi
```

Save the changes with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`. Open a **new** [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701) window for the changes to take effect and verify if the D-Bus session is available, by checking the output of the following command:

```bash
echo "$DBUS_SESSION_BUS_ADDRESS"
```

Then, verify if the Secret Service is available, by checking the output of the following commands:

```bash
ps -u "$USER" -o pid,args | grep -E '[g]nome-keyring-daemon'
```

```bash
secret-tool store --label='Test entry' test/key
```

```bash
secret-tool lookup test/key
```

```bash
secret-tool clear test/key
```

The keyring must be created and unlocked on the first use: a window asking for a password pops up and, if it's dismissed, the daemon doesn't start and every subsequent command fails with a `No such secret collection` or `org.freedesktop.secrets was not provided by any .service files` error. With [WSL](https://learn.microsoft.com/windows/wsl/), the daemon must also be started manually on each boot, by executing the following command:

```bash
echo -n test | gnome-keyring-daemon --unlock --components=secrets
```

`GNOME Keyring` has two failure modes that must be known: the keyring is **not unlocked** after a `WSL` restart, so the tools prompt for the keyring password instead of reading the secret, and some tools **fall back to plain text storage** silently when the Secret Service is unavailable. Always confirm the credential source reported by the tool and check the plain text configuration file after any authentication change. Given those caveats, this guide uses [`pass`](https://www.passwordstore.org/) as the default on the `WSL File System`; if you opt for `GNOME Keyring`, keep [`pass`](#1232-secret-storage-on-the-wsl-file-system) as the fallback.

The other sections of this guide that need to store secrets on the `WSL File System` build on the configurations described above.

### 1.3. Windows Terminal

The [**Windows Terminal**](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701) is a terminal application for users of command-line tools and shells like Command Prompt, PowerShell, and WSL. Its main features include multiple tabs, panes, Unicode and UTF-8 character support, a GPU accelerated text rendering engine, and custom themes, styles, and configurations.

#### 1.3.1. Installation

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

Open the [Microsoft Store](https://aka.ms/wslstore) and install the [**Windows Terminal**](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701).

### 1.4. Package Manager

A package manager is a software that easily automates the installation, upgradation, and configuration of third-party software or dependencies. [**Chocolatey**](https://chocolatey.org/) and [**winget**](https://github.com/microsoft/winget-cli) are both package managers for Windows software. Nowadays, I prefer [**winget**](https://github.com/microsoft/winget-cli) over [**Chocolatey**](https://chocolatey.org/) because [**winget**](https://github.com/microsoft/winget-cli) can be used to install software from the [Microsoft Store](https://apps.microsoft.com/home).

#### 1.4.1. Install winget

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

Windows Package Manager [**winget**](https://github.com/microsoft/winget-cli) command-line tool is available on Windows 11 and modern versions of Windows 10 as a part of the [App Installer](https://apps.microsoft.com/detail/9NBLGGH4NNS1). To check if [**winget**](https://github.com/microsoft/winget-cli) is available, open a PowerShell console and execute the following command:

```powershell
winget --version
```

If [**winget**](https://github.com/microsoft/winget-cli) is already available on your system, the current version of the software will be displayed and now you should make sure it is updated with the latest version.

If you need to install [**winget**](https://github.com/microsoft/winget-cli), open the [Microsoft Store](https://aka.ms/wslstore) and install the [App Installer](https://apps.microsoft.com/detail/9NBLGGH4NNS1) because that's how [**winget**](https://github.com/microsoft/winget-cli) is distribuited.

Upgrading applications with [**winget**](https://github.com/microsoft/winget-cli) is very easy. To identify which apps are in need of an update, open a PowerShell console and execute the following command:

```powershell
winget upgrade
```

The above command will output a list of which app (if any) have an available update. To upgrade all applications with an available update, open a PowerShell console and execute the following command:

```powershell
winget upgrade --all
```

When running [**winget**](https://github.com/microsoft/winget-cli) without administrator privileges, some applications may [require elevation](https://learn.microsoft.com/windows/security/application-security/application-control/user-account-control/how-it-works) to install. On those cases, Windows will prompt you to elevate. If you choose not to elevate, the application will fail to install/upgrade.

Check the [official documentation](https://learn.microsoft.com/windows/package-manager/winget/) to know the full potential of [**winget**](https://github.com/microsoft/winget-cli).

#### 1.4.2. Install Scoop

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

[**Scoop**](https://scoop.sh/) installs programs from the command line with a minimal amount of friction as it doesn't require Admin privileges.

To install [**Scoop**](https://scoop.sh/), open a PowerShell console and execute the following commands:

```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

To check if everything was properly installed and if further actions are necessary, execute the following command:

```powershell
scoop checkup
```

If the above command outputs a warning stating that *Windows Developer Mode* is not enabled, you should consider enabling it because operations relevant to [symlinks](https://blogs.windows.com/windowsdeveloper/2016/12/02/symlinks-windows-10/) may fail without proper rights. It is also recommended to enable *Long Paths* option on the **Advanced Windows Settings**.

To enable *Windows Developer Mode* and *Long Paths*, follow the instructions provided in the [Advanced Windows Settings](2-windows-configuration.md#21-advanced-windows-settings) of this guide.

The output of the command `scoop checkup`, might show some recommendations to install some additional packages. If it does, install it using the recommended commands.

To check if all issues were solved with the previous actions, re-run the following command:

```powershell
scoop checkup
```

The output of the above command, should now be `No problems identified!`.

To list all apps installed with [**Scoop**](https://scoop.sh/), execute the following command:

```powershell
scoop list
```

#### 1.4.3. Install Chocolatey

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

If you are going to do your development work on the `Windows Native File System` (instead of doing it exclusively on the `WSL File System`) you should also install [**Chocolatey**](https://chocolatey.org/).

Before proceeding with the installation of [**Chocolatey**](https://chocolatey.org/), you must ensure **Get-ExecutionPolicy** is not ***Restricted***. The following command, executed on a PowerShell console with *Administrator* privileges, will output the current [execution policy](https://go.microsoft.com/fwlink/?LinkID=135170).

```powershell
Get-ExecutionPolicy
```

If the output of the above command shows ***Restricted***, then run the following command on the same PowerShell console:

```powershell
Set-ExecutionPolicy Bypass -Scope Process
```

Or the following command, for quite a [bit more security](https://chocolatey.org/install):

```powershell
Set-ExecutionPolicy AllSigned
```

Then, on the same PowerShell console, execute the following command to install [**Chocolatey**](https://chocolatey.org/).

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

To list the installed chocolatey packages, execute the following command on a PowerShell console:

```powershell
choco list
```

### 1.5. Git & Git Bash

[**Git**](https://git-scm.com/) is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

#### 1.5.1. Installation

##### 1.5.1.1. Installation on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

[**Git**](https://git-scm.com/) is included on the [Ubuntu](https://ubuntu.com/) submodule of [WSL](https://learn.microsoft.com/windows/wsl/), therefore, it's not necessary to install it on the `WSL File System`.

##### 1.5.1.2. Installation on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

**Git Bash** comes included as part of the [Git's Windows package](https://git-scm.com/install/windows) and is an application for Microsoft Windows environments which provides an emulation layer for a [**Git**](https://git-scm.com/) command line experience.

[**Git**](https://git-scm.com/), as stated on the [official downloads page](https://git-scm.com/install/windows), can be installed on the `Windows Native File System` with [**winget**](https://github.com/microsoft/winget-cli). To install [**Git Bash**](https://git-scm.com/install/windows), open a PowerShell console and execute the following command:

```powershell
winget install --id Git.Git -e --source winget
```

The above command will start the [**Git**](https://git-scm.com/) installation. As the `-e` flag is used, it defaults to a "silent" or "headless" installation. It essentially skips the UI wizard and applies the default settings and doesn't requires _administrator privileges_ to perform the installation.

After the completion of the installation, to ensure LFS is initialized, execute the following command:

```powershell
git lfs install
```

To ensure ensure that the PATH environment is adjusted for [**Git**](https://git-scm.com/) from the command line and also from 3rd-party software add, in necessary, the following paths to your Windows User `Path` Environment Variable:

+ `%LocalAppData%\Programs\Git\cmd`
+ `%LocalAppData%\Programs\Git\mingw64\bin`
+ `%LocalAppData%\Programs\Git\usr\bin`

To add the above listed paths to your Windows `Path` Environment Variable, take the following steps:

1. Press `WIN + R`, type `rundll32.exe sysdm.cpl,EditEnvironmentVariables` and then press `Enter`
2. Under **User variables** (top section), select the `Path` variable and then click **Edit**
3. On the new window that is shown, for each path, click **New** and insert the required path

Enabling Windows ***Developer Mode*** is a prerequisite for [**Git**](https://git-scm.com/) to actually create symbolic links without requiring you to run every terminal as an Administrator. To enable *Windows Developer Mode*, follow the [Advanced Windows Settings](./2-windows-configuration.md#21-advanced-windows-settings) of this guide.

Configure the **Git Bash** profile on the [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701), executing the following steps:

1. Open the [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701);
2. Press `Ctrl + ,` (Comma) to open the [Windows Terminal](https://apps.microsoft.com/store/detail/windows-terminal/9N0DX20HK701) Settings;
3. Click **Add a new profile** (bottom left);
4. Click **+ New empty profile**;
5. Set the following:
    + **Name:** Git Bash
    + **Command line:** `%LocalAppData%\Programs\Git\bin\bash.exe -l -i`
    + **Starting directory:** `%USERPROFILE%`
    + **Icon:** `File` `%LocalAppData%\Programs\Git\mingw64\share\git\git-for-windows.ico`

#### 1.5.2. Git configuration

To set [Git's global configuration](https://www.learnenough.com/git-tutorial#sec-installation_and_setup), replace the **{LABELS}** in the following commands as appropriate and then execute them in a [Git Bash](https://git-scm.com/) terminal window.

```bash
git config --global core.autocrlf true
git config --global core.editor nano
git config --global core.fscache true
git config --global core.symlinks true
git config --global credential.helper manager
git config --global http.sslBackend openssl
git config --global init.defaultBranch master
git config --global pull.rebase true
git config --global user.name "{USER_NAME}"
git config --global user.email {USER_EMAIL}
git config --list
```

> **Label Definition**
>
> + **{USER_NAME}** : The name of the user
> + **{USER_EMAIL}** : The e-mail of the user

Instructions for a more detailed Git global configuration can be found in the [Git's Official Documentation](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup).

#### 1.5.3. Bash prompt customization

##### 1.5.3.1. Bash prompt customization on the WSL File System

![WSL](https://img.shields.io/badge/WSL-purple)

The customization of the bash prompt is very personal and the files used to accomplish my personal customization on the `WSL File System` are stored at the folder `root/home/user/.bash_USER` in the [**system-configuration-files**](https://github.com/EnduranceCode/system-configuration-files) repository. The easiest way to use the files on the referred repository is to start by cloning it to your local machine. Do it with the execution of the following command:

```bash
git clone https://github.com/EnduranceCode/system-configuration-files.git
```

To [copy](https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/) the mentioned folder (and files) to your local machine `home` folder, replace the ***{LABELS}*** in the following command as appropriate and execute it.

```bash
cp -r {SYSTEM_CONFIGURATION_FILES_REPOSITORY_ROOT_FOLDER}/root/home/user/.bash_USER ~/
```

> **Label Definition**
>
> + **{SYSTEM_CONFIGURATION_FILES_REPOSITORY_ROOT_FOLDER}** : Path to the system-configuration-files repository root folder

To be able to use the files copied in the previous step for the bash environment customization, execute the following commands:

```bash
mv ~/.bash_USER ~/.bash_"${USER}"
mv ~/.bash_"${USER}"/bash_USER.sh ~/.bash_"${USER}"/bash_"${USER}".sh
chown -R "${USER}":"${USER}" ~/.bash_"${USER}"
chmod -R 700 ~/.bash_"${USER}"
```

To complete the process, it's necessary to edit the file `.bashrc` located in the home folder and add the lines below to the end of the mentioned file.

```bash
# Source the file that enables personal prompt customization and implements custom alias
# All prompt customization alias implementation must be done in the file sourced below
#
if [ -f ~/.bash_"${USER}"/bash_"${USER}".sh ]; then
    . ~/.bash_"${USER}"/bash_"${USER}".sh
fi
```

Open the file `.bashrc` with the [Nano text editor](https://www.nano-editor.org/) executing the following command:

```bash
nano ~/.bashrc
```

After adding the necessary modifications, save the file with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`.

Make the changes effective with the following command:

```bash
source ~/.bashrc
```

##### 1.5.3.2. Bash prompt customization on the Windows Native File System

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

The files used to accomplish my personal customization on the `Windows Native File System` are stored at the folder `root/home/user/.bash_USER` in the [**system-configuration-files**](https://github.com/EnduranceCode/system-configuration-files) repository. The easiest way to use the files on the referred repository is to start by cloning it to your local machine. Do it with the execution of the following command:

```bash
git clone https://github.com/EnduranceCode/system-configuration-files.git
```

To [copy](https://linuxize.com/post/how-to-use-scp-command-to-securely-transfer-files/) the mentioned folder (and files) to your local machine `home` folder, replace the ***{LABELS}*** in the following command as appropriate and execute it.

```bash
cp -r {SYSTEM_CONFIGURATION_FILES_REPOSITORY_ROOT_FOLDER}/root/home/user/.bash_USER ~/
```

> **Label Definition**
>
> + **{SYSTEM_CONFIGURATION_FILES_REPOSITORY_ROOT_FOLDER}** : Path to the system-configuration-files repository root folder

The bash prompt customization provided by the files copied in the previous step depends on the existence of the environment variable `USER`. Check if the variable is set with the following command:

```bash
echo $USER
```

If the output of the above command is empty, it's necessary to edit the file `.bashrc` located in the home folder and add the snippet below to the end of the mentioned file.

```bash
# Match the Git Bash and Windows login
export USER="$USERNAME"
```

Open the file `.bashrc` with the [Nano text editor](https://www.nano-editor.org/) executing the following command:

```bash
nano ~/.bashrc
```

After adding the required snippet, save the file with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`. Make the changes effective with the following command:

```bash
source ~/.bashrc
```

Then, execute the following commands:

```bash
mv ~/.bash_USER ~/.bash_"${USER}"
mv ~/.bash_"${USER}"/bash_USER.sh ~/.bash_"${USER}"/bash_"${USER}".sh
```

To complete the process, it's necessary to edit the file `.bashrc` located in the home folder and add the lines below to the end of the mentioned file.

```bash
# Source the file that enables personal prompt customization and implements custom alias
# All prompt customization alias implementation must be done in the file sourced below
#
if [ -f ~/.bash_"${USER}"/bash_"${USER}".sh ]; then
    . ~/.bash_"${USER}"/bash_"${USER}".sh
fi
```

Open the file `.bashrc` with the [Nano text editor](https://www.nano-editor.org/) executing the following command:

```bash
nano ~/.bashrc
```

After adding the necessary modifications, save the file with the command `CTRL + O` and then exit the [Nano text editor](https://www.nano-editor.org/) with the command `CTRL + X`.

Make the changes effective with the following command:

```bash
source ~/.bashrc
```

#### 1.5.4. SSH Keys

The [SSH Protocol](https://en.wikipedia.org/wiki/Secure_Shell) is very useful to connect and authenticate to remote servers and services. The creation and setup of the SSH keys described here follows the instructions at [GitHub](https://help.github.com/en/articles/connecting-to-github-with-ssh).

##### 1.5.4.1. Checking for existing SSH keys

To check if the system already has an SSH key set, type the following command:

```bash
ls -al ~/.ssh
```

If the output of the above command contains a list of files (by default, the filenames of the public keys are *id_dsa.pub*, *id_ecdsa.pub*, *id_ed25519.pub* or *id_rsa.pub*), the system already has a SSH key and it can be used.

##### 1.5.4.2. Generating a new SSH key

To create a new SSH key, replace the **{LABEL}** in the following command as appropriate and then execute it in a [Git Bash](https://git-scm.com/) terminal window.

```bash
ssh-keygen -t ed25519 -C "{EMAIL_ADDRESS}"
```

> **Label Definition**
>
> + **{EMAIL_ADDRESS}** : The e-mail address to be used as label for the SSH key

The above command creates a new SSH key, using the provided email as a label.

```
> Generating public/private rsa key pair.
```

When prompted to "Enter a file in which to save the key," press Enter to accept the default file location.

```
> Enter a file in which to save the key (/home/you/.ssh/id_ed25519): [Press enter]
```

Type a secure passphrase when prompted. GitHub has further instructions on [working with SSH key passphrases](https://help.github.com/en/articles/working-with-ssh-key-passphrases).

```
> Enter passphrase (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```

##### 1.5.4.3. Adding the SSH key to the ssh-agent

To add the new SSH key to the `ssh-agent`, start it in the background with the following command:

```bash
eval "$(ssh-agent -s)"
```

The following command will add the private key to the `ssh-agent`:

```bash
ssh-add ~/.ssh/id_ed25519
```

##### 1.5.4.4. Adding a new SSH key to the remote servers

To display your public SSH key so that you can copy it, run the following command in a Git Bash terminal window:

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the output of the above command and then add the public SSH key to the remote servers you use ([GitHub](https://github.com/settings/keys), [Bitbucket](https://bitbucket.org/account/user/ssh-keys), etc.).

You can use your personal SSH keys not only to access remote servers but also to sign your commits and tags. Execute the following commands to tell Git that you want to use an SSH key for signing, to specify the SSH key to sign commits and tags with, and to automatically sign every commit and tag:

```bash
git config --global gpg.format ssh
git config --global user.signingkey ~/.ssh/id_ed25519.pub
git config --global commit.gpgsign true
git config --global tag.gpgsign true
```

To verify the signatures of the commits you push, you also need to add the public SSH key as a signing key to the remote servers you use ([GitHub](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification#ssh-commit-signature-verification), [Bitbucket](https://support.atlassian.com/bitbucket-cloud/docs/use-ssh-keys-to-sign-commits/), etc.).

### 1.6. KeePassXC

[**KeePassXC**](https://keepassxc.org/) is a cross-platform community-driven port of the Windows application [Keepass Password Safe](https://keepass.info/) that I choose to use precisely because it's cross-platform and it allows me to use it on every operating system that I work with.

#### 1.6.1. Installation

![WINDOWS](https://img.shields.io/badge/WINDOWS-blue)

To install [**KeePassXC**](https://keepassxc.org/), execute the following commands on a PowerShell console:

```powershell
scoop bucket add extras
scoop install extras/keepassxc
```

Check if the output of the above last command shows a suggestion to install `vcredist2022`. If it does, install it executing the following command on a PowerShell console:

```powershell
scoop install extras/vcredist2022
```

Following the execution of the above command, there will be several prompts for elevated permissions which must all be accepted to complete the installation. A restart of the machine will be necessary to complete the installation but before restarting the machine, check if the output of the installation command states that the `vcredist2022` installer can be removed. If it does, after the restart of the machine, execute the following command on a PowerShell console:

```powershell
scoop uninstall extras/vcredist2022
```

#### 1.6.2. Configuration

Set [**KeePassXC**](https://keepassxc.org/) preferences (`Tools->Settings`) as desired but make sure to enable the `Browser Integrations`. Then, setup [KeePassXC-Browser](https://chrome.google.com/webstore/detail/keepassxc-browser/oboonakemofpalcgghocfoadofidjkkk) extension to integrate it with the machine's installation of [**KeePassXC**](https://keepassxc.org/).
