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
## Optional / Extra
        apt-get --yes --assume-yes install jq openjdk-8-jdk gcovr expect-dev clang && \
## Doc generation
        apt-get --yes --assume-yes install python-bs4 python-xmltodict doxygen graphviz \
                                           linkchecker && \
## QA dependencies
        apt-get --yes --assume-yes install ruby iputils-ping jq netcat sox libxml2-utils python-lxml \
                                           python-pip libglib2.0-dev xsltproc libtool curl \
                                           python-pytest python-pexpect && \
## uLegato dependencies
        apt-get --yes --assume-yes install libtool flex gperf bison && \
## Platform-specific dependencies
        apt-get --yes --assume-yes install \
                                           python-pycparser python-crypto dos2unix p7zip-rar \
                                           lzop libncurses5-dev libncursesw5-dev lcov && \
## Testbench dependencies
        apt-get --yes --assume-yes install dnsmasq sudo iptables socat openssh-server && \
        apt-get clean \
    )

## Install python dependencies
RUN pip install --upgrade pip
RUN pip install openpyxl
RUN pip install tap.py

## UTF8 support
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

RUN ln -sf bash /bin/sh

