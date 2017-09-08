# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "minimal/xenial64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = 2
  end

  config.ssh.insert_key = false

  config.vm.provision "shell", inline: <<-SHELL
    update-locale LANG=C.UTF-8 LANGUAGE=
    sed -i.bak -e 's!http://\\(archive\\|security\\).ubuntu.com/!ftp://ftp.jaist.ac.jp/!g' /etc/apt/sources.list
  SHELL

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.verbose = true
    ansible.install = true
    ansible.install_mode = :pip
  end
end
