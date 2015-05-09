# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
	config.vm.define "server" do |server|
		server.vm.box = "hashicorp/precise64"
		server.vm.hostname = "server"
		server.vm.network "private_network", ip: "192.168.50.15"
		server.vm.provision :ansible do |ansible|
			ansible.playbook = "test.yml"
		end
	end
end
