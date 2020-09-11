# -*- mode: ruby -*-
# vi: set ft=ruby

Vagrant.configure("2") do |config|
  #------------------------------------------
  #--------------Config a web app------------
  #------------------------------------------
  config.vm.define "webserver" do |web1|
    web1.vm.box = "ubuntu/trusty64"
    web1.vm.hostname = "web01"
    #--assigning IP
    web1.vm.network "private_network", ip: "10.10.10.10"
    #--define provider virtualbox and config mem
    web1.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--name", "web01"]
      vb.memory = "512"      
    end
    #--Lets do provisioning
    web1.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      sudo mv /var/www/html /var/www/_html
      sudo ln -s /vagrant/web1 /var/www/html
    SHELL
  end  
end
