# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "debian/jessie64"
  config.vm.hostname="gitlab"
  config.vm.define :gitlab do |gitlab|
  end
  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network "forwarded_port", guest: 80, host:8080
  config.vm.network "forwarded_port", guest: 443, host:8443
  config.vm.network "forwarded_port", guest: 22, host:8022
  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
    vb.memory = "2048"
  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
  
  
    # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
	#sudo apt-get update
    sudo apt-get -y install git python-dev python-pip
	##sudo pip install --upgrade setuptools pip
	#installation ansible 
	sudo echo "deb http://ppa.launchpad.net/ansible/ansible/ubuntu trusty main" >> /etc/apt/sources.list
	sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 93C4A3FD7BB9C367
	sudo apt-get update
	sudo apt-get -y --force-yes install ansible 
	sudo pip install markupsafe
	#sudo apt-get install gitlab-ceJ'ai acc
	#on installe les roles d'ansible dont on a besoin
	sudo git clone https://github.com/sofiannagounine/ansible_gitlab.git
	sudo ansible-galaxy install -r requirements.yml
	cd /etc/ansible/roles
	#On modifie les fichiers inventory (changer le host) et le playbook (modifier le nom gitlab par le nom du host défini dans inventory)
	#sudo rm -rf geerlingguy.gitlab/
	sudo git clone https://github.com/sofiannagounine/roles_ansible_gitlab.git
    cd roles_ansible_gitlab/
	sudo mv gitlab/ ../gitlab/
	sudo mv firewall/ ../firewall/
	cd ..
	sudo rm -rf roles_ansible_gitlab/
	cd

	#cd ~/ansible-vagrant-examples/gitlab/provisioning
	#sudo chmod 777 inventory
	#sudo echo 'local ansible_connection=local' > inventory
	#sudo apt-get -y install zabbix-agent
	#Pour lancer l'application on tape dans le terminal:
	#ansible-playbook playbook.yml -i inventory -s -v
	#installation zabbix
	#sudo apt-get -y install ssh wget man vim build-essential checkinstall
	#creation d'un utilisateur zabbix
    #sudo groupadd -g 9000 zabbix
    #sudo useradd -u 9000 -g zabbix -d /usr/local/zabbix -c "Zabbix User" zabbix
    #sudo passwd zabbix
	#installation zabbix server
	#sudo apt-get -y install mysql-server libmysqlclient15-dev
	#mot de passe super user a rentrer pour mysql-server
	#pour avoir accès au fichier de config
	#sudo vim /etc/zabbix/zabbix_server.conf
	#installation du frontend
	#sudo apt-get -y install zabbix-frontend-php	
    #il faut editer le fichier de conf et modifier la timezone (date.timezone= “Europe/Paris”)
    #sudo vim /etc/php5/apache2/php.ini
	#et relancer le serveur
	#sudo /etc/init.d/apache2 restart 
  SHELL
end

