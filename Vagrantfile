# -*- mode: ruby -*-
# vi: set ft=ruby :
  Vagrant.configure("2") do |config|   
    config.vm.provision "shell", inline: "echo Hello"  
    
    config.vm.define "chefclient1" do |chefclient|
       chefclient.vm.box = "lucid32"
       chefclient.vm.network "private_network", ip: "192.168.100.133"
             chefclient.vm.network "public_network", bridge: 'en1: Wi-Fi (AirPort)'
    end 
    config.vm.define "chefclient2" do |chefclient|
           chefclient.vm.box = "lucid32"
	   chefclient.vm.network "private_network", ip: "192.168.100.134"
           chefclient.vm.network "public_network", bridge: 'en1: Wi-Fi (AirPort)'
	   end

    
    config.vm.define "redis" do |redis|     
     redis.vm.box = "centos64"    
     redis.vm.box_url = "http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.4-i386-v20131103.box"
     redis.vm.network "private_network", ip: "192.168.100.133"
      redis.vm.network "public_network", bridge: 'en1: Wi-Fi (AirPort)'
        redis.vm.provider "virtualbox" do |v|      
          v.customize ["modifyvm", :id, "--memory", 512]      
        end
      #redis.vm.provision :chef_solo do |chef|
      # chef.cookbooks_path = "cookbooks"
      # chef.add_recipe "redis"
      # chef.log_level = :debug
      # end 
    end
    
    config.vm.define "chefserver" do |chefserver|        
      chefserver.vm.box = "centos65"	     
      chefserver.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-6.5_chef-provisionerless.box"	     
      chefserver.vm.network "private_network", ip: "192.168.100.131"	     
      chefserver.vm.network "public_network", bridge: 'en1: Wi-Fi (AirPort)'		        
      chefserver.vm.provider "virtualbox" do |v|			      
      v.customize ["modifyvm", :id, "--memory", 1024]	 
      end
    end
end
