# Archibald Linux - Release Notes

## Version 1.0.0

### What's New

**Desktop Environment**
- KDE Plasma desktop with modern, intuitive interface
- SDDM display manager with autologin support
- Konsole terminal emulator

**Custom Installer**
- New graphical Python installer built with PyQt5
- Multi-threaded installation process
- User-friendly wizard interface
- Complete system configuration options

**System Tools**
- Comprehensive rescue toolkit (clonezilla, ddrescue, testdisk)
- Full filesystem support (ext4, btrfs, xfs, f2fs)
- Advanced partitioning tools (parted, gparted)
- LVM and RAID support

**Networking**
- Modern wireless daemon (iwd)
- VPN support (OpenVPN, OpenConnect)
- Multiple network configuration options

**Virtualization Support**
- Guest agents for QEMU, VirtualBox, VMware, Hyper-V

**Accessibility**
- Screen reader support (espeakup, brltty)
- Audio configuration tools

### System Requirements

- **Architecture**: x86_64
- **RAM**: Minimum 2GB (4GB recommended)
- **Storage**: 8GB minimum for installation
- **Boot**: USB or DVD

### Installation

1. Download the ISO
2. Write to USB: `dd if=archibald.iso of=/dev/sdX bs=4M`
3. Boot from USB
4. Launch installer from desktop
5. Follow the wizard

### Known Issues

- First release - may contain bugs
- Report issues on GitHub

### Download

Get the latest ISO from the [Releases](https://github.com/ArchibaldLinux-Project/Archibald-OS/releases) page.

### Support

- **Documentation**: See [README.md](README.md)
- **Issues**: [GitHub Issues](https://github.com/ArchibaldLinux-Project/Archibald-OS/issues)
- **Website**: https://archibald-linux.space

---

**Built on Arch Linux** | **Powered by KDE Plasma**
