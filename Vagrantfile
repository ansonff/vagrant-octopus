# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'
settings = YAML.load_file 'vagrant_local.yml'
vagrant_share = settings['sync-folder']['vagrant-share']
vagrant_common = settings['sync-folder']['vagrant-common']
cpu_cores = settings['cpu_cores']
ram_size = settings['ram_size']

if cpu_cores.to_s.strip.length == 0
	cpu_cores = "1"
end

if ram_size.to_s.strip.length == 0
	ram_size = "3072"
end

Vagrant.configure(2) do |config|

  config.vm.box = "redhat_docker-virtualbox.box"
  # config.vm.box_url = "http://10.46.3.208/vagrant/boxes/octopus/redhat_docker-virtualbox.box"
  config.vm.box_url = "H:\Backup\vagrant\box\redhat_docker-virtualbox.box.20191014"

  config.vm.synced_folder vagrant_share, "/vagrant-share"
  config.vm.synced_folder vagrant_common, "/vagrant-common"

  # config.vm.network "forwarded_port", id: "Portainer", guest: 19000, host: 19000, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", id: "ssh", guest: 22, host: 22222, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", id: "SQL Server", guest: 1433, host: 1433, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", id: "MQTT1", guest: 1883, host: 1883, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", id: "MQTT2", guest: 8083, host: 8083, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", id: "MQTT3", guest: 8084, host: 8084, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", id: "MQTT4", guest: 8883, host: 8883, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", id: "MQTT5", guest: 18083, host: 18083, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", id: "Kafka-zoo", guest: 2181, host: 2181, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", id: "Kafka", guest: 9092, host: 9092, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", id: "redis", guest: 6379, host: 6379, host_ip: "127.0.0.1"
  config.vm.hostname = "sjcpsvr"

  
  config.vm.provider "virtualbox" do |vb|
      # Display the VirtualBox GUI when booting the machine
      vb.gui = false
  
      # Customize the amount of memory on the VM:
      vb.memory = ram_size
	  vb.cpus = cpu_cores
	  vb.name = "SJCP - MEP Dev Offical"
	  
	  vb.customize ['modifyvm', :id, '--cableconnected1', 'on']
  end
  
  # Set development environment

end
