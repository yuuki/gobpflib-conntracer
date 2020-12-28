# Validate environment
['vagrant-reload', 'vagrant-vbguest'].each do |plugin|
  unless Vagrant.has_plugin?(plugin)
    raise "Vagrant plugin #{plugin} is not installed!"
  end
end

Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2010"
  config.vm.provision :shell, :privileged => false, :path => "provisioning/setup_dev.sh"
  config.vm.synced_folder "./", "/home/vagrant/gobpf-conntracer", mount_options: ['dmode=777','fmode=777']
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2500"
  end
end
