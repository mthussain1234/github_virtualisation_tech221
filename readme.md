# Virtualization 

## What is a virtual machine?

## What is a dev environment?

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

