# Install required plugins
required_plugins = ["vagrant-hostsupdater", "vagrant-berkshelf"]
required_plugins.each do |plugin|
  unless Vagrant.has_plugin? plugin
    puts "Installing vagrant plugin #{plugin}"
    # Use vagrant plugin manager to install all plugins
    Vagrant::Plugin::Manager.instance.install_plugin(plugin)
    puts "Installed vagrant plugin #{plugin}"
  end
end

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network("private_network", ip: "192.168.10.100")
  config.hostsupdater.aliases = ["development.local"]
  config.vm.synced_folder("./", "/home/vagrant/app" )
  config.vm.provision("chef-solo") do |chef|
    chef.add_recipe("python::default")
  end
  config.vm.provision("chef-solo") do |chef|
    chef.add_recipe("nginx::default")
  end
end
