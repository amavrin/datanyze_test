lb_address = "192.168.1.25"
web_address = []
web_address[1] = "192.168.1.26"
web_address[2] = "192.168.1.27"

bridge_if = "eth0"

Vagrant.configure("2") do |config|
 
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory=256
    vb.cpus=1
    vb.check_guest_additions=false
    config.vm.box_check_update=false
    config.vm.box="ubuntu/trusty64"
  end

  (1..2).each do |i|
    config.vm.define "web#{i}" do |node|
      node.vm.network "public_network", ip: web_address[i], bridge: bridge_if
      node.vm.hostname = "web#{i}"
    end
  end

  config.vm.define "lb" do |lb|
    lb.vm.network "public_network", ip: lb_address, bridge: bridge_if
    lb.vm.hostname = "lb"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/main.yml"
    ansible.groups = {
      "web" => ["web[1:2]"]
    }

    ansible.host_vars = {
      "web1" => { "app_listen_addr" => web_address[1] },
      "web2" => { "app_listen_addr" => web_address[2] }
    }
  end

end
