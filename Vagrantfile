# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "debian-9-amd64"
  config.vm.box_check_update = false
  config.vm.provision "file", source: "~/vagrant/files/git-config", destination: "~/.gitconfig"
  config.vm.provision "shell", path: "https://raw.githubusercontent.com/astuk/vagrant-lamp/master/vm-common"

  config.vm.define "web" do |web|
    web.vm.hostname = "web"
    web.vm.network "forwarded_port", guest: 80, host: 8080
    web.vm.provision "file", source: "~/vagrant/files/git-config", destination: "~/.gitconfig"
    web.vm.provision "shell", path: "https://raw.githubusercontent.com/astuk/vagrant-lamp/master/vm-web"
    web.vm.network "private_network", ip: "192.168.88.225"
    web.memory = "1024"
  end
  config.vm.define "db" do |db|
    db.vm.hostname = "db"
    #db.vm.network "forwarded_port", guest: 80, host: 8080
    db.vm.provision "file", source: "~/vagrant/files/git-config", destination: "~/.gitconfig"
    db.vm.provision "shell", path: "https://raw.githubusercontent.com/astuk/vagrant-lamp/master/vm-db"
    db.vm.network "private_network", ip: "192.168.88.226"
    db.memory = "1024"
  end

end
