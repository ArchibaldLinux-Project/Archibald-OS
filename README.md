# Archibald Linux

Archibald Linux is an Arch Linux-based live/rescue distribution featuring KDE Plasma desktop environment and a custom graphical installer. It provides a complete system administration toolkit with a modern, user-friendly interface.

## Features

### Desktop Environment
- **KDE Plasma**: Full-featured desktop environment with modern UI
- **SDDM**: Simple Desktop Display Manager with autologin support
- **Konsole**: Default terminal emulator
- **Xorg**: X11 window system

### System Tools
- **Archinstall**: Command-line installer (also available via GUI)
- **Custom Python Installer**: Graphical installer built with PyQt5
- **Filesystem Support**: ext4, btrfs, xfs, f2fs, and more
- **Partitioning Tools**: parted, gparted, gptfdisk
- **Backup/Clone**: clonezilla, fsarchiver, partclone, partimage

### Networking
- **iwd**: Modern wireless daemon
- **NetworkManager**: Network management via systemd-networkd
- **VPN Support**: openvpn, openconnect, vpnc
- **Dial-up**: wvdial, ppp, pptpclient

### Rescue Tools
- **Data Recovery**: ddrescue, testdisk, photorec
- **System Information**: dmidecode, smartmontools, lsscsi
- **Disk Management**: lvm2, mdadm, cryptsetup
- **Boot Repair**: grub, refind

### Virtualization Support
- **QEMU**: qemu-guest-agent
- **VirtualBox**: virtualbox-guest-utils-nox
- **VMware**: open-vm-tools, vmware-vmblock-fuse
- **Hyper-V**: hyperv daemons

### Accessibility
- **Screen Reader**: espeakup, brltty
- **Audio Support**: alsa-utils, livecd-sounds

### Additional Features
- **Cloud-init**: Cloud initialization support
- **SSH Server**: OpenSSH with root login enabled
- **System Monitoring**: htop, iotop, nmap, tcpdump
- **Text Editors**: vim, nano, mc (Midnight Commander)
- **Shells**: zsh with grml-zsh-config

## Building the ISO

### Prerequisites

You need an Arch Linux system with the following packages:
- archiso
- git

### Build Instructions

1. Clone the repository:
```bash
git clone https://github.com/ArchibaldLinux-Project/Archibald-OS.git
cd Archibald-OS
```

2. Build the ISO:
```bash
sudo mkarchiso -v -w work/ -o out/ archlive/
```

The ISO will be created in the `out/` directory.

## Installation

### Booting the ISO

1. Download or build the Archibald Linux ISO
2. Write it to a USB drive:
```bash
dd if=archibald-x86_64.iso of=/dev/sdX bs=4M status=progress
sync
```
3. Boot from the USB drive

### Using the Graphical Installer

1. After booting, you'll be automatically logged into KDE Plasma
2. Double-click the "Install Archibald Linux" icon on the desktop
3. Follow the wizard steps:
   - **Welcome**: Introduction to the installer
   - **Disk Configuration**: Select disk, partitioning mode, filesystem
   - **Locale & Timezone**: Configure locale, timezone, keyboard
   - **User Configuration**: Set root password and create user account
   - **Network Configuration**: Set hostname and network interface
   - **Package Selection**: Choose additional package groups
   - **Bootloader Configuration**: Select bootloader and boot drive
   - **Summary**: Review configuration before installation
   - **Installation**: Watch the installation progress

### Using the Command-line Installer

If you prefer the command line, you can use archinstall directly:

```bash
sudo archinstall
```

## System Configuration

### KDE Info Center

The KDE Info Center displays custom distribution information. This is configured via:
- `/etc/xdg/kcm-about-distrorc`: Main configuration
- `/usr/local/bin/archibald-info`: Custom info script
- `/etc/os-release`: Distribution metadata

### Neofetch

Neofetch is configured to display Archibald Linux branding:
- Configuration file: `/etc/neofetch/config.conf`
- Shows custom distribution name and logo

### Display Manager

SDDM is configured with:
- Autologin for root user (live environment)
- Plasma session as default
- Configuration: `/etc/sddm.conf`

### Network

Network is configured via systemd-networkd:
- Ethernet: `/etc/systemd/network/20-ethernet.network`
- Wi-Fi: `/etc/systemd/network/20-wlan.network`
- WWAN: `/etc/systemd/network/20-wwan.network`

DHCP is enabled by default for all interfaces.

## Project Structure

```
Archibald-OS/
├── archlive/                 # Main configuration directory
│   ├── profiledef.sh         # ISO build configuration
│   ├── packages.x86_64       # Package list for x86_64
│   ├── pacman.conf           # Pacman configuration
│   ├── airootfs/             # Root filesystem overlay
│   │   ├── etc/              # System configuration
│   │   ├── root/             # Root user files
│   │   └── usr/              # User programs
│   ├── grub/                 # GRUB configuration
│   ├── syslinux/             # Syslinux configuration
│   └── efiboot/              # EFI boot configuration
├── work/                     # Build working directory
└── out/                      # Output directory for ISO
```

## Customization

### Adding Packages

Edit `archlive/packages.x86_64` to add or remove packages:

```bash
# Add your package
vim archlive/packages.x86_64
```

### Modifying System Configuration

System configuration files are in `archlive/airootfs/etc/`. Common modifications:
- `/etc/sddm.conf`: Display manager settings
- `/etc/systemd/system/`: Systemd services
- `/etc/os-release`: Distribution information

### Customizing the Installer

The Python installer is located at `archlive/airootfs/usr/local/bin/archibald-installer`. You can modify it to add custom features or change the UI.

## Troubleshooting

### Build Fails

If the build fails, ensure:
- You're running as root
- All dependencies are installed
- There's enough disk space in the work directory

### Boot Issues

If the ISO doesn't boot:
- Verify the USB drive was written correctly
- Check BIOS/UEFI settings (enable USB boot, disable secure boot if needed)
- Try different USB ports

### Installer Issues

If the graphical installer fails:
- Check the log output in the installer window
- Try using the command-line archinstall instead
- Ensure you have sufficient disk space

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

### Development Workflow

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## License

Archibald Linux follows the same licensing as Arch Linux. The project is provided as-is for educational and personal use.

## Acknowledgments

- **Arch Linux**: The base distribution
- **archiso**: Tools for building Arch Linux ISOs
- **KDE Plasma**: Desktop environment
- **archinstall**: Arch Linux installer
- **PyQt5**: Python GUI framework

## Contact

- **GitHub**: https://github.com/ArchibaldLinux-Project/Archibald-OS
- **Website**: https://archibald-linux.space

## Status

This project is currently in active development. The ISO is functional but may contain bugs. Use at your own risk.

---

**Note**: Archibald Linux is not affiliated with Arch Linux. It is a derivative distribution built on top of Arch Linux.
