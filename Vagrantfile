# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "debian/jessie64"

  config.vm.network "forwarded_port", guest: 5432, host: 5432
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  config.vm.network "forwarded_port", guest: 5060, host: 5060, protocol: 'udp'

  config.vm.network "public_network", ip: "10.0.3.223"

  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "1024"
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "tests/build.yml"
  end


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
