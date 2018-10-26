FROM            ubuntu:16.04

## System upgrade
RUN ( \
        apt-get update && \
        apt-get upgrade -y -q && \
        apt-get dist-upgrade -y -q && \
        apt-get -y install locales && \
        apt-get -y -q autoclean && \
        apt-get -y -q autoremove \
    )

## Legato dependencies
RUN ( \
        apt-get update && \
        apt-get --yes --assume-yes install \
                                           build-essential \
                                           python python-jinja2 cmake \
                                           git subversion libsdl-dev \
                                           diffstat texinfo gawk chrpath wget cpio \
                                           vim zsh bash ninja-build screen sshpass \
                                           bc python-git unzip libxml2-utils gcovr \
                                           libcurl4-gnutls-dev zlib1g-dev libbz2-dev \
                                           bsdiff libssl-dev autoconf automake && \
## Multilib
        apt-get --yes --assume-yes install gcc-multilib g++-multilib && \
## Optional / Extra
        apt-get --yes --assume-yes install jq openjdk-8-jdk gcovr expect-dev clang && \
## Doc generation
        apt-get --yes --assume-yes install python-bs4 python-xmltodict doxygen graphviz \
                                           linkchecker && \
## uLegato dependencies
        apt-get --yes --assume-yes install libtool flex bison gperf libc6-dev-i386 && \
## Platform-specific dependencies
        apt-get --yes --assume-yes install \
                                           python-pycparser python-crypto dos2unix p7zip-rar \
                                           lzop libncurses5-dev libncursesw5-dev lcov && \
        apt-get clean \
    )

## UTF8 support
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

