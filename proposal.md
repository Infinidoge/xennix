# XenNix: A NixOS-based Xen Hypervisor distribution

### [GitHub](https://github.com/Infinidoge/xennix), Length: Medium (175 hours), Rating: Medium (Subject to debate)

XenNix aims to be a distribution of the Xen Hypervisor, similar to XenServer and XCP-ng, with NixOS as dom0 instead of CentOS or other distributions.
The benefit of this would be that the priviledged domain could be setup and managed declaratively and reproducibly, allowing for full knowledge and transparency of how dom0 is configured and the ability to reproduce it later.
Nixpkgs already has some infrastructure for doing this, however it is severely out of date, not supporting UEFI.
Additionally, XenNix has the goal of creating a full configured 'base' distribution, making dom0 minimal and secure by default instead of including unnecessary packages.

## Goals

### Primary

- Update and maintain Xen-related packages
  - `grub2_xen`, `grub2_pvgrup_image`
  - `qemu_xen`
  - `xenPackages` (`xen` and `light`/`slim`/`full` variants)
  - `xe-guest-utilities`
  - Xen-related `ocamlPackages`\
    (`mirage-xen`, `netchannel`, `vchan`, `xenstore`, `xenstore-tool`, `xenstore_transport`)
- Update and improve the Xen dom0 handling in Nixpkgs
  - Support UEFI
- Package Xen-related software
  - Xen Orchestra (Including setup module)
- Create a base set of configurable modules for a ready-made distribution
  - Minimize unnecessary packages where possible
  - Automatically create and setup relevant networking
  - Make storage locations as configurable as possible
  - As automated as possible by default, with opt-out available for manual setup 
- Installer
  - Partitions disks ready-made for setup
  - Supports partitioning via disko
  - Calls nixos-install

### Extra

- Support non-GRUB bootloaders
- Support declaring domU domains declaratively, in addition to imperatively
  - Disallow modifying domains made declaratively?
  - Extra options for NixOS domUs, similar to existing containers infrastructure
- Drop-in replacement XCP-ng
  - Could do an infect strategy
- dom0-hosted local binary cache for domU
  - Could run over local network
  - Xen-specific store protocol?
- [Impermanence](https://github.com/nix-community/impermanence) integration
  - tmpfs, zfs, and btrfs presets

## Aspirational

- Shared Nix store between dom0 and NixOS domUs
  - Hard to make secure
  - Can things built by the VMs be trusted in dom0 space?
  - Potential "request shared" over XenBus/XenStore?
  - See local binary cache above
- CI tested/vetted Nixpkgs pins for stable deployments
- Netboot support
- Secure boot via [lanzaboote](https://github.com/nix-community/lanzaboote)

## Required Skills

- Nix/NixOS
  - Nix packaging
  - Nix language
  - Module system
- Xen Hypervisor setup/usage

## Resources

- [Xen Project website](https://xenproject.org/)
- [Xen Project wiki](https://wiki.xenproject.org/)
  - [Software Overview](https://wiki.xenproject.org/wiki/Xen_Project_Software_Overview)
- [Arch Wiki page on running Xen](https://wiki.archlinux.org/title/Xen)
- [Gentoo Wiki page on running Xen](https://wiki.gentoo.org/wiki/Xen)

## Related Work

- [XCP-ng](https://xcp-ng.org/), a Xen distribution based on CentOS
  - [Architecture](https://xcp-ng.org/docs/architecture.html)
- [Qubes OS](https://www.qubes-os.org), an operating system based on using Xen for isolating software
  - [Architecture](https://www.qubes-os.org/doc/architecture/)
- [Nekroze/vms.nix](https://github.com/Nekroze/vms.nix)

## Potential Mentors

- None yet

# Personal Information

## Contact Info

- Name: Infinidoge, [redacted in public draft]
- Phone: `[redacted in public draft]`
- Email: `[redacted in public draft]`, `infinidoge@inx.moe`\
  (Any email @inx.moe will reach to me)\
  Prefer the former for personal/work matters, prefer the latter for code, etc. matters.
- Matrix: `@infinidoge@matrix.org`
- Website: https://inx.moe
- GitHub: https://github.com/Infinidoge

## About Me

I am a student at Purdue University studying computer science, with a personal focus on programming languages, operating systems, and software engineering.
I love computers and computing as a whole, so I have a very broad interest in the field overall, with few exceptions.
I have programmed for the vast majority of my life, having started with the very basics when I was young, and later being propelled forward with encouragement from my middle school programming teacher.
I learned about Nix sometime in 2020, and in 2021 I finally decided to switch everything over.
This was the start of my NixOS configuration, which started with the DevOS template based on the Digga library. Over 1,700 commits and several thousand lines of code later, I've grown to love the ecosystem, and I spend a (perhaps unhealthily) large amount of time thinking and using Nix.

## Past/Current Projects

In the Nix ecosystem, my most notable project has been [`nix-minecraft`](https://github.com/Infinidoge/nix-minecraft).
`nix-minecraft` packages a variety of software for hosting Minecraft servers, as well as a module to host multiple Minecraft servers at once (as opposed to the single-server limitation of the module in Nixpkgs).
It taught me a lot about project management and organization, as well as how to organize a Nix-based project to make it easier to maintain.
Learning how to better make use of Nix's laziness and recursion to easily inject dependencies into packages ([found here](https://github.com/Infinidoge/nix-minecraft/blob/25992bbf8fe0ec70b7afa2f26217f97fbb9c8bb4/flake.nix#L21-L24)).

For NixOS in particular, my greatest work is by far my NixOS configuration, [Universe](https://github.com/Infinidoge/universe), which has the configuration for my entire hoard of computers, large and small.
To help me with it, I've also written my own CLI in Rust, [universe-cli](https://github.com/Infinidoge/universe-cli).
This was born out of my move away from the Digga library in my configuration, and I was in need of a replacement for Bud, which was the shortcut tool from Digga that I used previously.

Another project I am particularly proud of is my recently-named [Xenia operating system for i386](https://github.com/Infinidoge/xenia-i386).
This is a 32-bit operating system born out of an operating systems class I took at my previous university.
When we were first given the project, it was built in an Ubuntu 16.04 LTS VM, and refused to build outside of that environment. 
I undertook the effort to learn how to get a cross-compiler from Nixpkgs and refactor the project to build it better and more properly, instead of hammering a system compiler into building a kernel.
Having gotten hooked on it, I spent a lot of time developing the kernel and working on it, eventually making a kernel-space sorting algorithm visualizer as a combination project for another class.
This project was cool enough to land a meeting with the department head to show him the project and talk about my experience with the course, and what I felt could be improved.

## Additional Notes

This is a project that I have been thinking about for quite a while, and I am personally interested in doing it regardless of if it is a Google Summer of Code project or not.
I hope it will be a GSoC project, since it will give me the opportunity to both have a mentor to guide me and be a good learning experience in dedicating myself to open source development.
