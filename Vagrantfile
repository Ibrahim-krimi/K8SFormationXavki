# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # Définir le fournisseur VirtualBox pour toutes les VMs
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus = 2
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

  # Définir la VM kubmaster
  config.vm.define "kubmaster" do |kub|
    kub.vm.box = "bento/ubuntu-20.04"
    kub.vm.hostname = "kubmaster"
    kub.vm.provision "docker"
    kub.vm.box_url = "bento/ubuntu-20.04"
    kub.vm.synced_folder ".", "/vagrant", type: "rsync"
    kub.vm.network :private_network, ip: "192.168.56.101"
  end

  # Définir la VM kubnode
  config.vm.define "kubnode" do |kubnode|
    kubnode.vm.box = "bento/ubuntu-20.04"
    kubnode.vm.hostname = "kubnode"
    kubnode.vm.provision "docker"
    kubnode.vm.box_url = "bento/ubuntu-20.04"
    kubnode.vm.network :private_network, ip: "192.168.56.102"
    kubnode.vm.synced_folder ".", "/vagrant", type: "rsync"
  end

end
