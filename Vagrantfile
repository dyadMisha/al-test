# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.provider "libvirt" do |libvirt|
    libvirt.driver = "kvm"
    libvirt.host = "10.10.21.107"
    libvirt.connect_via_ssh = true
    libvirt.username = "root"
    libvirt.storage_pool_name = "default"
    libvirt.default_prefix = ''
  end

  config.vm.box = "generic/debian11"

  config.vm.define "dhcp-server" do |dhcpserver|
    dhcpserver.vm.provider "libvirt" do |domain|
      domain.description = "test dhcp server"
      domain.memory = 1024
      domain.cpus = 1
    end
    dhcpserver.vm.hostname = "dhcp-server"
    dhcpserver.vm.network :private_network,
                          :libvirt__network_name => 'default',
			  :libvirt__dhcp_enabled => 'false',
			  :libvirt__always_destroy => 'false',
                          :libvirt__forward_mode => 'none'
    dhcpserver.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "dhcp-server-playbook.yaml"
    end
  end
 
  config.vm.define "dhcp-client" do |dhcpclient|
    dhcpclient.vm.provider "libvirt" do |domain|
      domain.description = "test dhcp client"
      domain.memory = 1024
      domain.cpus = 1
    end
    dhcpclient.vm.hostname = "dhcp-client"
    dhcpclient.vm.network :private_network,
                          :libvirt__network_name => 'default',
			  :libvirt__dhcp_enabled => 'false',
			  :libvirt__always_destroy => 'false',
                          :libvirt__forward_mode => 'none'
    dhcpclient.vm.provision "ansible" do |ansible|
      ansible.verbose = "v"
      ansible.playbook = "dhcp-client-playbook.yaml"
    end
 end


end
