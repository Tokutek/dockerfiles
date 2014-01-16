FROM base/arch:latest
RUN pacman -Syu --noconfirm
RUN pacman --noconfirm -S base-devel ccache git cmake zlib boost boost-libs ncurses libpcap readline pcre buildbot-slave
WORKDIR /data
CMD buildslave start && tail -f twistd.log
