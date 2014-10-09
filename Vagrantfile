# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|


  config.vm.define "controller" do |machine|
    machine.vm.box = "ubuntu/trusty64"
    machine.vm.network :private_network, ip: "10.1.0.2",
                       :netmask => "255.255.0.0"
    machine.vm.hostname = "controller"
    machine.vm.provider :virtualbox do |v| 
      v.customize ["modifyvm", :id, "--memory", 1280]
    end
  end

  #config.vm.define "compute-01" do |machine|
  #  machine.vm.box = "ubuntu/trusty64"
  #  machine.vm.network :private_network, ip: "10.1.0.3",
  #                     :netmask => "255.255.0.0"
  #  machine.vm.hostname = "compute-01"
  #  machine.vm.provider :virtualbox do |v| 
  #    v.customize ["modifyvm", :id, "--memory", 1280]
  #  end
  #end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "getreqs.yml"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
  end

end
