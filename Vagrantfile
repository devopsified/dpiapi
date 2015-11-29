# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

    config.vm.box = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_ubuntu-14.04_chef-provisionerless.box"
    config.vm.box_check_update = false
    config.berkshelf.enabled = true
    config.berkshelf.berksfile_path = 'Berksfile'
    config.vm.boot_timeout = 600
    config.vm.network  :forwarded_port, guest: 8080, host: 8800, id: "jenkins", auto_correct: true
    config.vm.network  :forwarded_port, guest: 80, host: 8888, id: "jenkins-proxy", auto_correct: true
    config.vm.network  :forwarded_port, guest: 443, host: 443, id: "dpi_api", auto_correct: true
    config.vm.synced_folder "codebase/", "/opt/data/dpi_api", create: true, owner: "vagrant", group: "vagrant"

    config.vm.provider "virtualbox" do |v|
#      v.gui = true
       v.memory = 2048
       v.name = 'dpi_vagrant_linux'

       v.customize ['modifyvm', :id, '--cpuexecutioncap', '100']
       v.customize ['modifyvm', :id, '--cpuhotplug', 'on']
       v.customize ['modifyvm', :id, '--cpus', 2]
       v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    #      v.customize ['modifyvm', :id, '--plugcpu', '1']
    end

   config.vm.provision :chef_solo do |chef|
#           chef.cookbooks_path = ["site-cookbooks"]
       chef.data_bags_path = ["data_bags"]
       chef.roles_path = ["roles"]
       chef.environments_path = ["environments"]

       chef.environment = 'dev'

       # Use 'doc' for very verbose output. Use 'min' for rspec style dots and letters.
       #chef.arguments = '-F doc'
       chef.log_level = :debug

#       chef.add_recipe 'linux_base::default'
#       chef.add_recipe 'api_server::default'
#       chef.add_recipe 'dpi_composer::configure'
#	   chef.add_recipe 'dpi_nginx::default'
#       chef.add_recipe 'user'
       #chef.add_recipe 'dpi_nginx::jenkins'
       #chef.add_recipe 'dpi_jenkins::default'
#       chef.add_recipe 'dpi_mysql::default'
#       chef.add_recipe 'elasticache::default'
   end

end
