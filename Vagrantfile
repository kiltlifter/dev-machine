# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
 
  config.vm.box = "seancdouglas/centos-dev"

  config.ssh.private_key_path = "insecure_private_key/id_rsa"
 
  #config.vm.network "forwarded_port", guest: 9000, host: 9000
 
  # config.vm.synced_folder "../", "/tmp"
 
   config.vm.provider "virtualbox" do |vb|
     # Use VBoxManage to customize the VM. For example to change memory:
     vb.customize ["modifyvm", :id, "--memory", "1024"]
   end

  # Enable provisioning with Ansible
  config.vm.define 'vagrant-centos' do |machine|
    machine.vm.hostname = 'vagrant-centos.local' 
    machine.vm.network "private_network", ip: "192.168.2.222"
    machine.vm.provision :ansible do |ansible|
      ansible.playbook = "playbook/site.yaml"
      ansible.inventory_path = "./hosts"
	  ansible.limit = 'vagrant'
	end
  end

end
