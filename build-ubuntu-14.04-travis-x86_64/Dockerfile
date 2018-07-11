FROM            ubuntu:14.04

## System upgrade
RUN ( \
        apt-get update && \
        apt-get upgrade -y -q && \
        apt-get dist-upgrade -y -q && \
        apt-get -y -q autoclean && \
        apt-get -y -q autoremove \
    )

## Legato dependencies
RUN ( \
        echo "deb http://ppa.launchpad.net/openjdk-r/ppa/ubuntu trusty main" >> /etc/apt/sources.list && \
        apt-get update && \
        apt-get --yes --assume-yes install \
                                           build-essential \
                                           python python-jinja2 cmake \
                                           git subversion libsdl-dev \
                                           diffstat texinfo gawk chrpath wget cpio \
                                           vim zsh bash ninja-build screen sshpass \
                                           bc python-git unzip libxml2-utils \
                                           libcurl4-gnutls-dev zlib1g-dev libbz2-dev \
                                           bsdiff libssl-dev autoconf automake && \
## Optional / Extra
        apt-get --yes --force-yes install jq openjdk-8-jdk gcovr expect-dev && \
## Doc generation
        apt-get --yes --assume-yes install python-bs4 doxygen graphviz && \
        apt-get clean \
    )

## Clang
ENV CLANG_VERSION 5.0.1
ENV CLANG_DIR "/usr/local/clang-${CLANG_VERSION}"
ENV PATH "${CLANG_DIR}/bin:${PATH}"
RUN ( \
        wget --quiet -O clang.tar.xz http://releases.llvm.org/${CLANG_VERSION}/clang+llvm-${CLANG_VERSION}-x86_64-linux-gnu-ubuntu-14.04.tar.xz && \
        mkdir -p ${CLANG_DIR} && \
        tar Jxf clang.tar.xz --strip 1 -C${CLANG_DIR} && \
        rm clang.tar.xz && \
        echo "PATH=${PATH}" > /etc/environment \
    )

## UTF8 support
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

