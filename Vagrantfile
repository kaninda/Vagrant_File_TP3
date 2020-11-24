# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2004"
  config.vm.hostname = "arnaud-vm"
  config.vm.network "forwarded_port", guest: 8080, host: 80
  config.vm.define "arnaud-wm"
  config.vm.synced_folder "./data", "/vagrant_data"
  config.vm.provider " " do |vb|
    vb.name = "arnaud-wm"
    vb.gui = false
    vb.memory = "2048"
  end

  config.vm.provision "shell", run: "always", inline: <<-SHELL
    echo "HELLO from Vagrantfile"
  SHELL

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "install_docker.yaml"
  end

end
