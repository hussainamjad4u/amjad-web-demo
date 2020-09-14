# -*- mode: ruby -*-
# vi: set ft=ruby

Vagrant.configure("2") do |config|
  #------------------------------------------
  #--------------Config a 3 tier infra architecture -----------
  #----------------- Configure webserver 01 -------------------------
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
  #----------------- Configure webserver 02 -------------------------
  config.vm.define "webserver" do |web2|
    web2.vm.box = "ubuntu/trusty64"
    web2.vm.hostname = "web02"
    #--assigning IP
    web2.vm.network "private_network", ip: "10.10.10.11"
    #--define provider virtualbox and config mem
    web2.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--name", "web02"]
      vb.memory = "512"      
    end
    #--Lets do provisioning
    web2.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      sudo mv /var/www/html /var/www/_html
      sudo ln -s /vagrant/web2 /var/www/html
    SHELL
  end
  #----------------- Configure Database Server - Single node 01 -------------------------
  config.vm.define "db01" do |db1|
    db1.vm.box = "bseller/oracle-xe"
    db1.vm.hostname = "db01"
    #--assigning IP
    db1.vm.network "private_network", ip: "10.10.10.12"
    #--define provider virtualbox and config mem
    db1.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--name", "db01"]
      vb.memory = "512"      
    end
    #--Lets do provisioning
    db1.vm.provision "shell", inline: <<-SHELL
      #apt-get update
      #apt-get install -y apache2
      #sudo mv /var/www/html /var/www/_html
      #sudo ln -s /vagrant/web2 /var/www/html
    SHELL
  end
end
