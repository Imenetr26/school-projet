# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Utilise la box officielle Bento Ubuntu 22.04
  config.vm.box = "bento/ubuntu-22.04"

  # Réseau privé en DHCP
config.vm.network "private_network", ip: "192.168.56.10"

  # Augmente le temps d’attente de démarrage à 10 minutes
  config.vm.boot_timeout = 600

  # Redirection de ports (modifiables si conflit)
  config.vm.network "forwarded_port", guest: 8080, host: 18081  # Jenkins
  config.vm.network "forwarded_port", guest: 9000, host: 19000  # SonarQube

  # Configuration VirtualBox
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"  # 2 Go de RAM
    vb.cpus = 2         # 2 CPU
    vb.gui = false      # Pas d'interface graphique
  end
end
