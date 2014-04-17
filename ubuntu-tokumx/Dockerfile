FROM ubuntu:precise
MAINTAINER Leif Walsh <leif.walsh@gmail.com>
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-key 505A7412
RUN echo "deb [arch=amd64] http://s3.amazonaws.com/tokumx-debs $(lsb_release -cs) main" > /etc/apt/sources.list.d/tokumx.list
RUN apt-get update
RUN apt-get install -y tokumx
