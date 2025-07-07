Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.hostname = "astest"

  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  config.vm.network "forwarded_port", guest: 10051, host: 10051 # zabbix agent port

  config.vm.network "private_network", ip: "192.168.56.101"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "astest"
    vb.memory = "2048"
    vb.cpus = 2
  end

  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
end
