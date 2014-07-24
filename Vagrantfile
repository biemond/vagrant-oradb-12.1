# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "OEL6_5"

  config.vm.hostname = "oradb.example.com"
  config.vm.network :private_network, ip: "10.10.10.5"

  config.vm.synced_folder "." , "/vagrant", :mount_options => ["dmode=777","fmode=777"]
  config.vm.synced_folder "/Users/edwin/software", "/software"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "2532"]
    vb.customize ["modifyvm", :id, "--name"  , "oradb"]
    vb.customize ["modifyvm", :id, "--cpus"  , 2]
  end

  config.vm.provision :shell, :inline => "ln -sf /vagrant/puppet/hiera.yaml /etc/puppet/hiera.yaml;rm -rf /etc/puppet/modules;ln -sf /vagrant/puppet/modules /etc/puppet/modules"
  
  config.vm.provision :puppet do |puppet|
    puppet.manifests_path    = "puppet/manifests"
    puppet.module_path       = "puppet/modules"
    puppet.manifest_file     = "oradb.pp"
    puppet.options           = "--verbose --hiera_config /vagrant/puppet/hiera.yaml"

    puppet.facter = {
      "environment" => "development",
      "vm_type"     => "vagrant",
    }
    
  end

end
