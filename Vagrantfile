# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "bento/centos-7.2"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 1
  end

  config.vm.synced_folder "/home/sukach/docs/Work/murka/crm", "/code"

  config.ssh.insert_key = false
  config.ssh.forward_agent = true

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "application.yml"
  end

  config.vm.network "forwarded_port", guest: 80, host: 8000
  config.vm.network "forwarded_port", guest: 15672, host: 15672
  config.vm.network "private_network", ip: "192.168.50.4"
end
