# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty64"
  
  #Networking  
  # Create a private network, which allows host-only access to the machine using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.22"
  
  # forward guest port 80 to our 8001
  config.vm.network "forwarded_port", guest: 80, host: 8001
  
  #by default guest:22 will forward to host:2222
  
  #Files & Directories
  # Share an additional folder to the guest VM. The first argument is the path on the host to the actual folder.
  # The second argument is the path on the guest to mount the folder.
  config.vm.synced_folder "./", "/var/www/html"
  
  # Sync ssh folder
  config.vm.synced_folder "~/.ssh", "/home/vagrant/.ssh", :mount_options => ["dmode=700", "fmode=700"]
  
  # Copy once .gitconfig file
  config.vm.provision "file", source: "~/.gitconfig", destination: ".gitconfig"  
  
  #Provisioning
  config.vm.provision :shell, path: "bootstrap.sh"
end
