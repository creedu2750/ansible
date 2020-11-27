# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
	config.vm.define:"ansible-server" do |cfg|
	   cfg.vm.box = "centos/7"
	   cfg.vm.provider:virtualbox do |vb|
		 vb.name="Ansible-Server"
	   end
	   cfg.vm.host_name="ansible-server"
	   cfg.vm.synced_folder ".", "/vagrant", disabled: true
	   cfg.vm.network "public_network", ip: "192.168.1.50"
	   cfg.vm.network "forwarded_port", guest: 22, host: 19250, auto_correct: false, id: "ssh"
	   cfg.vm.provision "shell", path: "bootstrap.sh"
	   cfg.vm.provision "file", source: "ansible_env.yml", destination: "ansible_env.yml"
	   cfg.vm.provision "shell", inline: "ansible-playbook ansible_env.yml"
	end
  end