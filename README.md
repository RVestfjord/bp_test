Content
=======

This repo contains all files necessary to configure and start a nginx microservice inside a Vagrant host.
As I didn't have a Linux machine around it is build for Windows and hence a bit clunkier than it need to be. 
Unfortunately Ansible doesn't work very well on Windows as a control host and configuring Ansible as provisioning provider is terrible. Hence the guest based Ansible provisionong.

Requirements
============

You need to install Virtualbox and Vagrant. It can be downloade from here: https://www.virtualbox.org/wiki/Downloads and here: https://www.vagrantup.com/downloads.html respectively.
You also need to install the vbguest plugin to be able to connect to the Vagrant box on its private network. To do so run "vagrant plugin install vagrant-vbguest" from your favoured terminal.


Usage
=====

Clone the repo onto your Windows host and run "vagrant up" from inside your repo. Once the deployment has finished you can connect to the Nginx on port 8080 of the "Virtualbox Host Only Network". As the private network is configured for DHCP you need to find out the address vagrant runs on by connection via "vagrant ssh" and run "ip addr" inside the box. Point your browser to the url http://<your ip>:8080 and you should see the "Hello World!" message. You can also set a static ip in the Vagrantfile but be careful to use an address in the correct range.

Troubleshooting
============

If you cannot connect to the port check that you are using the correct address. If you used a static address check that it is in the correct network. Use "ipconfig /all" to print oput the network configuration of you Windows machine and check what the network range for your "Virtualbox Host Only Network" is. Check that you did not use the default router address (usually but not always x.x.x.1) for your static ip. 
You can also connect to the box with "vagrant ssh" and run the commnad "curl http://localhost:8080". That should give you the html of the static page. If it doesn't work the container might not have started or nginx failed to start. 
