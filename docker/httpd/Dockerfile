FROM debian:jessie

MAINTAINER Rik van der Kemp <rik@mief.nl>

ENV DEBIAN_FRONTEND noninteractive

# Need wget, update and install
RUN apt-get update && apt-get install wget -y

RUN apt-get update

RUN apt-get install -yq \
        nginx

COPY docker/httpd/etc/nginx/nginx.conf /etc/nginx/nginx.conf
COPY docker/httpd/etc/nginx/sites-available/default /etc/nginx/sites-available/default

ENTRYPOINT ["nginx"]
