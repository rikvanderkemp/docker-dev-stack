FROM debian:jessie

MAINTAINER Rik van der Kemp <rik@mief.nl>

ENV DEBIAN_FRONTEND noninteractive

# Need wget, update and install
RUN apt-get update && apt-get install wget -y

# Add dotdeb
RUN echo 'deb http://packages.dotdeb.org jessie all' >> /etc/apt/sources.list  && echo 'deb-src http://packages.dotdeb.org jessie all' >> /etc/apt/sources.list

# Dotdeb requires apt key, get it and add
RUN wget http://www.dotdeb.org/dotdeb.gpg && apt-key add dotdeb.gpg

RUN apt-get update

RUN apt-get install -yq \
		php7.0  \ 
		php7.0-fpm  \
		php7.0-cli  \
		php7.0-curl \
		php7.0-gd \ 
		php7.0-intl \
		php7.0-mcrypt \ 
		php7.0-mysql \ 
		php7.0-xml \
		php7.0-xdebug

# https://hub.docker.com/r/phpdockerio/php7-fpm/~/dockerfile/
RUN sed -i "/listen = .*/c\listen = [::]:9000" /etc/php/7.0/fpm/pool.d/www.conf \
     && sed -i "/;access.log = .*/c\access.log = /proc/self/fd/2" /etc/php/7.0/fpm/pool.d/www.conf \
        && sed -i "/;clear_env = .*/c\clear_env = no" /etc/php/7.0/fpm/pool.d/www.conf \
        && sed -i "/;catch_workers_output = .*/c\catch_workers_output = yes" /etc/php/7.0/fpm/pool.d/www.conf \
        && sed -i "/pid = .*/c\;pid = /run/php/php7.0-fpm.pid" /etc/php/7.0/fpm/php-fpm.conf \
        && sed -i "/;daemonize = .*/c\daemonize = no" /etc/php/7.0/fpm/php-fpm.conf \
        && sed -i "/error_log = .*/c\error_log = /proc/self/fd/2" /etc/php/7.0/fpm/php-fpm.conf \
    && usermod -u 1000 www-data

EXPOSE 9000

CMD /usr/sbin/php-fpm7.0 -F