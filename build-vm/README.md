## Instructions to set up VM using Vagrant.

### Steps:
* Install [VirtualBox](https://www.virtualbox.org/) and [Vagrant](http://www.vagrantup.com/).
* Create a new folder and place this [VagrantFile](https://github.com/SoftwareEngineeringToolDemos/FSE-2012-ReImInfer/blob/master/build-vm/Vagrantfile) in it.
* Run the command "vagrant up". This will create a new ubuntu 12.04LTS virtual machine and install openjdk-1.7 in it.
* There are two ways to login into this virtual machine.
  * Use the gui provided by the Virtualbox.
  * Use ssh client(like putty or vagrant ssh) to start a new ssh session.
* Credentials for login.
  * Username: vagrant
  * Password: vagrant

### References:
* https://docs.vagrantup.com/v2/getting-started/up.html
