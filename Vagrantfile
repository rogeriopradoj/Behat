# -*- mode: ruby -*-
# vi: set ft=ruby :

# Requires `vagrant-berkshelf` plugin for Vagrant
unless Vagrant.has_plugin?('vagrant-berkshelf') and Vagrant.has_plugin?('vagrant-omnibus')
  msg = <<MSG
=====

 \033[31mABORT:\033[0m this project requires these plugins:
    - vagrant-berkshelf
    - vagrant-omnibus

 You can install them via:

    $ vagrant plugin install vagrant-berkshelf; vagrant plugin install vagrant-omnibus

=====
MSG
  abort(msg) 
end

Vagrant.configure("2") do |config|
  config.omnibus.chef_version = :latest
  config.berkshelf.enabled = true

  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"

  config.vm.provision :chef_solo do |chef|
    chef.add_recipe "apt"
    chef.add_recipe "php5_ppa::from_ondrej"
    chef.add_recipe "php"
 
    chef.json = {}
  end
end
