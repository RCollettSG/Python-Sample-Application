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
