FROM finalduty/archlinux:weekly

# Disable space checking
RUN sed -i 's/CheckSpace/#CheckSpace/g' /etc/pacman.conf

# Update
RUN ( pacman -Syu --noconfirm && pacman -Scc --noconfirm )
RUN ( \
        pacman -S --noconfirm make expect cmake gcc bison flex clang ninja autoconf automake \
                              python2 python2-jinja python2-beautifulsoup4 doxygen git graphviz pkg-config && \
        pacman -Scc --noconfirm \
    ) > /dev/null

