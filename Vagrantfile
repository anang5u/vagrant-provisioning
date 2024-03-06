# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

Vagrant.configure(2) do |config|

  config.vm.provision "shell", path: "bootstrap.sh"

  NodeCount = 1
  NodeNamePrefix = "server"
  NetworkIp = "10.104.10.200"

  # Nodes
  (1..NodeCount).each do |i|
    config.vm.define "#{NodeNamePrefix}#{i}" do |vb|
      vb.vm.box = "bento/ubuntu-22.04"
      vb.vm.hostname = "#{NodeNamePrefix}#{i}.example.com"
      vb.vm.network "private_network", ip: "#{NetworkIp}"
      vb.vm.provider "virtualbox" do |v|
        v.name = "#{NodeNamePrefix}#{i}"
        v.memory = 1024
        v.cpus = 2
      end
    end
  end

end
