# [NixOS](https://nixos.org/) on the [Raspberry Pi Zero W](https://www.raspberrypi.com/products/raspberry-pi-zero-w/)

## Configuration
Copy the files from the `template` directory to the root of the repository and edit to your requirements.

## Building
```bash
nix-build \
    -I nixpkgs=https://github.com/NixOS/nixpkgs/archive/refs/tags/24.11.tar.gz # nixos 24.11 on 2025-03-07
```

## Flashing
```bash
# set correct path for SD card
export SD_CARD=/dev/sda
# inflate image and write to SD card
zstd -dcf result/sd-image/*.img.zst | sudo dd status=progress bs=64k iflag=fullblock oflag=direct of=$SD_CARD && sync && sudo eject $SD_CARD
```

## Attribution
- inspired by [**illegalprime**/nixos-on-arm](https://github.com/illegalprime/nixos-on-arm)
- big thanks to **sternenseemann** for helping me with cross compilation
