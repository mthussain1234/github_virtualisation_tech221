# Monolith Deployment

1. To start off we have to provision our virtual machine to have the app folder and nginx.
2. To do this we edit our VagrantFile from the [Vagrant Virtualbox connection](https://github.com/mthussain1234/github_virtualisation_tech221#vagrant-virtualbox-connection) to have an additional line to sync the app folder to our Vagrant VM. `config.vm.synced...` is the new line we add.
```
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"
  config.vm.network "private_network", ip: "192.168.10.100"
  # syncing the app folder
  config.vm.synced_folder "app", "/home/vagrant/app"
end
```

3. To ensure Nginx is installed on startup we check our `provision.sh` and it should be as such: 
```
#!/bin/bash

sudo apt-get update -y
sudo apt-get upgrade -y
sudo apt-get install nginx -y
```

4.  To double check this works we will run `vagrant up` and `vagrant ssh` in our terminal, and copy and paste the ip address above into our browser, if we are welcomed to nginx then the provision script has been done correctly.
5.  To double check the vagrantfile, on our VM, we run `ls` to see the contents of the file, and if `app` is present then the vagrantfile has also been done correctly.
6.  Exiting the VM, we now want our `environment` folder to be present within the Vagrant directory, and we will simply `cd` into it, and then `cd` into another folder called `spec-tests`. 
7.  We now run the command `gem install bundler`, which is a package manager for Ruby which manages and installs dependices needed by Ruby.
8.  We then use the command `bundle`, which will then bundle up all the tests.
9.  We then use `rake spec` to check what is installed and what isn't, in order to run this app. The first time I did `rake spec` I ran into an error, and to rectify this I used `gem list` to see which dependencies I had, and the one which was missing was `serverspec`, `gem install serverspec` into the terminal ended up fixing the error, and we re-ran `rake spec`
10.  Depending on what was installed or not, it will notify you what tests have passed or failed, and in our case it was: `nodejs, nodejs --version, pm2`.
11.  In our terminal we now run : 
  ```
  sudo apt-get install nodejs -y
sudo apt-get install python-software-properties
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install nodejs -y
```
This will install what is needed to pass the tests we previously had failed.

12.  After running `rake spec` we can see that they have now been passed and no fails present.
14.  On the GitBash terminal we enter the command :
`sudo npm install pm2 -g`, to install the package manager for Node.js applications
14.  We now `cd` into the `app` folder previously discussed and run `npm install`.
15.  And at last we run `node app.js` to deploy the app.
16.  To test if the app has deployed we take our previous ip and add `:3000` at the end and the end result should look something like this below.


![image](https://user-images.githubusercontent.com/129314018/232801602-98de8a87-55a4-4326-82dd-4ff1d5d1f1cc.png)


![image](https://user-images.githubusercontent.com/129314018/232799997-ecc89a58-b2cc-417d-8bd1-7a64816b2dcb.png)

# Automating


![image](https://user-images.githubusercontent.com/129314018/232823447-d13e617e-11e0-4d5a-a7db-31bb524eb17e.png)
![image](https://user-images.githubusercontent.com/129314018/232823616-03b876c2-0ecb-47e6-98ea-2bdc998fd570.png)





