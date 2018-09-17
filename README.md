
#Mhaventhan
# Instructions To Developers

To install a virtual system for DevOps you'll need to follow the following steps as instructed below.

### Install Vagrant

To install vagrant you need to select the right operating system that you would like to install it on. https://www.vagrantup.com/downloads.html

Once you've completed installation successfully, to verify completion on Terminal enter

``vagrant --version``


### Install VirtualBox

To install VirtualBox you need to once again select the operating system you would like to install it on. Under the VirtualBox 5.2.18 platform packages
https://www.virtualbox.org/wiki/Downloads

### To set up a virtual environment through Terminal on Mac OSX

``Vagrant init ubuntu/xenial64``
``Vagrant up``

This will allow you to build and maintain a portable virtual  operating system in Linux Ubuntu

Once Vagrant file has been created open an text editor and enter the following code snip pit under the Vagrantfile

``Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network("private_network", ip: "192.168.10.100")
  config.hostsupdater.aliases = ["development.local"]
end
``

``Vagrant ssh``

This will allow you secure shell access to the virtual machine's terminal.

Then you need to update Ubuntu using the following command

`Sudo apt-get update -y``

Once the virtual machine has been successfully updated.You need to install Nginx using the following command below

``Sudo apt-get install nginx``

Nginx is a web server that will run on the virtual machine allowing you to host the web application.






# Sparta Node Sample App

## Description

This app is intended for use with the Sparta Global Devops Stream as a sample app. You can clone the repo and use it as is but no changes will be accepted on this branch.

To use the repo within your course you should fork it.

The app is a node app with three pages.

### Homepage

``localhost:3000``

Displays a simple homepage displaying a Sparta logo and message. This page should return a 200 response.

### Blog

``localhost:3000/posts``

This page displays a logo and 100 randomly generated blog posts. The posts are generated during the seeding step.

This page and the seeding is only accessible when a database is available and the DB_HOST environment variable has been set with it's location.

### A fibonacci number generator

``localhost:3000/fibonacci/{index}``

This page has be implemented poorly on purpose to produce a slow running function. This can be used for performance testing and crash recovery testing.

The higher the fibonacci number requested the longer the request will take. A very large number can crash or block the process.


### Hackable code

``localhost:3000/hack/{code}``

There is a commented route that opens a serious security vulnerability. This should only be enabled when looking at user security and then disabled immediately afterwards

## Usage

Clone the app

```
npm install
npm start
```

You can then access the app on port 3000 at one of the urls given above.

## Tests

There is a basic test framework available that uses the Mocha/Chai framework

```
npm test
```

The test for posts will fail ( as expected ) if the database has not been correctly setup.
