# -*- mode: ruby -*-
# vi: set ft=ruby :

# debian non permite login de root:
##Usuario:vagrant
##Pass: vagrant

# centos si permite login como root:
##user:root
##pass:vagrant
Vagrant.configure("2") do |config|
  config.vm.define "centos72" do |centos72|
    centos72.vm.boot_timeout = 1200

    centos72.vm.provider "qemu" do |qe|
      qe.arch = "x86_64"
      qe.machine = "q35"
      qe.cpu = "max"
      qe.net_device = "virtio-net-pci"
      qe.ssh_port = "50024" # vou cambiando o porto (o 50022 e o 50023 son probas)
    end

    # centos72.vm.box = "bento/centos-7.2"
    centos72.vm.box = "generic/centos7"    # tenho que colher as que tenhan de provider "libvirt" ou "qemu"
    centos72.vm.network "private_network", ip: "192.168.2.5"
    centos72.vm.hostname = "sercentos7" 
  end


  config.vm.define "debian2" do |debian2|
    debian2.vm.box = "generic/debian10"
    debian2.vm.boot_timeout = 1200

    debian2.vm.provider "qemu" do |qe|
      qe.arch = "x86_64"
      qe.machine = "q35"
      qe.cpu = "max"
      qe.net_device = "virtio-net-pci"
      qe.ssh_port = "50025" # vou cambiando o porto (o 50022 e o 50023 son probas)
    end

    debian2.vm.network "private_network", ip: "192.168.2.10"
    debian2.vm.hostname = "debian10"
  end


config.vm.define "centos62" do |centos62|
    # centos62.vm.box = "bento/centos-6.7"
    centos62.vm.box = "generic/centos6"
    config.vm.provider "qemu" do |qe|
      qe.arch = "x86_64"
      qe.machine = "q35"
      qe.cpu = "max"
      qe.net_device = "virtio-net-pci"
      qe.ssh_port = "50026" # vou cambiando o porto (o 50022 e o 50023 son probas)
    end

	centos62.vm.boot_timeout = 1200
	#config.ssh.insert_key = false
  centos62.vm.network "private_network", ip: "192.168.2.152"
  centos62.vm.hostname = "orion"
	centos62.vm.provision "shell", inline: <<-SHELL
	 rm -rf /etc/yum.repos.d/CentOS-Base.repo
	 cp /vagrant/*.repo /etc/yum.repos.d/
	 yum clean all
     SHELL
    
  end

end