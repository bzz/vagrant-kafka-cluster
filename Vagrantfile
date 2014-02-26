# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant::Config.run do |config|
  config.vm.box = "CentOS-6.4-x86_64" #http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.4-x86_64-v20130731.box

  config.vm.provision :shell, :inline => "sudo cp /vagrant/files/etc/hosts /etc/hosts"

  config.vm.define :kafka_node01 do |node01_config|
    node01_config.vm.host_name = "kafka-node01"
    node01_config.vm.network :hostonly, "192.168.57.2"
    node01_config.vm.customize ["modifyvm", :id, "--memory", 2048]
    # This shell provisioner installs librarian-puppet and runs it to install
    # puppet modules. After that it just runs puppet
    node01_config.vm.provision :shell, :path => "shell/bootstrap.sh"
  end

  config.vm.define :kafka_node02 do |node02_config|
    node02_config.vm.host_name = "kafka-node02"
    node02_config.vm.network :hostonly, "192.168.57.3"
    node02_config.vm.customize ["modifyvm", :id, "--memory", 2048]
    node02_config.vm.provision :shell, :path => "shell/bootstrap.sh"
  end

end
