
<h1 align="center">
  <br>
  <img src="https://i.ibb.co/LYYJzJC/logo.jpg" alt="Markdownify" width="2048">
  <br>
  GrassKernel
  <br>
</h1>

<h4 align="center">A custom kernel for the Exynos9611 devices.</h4>

<p align="center">
  <a href="#key-features">Key Features</a> •
  <a href="#how-to-build">How To Build</a> •
  <a href="#how-to-flash">How To Flash</a> •
  <a href="#credits">Credits</a>
</p>

## Key Features

* Disable Samsung securities, debug drivers, etc modifications
* Checkout and rebase against Android common kernel source, Removing Samsung additions to drivers like ext4,f2fs and more
* Compiled with bleeding edge Clang 19, with full LLVM binutils, LTO (Link time optimization) and -O3  
* Import Erofs, Incremental FS, BinderFS and several backports.
* Supports DeX touchpad for corresponding OneUI ports that have DeX ported.
* Lot of debug codes/configuration Samsung added are removed.
* Added [wireguard](https://www.wireguard.com/) driver, an open-source VPN driver in-kernel
* Added [KernelSU](https://kernelsu.org/)

## How To Build

You will need ubuntu, git, around 8GB RAM and bla-bla-bla...

```bash
# Install dependencies
$ sudo apt install -y bash git make libssl-dev curl bc pkg-config m4 libtool automake autoconf

# Clone this repository
$ git clone https://github.com/Gojikovi/kernel_samsung_universal9611

# Go into the repository
$ cd kernel_samsung_universal9611

# Install toolchain
# You could try any clang/LLVM based toolchain, however I use WeebX clang
# See the intructions: https://github.com/XSans0/WeebX-Clang

# Building kernel is simple, a python script is provided.
# Options inside parenthesis are optional, Parenthesis' with | between 
# means you have to provide one of those options inside.
$ python build_kernel.py (--aosp|--oneui) --target=m31 (--no-ksu) (--allow-dirty)
```

After build the image of the kernel will be in out/arch/arm64/boot/Image

## How To Flash

After a successful build, you can see the scripts/packaging/Grass*.zip archive.
This is your kernel. Just flash it via TWRP or adb sideload

## Credits

- [roynatech2544](https://github.com/roynatech2544)
- [Samsung Open Source](https://opensource.samsung.com/)
- [Android Open Source Project](https://source.android.com/)
- [The Linux Kernel](https://www.kernel.org/)

# Note

⚠️ This project is under testing
