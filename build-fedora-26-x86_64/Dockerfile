FROM            fedora:26

## System upgrade

## Legato dependencies
RUN ( \
        dnf -y --nogpgcheck \
               install vim expect \
               make cmake gcc-c++ coreutils curl fakeroot sed git-core gawk unzip bzip2 wget diffstat \
               python python-jinja2 python-pip python-pyparsing python-beautifulsoup \
               bison flex chrpath gmp mpfr readline libtool libxml2 perl-libxml-perl m4 scons \
               ninja-build clang autoconf doxygen graphviz libcurl-devel zlib-devel bzip2-devel \
               openssl-devel \
    )

## UTF8 support
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US:en
ENV LC_ALL en_US.UTF-8

