# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "base"
  
  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  config.vm.network :public_network

  config.vm.define "master" do |host|
      # The hostname the machine should have.
      host.vm.hostname = "jenkins-master"
      
      # Create a forwarded port mapping which allows access to a specific port
      # within the machine from a port on the host machine.
      host.vm.network "forwarded_port", guest: 8080, host: 8080

      # Provider-specific configuration so you can fine-tune various
      # backing providers for Vagrant. These expose provider-specific options.
      host.vm.provider "virtualbox" do |vb|
        # Use VBoxManage to customize the VM. For example to change memory:
        vb.customize ["modifyvm", :id, "--memory", "4096"]
      end
          
      # The shell provisioner allows you to upload and execute a script within
      # the guest machine.
      host.vm.provision "shell", path: "master.sh"
  end
  
  config.vm.define "slave" do |host|
      # The hostname the machine should have.
      host.vm.hostname = "jenkins-slave1"
  
      # The shell provisioner allows you to upload and execute a script within
      # the guest machine.
      host.vm.provision "shell", path: "slave.sh"
  end
end
