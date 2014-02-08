FROM stackbrew/ubuntu:12.04
RUN apt-get update
RUN apt-get install -y python-software-properties
RUN add-apt-repository -y ppa:ubuntu-toolchain-r/test
RUN add-apt-repository -y ppa:kalakris/cmake
RUN apt-get update
RUN for package in busybox-initramfs dmsetup initramfs-tools initscripts plymouth udev; do echo "$package hold"; done | dpkg --set-selections
RUN apt-get upgrade -y
RUN apt-get install -y build-essential ccache git gcc-4.8 g++-4.8 cmake zlib1g-dev libboost1.48-dev libboost-filesystem1.48-dev libboost-program-options1.48-dev libboost-system1.48-dev libboost-thread1.48-dev libpcap-dev libpcre3-dev libreadline-dev debhelper devscripts buildbot-slave valgrind
RUN for lang in python ruby java perl; do git clone https://github.com/Tokutek/mongo-$lang-driver; done
RUN apt-get install -y python-dev python-nose
RUN (cd mongo-python-driver; python2 setup.py --with-c-ext install)
RUN apt-get install -y rubygems
RUN REALLY_GEM_UPDATE_SYSTEM=1 gem update --system
RUN gem install bundler
RUN (cd mongo-ruby-driver; bundle install)
# hack to fake a real fuse installation because openjdk-7-jdk needs it
# via https://gist.github.com/henrik-muehe/6155333
RUN apt-get install libfuse2
RUN cd /tmp ; apt-get download fuse
RUN cd /tmp ; dpkg-deb -x fuse_* .
RUN cd /tmp ; dpkg-deb -e fuse_*
RUN cd /tmp ; rm fuse_*.deb
RUN cd /tmp ; echo -en '#!/bin/bash\nexit 0\n' > DEBIAN/postinst
RUN cd /tmp ; dpkg-deb -b . /fuse.deb
RUN cd /tmp ; dpkg -i /fuse.deb
RUN apt-get install -y openjdk-7-jdk maven
RUN (cd mongo-java-driver; mvn test-compile)
RUN apt-get install -y cpanminus libdist-zilla-perl
RUN (cd mongo-perl-driver; (dzil authordeps | cpanm -n) && (dzil listdeps | cpanm -n))
WORKDIR /data
CMD buildslave start && tail -f twistd.log
