FROM blalor/centos
RUN yum groupinstall -y 'Development Tools'
RUN curl http://people.centos.org/tru/devtools-1.1/devtools-1.1.repo -o /etc/yum.repos.d/devtools-1.1.repo
RUN yum install -y devtoolset-1.1 rpmdevtools git cmake28 ccache zlib-devel libpcap-devel pcre-devel
