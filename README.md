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
sudo locale-gen en_US.utf8
```

*Installing git-repo utility :*

```bash
mkdir ~/bin (this step may not be needed if bin directory already exists)
curl https://storage.googleapis.com/git-repo-downloads/repo > ~/bin/repo
chmod a+x ~/bin/repo
export PATH=~/bin:$PATH
```

*Configure your git credentials :*

```bash
git config --global user.name "Username"
git config --global user.email "user@email.com"
git config --list
```

## Configure your build environnement

*Create your working directory :*

```bash
mkdir imx-yocto-bsp
cd imx-yocto-bsp/
```

*Clone the nxp-imx repository :*

```bash
repo init -u https://github.com/nxp-imx/imx-manifest -b imx-linux-zeus -m imx-5.4.70-2.3.0.xml (branch and manifest were chosen according to the meta-solidrun-imx compatibility)
repo sync
```

*Add the meta-solidrun-imx layer :*

```bash
cd sources/
git clone https://github.com/SolidRun/meta-solidrun-arm-imx8.git -b zeus-imx8mp
cd ../
```

*Configure build directory to run bitbake command :*

```bash
DISTRO=fsl-imx-wayland MACHINE=imx8mpsolidun source imx-setup-release.sh -b build/
```
