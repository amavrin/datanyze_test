# Datanyze test

## Description
Deploy 3 VM:
* lb - load balancer
* web1, web2 - app server

## Requirements
* ansible installed (>2.0)
* virtualbox installed (>5.0)
* vagrant installed (>2.0)

## Things to consider
* using ubuntu/trusty64 vagrant base box
* using 'public_network' inside virtual box
* using 192.168.1 network in bridged mode, so be careful with IP addressing
* lb's address is 192.168.1.25, web1 - 192.168.1.26, web2 - 192.168.1.27
* using eth0 as bridge interface; if your is different, make changes in Vagrantfile

## Usage
vagrant up

## Checking
* point to http://192.168.1.26:8080 to access app on web1
* point to http://192.168.1.27:8080 to access app on web2

## TODOs

- [x] setup Vagrant environment with 3 VMs
- [x] uwsgi installation
- [x] nginx installation from nginx repo
- [x] app deploy
- [ ] install and configure haproxy load balancer
- [ ] configure access logs location and rotarion
- [ ] configure security updates
