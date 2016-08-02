FROM debian:jessie

MAINTAINER Rik van der Kemp <rik@mief.nl>

ENV DEBIAN_FRONTEND noninteractive


RUN echo 'deb http://ftp.debian.org/debian jessie-backports main' >> /etc/apt/sources.list

# Need wget, update and install
RUN apt-get update && apt-get install wget -y


RUN apt-get install -yq \
     openjdk-8-jre

RUN cd /opt && wget http://apache.cs.uu.nl/lucene/solr/6.1.0/solr-6.1.0.tgz
# use below for local testing
#COPY docker/solr/solr-6.1.0.tgz /opt/solr-6.1.0.tgz
RUN cd /opt && tar xvf solr-6.1.0.tgz

EXPOSE 8983

CMD /opt/solr-6.1.0/bin/solr start -f