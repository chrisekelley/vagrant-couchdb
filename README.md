# Vagrantfile for couchdb #

This vangrantfile is for use with my [chef-cookbook recipe repository](https://github.com/chrisekelley/chef-cookbooks),
which builds couchdb 1.5 from source.

The source from this Vagrantfile is from the [CouchDB source](https://apache.googlesource.com/couchdb/+/1.5.0/Vagrantfile).
It installs erlang and other development apps. My modification of this file points to my recipe for building CouchDB from source.
This recipe includes providers for amazon, rackspace, and others; I'm using the virtualbox provider. You don't have to do anything
special to use the virtualbox provider. Just run "vagrant up" and it will install the needful.

## Couchdb

The Vagrantfile does a port forwarding so that you may access the VM couchdb instance from your browser at

http://localhost:5999/_utils/

Code:

    config.vm.network :forwarded_port, guest: 5984, host: 5999

## Squid proxy

    chef.add_recipe("squid")

Add [vagrant-proxyconf](https://github.com/tmatilai/vagrant-proxyconf) plugin to Vagrant.

Add the following code to your Vagrantfile:

    if Vagrant.has_plugin?("vagrant-proxyconf")
      config.proxy.http     = "http://10.0.2.15:3128/"
      config.proxy.https    = "http://10.0.2.15:3128/"
    #  config.proxy.no_proxy = "localhost,127.0.0.1,.example.com"
    end

