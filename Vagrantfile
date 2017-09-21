# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'.freeze
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define 'ubuntu' do |ubuntu|
    ubuntu.vm.box = 'bento/ubuntu-16.04'
    ubuntu.vm.provider 'virtualbox' do |vb|
      vb.gui = false
      vb.memory = '1024'
    end
    ubuntu.vm.hostname = 'ubuntu.dev'
    ubuntu.vm.network 'public_network', bridge: %w(
      wlp3s0
      wlp4s0
      wlan0
    )
  end
end
