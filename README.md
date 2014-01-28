# Vagrantfile for couchdb #

This vangrantfile is for use with my [chef-cookbook recipe repository](https://github.com/chrisekelley/chef-cookbooks),
which builds couchdb 1.5 from source.

## Squid proxy

    chef.add_recipe("squid")

Add [vagrant-proxyconf](https://github.com/tmatilai/vagrant-proxyconf) plugin to Vagrant.

Add the following code to your Vagrantfile:

    if Vagrant.has_plugin?("vagrant-proxyconf")
      config.proxy.http     = "http://10.0.2.15:3128/"
      config.proxy.https    = "http://10.0.2.15:3128/"
    #  config.proxy.no_proxy = "localhost,127.0.0.1,.example.com"
    end

