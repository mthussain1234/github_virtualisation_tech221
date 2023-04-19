# Virtualization 

## What is a virtual machine?

* A virtual machine (VM) is a software-based computer system that divides a physical machine's resources among several virtual machines. 

* In order to deploy, test, and run legacy applications, each VM runs its own OS and applications in a separate environment.

## What is a dev environment?
* A dev environment is a setup that developers use to write and test software applications. 
* Includes all necessary tools, libraries, and configurations needed to create and run applications. 

## Purpose of making a dev environment?

* A development environment is a safe space for building and testing applications.
* It allows developers to experiment and debug without affecting the live site.
* Creating one promotes better software quality, reduces risk, and improves collaboration.

# Vagrant
![image](https://user-images.githubusercontent.com/129314018/232502184-71fbb7c6-a74e-4959-89eb-1403864f7f33.png)

* The developer will run Vagrant, which is used to manage virtual machines. Vagrant communicates with VirtualBox, to create virtual machines according to the developer's needs.

* The developer can use the virtual machine to test their software in an isolated environment that closely matches the production environment. 

* The virtual machine can be easily destroyed and recreated as needed, making it easy to test different configs and scenarios without using the developers "real" computer.

* Provisioners are tools that let you to automate the VM config. 
* They allow you to execute scripts and install software automatically when deploying the new VM


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

## Vagrant Provisioning

1. Assuming your VM is halted, `vagrant halt`, we create our shell script using `touch provision.sh`.
2. We use `nano provision.sh` to edit the contents and we enter the code in the following format:

    * `sudo apt-get update -y`
    * `sudo apt-get upgrade -y`
    * `sudo apt-get install nginx -y`
    * `systemctl status nginx`
    
3. We now change permissions by using `chmod -x provision.sh` this will make it executable
4. We now move over to VScode, our vagrant file we created in the Vagrant Virtualbox connection, we will now add another line to utilise this shell script on launch: `config.vm.provision "shell", path: "provision.sh"`.

We use provision.sh to automate the setup of the virtual machine, so that it is configured consistently every time you run it. It also makes it easier to version control the provisioning process.

5. Going back to our terminal, we use the command `vagrant up`. We can now `vagrant ssh` into the VM, on top of this, grab the ip address from the vagrant file we updated, and copy and paste the ip in the search bar. 

We are left with Nginx installed automatically as seen below.

![image](https://user-images.githubusercontent.com/129314018/232545391-d917ce9f-6d98-43f1-9f2d-7d8107567174.png)

## MongoDB Provisioning

[To know how we provisioned MongoDB, click on me!](https://github.com/mthussain1234/tech221_mongo/blob/main/README.md#provisioning-mongodb)

## 4 pillars of DevOps

* Cost
  *  Being efficient as possible, and focusing on reducing costs without sacrificing quality.
  *  Optimizing resources to improve efficiency.
* Flexibility
  * Quickly respond to changing customer needs and market demands
  * Increases agility
* Ease of use
  * User friendly UI allows for easy adoption by users, can lead to increased productivity and increase customer satisfaction
  * can make documentation easier to understand and easy to make
 * Robustness
  * involves automated etsting, monitoring and feedback mechanisms, ends up with software being thoroughly tested
  * allows for issues to be quickly resolved


## What makes a good dev environment

![image](https://user-images.githubusercontent.com/129314018/232513718-bd28afad-09e7-4aaf-97ad-8c7ef47cfae7.png)

* A good development environment should provide simple updates and user-friendly interfaces since they can increase developers' overall productivity and efficiency.

* If we have different environment == different software versions, configurations, or dependencies, can result in  unexpected errors, security vulnerabilities, or performance problems.

* When a development environment is designed to support only one application, it is easier to manage, maintain, and update, if not can become complex, cluttered, and difficult to manage.

* Same tools and resources for everyone ensures that all developers have access to them regardless of their location or the device they are using. If tools and resources were different can result in problems such as code conflicts, communication breakdowns, or integration issues.



