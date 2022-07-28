# -*- mode: ruby -*-
# vi: set ft=ruby :

$server_config = <<-SCRIPT

systemctl stop firewalld
systemctl disable firewalld

sudo echo "192.168.42.110  ayoub" >> /etc/hosts

SCRIPT

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "generic/centos8"
    config.vm.synced_folder ".", "/vagrant"

    config.vm.define "ayoub" do |server|
        server.vm.hostname = "ayoub"
        server.vm.network "private_network", ip: "192.168.42.110"
        server.vm.provider :virtualbox do |v|
            v.name = "ayoub"
            v.memory = 2000
            v.cpus = 1
        end
        # server.vm.provision "shell", inline: $server_config
        server.vm.provision "ansible" do |ansible| ansible.playbook = "provisioning/playbook.yaml"
        end

    end
    
end