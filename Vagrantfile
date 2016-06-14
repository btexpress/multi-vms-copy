# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "grtjn/centos-6.5"

  config.vbguest.auto_update = false

  config.vm.provision "file", source: "~/vagrant/files/git-config", destination: "~/.gitconfig"

  config.vm.provision "shell", path: "https://raw.githubusercontent.com/btexpress/vagrant/master/scripts/centos-common.sh"

  config.vm.define "web" do |web|
    web.vm.hostname = "web-server"
    web.vm.network "forwarded_port", guest: 80, host: 8080
    web.vm.network "private_network", ip: "192.168.10.2"
    web.vm.provision "shell", path: "https://raw.githubusercontent.com/btexpress/vagrant/master/scripts/centos-web.sh"
  end

  config.vm.define "db" do |db|
    db.vm.hostname = "database-server"
    web.vm.network "private_network", ip: "192.168.10.3"
    db.vm.provision "shell", path: "https://raw.githubusercontent.com/btexpress/vagrant/master/scripts/centos-database.sh"
  end

end
