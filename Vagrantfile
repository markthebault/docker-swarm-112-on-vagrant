# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

BOXE_IMG="ubuntu/trusty64"
SWARM_MASTER_IP="192.168.33.10"
SWARM_MASTER_PORT=2377
BOX_RAM="768"
NB_NODES=2 #MAX = 9


Vagrant.require_version ">= 1.8.1"

Vagrant.configure(2) do |config|

  config.vm.provision "shell", inline: <<-SHELL
    echo Hello
    uname -r
  SHELL

  config.vm.provider "virtualbox" do |v|
    v.memory = BOX_RAM
  end

  config.vm.define "master" do |master|
      master.vm.box = BOXE_IMG
      master.vm.network "private_network", ip: SWARM_MASTER_IP
      master.vm.hostname = "master"
  end

  (1..NB_NODES).each do |i|
    config.vm.define "node#{i}" do |node1|
        node1.vm.box = BOXE_IMG
        node1.vm.network "private_network", ip: "192.168.33.1#{i}"
        node1.vm.hostname = "node#{i}"
    end
  end


  # Run Ansible from the Vagrant Host
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.groups = {
      "nodes" => ["node[1:#{NB_NODES}]"],
      "masters" => ["master"],
      "all_groups:children" => ["masters", "nodes"],


      "nodes:vars" => {
        "SWARM_MASTER_IP" => SWARM_MASTER_IP,
        "SWARM_MASTER_PORT" => SWARM_MASTER_PORT},
      "masters:vars" => {
        "SWARM_MASTER_IP" => SWARM_MASTER_IP,
        "SWARM_MASTER_PORT" => SWARM_MASTER_PORT}
    }
  end
end
