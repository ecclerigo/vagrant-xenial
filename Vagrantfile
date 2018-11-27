# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  # config.vm.box_check_update = false

  # Network 
  # config.vm.network "forwarded_port", guest: 80, host: 8080
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  config.vm.network "private_network", ip: "192.168.33.40"
  # config.vm.network "public_network"

  # Folder
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider
   config.vm.provider "virtualbox" do |vb|
     # Display the VirtualBox GUI when booting the machine
     vb.customize ["modifyvm", :id, "--cpuexecutioncap", "90"]
     vb.memory = "2048"
     vb.cpus = 2
   end

  # Provisioning 
   config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install -y software-properties-common
     apt-add-repository ppa:ansible/ansible
     apt-get update
     apt-get install -y ansible
   SHELL
   config.vm.provision "ansible" do |ansible|
     ansible.playbook = "provisioning/playbook.yml"
   end


end
