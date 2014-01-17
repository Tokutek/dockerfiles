FROM base/arch:latest
RUN pacman -Syu --noconfirm
RUN pacman --noconfirm -S base-devel ccache git cmake zlib boost boost-libs ncurses libpcap readline pcre buildbot-slave valgrind
RUN sed -i'' -e 's/!ccache/ccache/' /etc/makepkg.conf
WORKDIR /data
CMD buildslave start && tail -f twistd.log
