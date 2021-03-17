                                   ### VAGRANT ###
                                          
  
 prérequis: 
    
    - Virtualbox ou VMWare
  
installation Vagrant:   

    $ sudo curl -O https://releases.hashicorp.com/vagrant/2.2.6/vagrant_2.2.6_x86_64.deb

    $ sudo apt install ./vagrant_2.2.6_x86_64.deb
    
    $ sudo rm -rf vagrant_2.2.6_x86_64.deb

    $ vagrant --version
    
Utilisation Vagrant:

    $ git clone https://github.com/GregLebreton/vagrant.git
    
    $ cd vagrant
    
    $ vagrant up
