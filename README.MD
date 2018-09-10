# Datanyze test

## Description
Vagrantfile sets up 3 VM using ubuntu/trusty64 (Ubuntu 14.04) vagrant base box:
* lb - load balancer (haproxy)
* web1, web2 - app server (nginx + uwsgi)

Ansible configuration, files and templates are located under the provisioning/ directory.
Main playbook is provisioning/main.yml .
Roles are under provisioning/roles/ .

## Prerequisites
* ansible installed
* virtualbox installed
* vagrant installed
* Internet connection

## Things to consider
* using 'public_network' inside virtual box with 192.168.1 network in bridged mode, so be careful with IP addressing
* using eth0 as bridge interface; if yours is different, change it in Vagrantfile

## Usage
* adjust Vagrantfile variables `lb_address`, `web_address[1]`, `web_address[2]`, `bridge_if` if necessary; defaults are 192.168.1.25, 192.168.1.26, 192.168.1.27 and "eth0", respectively.
* execute `vagrant up`

## Checking
* point to http://x.x.x.x/ to access app via load balancer (where x.x.x.x is lb's IP, default http://192.168.1.25/ )
* point to http://y.y.y.y:8080/ to check app on web1/web2 (where y.y.y.y is web1's or web2's IP; defaults are http://192.168.1.26:8080/ for web1, http://192.168.1.27:8080/ for web2)
