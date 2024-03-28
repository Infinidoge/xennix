# XenNix: A NixOS-based Xen Hypervisor distribution
### Please see the full [proposal](./proposal.md)!

This is currently a proposed Google Summer of Code project for the NixOS foundation.

## Goals

### Primary

- Update and maintain Xen-related packages
  - `grub2_xen`, `grub2_pvgrup_image`
  - `qemu_xen`
  - `xenPackages` (`xen` and `light`/`slim`/`full` variants)
  - `xe-guest-utilities`
  - Xen-related `ocamlPackages`
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
