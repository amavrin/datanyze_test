# Datanyze test

## Description
3 VM with ubuntu/trusty64 vagrant base box:
* lb - load balancer (haproxy)
* web1, web2 - app server (nginx + uwsgi)

## Prerequisites
* ansible installed
* virtualbox installed
* vagrant installed
* Internet connection available

## Things to consider
* using 'public_network' inside virtual box with 192.168.1 network in bridged mode, so be careful with IP addressing
* using eth0 as bridge interface; if your is different, change it in Vagrantfile

## Usage
* adjust Vagrantfile (lb_address, web_address[1], web_address[2], bridge_if); default is 192.168.1.25, 192.168.1.26, 192.168.1.27 and "eth0", respectively.
* vagrant up

## Checking
* point to http://x.x.x.x/ to access app via load balancer (where x.x.x.x is lb's IP, default 192.168.1.25)
* point to http://y.y.y.y:8080/ to check app on web1/web2 (where y.y.y.y is web1's or web2's IP; default web1's IP is 192.168.1.26, web2's - 192.168.1.27)
