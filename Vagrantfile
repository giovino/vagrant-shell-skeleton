# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_LOCAL = 'Vagrantfile.local'

# Vagrant configuration options
Vagrant.configure("2") do |config|
  config.vm.box = "debian/wheezy64"

  # config.vm.network "forwarded_port", guest: 80, host: 8080
  # config.vm.network "private_network", ip: "192.168.33.10"
  config.vm.network "private_network", type: "dhcp"
  config.vm.synced_folder "src/", "/vagrant"
  # config.vm.provision "shell", path: "scripts/bootstrap.sh", privileged: false

  # Personal Vagrant configuration options
  if File.file?(VAGRANTFILE_LOCAL)
    external = File.read VAGRANTFILE_LOCAL
    eval external
  end

  # Provider specific configuration options
  config.vm.provider "virtualbox" do |vb|
      # v.gui = true
      # v.name = "my_vm"
      vb.customize ["modifyvm", :id, "--cpus", "2", "--ioapic", "on", "--memory", "1024"]
  end
end
