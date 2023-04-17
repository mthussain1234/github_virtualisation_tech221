# Virtualization 

## What is a virtual machine?

* A virtual machine (VM) is a software-based computer system that divides a physical machine's resources among several virtual machines. 

* In order to deploy, test, and run legacy applications, each VM runs its own OS and applications in a separate environment.

## What is a dev environment?
* A dev environment is a setup that developers use to write and test software applications. 
* Includes all necessary tools, libraries, and configurations needed to create and run applications. 

## Purpose of making a dev environment?

## Type vagrant into your terminal and sopy and paste the output as a Vagrant cheatsheet into your README.
```
$ vagrant
Usage: vagrant [options] <command> [<args>]

    -h, --help                       Print this help.

Common commands:
     autocomplete    manages autocomplete installation on host
     box             manages boxes: installation, removal, etc.
     cloud           manages everything related to Vagrant Cloud
     destroy         stops and deletes all traces of the vagrant machine
     global-status   outputs status Vagrant environments for this user
     halt            stops the vagrant machine       
     help            shows the help for a subcommand 
     init            initializes a new Vagrant environment by creating a Vagrantfile
     login
     package         packages a running vagrant environment into a box
     plugin          manages plugins: install, uninstall, update, etc.
     port            displays information about guest port mappings
     powershell      connects to machine via powershell remoting
     provision       provisions the vagrant machine  
     push            deploys code in this environment to a configured destination
     rdp             connects to machine via RDP     
     reload          restarts vagrant machine, loads new Vagrantfile configuration
     resume          resume a suspended vagrant machine
     serve           start Vagrant server
     snapshot        manages snapshots: saving, restoring, etc.
     ssh             connects to machine via SSH     
     ssh-config      outputs OpenSSH valid configuration to connect to the machine
     status          outputs status of the vagrant machine
     suspend         suspends the machine
     up              starts and provisions the vagrant environment
     upload          upload to machine via communicator
     validate        validates the Vagrantfile       
`vagrant list-commands`.
        --[no-]color                 Enable or disable color output
        --machine-readable           Enable machine readable output
    -v, --version                    Display Vagrant version
        --debug                      Enable debug output
        --timestamp                  Enable timestamps on log output
        --debug-timestamp            Enable debug output with timestamps
        --no-tty                     Enable non-interactive output
```

# Vagrant
![image](https://user-images.githubusercontent.com/129314018/232502184-71fbb7c6-a74e-4959-89eb-1403864f7f33.png)

## Vagrant Virtualbox connection

1. After installing both VirtualBox and Vagrant, create a new directory for a new Vagrant Project (use git bash command `mkdir <filename>` in preferred location.
2. Open Git Bash terminal and using `cd` and `ls` navigate to the created directory, and initialise a new vagrant project using `vagrant init`
3. Open the Vagrant file made in this directory, we used VScode to edit, and after altering all the commented lines and changing `base` to `ubuntu` (as we want to use ubuntu), your code should look like this:
```
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"
end
```

4. Be sure to save the vagrant file, and turn on **autosave** for future reference
5. To start the VM by running `vagrant up`.
6. We now use `vagrant ssh` to ssh into the virtual machine, and another terminal session will open in the VM.
7. When finished with the VM, use `vagrant halt`, and if you want to destroy the VM we use `vagrant destroy`, this deletes the VM.

## 4 pillars of DevOps

![1520187193360](https://user-images.githubusercontent.com/129314018/232506903-be77be8f-a895-4ba1-b20d-ee64144d615f.jpg)

* Collaboration and effective communication across teams are essential to avoiding misunderstandings and enhancing the calibre of software.

* Collaboration: An environment that values cooperation and shared accountability in order to improve all facets of the software delivery lifecycle.

* Automation is the practise of using tools and technology to speed up the supply of software while reducing mistakes and inconsistent results from human procedures.

* Monitoring: Constantly keeping track on and measuring performance to find and fix problems as they arise.

## What makes a good dev environment

![image](https://user-images.githubusercontent.com/129314018/232513718-bd28afad-09e7-4aaf-97ad-8c7ef47cfae7.png)

A good development environment should provide simple updates and user-friendly interfaces since they can increase developers' overall productivity and efficiency.

If we have different environment == different software versions, configurations, or dependencies, can result in  unexpected errors, security vulnerabilities, or performance problems.

When a development environment is designed to support only one application, it is easier to manage, maintain, and update, if not can become complex, cluttered, and difficult to manage.

Same tools and resources for everyone ensures that all developers have access to them regardless of their location or the device they are using. If tools and resources were different can result in problems such as code conflicts, communication breakdowns, or integration issues.
