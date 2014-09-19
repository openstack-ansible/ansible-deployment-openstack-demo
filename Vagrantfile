# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|


  config.vm.define "axel07" do |machine|
    machine.vm.box = "ubuntu/trusty64"
    machine.vm.network :private_network, ip: "10.1.0.2",
                       :netmask => "255.255.0.0"
    machine.vm.hostname = "axel07"
    machine.vm.provider :virtualbox do |v| 
      v.customize ["modifyvm", :id, "--memory", 1024]
    end
  end

  config.vm.define "maia01" do |machine|
    machine.vm.box = "box-cutter/centos64"
    machine.vm.network :private_network, ip: "10.1.0.3",
                       :netmask => "255.255.0.0"
    machine.vm.hostname = "maia01"
    machine.vm.provider :virtualbox do |v| 
      v.customize ["modifyvm", :id, "--memory", 1024]
    end
  end

  #config.vm.provision "ansible" do |ansible|
  #  ansible.playbook = "getroles.yml"
  #end

  #config.vm.provision "ansible" do |ansible|
  #  ansible.playbook = "site.yml"
  #end

end
