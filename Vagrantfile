# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    
    config.vm.box = "ubuntu/trusty64"
    config.vm.hostname = "ELK"
    config.vm.network :private_network, ip: "192.168.33.16"
    
    config.ssh.insert_key = false
    
    config.vm.provider :virtualbox do |v|
        v.name = "ELK"
        v.memory = 1024
        v.cpus = 1
        v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        v.customize ["modifyvm", :id, "--ioapic", "on"]
    end
    
    config.vm.provision "ansible" do |ansible|
        ansible.verbose = "v"
        ansible.limit = "all"
        ansible.playbook = "vagrant.yml"
        ansible.inventory_path = "test_hosts"
    end
end
