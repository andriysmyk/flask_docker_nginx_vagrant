Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"
  config.vm.hostname = "astest"

  # Прокидаємо порти: 80 для nginx, 8000 для веб-апки, 8080 для zabbix (пізніше)
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 8000, host: 8000
  config.vm.network "forwarded_port", guest: 10051, host: 10051 # zabbix agent port

  # Додаємо приватну мережу з фіксованою IP
  config.vm.network "private_network", ip: "192.168.56.101"

  # Виділяємо ресурси
  config.vm.provider "virtualbox" do |vb|
    vb.name = "astest"
    vb.memory = "2048"
    vb.cpus = 2
  end

  # Опційно: налаштування папки для синхронізації (якщо треба)
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
end
