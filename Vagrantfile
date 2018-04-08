# -*- mode: ruby -*-
# vi: set ft=ruby :

$nodes = 4
$network_plugin = "flannel"

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  (1..$nodes).each do |i|
	config.vm.define vm_name = "node-#{i}"  do |config |
		config.vm.hostname = vm_name
  		config.vm.network "private_network", type: "dhcp"
  		
		# Forwarded ports
		# config.vm.network "forwarded_port", guest: 6443, host: 8080, host_ip: "0.0.0.0"
  		
		# Shraed dives
		#config.vm.synced_folder "./shared", "/shared"
  		config.vm.provider "virtualbox" do |vb|
    			vb.memory = "32024"
     			vb.cpus = 4
  		end
  		config.vm.provision "shell", inline: <<-SHELL
    			swapoff -a
  		SHELL
	end
 end
end
