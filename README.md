<div align="center">
<img src=".github/logo.png" alt="Quickemu" width="256" />

# Quickemu

**Quickly create and run optimised Windows, macOS and Linux virtual machines:**

**Made with 💝 for <img src=".github/tux.png" align="top" width="24" alt="Tux (Linux)"/> & <img src=".github/apple.png" align="top" width="24" alt="Apple (macOS)"/>**
</div>

<p align="center">
  &nbsp;<a href="https://wimpysworld.io/discord" target="_blank"><img alt="Discord" src="https://img.shields.io/discord/712850672223125565?style=for-the-badge&logo=discord&logoColor=%23ffffff&label=Discord&labelColor=%234253e8&color=%23e4e2e2"></a>&nbsp;
  &nbsp;<a href="https://fosstodon.org/@wimpy" target="_blank"><img alt="Mastodon" src="https://img.shields.io/badge/Mastodon-6468fa?style=for-the-badge&logo=mastodon&logoColor=%23ffffff"></a>&nbsp;
  &nbsp;<a href="https://twitter.com/m_wimpress" target="_blank"><img alt="Twitter" src="https://img.shields.io/badge/Twitter-303030?style=for-the-badge&logo=x&logoColor=%23ffffff"></a>&nbsp;
  &nbsp;<a href="https://linkedin.com/in/martinwimpress" target="_blank"><img alt="LinkedIn" src="https://img.shields.io/badge/LinkedIn-1667be?style=for-the-badge&logo=linkedin&logoColor=%23ffffff"></a>&nbsp;
</p>


# Introduction

**Quickemu** is a wrapper for the excellent [QEMU](https://www.qemu.org/) that
automatically *"does the right thing"* when creating virtual machines. No
requirement for exhaustive configuration options. You decide what operating
system you want to run and Quickemu takes care of the rest 🤖

- `quickget` **automatically downloads the upstream OS** and creates the configuration 📀
- `quickemu` enumerates your hardware and launches the virtual machine with the **optimum configuration best suited to your computer** ⚡️

The original objective of the project was to [enable quick testing of Linux
distributions](https://github.com/quickemu-project/quickemu/wiki/02-Create-Linux-virtual-machines)
where the virtual machines and their configuration can be stored anywhere (such
as external USB storage or your home directory) and no elevated permissions are
required to run the virtual machines.

**Today, Quickemu includes comprehensive support for [macOS](https://github.com/quickemu-project/quickemu/wiki/03-Create-macOS-virtual-machines),
[Windows](https://github.com/quickemu-project/quickemu/wiki/04-Create-Windows-virtual-machines)**, most of the BSDs, novel non-Linux operating systems such as FreeDOS, Haiku, KolibriOS, OpenIndiana, ReactOS, and more.

# Features

- Host support for **Linux and macOS**
- **macOS** Sonoma, Ventura, Monterey, Big Sur, Catalina & Mojave
- **Windows** 10 and 11 including TPM 2.0
- **Windows Server** 2022 2019 2016
- [Ubuntu](https://ubuntu.com/desktop) and all the **[official Ubuntu
  flavours](https://ubuntu.com/download/flavours)**
- **Nearly 1000 operating system editions are supported!**
- Full SPICE support including host/guest clipboard sharing
- VirtIO-webdavd file sharing for Linux and Windows guests
- VirtIO-9p file sharing for Linux and macOS guests
- [QEMU Guest Agent
  support](https://wiki.qemu.org/Features/GuestAgent); provides access
  to a system-level agent via standard QMP commands
- Samba file sharing for Linux, macOS and Windows guests (*if `smbd`
  is installed on the host*)
- VirGL acceleration
- USB device pass-through
- Smartcard pass-through
- Automatic SSH port forwarding to guests
- Network port forwarding
- Full duplex audio
- Braille support
- EFI (with or without SecureBoot) and Legacy BIOS boot

## As featured on [Linux Matters](https://linuxmatters.sh) podcast!

The presenters of Linux Matters 🐧🎙️ are the creators of each of the principal Quickemu projects. We discussed Quickemu's 2024 reboot in [Episode 30 - Quickemu Rising From the Bashes](https://linuxmatters.sh/30). <!-- and in [Episode 32 - Quick, quicker, quickest](https://linuxmatters.sh/32) [Martin](https://github.com/flexiondotorg) unveils macOS host support for [**Quickemu**](https://github.com/quickemu-project/quickemu), [Mark](https://github.com/marxjohnson) explains the origins of the [**Quickgui**](https://github.com/quickemu-project/quickgui) desktop app and upcoming improvements, and [Alan](https://github.com/popey) debuts [**Quicktest**](https://github.com/quickemu-project/quicktest); a framework for automatically testing operating systems via Quickemu -->

<div align="center">
  <a href="https://linuxmatters.sh" target="_blank"><img src="https://github.com/wimpysworld/nix-config/raw/main/.github/screenshots/linuxmatters.png" alt="Linux Matters Podcast"/></a>
  <br />
  <em>Linux Matters Podcast</em>
</div>

# Quick start

[Once Quickemu is installed](https://github.com/quickemu-project/quickemu/wiki/01-Installation), there are two simple steps to create and run a virtual machine:

- `quickget` automatically downloads the ISO image for the operating system you want to run and creates a configuration file for the virtual machine.

``` shell
quickget nixos unstable minimal
```

- `quickemu` starts the virtual machine using the configuration file created by `quickget`.

``` shell
quickemu --vm nixos-unstable-minimal.conf
```

Execute `quickget` (with no arguments) to see a list of all the supported operating systems.

## Demo

<div align="center">

<a href="https://asciinema.org/a/658148?autoplay=1" target="_blank"><img src="https://asciinema.org/a/658148.svg" /></a>

</div>

# Documentation

The wiki describes how to get up and running with Quickemu and also covers more advanced configuration and usage.

- [**Installation**](https://github.com/quickemu-project/quickemu/wiki/01-Installation) 💾
- [**Create Linux virtual machines**](https://github.com/quickemu-project/quickemu/wiki/02-Create-Linux-virtual-machines) 🐧
- [**Create macOS virtual machines**](https://github.com/quickemu-project/quickemu/wiki/03-Create-macOS-virtual-machines) 🍏
- [**Create Windows virtual machines**](https://github.com/quickemu-project/quickemu/wiki/04-Create-Windows-virtual-machines) 🪟
- [**Advanced quickemu configuration**](https://github.com/quickemu-project/quickemu/wiki/05-Advanced-quickemu-configuration) 🔧
- [**Advanced quickget features**](https://github.com/quickemu-project/quickemu/wiki/06-Advanced-quickget-features) 🤓
- [**Alternative frontends**](https://github.com/quickemu-project/quickemu/wiki/07-Alternative-frontends) 🧑‍💻
- [**References**](https://github.com/quickemu-project/quickemu/wiki/08-References) 📚️

<!-- TABLE -->
| OS|RELEASES|EDITIONS|ISOS |
|---|---|---|---|
| agarimos | latest | xfce4 plasma lxqt-kwin gnome cinnamon |  |
| alma | 9 8 | minimal dvd boot |  |
| alpine | v3.21 v3.20 v3.19 v3.18 v3.17 v3.16 v3.15 v3.14 v3.13 |  |  |
| android | 9.0 8.1 7.1 | x86_64 x86 |  |
| antix | 23.2 23.1 23 22 21 | net-sysv net-runit full-sysv full-runit core-sysv core-runit base-sysv base-runit |  |
| archcraft | latest |  |  |
| archlinux | latest |  |  |
| arco |  |  |  |
| artixlinux | 20250407 | xfce-s6 xfce-runit xfce-openrc xfce-dinit plasma-s6 plasma-runit plasma-openrc plasma-dinit mate-s6 mate-runit mate-openrc mate-dinit lxqt-s6 lxqt-runit lxqt-openrc lxqt-dinit lxde-s6 lxde-runit lxde-openrc lxde-dinit community-qt community-gtk cinnamon-s6 cinnamon-runit cinnamon-openrc cinnamon-dinit base-s6 base-runit base-openrc base-dinit |  |
| athenaos | v23.11 v23.06.23 |  |  |
| batocera | 41 40 39 38 37 |  |  |
| bazzite | latest | kde gnome |  |
| biglinux | 2025-05-12 | k614 |  |
| blendos | latest |  |  |
| bodhi | 7.0.0 | standard s76 hwe apppack |  |
| bunsenlabs | boron |  |  |
| cachyos | latest | handheld desktop |  |
| centos-stream | 9 10 | dvd1 boot |  |
| cereus | latest | xfce musl-xfce musl-lxqt musl-base lxqt base |  |
| chimeralinux | latest | gnome base |  |
| crunchbang++ | 9.0 12.0 11.2 10.1 |  |  |
| debian | 12.10.0 11.11.0 10.13.0 | xfce standard netinst mate lxqt lxde kde gnome cinnamon |  |
| deepin | 25-alpha 23.1 23 20.9 |  |  |
| devuan | daedalus chimaera beowulf |  |  |
| dietpi | uefi bios | Trixie Bullseye Bookworm |  |
| dragonflybsd | 6.4.2 6.4.1 6.4.0 6.2.2 6.2.1 6.0.1 6.0.0 5.8.3 5.8.2 5.8.1 5.8.0 5.6.3 5.6.2 5.6.1 5.6.0 5.4.3 5.4.2 5.4.1 5.4.0 5.2.2 5.2.1 5.2.0 5.0.2 5.0.1 5.0.0 |  |  |
| dsl | 2024.rc7 | lz4 cdrom |  |
| easyos | 5.9 5.8.5 |  |  |
| edubuntu |  |  |  |
| elementary | 8.0 7.1 7.0 |  |  |
| endeavouros | mercury-neo-2025.03.19 mercury-2025.02.08 gemini-2024.04.20 galileo-neo-2024.01.25 galileo-11-2023

$(web_pipe ${URL}/ | grep -o '<a href |  |  |
| endless | 6.0.4 | pt_BR fr es en base |  |
| fedora | 42 41 40 | i3 Xfce Workstation Sway Silverblue Server Sericea Onyx MiracleWM Mate LXQt LXDE Kinoite KDE_Mobile KDE Cinnamon COSMIC-Atomic COSMIC Budgie |  |
| freebsd | 14.2 14.1 13.5 13.4 | dvd1 disc1 |  |
| freedos | 1.3 1.2 |  |  |
| fvoid | latest |  |  |
| gabeeos | latest | i3-gaps Qtile Openbox |  |
| garuda | latest | xfce sway mokka kde-lite i3 hyprland gnome dr460nized-gaming dr460nized cinnamon |  |
| gentoo | latest | minimal livegui |  |
| ghostbsd | 25.01-R14.2p1 24.10.1 24.07.3 | xfce mate |  |
| gnomeos | nightly 48.rc 48.beta 48.alpha 48.0 47.rc 47.beta 47.alpha 47.0 46.rc 46.beta 46.alpha 46.0 45.rc 45.beta 44.rc 44.beta 44.0 43.beta 43.alpha 43.0 42.rc 42.beta 42.0 41.rc 41.beta 41.0 40.rc 40.beta 40.0 3.38.1 3.38.0 |  |  |
| guix | 1.4.0 1.3.0 |  |  |
| haiku | r1beta5 r1beta4 r1beta3 | x86_gcc2h x86_64 |  |
| kali | kali-weekly current |  |  |
| kdeneon | user unstable testing developer |  |  |
| kodachi | latest |  |  |
| kolibrios | latest | ru_RU it_IT es_ES en_US |  |
| kubuntu |  |  |  |
| linuxlite | 6.6 6.4 6.2 6.0 |  |  |
| linuxmint | 22.1 22 21.3 21.2 21.1 21 20.3 20.2 | xfce mate cinnamon |  |
| lmde | 6 | cinnamon |  |
| loc-os | latest | xfce lxde kde |  |
| lubuntu |  |  |  |
| maboxlinux | latest |  |  |
| macos | ventura sonoma monterey mojave catalina big-sur |  |  |
| mageia | 9 8 | Xfce Plasma GNOME |  |
| manjaro | xfce sway plasma i3 gnome cinnamon | minimal full |  |
| miyo | 2022 | Openbox MATE Kwin JWM Deboot-Ceres |  |
| mxlinux | 23.6 | Xfce KDE Fluxbox |  |
| netboot | latest |  |  |
| netbsd | 9.4 9.3 10.1 10.0 |  |  |
| nitrux | latest |  |  |
| nixos | unstable 24.11 24.05 | plasma minimal gnome |  |
| nwg-shell | 2025.04.20 2025.02.23 |  |  |
| openbsd | 7.7 7.6 |  |  |
| openindiana |  |  |  |
| opensuse | tumbleweed microos aeon 15.6 15.5 15.4 15.3 15.2 15.1 15.0 |  |  |
| oraclelinux | 9.3 9.2 9.1 9.0 8.9 8.8 8.7 8.6 8.5 8.4 7.9 7.8 7.7 |  |  |
| parrotsec | 6.3.2 6.2 6.1 | security htb home |  |
| pbpuppy | 250502 250501 250404 250402 250314 250301 | VoidPup64 S15Pup64 BookwormPup64-ghtest |  |
| peppermint | latest | devuan-xfce devuan-gnome debian-xfce debian-gnome |  |
| popos | 22.04 20.04 | nvidia intel |  |
| porteus | 5.01 | xfce openbox mate lxqt lxde kde gnome cinnamon |  |
| primtux | 7 | 2022-10 |  |
| proxmox-ve | 8.4-1 8.3-1 7.4-1 6.4-1 5.4-1 |  |  |
| pureos | 10.3 | plasma gnome |  |
| reactos | latest |  |  |
| rebornos | latest |  |  |
| rhino | 2025.1 |  |  |
| rockylinux | 9.5 9.4 9.3 9.2 9.1 9.0 8.9 8.8 8.7 8.6 8.5 8.4 8.3 | minimal dvd boot |  |
| siduction | latest | xorg xfce nox lxqt kde |  |
| slackware | 15.0 14.2 14.1 14.0 13.37 |  |  |
| slax | latest | slackware debian |  |
| slint | 15.0-5 |  |  |
| slitaz | preinit loram core64 core-5in1 core |  |  |
| solus |  |  |  |
| sparkylinux | 7.7 | xfce minimalgui minimalcli mate lxqt kde |  |
| spirallinux | latest | XFCE Plasma Mate LXQt Gnome Cinnamon Builder Budgie |  |
| tails | stable |  |  |
| tinycore | 15 14 | TinyCorePure64 TinyCore CorePure64 CorePlus Core |  |
| trisquel | 11.0 10.0.1 | sugar mate lxde kde |  |
| truenas-core | 13 |  |  |
| truenas-scale | 24 |  |  |
| tuxedo-os | current |  |  |
| ubuntu-budgie |  |  |  |
| ubuntu-cinnamon |  |  |  |
| ubuntu-kylin |  |  |  |
| ubuntu-mate |  |  |  |
| ubuntu-server |  |  |  |
| ubuntu-unity |  |  |  |
| ubuntu |  |  |  |
| ubuntustudio |  |  |  |
| vanillaos | 22.10-r8 22.10-r7.5 22.10-r7 22.10-r6 22.10-r5 22.10-r4 22.10-r3 22.10-r2 22.10-r1 22.10 2.0 |  |  |
| ventoy | 1.1.05 1.1.04 1.1.02 1.1.01 1.1.00 1.0.99 1.0.98 1.0.97 1.0.96 1.0.95 1.0.94 1.0.93 1.0.91 1.0.90 1.0.89 1.0.88 1.0.87 1.0.86 1.0.85 |  |  |
| void | current | xfce-musl xfce-glibc musl glibc |  |
| vxlinux | 6.1.5 |  |  |
| windows-server |  |  |  |
| windows |  |  |  |
| xubuntu |  |  |  |
| zorin | 17 16 | lite64 education64 core64 |  |

