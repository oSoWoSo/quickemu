<h1 align="center">   <img src=".github/logo.png" alt="Quickemu" width="256"><br>Quickemu </h1>

<p align="center"><b>Rychle vytvářejte a spouštějte optimalizované desktopové virtuální stroje Windows, macOS a Linux.</b></p>
<div align="center"><img src=".github/screenshot.png" alt="Snímek obrazovky Quickemu"></div>
<p align="center">Vyrobeno s 💝 pro<img src=".github/tux.png" align="top" width="18"></p>

## Úvod

Rychle vytvářejte a spouštějte vysoce optimalizované virtuální stroje pro stolní počítače pro Linux, macOS a Windows; pouze dvěma příkazy. Vy se rozhodnete, jaký operační systém chcete používat, a Quickemu přijde na nejlepší způsob, jak to udělat za vás. Například:

```bash
quickget ubuntu-mate 22.04
quickemu --vm ubuntu-mate-22.04.conf
```

Původním cílem projektu bylo umožnit rychlé testování linuxových distribucí, kde lze konfigurace virtuálních strojů uložit kdekoli, jako je externí úložiště USB nebo váš domovský adresář, a ke spuštění virtuálních strojů nejsou vyžadována žádná zvýšená oprávnění. **Quickemu nyní také zahrnuje komplexní podporu pro macOS a Windows** .

## Funkce

- **macOS** Monterey, Big Sur, Catalina, Mojave a High Sierra
- **Windows** 10 a 11 včetně TPM 2.0
- [Ubuntu](https://ubuntu.com/desktop) a všechny **[oficiální příchutě Ubuntu](https://ubuntu.com/download/flavours)**
- **Je podporováno více než 360 edic operačního systému!**
- Plná podpora SPICE včetně sdílení schránky hostitele / hosta
- Sdílení souborů VirtIO-webdavd pro hosty se systémem Linux a Windows
- Sdílení souborů VirtIO-9p pro hosty se systémy Linux a macOS
- [podpora QEMU Guest Agent](https://wiki.qemu.org/Features/GuestAgent) ; poskytuje přístup k agentovi na systémové úrovni prostřednictvím standardních příkazů QMP
- Sdílení souborů Samba pro hosty se systémy Linux, macOS a Windows ( *pokud je na hostiteli nainstalován `smbd`* )
- Zrychlení VirGL
- Průchod zařízení USB
- Průchozí čipová karta
- Automatické přesměrování SSH portu hostům
- Přesměrování síťového portu
- Plně duplexní zvuk
- Podpora Braillova písma
- EFI (s nebo bez SecureBoot) a zavádění Legacy BIOS
- K dispozici jsou grafická uživatelská rozhraní

Quickemu je obal pro vynikající [QEMU](https://www.qemu.org/) , který se pokouší automaticky *"dělat správnou věc"* místo toho, aby vystavoval vyčerpávající možnosti konfigurace.

Pro tento projekt máme Discord: [](https://discord.gg/sNmz3uw)![Svár](https://img.shields.io/discord/712850672223125565?color=0C306A&label=WimpysWorld%20Discord&logo=Discord&logoColor=ffffff&style=flat-square)

Podívejte se na toto (staré) video, kde vysvětluji některé ze svých motivací pro vytvoření Quickemu.

[](https://www.youtube.com/watch?v=AOTYWEgw0hI)<img src="https://img.youtube.com/vi/AOTYWEgw0hI/0.jpg" alt="Nahraďte VirtualBox pomocí Bash &amp;&lt;span translate=" no=""> QEMU" data-md-type="image"&gt;

## Požadavky

- [QEMU](https://www.qemu.org/) ( *6.0.0 nebo novější* ) **s podporou GTK, SDL, SPICE a VirtFS**
- [bash](https://www.gnu.org/software/bash/) ( *4.0 nebo novější* )
- [Coreutils](https://www.gnu.org/software/coreutils/)
- [EDK II](https://github.com/tianocore/edk2)
- [grep](https://www.gnu.org/software/grep/)
- [jq](https://stedolan.github.io/jq/)
- [LSB](https://wiki.linuxfoundation.org/lsb/start)
- [procps](https://gitlab.com/procps-ng/procps)
- [python3](https://www.python.org/)
- [macrecovery](https://github.com/acidanthera/OpenCorePkg/tree/master/Utilities/macrecovery)
- [mkisofs](http://cdrtools.sourceforge.net/private/cdrecord.html)
- [usbutils](https://github.com/gregkh/usbutils)
- [util-linux](https://github.com/karelzak/util-linux)
- [sed](https://www.gnu.org/software/sed/)
- [socat](http://www.dest-unreach.org/socat/)
- [pikantní](https://gitlab.freedesktop.org/spice/spice-gtk)
- [swtpm](https://github.com/stefanberger/swtpm)
- [Wget](https://www.gnu.org/software/wget/)
- [xdg-user-dirs](https://www.freedesktop.org/wiki/Software/xdg-user-dirs/)
- [xrandr](https://gitlab.freedesktop.org/xorg/app/xrandr)
- [zsync](http://zsync.moria.org.uk/)
- [rozepnout](http://www.info-zip.org/UnZip.html)

### Požadavky na instalaci

U systémů Ubuntu, Arch a nixos se o závislosti postarají balíčky [ppa](https://launchpad.net/~flexiondotorg/+archive/ubuntu/quickemu) , [AUR](https://aur.archlinux.org/packages/quickemu) nebo [nix](https://github.com/NixOS/nixpkgs/tree/master/pkgs/development/quickemu) . Pro jiné hostitelské distribuce nebo operační systémy bude nutné nainstalovat výše uvedené požadavky nebo jejich ekvivalenty.

Tyto příklady mohou ušetřit trochu psaní

Debian (a přímé deriváty, jako je MX Linux):

```
sudo apt install qemu bash coreutils ovmf grep jq lsb-base procps python3 genisoimage usbutils util-linux sed spice-client-gtk libtss2-tcti-swtpm0 wget xdg-user-dirs zsync unzip
```

Fedora:

```
sudo dnf install qemu bash coreutils edk2-tools grep jq lsb procps python3 genisoimage usbutils util-linux sed spice-gtk-tools swtpm wget xdg-user-dirs xrandr unzip
```

Operační Systém Mac:

Na tomto procesu se pracuje (další kroky a změny, které mohou umožnit spuštění na MacOS, najdete [v čísle 248](https://github.com/quickemu-project/quickemu/issues/248) )

```
brew install qemu bash coreutils grep jq python@3.10 cdrtools gnu-sed spice-gtk wget zsync
```

# Používání

## Grafická uživatelská rozhraní

Zatímco `quickemu` a `quickget` jsou navrženy pro terminál, k dispozici je také grafické uživatelské rozhraní:

- **[Quickgui](https://github.com/quickgui/quickgui)** od [Marka Johnsona](https://github.com/marxjohnson) a [Yannicka Mauraye](https://github.com/ymauray) .

Mnohokrát děkujeme [Luke Wesley-Holleymu](https://github.com/Lukewh) a [Philippu Kiemlemu](https://github.com/daPhipz) za vytvoření **[ikon Quickemu](https://github.com/Lukewh/quickemu-icons)** 🎨

### Quickgui pro Ubuntu

```bash
sudo add-apt-repository ppa:yannick-mauray/quickgui
sudo apt update
sudo apt install quickgui
```

### projekt terminálu quickemu quickget X

Od listopadu 2023 je k dispozici také více možností integrované textové rozhraní pro stolní počítače se spoustou jedinečných nástrojů a utilit, které vám pomohou usnadnit instalace, snímky a správu disků.

- **[qqX](https://github.com/TuxVinyards/qqX)** je nezávisle kurátorem [Alex Genovese](https://github.com/TuxVinyards) (viz stránky github)

![qqX-vmm](https://github.com/TuxVinyards/qqX/assets/3956806/18e5c495-8072-49a5-8b9c-e1302549efcf)

# Nainstalujte Quickemu

## Oblouk

Quickemu je k dispozici z AUR (Arch user repository) a lze jej nainstalovat pomocí libovolného pomocníka AUR. Za předpokladu, že váš pomocník AUR je yay, spusťte následující příkaz:

```bash
yay -Sy quickemu
```

## Ubuntu

Quickemu je k dispozici z PPA pro uživatele Ubuntu. Quickemu PPA také obsahuje zadní port QEMU 6.0.0 pro 20.04 (Focal) a 21.04 (Hirsute). Chcete-li nainstalovat Quickemu a všechny závislosti, spusťte v terminálu následující:

```bash
sudo apt-add-repository ppa:flexiondotorg/quickemu
sudo apt update
sudo apt install quickemu
```

## Jiný Linux

```bash
git clone --filter=blob:none https://github.com/wimpysworld/quickemu
cd quickemu
```

Nyní nainstalujte všechny výše zdokumentované **požadavky** .

### Jiné zdroje

[Repology.org](https://repology.org/) zjistil, že následující verze byla zabalena.

#### Quickemu

[](https://repology.org/project/quickemu/versions)<img src="https://repology.org/badge/vertical-allrepos/quickemu.svg" alt="Balení&lt;span translate=" no=""> status" data-md-type="image"&gt;

#### Quickgui

[](https://repology.org/project/quickgui/versions)<img src="https://repology.org/badge/vertical-allrepos/quickgui.svg" alt="Balení&lt;span translate=" no=""> status" data-md-type="image"&gt;

## Host Ubuntu

`quickget` automaticky stáhne vydání Ubuntu a vytvoří konfiguraci virtuálního počítače.

```bash
quickget ubuntu 22.04
quickemu --vm ubuntu-22.04.conf
```

- Dokončete instalaci jako obvykle.
- Po instalaci:
    - Nainstalujte do hosta agenta SPICE ( `spice-vdagent` ), abyste povolili kopírování/vkládání a přesměrování USB
        - `sudo apt install spice-vdagent`
    - Chcete-li povolit sdílení souborů, nainstalujte do hosta agenta SPICE WebDAV ( `spice-webdavd` ).
        - `sudo apt install spice-webdavd`

### Ubuntu devel (denní) obrázky

`quickget` může také stahovat/obnovovat devel obrázky přes `zsync` pro vývojáře a testery Ubuntu.

```bash
quickget ubuntu devel
quickemu --vm ubuntu-devel.conf
```

`quickget ubuntu devel` můžete spouštět a obnovovat svůj každodenní vývojový obraz tak často, jak chcete, dokonce se automaticky přepne na novou sérii.

### Příchutě Ubuntu

Všechny oficiální příchutě Ubuntu jsou podporovány, stačí nahradit `ubuntu` vámi preferovanou příchutí.

- `edubuntu` (Edubuntu)
- `kubuntu` (Kubuntu)
- `lubuntu` (Lubuntu)
- `ubuntu-budgie` (Ubuntu andulka)
- `ubuntucinnamon` (Ubuntu skořice)
- `ubuntukylin` (Ubuntu Kylin)
- `ubuntu-mate` (Ubuntu MATE)
- `ubuntu-server` (Ubuntu Server)
- `ubuntustudio` (Ubuntu Studio)
- `ubuntu` (Ubuntu)
- `ubuntu-unity` (Ubuntu Unity)
- `xubuntu` (Xubuntu)

Můžete také použít `quickget` s možnostmi:

```shell
    # show an OS ISO download URL for {os} {release} [edition]
    quickget --show-iso-url fedora 38 Silverblue
    # test if and OS ISO is available for {os} {release} [edition]
    quickget --test-iso-url nixos 23.05 plasma5
    # open an OS distribution homepage in a browser
    quickget --open-distro-homepage  ubuntu-mate
```

Možnosti `--show-iso-url` a `--test-iso-url` **nefungují** pro `Windows` ( `quickget` začne stahovat požadované vydání a vydání systému Windows)

## Jiné operační systémy

`quickget` také podporuje:

- `alma` (Alma Linux)
- `alpine` (Alpine Linux)
- `android` (Android x86)
- `antix` (Antix)
- `archcraft` (Archcraft)
- `archlinux` (Arch Linux)
- `arcolinux` (Arco Linux)
- `batocera` (Batocera)
- `blendos` (BlendOS)
- `bodhi` (bodhi)
- `bunsenlabs` (Bunsenlabs)
- `cachyos` (CachyOS)
- `centos-stream` (CentOS Stream)
- `debian` (Debian)
- `deepin` (Deepin)
- `devuan` (devuan)
- `dragonflybsd` (DragonFlyBSD)
- `elementary` (základní OS)
- `endeavouros` (EndeavourOS)
- `endless` (nekonečný OS)
- `fedora` (Fedora)
- `freebsd` (FreeBSD)
- `freedos` (FreeDOS)
- `garuda` (Garuda Linux)
- `gentoo` (Gentoo)
- `ghostbsd` (GhostBSD)
- `haiku` (haiku)
- `holoiso` (SteamOS HoloISO)
- `kali` (kali)
- `kdeneon` (KDE Neon)
- `kolibrios` (KolibriOS)
- `linuxlite` (Linux Lite)
- `linuxmint` (Linux Mint)
- `lmde` (Linux Mint Debian Edition)
- `mageia` (Mageia)
- `manjaro` (mandžáro)
- `mxlinux` (MX Linux)
- `netboot` (netboot.xyz)
- `netbsd` (NetBSD)
- `nixos` (NixOS)
- `openbsd` (OpenBSD)
- `openindiana` (OpenIndiana)
- `opensuse` (openSUSE)
- `oraclelinux` (Oracle Linux)
- `peppermint` (PeppermintOS)
- `popos` (Pop!_OS)
- `porteus` (Porteus)
- `reactos` (ReactOS)
- `rebornos` (RebornOS)
- `rockylinux` (Rocky Linux)
- `siduction` (Siduction)
- `slackware` (slackware)
- `solus` (Solus)
- `spiral` (spirála)
- `tails` (ocásky)
- `tinycore` (Tiny Core Linux)
- `trisquel` (trisquel)
- `truenas-core` (TrueNAS Core)
- `truenas-scale` (TrueNAS Scale)
- `vanillaos` (Vanilla OS)
- `void` (Void Linux)
- `vxlinux` (VX Linux)
- `xerolinux` (XeroLinux)
- `zorin` (OS Zorin)

Nebo si můžete stáhnout image Linuxu a ručně vytvořit konfiguraci virtuálního počítače.

- Stáhněte si obraz .iso distribuce Linuxu
- Vytvořte konfigurační soubor virtuálního počítače; například `debian-bullseye.conf`

```bash
guest_os="linux"
disk_img="debian-bullseye/disk.qcow2"
iso="debian-bullseye/firmware-11.0.0-amd64-DVD-1.iso"
```

- Ke spuštění virtuálního počítače použijte `quickemu` :

```bash
quickemu --vm debian-bullseye.conf
```

- Dokončete instalaci jako obvykle.
- Po instalaci:
    - Nainstalujte do hosta agenta SPICE ( `spice-vdagent` ), abyste umožnili kopírování/vkládání a přesměrování USB.
    - Chcete-li povolit sdílení souborů, nainstalujte do hosta agenta SPICE WebDAV ( `spice-webdavd` ).

## host macOS

`quickget` automaticky stáhne obraz pro obnovení macOS a vytvoří konfiguraci virtuálního počítače.

```bash
quickget macos catalina
quickemu --vm macos-catalina.conf
```

Podporovány jsou macOS `high-sierra` , `mojave` , `catalina` , `big-sur` , `monterey` a `ventura` .

- Pomocí kurzorových kláves a klávesy Enter vyberte **základní systém macOS**
- Z **nástrojů macOS**
    - Klepněte na **Disk Utility** a **Pokračovat**
        - Ze seznamu vyberte `QEMU HARDDISK Media` (~103,08 GB) (na Big Sur a výše použijte `Apple Inc. VirtIO Block Device` ) a klikněte na **Vymazat** .
        - Zadejte `Name:` pro disk
        - Pokud instalujete macOS Mojave nebo novější (Catalina, Big Sur, Monterey a Ventura), vyberte jako souborový systém kteroukoli z možností APFS. MacOS Extended nemusí fungovat.
    - Klikněte na **Vymazat** .
    - Klikněte **na Hotovo** .
    - Zavřete Disk Utility
- Z **nástrojů macOS**
    - Klikněte **na Přeinstalovat macOS** a **pokračovat**
- Dokončete instalaci obvyklým způsobem.
    - Při prvním restartu pomocí kurzorových kláves a klávesy Enter vyberte **instalační program macOS**
    - Při dalších restartech použijte kurzorové klávesy a klávesu Enter pro výběr disku, který jste pojmenovali
- Jakmile dokončíte instalaci macOS, zobrazí se vám připravený průvodce prvním spuštěním pro konfiguraci různých možností a nastavení uživatelského jména a hesla.
- VOLITELNÉ: Po dokončení přednastaveného průvodce možná budete chtít povolit funkci TRIM, kterou počítačový průmysl vytvořil pro disky SSD. Tato funkce v naší instalaci macOS umožní QuickEmu zkomprimovat (zmenšit) váš obraz disku macOS, kdykoli odstraníte soubory ve virtuálním počítači. Bez tohoto kroku se obraz disku macOS pouze zvětší a nezmenší se, ani když v macOS smažete spoustu dat.
    - Chcete-li povolit TRIM, otevřete aplikaci Terminál a zadejte následující příkaz a poté stiskněte příkaz na pevném disku, když jsou soubory odstraněny:

```bash
sudo trimforce enable
```

Budete vyzváni k zadání hesla k účtu, abyste získali potřebná oprávnění. Jakmile zadáte své heslo a stisknete ve formě dvou otázek, které vyžadují, abyste napsali odpověď, jako byste řekli „ne“:

```plain
IMPORTANT NOTICE: This tool force-enables TRIM for all relevant attached devices, even though such devices may not have been validated for data integrity while using TRIM. Use of this tool to enable TRIM may result in unintended data loss or data corruption. It should not be used in a commercial operating environment or with important data. Before using this tool, you should back up all of your data and regularly back up data while TRIM is enabled. This tool is provided on an "as is" basis. APPLE MAKES NO WARRANTIES, EXPRESS OR IMPLIED, INCLUDING WITHOUT LIMITATION THE IMPLIED WARRANTIES OF NON-INFRINGEMENT, MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE, REGARDING THIS TOOL OR ITS USE ALONE OR IN COMBINATION WITH YOUR DEVICES, SYSTEMS, OR SERVICES. BY USING THIS TOOL TO ENABLE TRIM, YOU AGREE THAT, TO THE EXTENT PERMITTED BY APPLICABLE LAW, USE OF THE TOOL IS AT YOUR SOLE RISK AND THAT THE ENTIRE RISK AS TO SATISFACTORY QUALITY, PERFORMANCE, ACCURACY AND EFFORT IS WITH YOU.
Are you sure you with to proceed (y/N)?
```

A druhé potvrzení, jakmile potvrdíte předchozí:

```plain
Your system will immediately reboot when this is complete.
Is this OK (y/N)?
```

Jak uvádí poslední zpráva, váš systém se automaticky restartuje, jakmile bude příkaz dokončen.

Výchozí konfigurace macOS vypadá takto:

```bash
guest_os="macos"
img="macos-catalina/RecoveryImage.img"
disk_img="macos-catalina/disk.qcow2"
macos_release="catalina"
```

- `guest_os="macos"` instruuje Quickemu k optimalizaci pro macOS.
- `macos_release="catalina"` dává Quickemu pokyn k optimalizaci pro konkrétní vydání macOS.
    - Například VirtIO Network a Memory Ballooning jsou dostupné v Big Sur a novějších, ale ne v předchozích verzích.
    - A VirtIO Block Media (disky) jsou podporovány/stabilní v Catalina a novějších.

### kompatibilita s macOS

Při spouštění systému macOS přes Quickemu je třeba zvážit.

- Podporovaná vydání macOS:
    - Vysoká Sierra
    - Mojave
    - Catalina **(doporučeno)**
    - Velký Sur
    - Monterey
    - Ventura
- `quickemu` automaticky stáhne požadovaný zavaděč [OpenCore](https://github.com/acidanthera/OpenCorePkg) a firmware OVMF z [OSX-KVM](https://github.com/kholia/OSX-KVM) .
- Ve výchozím nastavení optimalizováno, ale není k dispozici žádná akcelerace GPU.
    - Je zjištěn dodavatel hostitelského CPU a hostovaný CPU je podle toho optimalizován.
    - [VirtIO Block Media](https://www.kraxel.org/blog/2019/06/macos-qemu-guest/) se používá pro systémový disk tam, kde je podporováno.
    - Pro myš je použit [`usb-tablet` VirtIO](http://philjordan.eu/osx-virt/) .
    - Síť VirtIO ( `virtio-net` ) je podporována a povolena na macOS Big Sur a novějších, ale předchozí verze používají `vmxnet3` .
    - VirtIO Memory Ballooning je podporováno a povoleno v macOS Big Sur a novějších, ale pro ostatní verze podpory macOS je zakázáno.
- Hostitel USB a průchod SPICE je:
    - UHCI (USB 2.0) na macOS Catalina a dřívějších verzích.
    - XHCI (USB 3.0) na macOS Big Sur a novějších.
- Rozlišení displeje lze změnit pouze prostřednictvím předvoleb systému macOS.
- **Plně duplexní zvuk vyžaduje [VoodooHDA OC](https://github.com/chris1111/VoodooHDA-OC) nebo přenos přes USB audio zařízení do hostujícího virtuálního počítače macOS** .
- POZNÁMKA! Chcete-li nainstalovat VoodooHDA OC, je třeba vypnout [Gatekeeper](https://disable-gatekeeper.github.io/) a [System Integrity Protection (SIP).](https://developer.apple.com/documentation/security/disabling_and_enabling_system_integrity_protection)
- Sdílení souborů mezi hostem a hostitelem je dostupné přes [virtio-9p](https://wiki.qemu.org/Documentation/9psetup) a [SPICE webdavd](https://gitlab.gnome.org/GNOME/phodav/-/merge_requests/24) .
- Kopírování/vkládání prostřednictvím agenta SPICE **není v systému macOS k dispozici** .

### macOS App Store

Pokud se při pokusu o přihlášení do App Store zobrazí zpráva *„Vaše zařízení nebo počítač nelze ověřit“* , ujistěte se, že je vaše zařízení s kabelovou ethernetovou sítí `en0` . K ověření použijte `ifconfig` v terminálu.

Pokud kabelové ethernetové zařízení není `en0` , přejděte do *Předvolby systému* -&gt; *Síť* , odstraňte všechna síťová zařízení a použijte změny. Dále otevřete terminál a spusťte následující:

```bash
sudo rm /Library/Preferences/SystemConfiguration/NetworkInterfaces.plist
```

Nyní restartujte a App Store by měl fungovat.

## Windows 8, 10 a 11 pro hosty

`quickget` dokáže automaticky stáhnout [Windows10](https://www.microsoft.com/software-download/windows10) a [Windows 11](https://www.microsoft.com/software-download/windows11) a vytvořit optimalizovanou konfiguraci virtuálního stroje. Tato konfigurace také zahrnuje [ovladače VirtIO pro Windows](https://fedorapeople.org/groups/virt/virtio-win/direct-downloads/) .

Windows 8.1 je také podporován, ale neobsahuje žádnou automatickou instalaci ani optimalizaci ovladačů.

```bash
quickget windows 11
quickemu --vm windows-11.conf
```

- Dokončete instalaci obvyklým způsobem.
- Všechny příslušné ovladače a služby by se měly nainstalovat automaticky.
- Automaticky se vytvoří uživatelský účet místního správce s těmito přihlašovacími údaji:
    - Uživatelské jméno: `Quickemu`
    - Heslo: `quickemu`

Výchozí konfigurace Windows 11 vypadá takto:

```bash
guest_os="windows"
disk_img="windows-11/disk.qcow2"
iso="windows-11/windows-11.iso"
fixed_iso="windows-11/virtio-win.iso"
tpm="on"
secureboot="off"
```

- `guest_os="windows"` instruuje `quickemu` k optimalizaci pro Windows.
- `fixed_iso=` určuje obraz ISO, který poskytuje ovladače VirtIO.
- `tpm="on"` dává pokyn `quickemu` k vytvoření softwarově emulovaného zařízení TPM pomocí `swtpm` .

# KOŘENÍ

Při používání protokolu SPICE jsou k dispozici následující funkce:

- Zkopírujte/vložte mezi hostem a hostitelem
- Host sdílení souborů s hostem
- přesměrování zařízení USB

Chcete-li použít SPICE add `--display spice` do vyvolání Quickemu, vyžaduje to, aby byl nainstalován klient `spicy` , který je k dispozici z balíčku `spice-client-gtk` v Debian/Ubuntu.

```bash
quickemu --vm ubuntu-22.04.conf --display spice
```

Chcete-li povolit kopírování/vkládání s hostem Windows, nainstalujte do hostovaného virtuálního počítače [nástroje SPICE Windows](https://www.spice-space.org/download.html) .

## Bezhlavý

Chcete-li spustit VM s povoleným SPICE, ale bez připojeného displeje, použijte `--display none` . To vyžaduje, aby byl nainstalován `spicy` klient dostupný z balíčku `spice-client-gtk` v Debian/Ubuntu pro připojení k běžícímu virtuálnímu počítači.

```bash
quickemu --vm ubuntu-22.04.conf --display none
```

Můžete také použít soubor `.ports` v adresáři VM k vyhledání portů SSH a SPICE, ke kterým je VM připojen.

```bash
cat ubuntu-22.04/ubuntu-22.04.ports
```

Pokud je například port SSH nastaven na 22220 a za předpokladu, že váš virtuální počítač má spuštěnou službu SSH (podrobnosti se liší podle OS), můžete do něj obvykle SSH připojit z hostitele takto:

```bash
ssh -p 22220 your_vm_user@localhost
```

# Přístupnost

Qemu poskytuje podporu pro použití BrlAPI k zobrazení braillského výstupu na skutečném nebo falešném zařízení.

```bash
quickemu --vm ubuntu-22.04.conf --braille --display sdl
```

# BIOS a EFI

Protože Quickemu 2.1.0 je `efi` výchozí možností spouštění. Pokud chcete toto chování přepsat, přidejte do konfigurace virtuálního počítače následující řádek, abyste povolili starší verzi systému BIOS.

- `boot="legacy"` - Povolí spouštění staršího systému BIOS

# Ladění procesorových jader, RAM a disků

Ve výchozím nastavení Quickemu vypočítá počet jader CPU a RAM pro přidělení virtuálnímu počítači na základě specifikací vašeho hostitelského počítače. Toto výchozí chování můžete přepsat a vyladit konfiguraci virtuálního počítače podle svých představ.

Přidejte další řádky do konfigurace virtuálního počítače:

- `cpu_cores="4"` - Zadejte počet jader CPU přidělených virtuálnímu počítači
- `ram="4G"` – Určete množství paměti RAM, které se má přidělit virtuálnímu počítači
- `disk_size="16G"` - Zadejte velikost virtuálního disku přiděleného virtuálnímu počítači

## Předběžné přidělení disku

Režim předběžného přidělení (povolené hodnoty: `off` (výchozí), `metadata` , `falloc` , `full` ). Obrázek s předem přidělenými metadaty je zpočátku větší, ale může zlepšit výkon, když obrázek potřebuje růst.

Určete, jaké předběžné přidělení disku se má použít, pokud existuje, při vytváření bitové kopie systémového disku přidáním takového řádku do konfigurace virtuálního počítače.

- `preallocation="metadata"`

## CD-ROM disky

Pokud chcete zpřístupnit obraz ISO z hostitele hostovi, přidejte do konfigurace virtuálního počítače následující řádek:

- `fixed_iso="/path/to/image.iso"`

## Diskety

Pokud jste jako [Alan Pope,](https://popey.com) pravděpodobně budete chtít připojit obraz diskety do hosta. Chcete-li tak učinit, přidejte do konfigurace virtuálního počítače následující řádek:

- `floppy="/path/to/floppy.img"`

# Sdílení souborů

Všechny možnosti sdílení souborů zpřístupní hostujícím virtuálním počítačům pouze `~/Public` (nebo lokalizované varianty) pro aktuálního uživatele.

## Samba 🐧 🍏 🪟

Pokud je na hostiteli k dispozici `smbd` , Quickemu automaticky povolí vestavěnou podporu QEMU pro vystavení sdílení Samba z hostitele hostovi.

Minimální komponenty Samba můžete nainstalovat na Ubuntu pomocí:

```bash
sudo apt install --no-install-recommends samba
```

Pokud je vše správně nastaveno, `smbd` adresa se vytiskne při spuštění virtuálního stroje. Například:

```
 - smbd:     On guest: smb://10.0.2.4/qemu
```

Pokud používáte hosta Windows, klikněte pravým tlačítkem na "Tento počítač", klikněte na "Přidat síťové umístění" a vložte tuto adresu, odstraňte `smb:` a nahraďte dopředná lomítka zpětnými lomítky (v tomto příkladu `\10.0.2.4\qemu` ).

## SPICE WebDAV 🐧 🪟

- TBD

## VirtIO-9P 🐧 🍏

- TBD

# Přesměrování síťového portu

Přidejte další řádek do konfigurace virtuálního počítače. Například:

- `port_forwards=("8123:8123" "8888:80")`

V příkladu výše:

- Port 8123 na hostiteli je přesměrován na port 8123 na hostovi.
- Port 8888 na hostiteli je přesměrován na port 80 na hostiteli.

# Zakázat práci v síti

Chcete-li úplně zakázat všechna síťová rozhraní v hostovaném virtuálním počítači, přidejte do konfigurace virtuálního počítače tento další řádek:

- `network="none"`

# Omezené vytváření sítí

Hosta můžete izolovat od hostitele (a širší sítě) pomocí možnosti omezení, která omezí práci v síti pouze na hosta a jakákoli virtuální zařízení.

Toho lze využít k tomu, aby software běžící uvnitř hosta nemohl telefonovat domů a přitom stále poskytoval síť uvnitř hosta. Přidejte tento další řádek do konfigurace virtuálního počítače:

- `network="restrict"`

# Přemostěné sítě

Připojte svůj virtuální počítač k předem nakonfigurovanému síťovému mostu. Přidejte další řádek do konfigurace virtuálního počítače:

- `network="br0"`

Pokud chcete mít trvalou MAC adresu pro vaše přemostěné síťové rozhraní v hostujícím virtuálním počítači, můžete do konfigurace virtuálního počítače přidat `macaddr` . QEMU vyžaduje, aby adresa MAC byla v rozsahu: **52:54:00:AB:00:00 - 52:54:00:AB:FF:FF**

Takže si můžete generovat své vlastní MAC adresy pomocí:

- `macaddr="52:54:00:AB:51:AE"`

# přesměrování USB

Quickemu podporuje přesměrování USB přes SPICE pass-through a host pass-through.

## Přesměrování SPICE (doporučeno)

Použití SPICE pro USB pass-through je nejjednodušší, protože nevyžaduje žádná zvýšená oprávnění, spusťte Quickemu s `--display spice` a poté z nabídky vyberte `Input` -&gt; `Select USB Device for redirection` a vyberte, která zařízení chcete připojit k hostovi.

## Přesměrování hostitele **NENÍ doporučeno**

**Přesměrování USB hostitele se nedoporučuje** , je poskytováno čistě pro zpětnou kompatibilitu se staršími verzemi Quickemu. Preferuje se použití SPICE, viz výše.

Přidejte další řádek do konfigurace virtuálního počítače. Například:

- `usb_devices=("046d:082d" "046d:085e")`

V příkladu výše:

- Zařízení USB s vendor_id 046d a product_id 082d bude vystaveno hostovi.
- Zařízení USB s vendor_id 046d a product_id 085e bude vystaveno hostovi.

Pokud na zařízení USB nelze zapisovat, `quickemu` zobrazí příslušné příkazy pro úpravu přístupových oprávnění zařízení USB, například takto:

```
 - USB:      Host pass-through requested:
              - Sennheiser Communications EPOS GTW 270 on bus 001 device 005 needs permission changes:
                sudo chown -v root:user /dev/bus/usb/001/005
                ERROR! USB permission changes are required 👆
```

# TPM

Od Quickemu 2.2.0 lze k hostujícím virtuálním počítačům přidat softwarově emulované zařízení TPM. Stačí přidat `tpm="on"` do konfigurace virtuálního počítače. `quickget` automaticky přidá tento řádek do virtuálních počítačů Windows 11.

# Všechny možnosti

Zde jsou pokyny k použití:

<!-- [[[cog
import subprocess

import cog
# cannot use check_result() because of non-zero return
result=subprocess.run(["./quickemu", "--help"], capture_output=True, text=True)
help=result.stdout
cog.out(f"\n```\n{help}\n```\n")
]]] -->

```

Usage
  quickemu --vm ubuntu.conf

You can also pass optional parameters
  --access                          : Enable remote spice access support. 'local' (default), 'remote', 'clientipaddress'
  --braille                         : Enable braille support. Requires SDL.
  --delete-disk                     : Delete the disk image and EFI variables
  --delete-vm                       : Delete the entire VM and it's configuration
  --display                         : Select display backend. 'sdl' (default), 'gtk', 'none', 'spice' or 'spice-app'
  --fullscreen                      : Starts VM in full screen mode (Ctl+Alt+f to exit)
  --ignore-msrs-always              : Configure KVM to always ignore unhandled machine-specific registers
  --screen <screen>                 : Use specified screen to determine the window size.
  --screenpct <percent>             : Percent of fullscreen for VM if --fullscreen is not specified.
  --shortcut                        : Create a desktop shortcut
  --snapshot apply <tag>            : Apply/restore a snapshot.
  --snapshot create <tag>           : Create a snapshot.
  --snapshot delete <tag>           : Delete a snapshot.
  --snapshot info                   : Show disk/snapshot info.
  --status-quo                      : Do not commit any changes to disk/snapshot.
  --viewer <viewer>                 : Choose an alternative viewer. @Options: 'spicy' (default), 'remote-viewer', 'none'
  --ssh-port <port>                 : Set ssh-port manually
  --spice-port <port>               : Set spice-port manually
  --public-dir <path>               : Expose share directory. @Options: '' (default: xdg-user-dir PUBLICSHARE), '<directory>', 'none'
  --monitor <type>                  : Set monitor connection type. @Options: 'socket' (default), 'telnet', 'none'
  --monitor-telnet-host <ip/host>   : Set telnet host for monitor. (default: 'localhost')
  --monitor-telnet-port <port>      : Set telnet port for monitor. (default: '4440')
  --monitor-cmd <cmd>               : Send command to monitor if available. (Example: system_powerdown)
  --serial <type>                   : Set serial connection type. @Options: 'socket' (default), 'telnet', 'none'
  --serial-telnet-host <ip/host>    : Set telnet host for serial. (default: 'localhost')
  --serial-telnet-port <port>       : Set telnet port for serial. (default: '6660')
  --keyboard <type>                 : Set keyboard. @Options: 'usb' (default), 'ps2', 'virtio'
  --keyboard_layout <layout>        : Set keyboard layout.
  --mouse <type>                    : Set mouse. @Options: 'tablet' (default), 'ps2', 'usb', 'virtio'
  --usb-controller <type>           : Set usb-controller. @Options: 'ehci' (default), 'xhci', 'none'
  --sound-card <type>               : Set sound card. @Options: 'intel-hda' (default), 'ac97', 'es1370', 'sb16', 'none'
  --extra_args <arguments>          : Pass additional arguments to qemu
  --version                         : Print version

```

<!-- [[[end]]] -->

## Zástupci na ploše

Pro virtuální počítač lze vytvořit zástupce na ploše, zástupci jsou uloženi v `~/.local/share/applications` . Zde je příklad, jak vytvořit zástupce.

```bash
quickemu --vm ubuntu-22.04-desktop.conf --shortcut
```

## Velikost obrazovky a okna (pouze pro hosty se systémem Linux)

`qemu` bude vždy výchozí primární monitor pro zobrazení okna virtuálního počítače.

Bez možnosti `--screen` bude `quickemu` hledat velikost nejmenšího monitoru a použije velikost, která se na daný monitor vejde.

Volba `--screen` nutí `quickemu` použít pro výpočet velikosti okna velikost daného monitoru. **Nepoužije tento monitor k zobrazení okna virtuálního počítače, pokud to není primární monitor** . To je užitečné, pokud primární monitor, ne-li nejmenší, a pokud není nutné přesouvat okno virtuálního počítače.

Volba `--screen` je také užitečná s volbou `--fullscreen` , opět proto, že `qemu` bude vždy používat primární monitor. Aby režim celé obrazovky fungoval správně, musí rozlišení okna virtuálního počítače odpovídat rozlišení obrazovky.

Chcete-li vědět, kterou obrazovku použít, zadejte:

```bash
xrandr --listmonitors | grep -v Monitors
```

Příkaz vypíše něco takového:

```bash
 0: +*HDMI-0 2560/597x1440/336+1920+0  HDMI-0
 1: +DVI-D-0 1920/527x1080/296+0+0  DVI-D-0
```

První číslo je to, co je třeba předat volbě `--screen` .

Například:

```bash
quickemu --vm vm.conf --screen 0
```

Výše uvedené používá obrazovku 2560x1440 pro výpočet velikosti okna, které Quickemu velikosti 2048x1152. Bez možnosti `--screen` by Quickemu použilo monitor 1920x1080, což má za následek velikost okna 1664x936.

'--screenpct' je volitelná celočíselná hodnota mezi 25 &lt;= pct &lt; 100, která přepíše výchozí velikosti obrazovky systému. Velikost virtuálního počítače bude 'pct' zvolené obrazovky. **Je-li zvoleno --fullscreen, bude obrazovka plná, místo toho, aby byla zmenšena o hodnotu --screenpct.**

# Reference

Užitečná reference, která pomohla vývoji Quickemu.

- Všeobecné
    - [Dokumentace QEMU!](https://qemu.readthedocs.io/en/latest/)
    - [https://pve.proxmox.com/wiki/Qemu/KVM_Virtual_Machines](https://pve.proxmox.com/wiki/Qemu/KVM_Virtual_Machines)
    - [https://www.kraxel.org/blog/2020/01/qemu-sound-audiodev/](https://www.kraxel.org/blog/2020/01/qemu-sound-audiodev/)
- Operační Systém Mac
    - [https://www.nicksherlock.com/2020/06/installing-macos-big-sur-on-proxmox/](https://www.nicksherlock.com/2020/06/installing-macos-big-sur-on-proxmox/)
    - [https://passthroughpo.st/mac-os-adds-early-support-for-virtio-qemu/](https://passthroughpo.st/mac-os-adds-early-support-for-virtio-qemu/)
    - [https://github.com/kholia/OSX-KVM](https://github.com/kholia/OSX-KVM)
    - [https://github.com/thenickdude/KVM-Opencore](https://github.com/thenickdude/KVM-Opencore)
    - [https://github.com/acidanthera/OpenCorePkg/tree/master/Utilities/macrecovery](https://github.com/acidanthera/OpenCorePkg/tree/master/Utilities/macrecovery)
    - [https://www.kraxel.org/blog/2017/09/running-macos-as-guest-in-kvm/](https://www.kraxel.org/blog/2017/09/running-macos-as-guest-in-kvm/)
    - [https://www.nicksherlock.com/2017/10/passthrough-of-advanced-cpu-features-for-macos-high-sierra-guests/](https://www.nicksherlock.com/2017/10/passthrough-of-advanced-cpu-features-for-macos-high-sierra-guests/)
    - [http://philjordan.eu/osx-virt/](http://philjordan.eu/osx-virt/)
    - [https://github.com/Dids/clover-builder](https://github.com/Dids/clover-builder)
    - [Konfigurátor OpenCore](https://mackie100projects.altervista.org)
- Okna
    - [https://www.heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/](https://www.heiko-sieger.info/running-windows-10-on-linux-using-kvm-with-vga-passthrough/)
    - [https://leduccc.medium.com/improving-the-performance-of-a-windows-10-guest-on-qemu-a5b3f54d9cf5](https://leduccc.medium.com/improving-the-performance-of-a-windows-10-guest-on-qemu-a5b3f54d9cf5)
    - [https://frontpagelinux.com/tutorials/how-to-use-linux-kvm-to-optimize-your-windows-10-virtual-machine/](https://frontpagelinux.com/tutorials/how-to-use-linux-kvm-to-optimize-your-windows-10-virtual-machine/)
    - [https://turlucode.com/qemu-command-line-args/](https://turlucode.com/qemu-command-line-args/)
    - [https://github.com/pbatard/Fido](https://github.com/pbatard/Fido)
    - [https://www.catapultsystems.com/blogs/create-zero-touch-windows-10-iso/](https://www.catapultsystems.com/blogs/create-zero-touch-windows-10-iso/)
- TPM
    - [https://qemu-project.gitlab.io/qemu/specs/tpm.html](https://qemu-project.gitlab.io/qemu/specs/tpm.html)
    - [https://www.tecklyfe.com/how-to-create-a-windows-11-virtual-machine-in-qemu/](https://www.tecklyfe.com/how-to-create-a-windows-11-virtual-machine-in-qemu/)
- 9p a virtiofs
    - [https://wiki.qemu.org/Documentation/9p](https://wiki.qemu.org/Documentation/9p)
    - [https://wiki.qemu.org/Documentation/9psetup](https://wiki.qemu.org/Documentation/9psetup)
    - [https://www.kraxel.org/blog/2019/06/macos-qemu-guest/](https://www.kraxel.org/blog/2019/06/macos-qemu-guest/)
    - [https://superuser.com/questions/628169/how-to-share-a-directory-with-the-host-without-networking-in-qemu](https://superuser.com/questions/628169/how-to-share-a-directory-with-the-host-without-networking-in-qemu)
    - [https://virtio-fs.gitlab.io/](https://virtio-fs.gitlab.io/)
