# thirty bees Vagrantfile
This Vagrantfile will help you get a local instance of thirty bees up and running in no time. 
The included ansible provisioning script will install and configure a Linux - nginx - PHP - MySQL stack with thirty bees for you.

## Instructions

First you need to clone this repository

```shell
$ git clone https://github.com/thirtybees/vagrant
```

then build Vagrant:

```
$ cd vagrant
$ vagrant up
```

This will launch an instance at 10.0.0.30, but it'll listen to the hostname `thirty.bees`. Therefore it is wise to add the following to your hosts file (`/etc/hosts` on Linux/OS X):
```
# thirty bees vagrant
10.0.0.30 thirty.bees
```
## Optional Vagrant Plugins

Some optional plugins you can install are:
- `vagrant plugin install vagrant-vbguest` - Making sure you have VirtualBox' Guest additions on your VM
- `vagrant plugin install vagrant-hostsupdater` - Make Vagrant update your hosts file in order to automatically assign the custom domain name

## Login

Once the instance is up and running, you can reach it via the following URLs:
- [http://thirty.bees/](http://thirty.bees/) for the Front Office  
- [http://thirty.bees/admin-dev](http://thirty.bees/admin-dev) for the Back Office

The admin panel credentials are:
- username: `test@thirty.bees`  
- password: `thirtybees`

## Fine-tuning

### Server specs

By default the script configures a VirtualBox VM with 1 vCPU and 1GB ram. You can change these values in the `Vagrantfile`.

### Hostname

The hostname can be changed by 
- changing the `server_name` variable in the file `/playbooks/roles/thirty-bees/templates/nginx.conf.j2`
- and updating the installation command at the step "Install thirty bees itself" in the file `/playbooks/roles/thirty-bees/tasks/main.yml`

### IP Address

The IP address that the VM uses can be changed in the `Vagrantfile`

### thirty bees version

The thirty bees version is set in the file `/playbooks/roles/thirty-bees/tasks/main.yml`. The version here refers to the git tag. thirty bees tags every stable release. This allows you to pick any stable release via this file.
