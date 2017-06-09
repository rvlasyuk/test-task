# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.require_version ">= 1.7.0"

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
	config.vm.box = "ubuntu/trusty64"
	config.ssh.insert_key = false

	config.vm.hostname = "test"
    config.vm.network :private_network, ip: "192.168.13.13"
    config.vm.network "forwarded_port", guest: 80, host: 80, auto_correct: true

    config.vm.define :test do |test|
    end

    config.vm.provision "ansible_local" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "provisioning/playbook.yml"
      ansible.sudo = true
    end
end
