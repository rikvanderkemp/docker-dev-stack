# About

A simple (Symfony2) web-dev-stack consisting of:
    
    - NGINX
    - SOLR 6.1.0
    - PHP 7.0.x
    
There are a lot of defaults still, such as nginx.conf. These will be customised when needed, I tend to keep things simple and clean.

# Instructions

## General

Use docker-compose up to start the containers.

## SOLR

The folder `./.data/solr/core/conf` will be linked to the internal container directory `/opt/solr-6.1.0/server/solr/core/conf`.
Therefore, you will need to make sure you symlink a specific SOLR config to this folder before starting.

I usually end-up having, inside the root folder, a `./etc/solr/CORENAME/conf` folder which I symlink to this directory.
