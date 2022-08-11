FROM ubuntu:20.04

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive TZ=Etc/UTC \
    apt-get install -y \
        sudo time git-core subversion build-essential gcc-multilib \
        libncurses5-dev zlib1g-dev gawk flex gettext wget unzip \
        grep rsync python3 python3-distutils && \
    apt-get clean

RUN useradd -m openwrt && \
    echo 'openwrt ALL=NOPASSWD: ALL' > /etc/sudoers.d/openwrt

USER openwrt
WORKDIR /home/openwrt

RUN git clone git://git.openwrt.org/openwrt/openwrt.git -b openwrt-22.03 && \
    openwrt/scripts/feeds update -a
