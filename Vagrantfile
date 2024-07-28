# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "ansibleControl" do |app|
    app.vm.box = "centos/7"
    app.vm.network :private_network, ip: "192.168.33.10"
    app.vm.network "public_network"
    config.ssh.insert_key = false
  end

  config.vm.define "ansible1" do |app|
    app.vm.box = "centos/7"
    app.vm.network :private_network, ip: "192.168.33.11"
    app.vm.network "public_network"
    config.ssh.insert_key = false
  end

  config.vm.define "ansible2" do |app|
    app.vm.box = "centos/7"
    app.vm.network :private_network, ip: "192.168.33.12"
    app.vm.network "public_network"
    config.ssh.insert_key = false
  end

  config.vm.define "ansible3" do |app|
    app.vm.box = "centos/7"
    app.vm.network :private_network, ip: "192.168.33.13"
    app.vm.network "public_network"
    config.ssh.insert_key = false
  end

  config.vm.define "ansible4" do |app|
    app.vm.box = "centos/7"
    app.vm.network :private_network, ip: "192.168.33.14"
    app.vm.network "public_network"
    config.ssh.insert_key = false
  end

  # for index in 1..4 do
  #   currentIp = "192.168.33.1#{index}"
  #   puts currentIp
  #   config.vm.define "ansible#{index}" do |app|
  #     app.vm.box = "centos/7"
  #     app.vm.network :private_network, ip: currentIp
  #     app.vm.network "public_network"
  #     config.ssh.insert_key = false
  #   end
  # end

  config.vm.provision "shell", inline: <<-SHELL
    sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config    
    systemctl restart sshd.service
    sed -i s/mirror.centos.org/vault.centos.org/g /etc/yum.repos.d/*.repo
    sed -i s/^#.*baseurl=http/baseurl=http/g /etc/yum.repos.d/*.repo
    sed -i s/^mirrorlist=http/#mirrorlist=http/g /etc/yum.repos.d/*.repo
  SHELL

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "1024"
    vb.cpus = "2"
  end
end
