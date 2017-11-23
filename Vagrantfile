# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "debian/jessie64"

  config.vm.network "forwarded_port", guest: 80, host: 8081
  config.vm.network "forwarded_port", guest: 5060, host: 5061, protocol: 'udp'

  # Freeswitch
  #config.vm.define "freeswitch" do |freeswitch|
  #  freeswitch.vm.hostname = "freeswitch-mw.dev"
  #  freeswitch.vm.network :public_network, ip: "10.0.3.223"
  #  freeswitch.vm.provision "shell",
  #    inline: "sudo apt-get update && sudo apt-get install -f ansible"
  #end

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", 512]
    vb.customize ["modifyvm", :id, "--cpus", 1]
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  #config.vm.provision "ansible_local" do |ansible|
  #  ansible.playbook = "tests/build.yml"
  #end

  config.vm.synced_folder ".", "/usr/local/src/freeswitch-mw"

  # config.ssh.username = "vagrant"
  # config.ssh.password = "vagrant"

   # config.vm.provider "virtualbox" do |vb|
   #   vb.gui = true
   # end

  #config.ssh.username = "vagrant"
  #config.ssh.password = "vagrant"
  #config.ssh.insert_key = false
  #config.vm.boot_timeout = 240

  config.vbguest.auto_update = true
  config.vbguest.auto_reboot = true
  config.vbguest.installer_arguments = ['--nox11']
end
