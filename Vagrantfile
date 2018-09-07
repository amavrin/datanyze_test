Vagrant.configure("2") do |config|
 
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory=256
    vb.cpus=1
    vb.check_guest_additions=false
    config.vm.box_check_update=false
    config.vm.box="ubuntu/trusty64"
  end

  config.vm.define "lb" do |lb|
    lb.vm.network "public_network", ip: "192.168.1.25", bridge: "eth0"
    lb.vm.hostname = "lb"
  end

  (1..2).each do |i|
    config.vm.define "web#{i}" do |node|
      node.vm.network "public_network", ip: "192.168.1.#{25+i}", bridge: "eth0"
      node.vm.hostname = "web#{i}"
    end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision/main.yml"
  end

end
