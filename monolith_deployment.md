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

`sudo apt-get update -y`: Updates the package lists from the repositories.

`sudo apt-get upgrade -y`: Upgrades the installed packages to their latest version.

`sudo apt-get install nginx -y`: Installs the Nginx web server.

`sudo service nginx start`: Starts the Nginx web server.

`sudo apt-get install python-software-properties -y`: Installs the necessary software properties for adding new PPA repositories. PPA ( PERSONAL PACKAGE ARCHIVE)

`curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash`: Downloads and runs a script that adds the Node.js repository to the package sources.

`sudo apt-get install nodejs -y`: Installs Node.js.

`sudo npm install pm2 -g`: Installs PM2, a process manager for Node.js applications.

`cd app`: Changes the current directory to the "app" directory.

`npm install`: Installs the dependencies for the Node.js application in the "app" directory.

`npm start`: Starts the Node.js application in the "app" directory.

![image](https://user-images.githubusercontent.com/129314018/232823616-03b876c2-0ecb-47e6-98ea-2bdc998fd570.png)

# How to run a process as a background process in Linux

* To run a process as a background process in Linux we type the command which should be followed by `&`
  * For example : `npm install &` - will start Node.js application in the background and return control to the user.

### Running PM2 as a background process

[ERRORS]
* We follow the steps we did before and we add an `&` at the end of the `npm install`, which will now start the app with the pm2 process manager, but a key different from before is it will now run in the background
* All the while giving us control, as opposed to before.


[IMPORVEMENTS]

**When using this method `&` we do in fact go through errors, as the process can terminate when you exit the terminal**

**We instead use `pm2 start app.js` but to use this we must change our node support version whcih was ay 6.x to 16.x and the code for that is:**

`curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -`

![image](https://user-images.githubusercontent.com/129314018/233321285-226b46bd-cac4-4c53-a54a-2fc9068adf1f.png)

* When running through the app again `vagrant up` and `vagrant ssh`, it should launch both virtual machines we had previously made without it hanging, as this gives back control to the user, and should look something like this: 

![image](https://user-images.githubusercontent.com/129314018/233325101-b5634120-ae96-4f90-bf7b-39276f1fd0a6.png)

# Connect `app` VM to `db` VM using environmental variable?

1. From the previous steps, we remove `pm2 start app.js` as it can interfere with it from the `app` shell script
2. We `vagrant up` then `vagrant ssh app` and `vagrant ssh db` to access both virtual machines


![image](https://user-images.githubusercontent.com/129314018/233373798-b140d81c-8d36-45ba-bfea-f9f8b7f7fd0a.png)


3. On our `db` virtual machine we use command `sudo nano /etc/mongod.conf`, once we enter the nano editor
we change the `bindIP` to 0.0.0.0 (scroll down)

![image](https://user-images.githubusercontent.com/129314018/233374170-e3dd6dd7-351e-464a-a6d7-180ff4f439c8.png)

4. Save and exit by doing these in order, `CTRL + X` -> `y` -> `Enter`
5. On the `app` we use `sudo nano .bashrc` and we add at the end of the file `export DB_HOST=mongodb://192.168.10.150:27017/posts` - check if DB_HOST is on right ip address
6. `CTRL X` `Y` `ENTER`, to save.
7. `source .bashrc - this runs the bashrc file and applies changes
8.  Now we enter command ` printenv DB_HOST`, and then `cd` into our app directory
9.  `npm install` - we manually install app now due to the reason we got rid of `pm2 start app.js`


![image](https://user-images.githubusercontent.com/129314018/233376306-39d6f3d5-77e4-4c75-9751-6b988629ecad.png)

8. When you see the Database cleared and seeded as shown above we run the following 2 commands:
   * `node seeds/seed.js` and `node app.js` - which will seed the database and run the app


9. If all is well we should recieve the following output from the `db` virtual machine as shown below

![image](https://user-images.githubusercontent.com/129314018/233376768-1f901a56-efa5-4cd2-a550-dda56ce8339a.png)

10. Lastly, to test whether it works, we will type `192.168.10.100:3000/posts` - to see if it carried over
![image](https://user-images.githubusercontent.com/129314018/233376930-cf0bf893-e511-4adf-aea9-68f806c95f6f.png)


















