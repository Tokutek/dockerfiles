FROM stackbrew/debian:7.3
RUN apt-get update
#RUN for package in busybox-initramfs dmsetup initramfs-tools initscripts plymouth udev; do echo "$package hold"; done | dpkg --set-selections
RUN apt-get upgrade -y
RUN apt-get install -y build-essential ccache git cmake zlib1g-dev libboost-dev libboost-filesystem-dev libboost-program-options-dev libboost-system-dev libboost-thread-dev libpcap-dev libpcre3-dev libreadline-dev debhelper devscripts buildbot-slave
