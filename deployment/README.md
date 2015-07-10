Ansible Playbook
================

## Installation

If Ansible is not installed yet on your machine, install `ansible`: `pip install ansible`

## Local deployment with Vagrant

### Starting up the VM

1. From within the `deployment` directory, run `vagrant up` to create the VMs.<br/>
*Note that this does not run the provisioning. Provisioning is done by Ansible.*
2. Run `ANSIBLE_HOST_KEY_CHECKING=False ansible-playbook vagrant.yml -i hosts -vvvv --ask-vault-pass` This sets up the cluster in your local Vagrant environment. You may instead want to use the stand-alone version (without clustering) of this by substituting the ansible script file clause `vagrant.yml` to `vagrant-standalone.yml`.
3. Provide the ansible-vault key when prompted.

This sets up the push tool using the developer certs for Urban Airship on a locally running VM at https://192.168.33.16:3040/.

You will likely be warned by your browser that the SSL certificates are not properly signed. You can safely ignore this warning since they were self signed when provisioning the VM.

It also sets up 3 mongo servers with 1 primary, 1 secondary, and 1 arbiter.

If you do not need the 3 mongo servers separately, you may use the vagrant-standalone.yml playbook instead, and you will only need to bring up the *web* VM via using the `vagrant up web` command.

### Getting rid of the VM

You can stop and remove the VM entirely via `vagrant destroy`.

See more options via `vagrant help`.
