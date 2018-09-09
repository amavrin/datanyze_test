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
* adjust Vagrantfile (lb_address, web_address[1], web_address[2], bridge_if)
* vagrant up

## Checking
* point to http://*lb_address*/ to access app on web1 (default 192.168.1.25)
* point to http://*web1_address*:8080/ to access app on web1 (default 192.168.1.26)
* point to http://*web2_address*:8080/ to access app on web2 (default 192.168.1.26)

## TODOs

- [x] setup Vagrant environment with 3 VMs
- [x] uwsgi installation
- [x] nginx installation from nginx repo
- [x] app deploy
- [x] install and configure haproxy load balancer
- [x] configure access logs location and rotarion
- [ ] configure security updates
## Other issues
- [ ] resolve issue with Let's Encrypt SSL Cert not trusted by apt-key module
- [x] make IP addresses and network interface parameters in Vagrantfile
