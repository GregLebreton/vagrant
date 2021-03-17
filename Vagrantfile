

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # General Vagrant VM configuration.
  # All VMs will run under centos7 exploitation system
  config.vm.box = "debian/jessie64"
  # If true, Vagrant will automatically insert a keypair
  # to use for SSH, replacing Vagrant's default insecure key
  # inside the machine if detected. By default, this is true
  config.ssh.insert_key = false
  # Configures synced folders on the machine, so that folders
  # on your host machine can be synced to and from the guest machine
  config.vm.synced_folder ".", "/vagrant", disabled: true
  # VM Provider
  config.vm.provider :virtualbox do |v|
  v.memory = 256
  v.linked_clone = true
  end

  # Apache server
  config.vm.define "apach" do |apach|
    apach.vm.hostname = "apach.dev"
     # static ip address
    apach.vm.network :private_network, ip: "192.168.60.2"
    #config.vm.provision "ansible" do |ansible|
      #ansible.playbook = "install_apache_playbook.yml"
      #ansible.playbook= "site.yml"
      #ansible.inventory_path="./inventory"
      #ansible.limit="apach"
      #end      
  end

  # Wordpress
  config.vm.define "wordpress" do |apach|
    apach.vm.hostname = "wordpress.dev"
     # static ip address
    apach.vm.network :private_network, ip: "192.168.60.3"
    #config.vm.provision "ansible" do |ansible|
      #ansible.playbook = "install_apache_playbook.yml"
      #ansible.playbook= "site.yml"
      #ansible.inventory_path="./inventory"
      #ansible.limit="apach"
      #end     
  end

  # MariaDB server
  config.vm.define "database" do |database|
    database.vm.hostname = "database.dev"
    # static ip address
    database.vm.network :private_network, ip: "192.168.60.4"
  #julconfig.vm.provision "ansible" do |ansible|
    #ansible.playbook = "install_mariadb_playbook.yml"
    #ansible.playbook= "site.yml"
    #ansible.inventory_path="./inventory"
    #ansible.limit="database"
    #end
  end
end
