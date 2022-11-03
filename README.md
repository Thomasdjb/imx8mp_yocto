# IMX8MP HUMMINGBOARD PULSE YOCTO

Routine to build a Yocto image for Solidrun's HummingBoard Pulse

## REQUIREMENTS

To build this image, you will need a Ubuntu 20.04 distribution. You can use directly a host computer running Ubuntu20.04 but if like me you don't have one, you can still build the image using either :

* Virtual Machine (depending on your computer resources this might take a very long time)
* WSL which is much faster

 To be able to use WSL in your Windows environnement you should follow [these](https://learn.microsoft.com/fr-fr/windows/wsl/install) instructions.

Make sure to install an Ubuntu20.04 distros.

Once you have a working Ubuntu20.04 configured, you can start to install the required packages :

```bash
sudo apt update
sudo apt install gawk wget git diffstat unzip texinfo gcc-multilib build-essential chrpath socat cpio python python3 \
python3-pip python3-pexpect xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev \
pylint3 xterm rsync curl zstd lz4 libssl-dev time file g++-multilib python3-distutils liblz4-tool
```
