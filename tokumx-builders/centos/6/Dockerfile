FROM blalor/centos
RUN yum groupinstall -y 'Development Tools'
RUN curl http://people.centos.org/tru/devtools-1.1/devtools-1.1.repo -o /etc/yum.repos.d/devtools-1.1.repo
RUN yum install -y devtoolset-1.1 rpmdevtools git cmake28 ccache zlib-devel libpcap-devel pcre-devel python-devel python-pip
RUN ln -sn cmake28 /usr/bin/cmake
RUN scl enable devtoolset-1.1 'pip install buildbot-slave'
WORKDIR /data
CMD scl enable devtoolset-1.1 'buildslave start' && tail -f twistd.log
