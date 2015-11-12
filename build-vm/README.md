## Instructions to set up Virtual Machine(VM) using Vagrant.

### Steps:
* Install [Oracle VirtualBox](https://www.virtualbox.org/) and [Vagrant](http://www.vagrantup.com/).
* Create a folder for VM on your machine and place this [VagrantFile](https://github.com/SoftwareEngineeringToolDemos/FSE-2012-ReImInfer/blob/master/build-vm/Vagrantfile) in it.
* Now navigate to the folder and run the command "vagrant up". This will create a new ubuntu 12.04LTS virtual machine and installs oracle java 1.6 in it.
* Please wait until "vagrant up" command has completed succesfully and then you can use the virtual machine.
* There are two ways to login into this virtual machine.
  * Use the gui provided by the Virtualbox.
  * Use ssh client(like putty or vagrant ssh) to start a new ssh session.
* Credentials for login.
  * Username: vagrant
  * Password: vagrant

### References:

* https://docs.vagrantup.com/v2/getting-started/up.html
* http://askubuntu.com/questions/67909/how-do-i-install-oracle-jdk-6
* http://stackoverflow.com/questions/19275856/auto-yes-to-the-license-agreement-on-sudo-apt-get-y-install-oracle-java7-instal
