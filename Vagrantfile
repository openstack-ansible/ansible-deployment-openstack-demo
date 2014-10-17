# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|


  #config.vm.define "network" do |machine|
  #  machine.vm.box = "ubuntu/trusty64"
  #  machine.vm.network :private_network, ip: "10.1.0.3",
  #                     :netmask => "255.255.0.0"
  #  machine.vm.network :private_network, ip: "10.2.0.3",
  #                     :netmask => "255.255.0.0"
  #  machine.vm.hostname = "network"
  #  machine.vm.provider :virtualbox do |v| 
  #    v.customize ["modifyvm", :id, "--memory", 2048]
  #    v.customize ["modifyvm", :id, "--nicpromisc2", "allow-vms"]
  #  end
  #end

  config.vm.define "compute-001" do |machine|
    machine.vm.box = "ubuntu/trusty64"
    machine.vm.network :private_network, ip: "10.1.0.4",
                       :netmask => "255.255.0.0"
    machine.vm.hostname = "compute-001"
    machine.vm.provider :virtualbox do |v| 
      v.customize ["modifyvm", :id, "--memory", 2048]
    end
  end

  config.vm.define "controller" do |machine|
    machine.vm.box = "ubuntu/trusty64"
    machine.vm.network :private_network, ip: "10.1.0.2",
                       :netmask => "255.255.0.0"
    machine.vm.network :private_network, ip: "10.2.0.2",
                       :netmask => "255.255.0.0"
    machine.vm.hostname = "controller"
    machine.vm.provider :virtualbox do |v| 
      v.customize ["modifyvm", :id, "--memory", 2048]
      v.customize ["modifyvm", :id, "--nicpromisc3", "allow-vms"]
    end

    machine.vm.provision "ansible" do |ansible|
      ansible.playbook = "getreqs.yml"
      ansible.inventory_path = "development.ini"
      ansible.limit = 'all'
    end

    machine.vm.provision "ansible" do |ansible|
      ansible.playbook = "prep.yml"
      ansible.inventory_path = "development.ini"
      ansible.limit = 'all'
    end

    machine.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy.yml"
      ansible.inventory_path = "development.ini"
      ansible.groups = {
        "network" => ["controller"],
      }
      ansible.limit = 'all'
    end

    machine.vm.provision "ansible" do |ansible|
      ansible.playbook = "test.yml"
      ansible.inventory_path = "development.ini"
      ansible.limit = 'all'
    end

  end

end
