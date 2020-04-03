# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"
  config.vm.box_check_update = false

  config.vm.network "public_network", ip: "192.168.2.100"

  config.vm.synced_folder "nginx_reverseproxy", "/home/vagrant/nginx_reverseproxy"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
  end

  #config.vm.provision "file", source: "~/.ssh/vagrant-local.pub", destination: "~/.ssh/authorized_keys"
  config.vm.provision "shell", inline: <<-SHELL
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    sudo apt-get update
    sudo apt-get upgrade -y 
    sudo apt-get install -y docker-ce docker-compose jq
  SHELL
  config.vm.provision "shell", inline: <<-SHELL
    sudo adduser vagrant docker
  SHELL

end
