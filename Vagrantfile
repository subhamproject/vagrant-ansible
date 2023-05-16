# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'
Vagrant.configure("2") do |config|
  config.vm.define "cent01" do |config|
  config.vm.hostname = "cent01"
  config.vm.box = "bento/centos-8"
  config.vm.box_check_update = false
  config.vm.provision :ansible do |ansible|
    ansible.limit = "all"
    ansible.playbook = "provision/playbook.yml"
  end
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 1
    end
  end
end
