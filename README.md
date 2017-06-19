# Ansible Vagrant Examples

This repository contains a gitlab full installation. VMs are created using Vagrant and deployed using Ansible.

# Pre-requisites (for Windows users)

## Install Git, Vagrant, VirtualBox

* [Vagrant](http://vagrantup.com/)
* [VirtualBox](https://www.virtualbox.org/) 
* [Git](https://git-scm.com/download/win)

## Install the 'putty' plugin to emulate the unix `vagrant ssh` command

        vagrant plugin install vagrant-multi-putty

# Run:

Clone this repo

        git clone -b evol/slef https://github.com/silefort/ansible_gitlab.git

Run the VM

        cd ansible_gitlab
        vagrant up

Connect to your Gitlab Instance using your browser at `https://localhost:8443`

You can ssh into you VM using `vagrant putty`

# Author Information

created in 2017 by [Sofiann Agounine]
