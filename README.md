vagrant-oradb-12.1
==================

##Details
- Oracle Linux 6.5 vagrant box
- Puppet 3.6.2
- Vagrant >= 1.41
- Oracle Virtualbox >= 4.3.6 

##Setup
Add the Oracle binaries to the /software share

edit Vagrantfile and update the software share
- oradb.vm.synced_folder "/Users/edwin/software", "/software"

###Satabase software
- linuxamd64_12c_database[1-2].zip

###Setup puppet modules from the desktop
-gem install librarian-puppet
-cd puppet
-rm -rf modules
-librarian-puppet install

## Startup the database server  
vagrant up

##user accounts
- OS oracle, pw oracle
- OS vagrant, pw vagrant
- Oracle db sys, pw Welcome01
