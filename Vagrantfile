# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

	#Ansible-Node01
	config.vm.define:"ansible-node01" do |cfg|
	   cfg.vm.box = "centos/7"
	   cfg.vm.provider:virtualbox do |vb|
		 vb.name="Ansible-Node01"
		 vb.customize ["modifyvm", :id, "--cpus",1]
		 vb.customize ["modifyvm", :id, "--memory",512]
	   end
	   cfg.vm.host_name="ansible-node01"
	   cfg.vm.synced_folder ".", "/vagrant", disabled: true
	   cfg.vm.network "public_network", ip: "192.168.1.61"
	   cfg.vm.network "forwarded_port", guest: 22, host: 19261, auto_correct: false, id: "ssh"
	end
	
	#Ansible-Node02	 
	config.vm.define:"ansible-node02" do |cfg|
	   cfg.vm.box = "centos/7"
	   cfg.vm.provider:virtualbox do |vb|
		 vb.name="Ansible-Node02"
		 vb.customize ["modifyvm", :id, "--cpus",1]
		 vb.customize ["modifyvm", :id, "--memory",512]
	   end
	   cfg.vm.host_name="ansible-node02"
	   cfg.vm.synced_folder ".", "/vagrant", disabled: true
	   cfg.vm.network "public_network", ip: "192.168.1.62"
	   cfg.vm.network "forwarded_port", guest: 22, host: 19262, auto_correct: false, id: "ssh"
	end
	
	#Ansible-Server
	config.vm.define:"ansible-server" do |cfg|
	   cfg.vm.box = "centos/7"
	   cfg.vm.provider:virtualbox do |vb|
		 vb.name="Ansible-Server"
	   end
	   cfg.vm.host_name="ansible-server"
	   cfg.vm.synced_folder ".", "/vagrant", disabled: true
	   cfg.vm.network "public_network", ip: "192.168.1.60"
	   cfg.vm.network "forwarded_port", guest: 22, host: 19260, auto_correct: false, id: "ssh"
	   cfg.vm.provision "shell", path: "bootstrap.sh"
	   cfg.vm.provision "file", source: "ansible_env.yml", destination: "ansible_env.yml"
	   cfg.vm.provision "shell", inline: "ansible-playbook ansible_env.yml"
	   cfg.vm.provision "shell", path: "ssh_auth.sh", privileged: false
	end
	
  end