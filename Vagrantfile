# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "kmm/ubuntu-xenial64"
  config.vm.hostname = "nvr-#{Socket.gethostname}"

  config.vm.provider :hyperv do |hv, override|
    hv.memory = "1024"
    hv.maxmemory = "2048"
    hv.cpus = 2
  end

  config.vm.network "public_network", bridge: "Vagrant Virtual Switch"

  config.vm.network :forwarded_port, guest: 8080, host: 8005

  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    apt-get upgrade -y 
    apt-get install -y git build-essential libssl-dev unzip curl bash-completion software-properties-common python-software-properties
  SHELL
end
