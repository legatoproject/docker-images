FROM            i686/ubuntu:14.04

## Workaround 'Failed to connect to socket /com/ubuntu/upstart: Connection refused'
RUN ( \
        dpkg-divert --local --rename --add /sbin/initctl && \
        ln -s /bin/true /sbin/initctl \
    )

## System upgrade
RUN ( \
        apt-get update && \
        apt-get -y -q autoclean && \
        apt-get -y -q autoremove \
    )


        #apt-get upgrade -y -q && \
        #apt-get dist-upgrade -y -q && \

## Legato dependencies
RUN ( \
        apt-get --yes --assume-yes install vim expect-dev \
                                           build-essential cmake coreutils curl fakeroot sed git-core gawk unzip wget diffstat \
                                           python python-jinja2 python-pip python-pyparsing python-pysqlite2 python-beautifulsoup \
                                           bison flex chrpath libgmp3-dev libmpfr-dev libreadline6-dev libtool libxml2-dev \
                                           libxml-libxml-perl m4 scons clang ninja-build autoconf pkg-config doxygen graphviz \
                                           libcurl4-gnutls-dev zlib1g-dev libbz2-dev libssl-dev && \
        apt-get remove --yes --assume-yes ccache && \
        apt-get clean \
    )

## UTF8 support
RUN locale-gen en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

