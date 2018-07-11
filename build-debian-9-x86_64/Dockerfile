FROM            debian:9

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
        apt-get --yes --assume-yes install jq gcovr expect-dev clang && \
## Doc generation
        apt-get --yes --assume-yes install python-bs4 python-xmltodict doxygen graphviz && \
        apt-get clean \
    )


## UTF8 support
RUN apt-get -y install locales && apt-get clean
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

