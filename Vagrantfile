# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'
HOST_IP = '192.168.33.40'
HOST2_IP = '192.168.33.41'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
config.vm.define "jenkis-master" do |ansible1|
ansible1.vm.hostname = "ansible1.rnstech.com"
ansible1.vm.box = "centos/7"
ansible1.vm.box_url = "centos/7"
ansible1.vm.network :private_network,
      ip: HOST_IP,
      netmask: '255.255.255.0'
ansible1.vm.network :forwarded_port, guest: 8800, host: 8080
#ansible1.vm.synced_folder 'html', '/var/www/html'
ansible1.vm.provision 'shell', path: 'provision.sh'	
end

config.vm.define "jenkins-slave" do |ansible2|
ansible2.vm.hostname = "ansible2.rnstech.com"
ansible2.vm.box = "centos/7"
ansible2.vm.box_url = "centos/7"
ansible2.vm.network :private_network,
      ip: HOST2_IP,
      netmask: '255.255.255.0'
#ansible1.vm.network :forwarded_port, guest: 8800, host: 8080
#ansible1.vm.synced_folder 'html', '/var/www/html'
ansible2.vm.provision 'shell', path: 'provision1.sh'
end
end