# nodesource/distributions: NodeSource Node.js Binary Distributions

[https://github.com/nodesource/distributions#debinstall](https://github.com/nodesource/distributions#debinstall)

# [NodeSource](https://nodesource.com/) Node.js Binary Distributions

![nodesource%20cd394/ns-linux-distributions.svg](nodesource%20cd394/ns-linux-distributions.svg)

[nodesource%20cd394/68747470733a2f2f636972636c6563692e636f6d2f67682f6e6f6465736f757263652f646973747269627574696f6e732f747265652f6d61737465722e7376673f7374796c653d737667](nodesource%20cd394/68747470733a2f2f636972636c6563692e636f6d2f67682f6e6f6465736f757263652f646973747269627574696f6e732f747265652f6d61737465722e7376673f7374796c653d737667)

This repository contains documentation for using the **[NodeSource](https://nodesource.com/)** **[Node.js](http://nodejs.org/)** Binary Distributions via .rpm and .deb as well as their setup and support scripts.

If you are looking for NodeSource's low-impact Node.js performance monitoring platform, please **[get started here](https://accounts.nodesource.com/sign-up-linuxdistro).**

Please file an issue if you are experiencing a problem or would like to discuss something related to the distributions.

Pull requests are encouraged if you have changes you believe would improve the setup process or increase compatibility across Linux distributions.

## Table of Contents

- **[Debian and Ubuntu based distributions](https://github.com/nodesource/distributions#deb)** (deb)
    - [Installation instructions](https://github.com/nodesource/distributions#debinstall)
    - [Manual installation](https://github.com/nodesource/distributions#debmanual)
- **[Enterprise Linux based distributions](https://github.com/nodesource/distributions#rpm)** (rpm)
    - [Installation instructions](https://github.com/nodesource/distributions#rpminstall)
- **[Tests](https://github.com/nodesource/distributions#tests)**
- **[FAQ](https://github.com/nodesource/distributions#questions)**
- **[Requested Distributions](https://github.com/nodesource/distributions#requests)**
- **[License](https://github.com/nodesource/distributions#project-license)**

## Debian and Ubuntu based distributions

**Available architectures:**

NodeSource will continue to maintain the following architectures and may add additional ones in the future.

- **amd64** (64-bit)
- **armhf** (ARM 32-bit hard-float, ARMv7 and up: *arm-linux-gnueabihf*)
- **arm64** (ARM 64-bit, ARMv8 and up: *aarch64-linux-gnu*)

**Supported Ubuntu versions:**

NodeSource will maintain Ubuntu distributions in active support by Canonical, including LTS and the intermediate releases.

- **Ubuntu 16.04 LTS** (Xenial Xerus)
- **Ubuntu 18.04 LTS** (Bionic Beaver)
- **Ubuntu 18.10** (Cosmic Cuttlefish)
- **Ubuntu 19.04** (Disco Dingo)
- **Ubuntu 19.10** (Eoan Ermine)
- **Ubuntu 20.04 LTS** (Focal Fossa)
- **Ubuntu 20.10** (Groovy Gorilla)
- **Ubuntu 21.04** (Hirsute Hippo)
- **Ubuntu 21.10** (Impish Indri)

**Supported Debian versions:**

NodeSource will maintain support for stable, testing and unstable releases of Debian, due to the long release cycle a considerable number of users are running unstable and testing.

- **Debian 9 / oldoldstable** (Stretch)
- **Debian 10 / oldstable** (Buster)
- **Debian 11 / stable** (Bullseye)
- **Debian unstable** (Sid)
- **Debian testing** (Bookworm)

**Supported Linux Mint versions:**

- **Linux Mint 18 "Sarah"** (via Ubuntu 16.04 LTS)
- **Linux Mint 18.1 "Serena"** (via Ubuntu 16.04 LTS)
- **Linux Mint 18.2 "Sonya"** (via Ubuntu 16.04 LTS)
- **Linux Mint 18.3 "Sylvia"** (via Ubuntu 16.04 LTS)
- **Linux Mint Debian Edition (LMDE) 2 "Betsy"** (via Debian 8)
- **Linux Mint 19 "Tara"** (via Ubuntu 18.04 LTS)
- **Linux Mint 19.1 "Tessa"** (via Ubuntu 18.04 LTS)
- **Linux Mint 19.2 "Tina"** (via Ubuntu 18.04 LTS)
- **Linux Mint 19.3 "Tricia"** (via Ubuntu 18.04 LTS)
- **Linux Mint 20 "Ulyana"** (via Ubuntu 20.04 LTS)
- **Linux Mint 20.1 "Ulyssa"** (via Ubuntu 20.04 LTS)
- **Linux Mint 20.2 "Uma"** (via Ubuntu 20.04 LTS)
- **Linux Mint 20.3 "Una"** (via Ubuntu 20.04 LTS)
- **Linux Mint Debian Edition (LMDE) 3 "Cindy"** (via Debian 9)
- **Linux Mint Debian Edition (LMDE) 4 "Debbie"** (via Debian 10)

**Supported Devuan versions:**

- **Ascii / oldoldstable** (via Debian 9)
- **Beowulf / oldstable** (via Debian 10)
- **Chimaera / stable** (via Debian 11)
- **Ceres / unstable** (via Debian unstable)

**Supported elementary OS versions:**

- **elementary OS 0.4 Loki** (via Ubuntu 16.04 LTS)
- **elementary OS 5 Juno** (via Ubuntu 18.04 LTS)
- **elementary OS 5.1 Hera** (via Ubuntu 18.04 LTS)
- **elementary OS 6 Odin** (via Ubuntu 20.04 LTS)
- **elementary OS 6.1 Jolnir** (via Ubuntu 20.04 LTS)

**Supported Trisquel versions:**

- **Trisquel 8 "Flidas"** (via Ubuntu 16.04 LTS)
- **Trisquel 9 "Etiona"** (via Ubuntu 18.04 LTS)

**Supported BOSS versions:**

- **BOSS 7.0 "Drishti"** (via Debian 9)
- **BOSS 8.0 "Unnati"** (via Debian 10)

**Supported BunsenLabs versions:**

- **Helium** (via Debian 9)
- **Lithium** (via Debian 10)

**Supported MX Linux versions:**

- **MX-17 Horizon** (via Debian 9)
- **MX-18 Continuum** (via Debian 9)
- **MX-19 Patito Feo** (via Debian 10)
- **MX-21 Wildflower** (via Debian 11)

**Supported Sparky Linux versions:**

- **Sparky 4.x "Tyche"** (via Debian 9)
- **Sparky 5.x "Nibiru"** (via Debian 10)
- **Sparky 6.x "Po Tolo"** (via Debian 11)

**Supported PureOS Linux versions:**

- **PureOS 9.0 "Amber"** (via Debian 10)
- **PureOS 10.0 "Byzantium"** (via Debian 11)

**Supported Astra Linux CE versions:**

- **Astra Linux CE 2.12 "Orel"** (via Debian 9)

**Supported Ubilinux versions:**

- **Ubilinux 4.0 "Dolcetto"** (via Debian 9)

### Installation instructions

**Node.js v17.x**:

```
# Using Ubuntu
curl -fsSL https://deb.nodesource.com/setup_17.x | sudo -E bash -
sudo apt-get install -y nodejs

# Using Debian, as root
curl -fsSL https://deb.nodesource.com/setup_17.x | bash -
apt-get install -y nodejs
```

**Node.js v16.x**:

```
# Using Ubuntu
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt-get install -y nodejs

# Using Debian, as root
curl -fsSL https://deb.nodesource.com/setup_16.x | bash -
apt-get install -y nodejs
```

**Node.js v14.x**:

```
# Using Ubuntu
curl -fsSL https://deb.nodesource.com/setup_14.x | sudo -E bash -
sudo apt-get install -y nodejs

# Using Debian, as root
curl -fsSL https://deb.nodesource.com/setup_14.x | bash -
apt-get install -y nodejs
```

**Node.js v12.x**:

```
# Using Ubuntu
curl -fsSL https://deb.nodesource.com/setup_12.x | sudo -E bash -
sudo apt-get install -y nodejs

# Using Debian, as root
curl -fsSL https://deb.nodesource.com/setup_12.x | bash -
apt-get install -y nodejs
```

**Node.js LTS (v16.x)**:

```
# Using Ubuntu
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs

# Using Debian, as root
curl -fsSL https://deb.nodesource.com/setup_lts.x | bash -
apt-get install -y nodejs
```

**Node.js Current (v17.x)**:

```
# Using Ubuntu
curl -fsSL https://deb.nodesource.com/setup_current.x | sudo -E bash -
sudo apt-get install -y nodejs

# Using Debian, as root
curl -fsSL https://deb.nodesource.com/setup_current.x | bash -
apt-get install -y nodejs
```

***Optional***: install build tools

To compile and install native addons from npm you may also need to install build tools:

```
# use `sudo` on Ubuntu or run this as root on debian
apt-get install -y build-essential
```

### Manual installation

If you're not a fan of `curl <url> | bash -`, or are using an unsupported distribution, you can try a manual installation.

These instructions assume `sudo` is present, however some distributions do not include this command by default, particularly those focused on a minimal environment. In this case, you should install `sudo` or `su` to root to run the commands directly.

**1. Remove the old PPA if it exists**

This step is only required if you previously used Chris Lea's Node.js PPA.

```
# add-apt-repository may not be present on some Ubuntu releases:
# sudo apt-get install python-software-properties
sudo add-apt-repository -y -r ppa:chris-lea/node.js
sudo rm -f /etc/apt/sources.list.d/chris-lea-node_js-*.list
sudo rm -f /etc/apt/sources.list.d/chris-lea-node_js-*.list.save
```

**2. Add the NodeSource package signing key**

```
KEYRING=/usr/share/keyrings/nodesource.gpg
curl -fsSL https://deb.nodesource.com/gpgkey/nodesource.gpg.key | gpg --dearmor | sudo tee "$KEYRING" >/dev/null
# wget can also be used:
# wget --quiet -O - https://deb.nodesource.com/gpgkey/nodesource.gpg.key | gpg --dearmor | sudo tee "$KEYRING" >/dev/null
gpg --no-default-keyring --keyring "$KEYRING" --list-keys
```

The key ID is `9FD3B784BC1C6FC31A8A0A1C1655A0AB68576280`.

**3. Add the desired NodeSource repository**

```
# Replace with the branch of Node.js or io.js you want to install: node_6.x, node_8.x, etc...
VERSION=node_8.x
# Replace with the keyring above, if different
KEYRING=/usr/share/keyrings/nodesource.gpg
# The below command will set this correctly, but if lsb_release isn't available, you can set it manually:
# - For Debian distributions: jessie, sid, etc...
# - For Ubuntu distributions: xenial, bionic, etc...
# - For Debian or Ubuntu derived distributions your best option is to use the codename corresponding to the upstream release your distribution is based off. This is an advanced scenario and unsupported if your distribution is not listed as supported per earlier in this README.
DISTRO="$(lsb_release -s -c)"
echo "deb [signed-by=$KEYRING] https://deb.nodesource.com/$VERSION $DISTRO main" | sudo tee /etc/apt/sources.list.d/nodesource.list
echo "deb-src [signed-by=$KEYRING] https://deb.nodesource.com/$VERSION $DISTRO main" | sudo tee -a /etc/apt/sources.list.d/nodesource.list

```

**4. Update package lists and install Node.js**

```
sudo apt-get update
sudo apt-get install nodejs
```

## Enterprise Linux based distributions

**Available architectures:**

NodeSource will continue to maintain the following architectures and may add additional ones in the future.

- **x86_64** (64-bit)
- **arm64** (ARM 64-bit, ARMv8 and up: *aarch64-linux-gnu*)

**Supported Red Hat® Enterprise Linux® versions:**

- **RHEL 7** (64-bit)
- **RHEL 8** (64-bit)

**Supported CentOS versions:**

- **CentOS 7** (64-bit)
- **CentOS 8** (64-bit)
- **CentOS 8 Stream** (64-bit)

**Supported AlmaLinux OS versions:**

- **AlmaLinux 8** (64-bit)

**Supported Mageia Linux versions:**

- **Mageia 7** (64-bit)
- **Mageia 8** (64-bit)

**Supported Rocky Linux OS versions:**

- **Rocky 8** (64-bit)

**Supported CloudLinux versions:**

- **CloudLinux 6** (32-bit for Node <= 10.x and 64-bit)

**Supported Fedora versions:**

- **Fedora 33** (64-bit)
- **Fedora 34** (64-bit)
- **Fedora 35** (64-bit)

**Supported Amazon Linux versions:**

- **Amazon Linux** (64-bit)
- **Amazon Linux 2** (64-bit)

### Installation instructions

*NOTE: If you are using RHEL 6 or CentOS 6, you might want to read about [running Node.js on older distros](https://github.com/nodesource/distributions/blob/master/OLDER_DISTROS.md).*

The Nodesource RPM package signing key is available here: [https://rpm.nodesource.com/pub/el/NODESOURCE-GPG-SIGNING-KEY-EL](https://rpm.nodesource.com/pub/el/NODESOURCE-GPG-SIGNING-KEY-EL)

Run on RHEL, CentOS, CloudLinux, Amazon Linux or Fedora:

**Node.js v17.x**

```
# As root
curl -fsSL https://rpm.nodesource.com/setup_17.x | bash -

# No root privileges
curl -fsSL https://rpm.nodesource.com/setup_17.x | sudo bash -
```

**Node.js v16.x**

```
# As root
curl -fsSL https://rpm.nodesource.com/setup_16.x | bash -

# No root privileges
curl -fsSL https://rpm.nodesource.com/setup_16.x | sudo bash -
```

**Node.js v14.x**

```
# As root
curl -fsSL https://rpm.nodesource.com/setup_14.x | bash -

# No root privileges
curl -fsSL https://rpm.nodesource.com/setup_14.x | sudo bash -
```

**Node.js v12.x**

```
# As root
curl -fsSL https://rpm.nodesource.com/setup_12.x | bash -

# No root privileges
curl -fsSL https://rpm.nodesource.com/setup_12.x | sudo bash -
```

**Node.js LTS (16.x)**

```
# As root
curl -fsSL https://rpm.nodesource.com/setup_lts.x | bash -

# No root privileges
curl -fsSL https://rpm.nodesource.com/setup_lts.x | sudo bash -
```

**Node.js Current (17.x)**

```
# As root
curl -fsSL https://rpm.nodesource.com/setup_current.x | bash -

# No root privileges
curl -fsSL https://rpm.nodesource.com/setup_current.x | sudo bash -
```

***Optional***: install build tools

To compile and install native addons from npm you may also need to install build tools:

```
yum install gcc-c++ make
# or: yum groupinstall 'Development Tools'

```

## Tests

To test an installation is working (and that the setup scripts are working!) use:

```
curl -fsSL https://deb.nodesource.com/test | bash -
```

# FAQ

Q: How do I use this repo when behind a proxy?

A: Please take a look at [issue #9](https://github.com/nodesource/distributions/issues/9)

Q: How do I pin to specific versions of Node.js?

A: Please take a look at [issue #33](https://github.com/nodesource/distributions/issues/33#issuecomment-169345680)

Q: I upgraded to a new major version of Node.js using the scripts, but the old version is still being installed, what is going on?

A: You probably need to clear out your package manager's cache. Take a look at [issue #191](https://github.com/nodesource/distributions/issues/191)

Q: I'm trying to install Node.js on CentOS 5 / RHEL 5 and it is failing, why?

A: Due to the limitations of the compiler toolchain on EL 5 and its end of general support, we no longer support. See [issue #190](https://github.com/nodesource/distributions/issues/190)

Q: I'm seeing "Your distribution, identified as "*.i686" or "*.i386, is not currently supported, why?

A: Node.js 4.x and newer require a 64bit os for rpms. See [issue #268](https://github.com/nodesource/distributions/issues/268)

Q: Why have certain versions of platforms/releases stopped receiving updates to Node.js?

A: Unfortunately, newer versions of V8 require a modern compiler toolchain. On some platforms, such as ARM wheezy, that toolchain is not available. See [issue #247](https://github.com/nodesource/distributions/issues/247)

Q: Why is my Node.js version newer than the one of the script I've run?

A: Your package manager is probably installing a newer Node.js version from a different source. See [issue #657](https://github.com/nodesource/distributions/issues/657)

Q: What is the current status of IPv6 support?

A: See [issue #170](https://github.com/nodesource/distributions/issues/170)

Q: I cannot install Node.js on Debian Jessie or Ubuntu Trusty Tahr: GPG error, why?

A: See [issue #1181](https://github.com/nodesource/distributions/issues/1181)

# Requested Distributions

We, unfortunately, do not have the resources necessary to support and test the plethora of Linux releases in the wild, so we rely on community members such as yourself to get support on your favorite distributions! This is a list of releases that have been requested by the community. If you are interested in contributing to this project, this would be a great place to start!

- OpenSUSE - [Issue #199](https://github.com/nodesource/distributions/issues/199)
- Scientific Linux - [Issue #251](https://github.com/nodesource/distributions/issues/251)
- TANGLU Bartholomea - [Issue #81](https://github.com/nodesource/distributions/issues/81)
- Korora - [Issue #130](https://github.com/nodesource/distributions/issues/130)
- FreePBX - [Issue #257](https://github.com/nodesource/distributions/issues/257)
- Deepin - [Issue #638](https://github.com/nodesource/distributions/issues/638)
- PopOS - [Issue #924](https://github.com/nodesource/distributions/issues/924)
- Kylin - [Issue #1011](https://github.com/nodesource/distributions/issues/1011)
- MakuluLinux - [Issue #1012](https://github.com/nodesource/distributions/issues/1012)
- Parrot OS - [Issue #1205](https://github.com/nodesource/distributions/issues/1205)
- GuixSD - [Issue #1297](https://github.com/nodesource/distributions/issues/1297)
- XCP-ng - [Issue #1061](https://github.com/nodesource/distributions/issues/1061)
- VzLinux - [Issue #1060](https://github.com/nodesource/distributions/issues/1060)

## Authors and Contributors

[Untitled](nodesource%20cd394/Untitled%20D%2095ba6.csv)

Contributions are welcomed from anyone wanting to improve this project!

## License

This material is Copyright (c) NodeSource and licensed under the MIT license. All rights not explicitly granted in the MIT license are reserved. See the included [LICENSE.md](https://github.com/nodesource/distributions/blob/master/LICENSE.md) file for more details.

*Supported with love by the [NodeSource](https://nodesource.com/) team*

*This project is not affiliated with Debian, Ubuntu, Red Hat, CentOS or Fedora.Ubuntu is a registered trademark of Canonical Ltd.Debian is a registered trademark owned by Software in the Public Interest, Inc.Red Hat, CentOS and Fedora are trademarks of Red Hat, Inc.CloudLinux is a trademark of Cloud Linux, Inc*
