## Get the source

- `$ git clone git@github.com:builddoctor/CiForTheWorld.git`
- `$ cd CiForTheWorld`

## (optional) install rvm

## Install bundler
`$ gem install bundler`

## Install relate gems
`$ bundle install`

This installs:

- veewee
- vagrant
- mccloud

## Create a basebox with veewee

https://github.com/jedi4ever/veewee

*Demo:*

- `$ vagrant basebox define 'ubuntu64' 'ubuntu-10.10-server-i386'

*Speaker:*

- this will download iso
- show contents of definitions/ubuntu64/

*Demo:*

- `$ vagrant basebox build ubuntu64`
- `$ vagrant basebox validate ubuntu64`
- `$ vagrant basebox export 'ubuntu64`

## Add the basebox to vagrant

*Demo:*

- `$ vagrant basebox add 'ubuntu64' 'ubuntu64.box'

*Speaker:*

- show contents of $HOME/.vagrant

## Create a vagrant project

*Demo:*

- `$ vagrant init 'ubuntu64'`

*Speaker:*

- show contents of Vagrantfile and show ubuntu64 link


## Start vm

*Speaker:*

- start Virtualbox and see how it is created


*Demo:*

- `$ vagrant up`

*Demo:*

- `$ vagrant ssh`

## Create webserver (via chef)

*Demo:*

- `$ cp Vagrantfile.webserver Vagrantfile`

*Speaker:*

- show Vagrantfile 
- show apache recipe in chef-repo/cookbooks
- show site recipe in chef-repo/site-cookbooks

*Demo:*

- `$ vagrant reload`
- `$ vagrant provision`

## Create jenkins vm (puppet)

*Demo:*

- `$ cp Vagrantfile.jenkins Vagrantfile`
- `$ vagrant provision`

@builddoctor - add puppet manifests to the puppet-repo dir 
@builddoctor - the jenkins file contains a sample setup for puppet , feel free to change 

## Setup app in jenkins

@builddoctor - maybe we need to split this into 4 git repo's 
	- ciForTheWorld-vagrant
	- ciForTheWorld-chef
	- ciForTheWorld-puppet
	- ciForTheWorld-app
	- ciForTheWorld-mccloud 
	
After all this is how it works in reality in that way we can trigger jenkins if any of these projects change

## Run tests (cucumber-nagios)

- [http://www.jedi.be/blog/2011/03/29/vagrant-testing-testing-one-two/](http://www.jedi.be/blog/2011/03/29/vagrant-testing-testing-one-two/)

## Deploy in production with (mccloud) 

*Speaker:*

- Show mccloudfile (demo1, demo2)

*Demo:*

- `$ cp Vagrantfile.app Vagrantfile`
- `$ mccloud up demo1`
- `$ mccloud up demo2`

*Speaker:*

- Change the version and reprovision

*Demo:*

- `$ mccloud provision demo1`
- `$ mccloud provision demo2`

## Demo loadbalancing in production with (mccloud) 

*Speaker:*

- show the definition of the loadbalancer

*Demo:*

- `$ mccloud loadbalance`

*Speaker:*

- remove one server from config file

- `$ mccloud loadbalance`

