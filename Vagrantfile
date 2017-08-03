# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "debian/jessie64"
  config.vm.hostname="gitlab"
  config.vm.define :gitlab do |gitlab|
  end

  config.vm.network "forwarded_port", guest: 80, host:8080
  config.vm.network "forwarded_port", guest: 443, host:8443

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end

  config.vm.provision "shell", inline: <<-SHELL
    # Install Ansible and needed dependencies
    ## Add Ansible repo to apt sources
    sudo echo "deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main" >> /etc/apt/sources.list
    sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
    sudo apt-get update

    ## Install needed repos
    sudo apt-get -y install git python-dev python-pip 
    sudo apt-get -y --force-yes install ansible 
    # Fetch Gitlab Ansible playbook and associated roles
    mkdir -p /app/deploy
    cd /app/deploy
    sudo git clone https://github.com/sofiannagounine/ansible_gitlab.git 
	
    cd /app/deploy/ansible_gitlab/provisioning
    ## To run the playbook, type:
    sudo ansible-playbook playbook.yml -i inventory -b -v --ask-pass
  SHELL
end
