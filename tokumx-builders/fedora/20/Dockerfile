FROM fedora:20
RUN yum groupinstall -y 'Development Tools'
RUN yum install -y gcc-c++ rpmdevtools git cmake ccache zlib-devel libpcap-devel pcre-devel buildbot-slave
WORKDIR /data
CMD buildslave start && tail -f twistd.log
