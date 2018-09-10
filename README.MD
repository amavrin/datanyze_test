# Datanyze test

## Description
Vagrantfile sets up 3 VM using ubuntu/trusty64 (Ubuntu 14.04) vagrant base box:
* **lb** - load balancer (haproxy)
* **web1** and **web2** - app servers (nginx + uwsgi)

Ansible configuration, files and templates are located under the `provisioning/` directory.
Main playbook is `provisioning/main.yml` .
Roles are under `provisioning/roles/` .

## Prerequisites
* ansible installed
* virtualbox installed
* vagrant installed
* Internet connection

## Things to consider
* using 'public_network' inside virtual box with 192.168.1 network in bridged mode so
  * choose IP for lb, web1 and web2 **on the same subnet as your host's interface**, otherwise VM would not be accessible; other option is to forward some port on 127.0.0.1 (say 9991) to lb's :80 with virtualbox via NAT interface and access lb with http://127.0.0.1:9991/ (but it is not on by default)
  * be careful with IP addressing not to make conflicts with existing IPs in your subnet
* using eth0 as bridge interface; if yours is different, change it in Vagrantfile

## Usage
* adjust Vagrantfile variables `lb_address`, `web_address[1]`, `web_address[2]`, `bridge_if` if necessary; defaults are 192.168.1.25, 192.168.1.26, 192.168.1.27 and "eth0", respectively;
* execute `vagrant up`

## Checking
* point to http://x.x.x.x/ where x.x.x.x is lb's IP to access app via load balancer (default is http://192.168.1.25/ )
* point to http://y.y.y.y:8080/ to check app on web1/web2, where y.y.y.y is web1's or web2's IP (defaults are http://192.168.1.26:8080/ for web1 and http://192.168.1.27:8080/ for web2)
