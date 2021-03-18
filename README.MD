                                            ### VAGRANT ###
                                          
  
 prérequis: 
    
    - Virtualbox 6.0 ou VMWare
  
installation Vagrant:   

    $ sudo curl -O https://releases.hashicorp.com/vagrant/2.2.6/vagrant_2.2.6_x86_64.deb

    $ sudo apt install ./vagrant_2.2.6_x86_64.deb
    
    $ sudo rm -rf vagrant_2.2.6_x86_64.deb

    $ vagrant --version
    
Utilisation Vagrant:

    $ git clone https://github.com/GregLebreton/vagrant.git
    
    $ cd vagrant
    
    $ vagrant up
    
Vous devriez avoir des flags verts vous indiquant que les 3 VM sont fonctionnelles.
éffectuez une connection SSH à l'une des VM:

    $ sudo vagrant ssh apach
 
 
Vous êtes désormais sur le terminal de la machine apach en tant qu'utilisateur vagrant.    

```

```

Troobleshooting:

Pour Debian 10 (kernel 5.09 / 5.10)
ces versions ne sont compatible avec Virtualbox qu'à partir de la 6.1. Il faut donc ajouter cette version dans les 
providers de Vagrant:

```
    $ sudo nano /opt/vagrant/embedded/gems/2.2.6/gems/vagrant-2.2.6/plugins/providers/virtualbox/driver/meta.rb

    @logger.debug("Finding driver for VirtualBox version: #{@@version}")

          driver_map   = {

          "4.0" => Version_4_0,

          "4.1" => Version_4_1,

          "4.2" => Version_4_2,

          "4.3" => Version_4_3,

          "5.0" => Version_5_0,

          "5.1" => Version_5_1,

          "5.2" => Version_5_2,

          "6.0" => Version_6_0,

          "6.1" => Version_6_1,

          }
          
```
Copier le fichier "version_6_1.rb" dans les dossier des drivers de VB:
```
      $ cp kernel_5.10/version_6_1.rb /opt/vagrant/embedded/gems/2.2.6/gems/vagrant-2.2.6/plugins/providers/virtualbox/driver/


      $ nano /opt/vagrant/embedded/gems/2.2.6/gems/vagrant-2.2.6/plugins/providers/virtualbox/plugin.rb
```

Dans "module Driver" ajouter la derniere ligne:

```
# our drivers only when they are needed.

module Driver

  autoload :Meta, File.expand_path("../driver/meta", __FILE__)

  autoload :Version_4_0, File.expand_path("../driver/version_4_0", __FILE__)

  autoload :Version_4_1, File.expand_path("../driver/version_4_1", __FILE__)

  autoload :Version_4_2, File.expand_path("../driver/version_4_2", __FILE__)

  autoload :Version_4_3, File.expand_path("../driver/version_4_3", __FILE__)

  autoload :Version_5_0, File.expand_path("../driver/version_5_0", __FILE__)

  autoload :Version_5_1, File.expand_path("../driver/version_5_1", __FILE__)

  autoload :Version_5_2, File.expand_path("../driver/version_5_2", __FILE__)

  autoload :Version_6_0, File.expand_path("../driver/version_6_0", __FILE__)

  autoload :Version_6_1, File.expand_path("../driver/version_6_1", __FILE__)

end
```

Vagrant connait désormais VB 6.1 comme provider!
