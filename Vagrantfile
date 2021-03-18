

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "debian/jessie64"
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true
  # VM Provider
  config.vm.provider :virtualbox do |v|
  v.memory = 256
  v.linked_clone = true
  end

  # Nginx server
  config.vm.define "nginxserver" do |nginx|
    nginx.vm.hostname = "nginx.dev"
     # static ip address
    nginx.vm.network :private_network, ip: "192.168.60.2"     
  end

  # Wordpress
  config.vm.define "wordpress" do |wordpress|
    wordpress.vm.hostname = "wordpress.dev"
     # static ip address
    wordpress.vm.network :private_network, ip: "192.168.60.3"    
  end

  # MariaDB server
  config.vm.define "database" do |database|
    database.vm.hostname = "database.dev"
    # static ip address
    database.vm.network :private_network, ip: "192.168.60.4"
  end
end
