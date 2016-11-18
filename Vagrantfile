# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.provision "shell", inline: <<-SHELL
    apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
    echo "deb https://apt.dockerproject.org/repo ubuntu-xenial main" | sudo tee /etc/apt/sources.list.d/docker.list
    sed -i "s/us.archive.ubuntu.com/id.archive.ubuntu.com/g" /etc/apt/sources.list
    apt-get update
    apt-get install -y --allow-unauthenticated docker-engine
    usermod -aG docker vagrant
    su vagrant -c "docker info"
    wget http://downloads.drone.io/drone-cli/drone_linux_amd64.tar.gz
    tar -xzvf drone_linux_amd64.tar.gz
  SHELL
end