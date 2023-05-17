# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'
Vagrant.configure("2") do |config|
  config.vm.define "ansible-test" do |config|
  config.vm.hostname = "ansible-test"
  config.vm.boot_timeout = 600
  config.vbguest.installer_options = { allow_kernel_upgrade: true }
  #config.vbguest.iso_path = "https://download.virtualbox.org/virtualbox/6.1.32/VBoxGuestAdditions_6.1.32.iso"
  config.vm.box = "bento/ubuntu-22.04"
  config.vm.network :private_network, ip: "192.168.10.10"
  config.vm.box_check_update = false
  config.vm.provision :ansible_local do |ansible|
  ansible.limit = "all"
  ansible.install = true
  ansible.provisioning_path = "/vagrant/"
  ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3" }
  ansible.playbook = "playbook.yml"
  ansible.install_mode = "pip3"
  #ansible.verbose = "v"
  ansible.pip_install_cmd = "sudo apt-get -y install python3-pip"
  #ansible.inventory_path = "inventory"
  #ansible.version = "2.7.13"
  ansible.become = true
  #ansible.config_file = "ansible.cfg"
  ansible.compatibility_mode = "2.0"
  end
  config.vm.provider "virtualbox" do |v|
    v.memory = 2048
    v.name = "ansible-test"
    v.cpus = 1
    end
  end
end
