VAGRANTFILE_API_VERSION = "2"

Vagrant.require_version ">= 1.6.3"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "default" do |default|
    default.vm.box = "yungsang/boot2docker"
    default.vm.network "private_network", ip: "192.168.11.11"
    default.vm.network "forwarded_port", guest: 9443, host: 9443
    default.vm.network "forwarded_port", guest: 9445, host: 9445
    default.vm.synced_folder ".", "/var/www", type: "nfs"

    default.vm.provider "virtualbox" do |virtualbox|
      virtualbox.memory = 2048

    end

    default.vm.provision "docker" do |docker|
     # docker.build_image "/var/www/config/environment/docker/nginx", args: "-t vagrantdocker/nginx"
     # docker.build_image "/var/www/config/environment/docker/phpfpm", args: "-t vagrantdocker/phpfpm"
    end

#       default.ssh.insert_key = false
#    default.ssh.username = "docker"
#    default.ssh.password = "docker"
  end

  ##
  # A pretty simple scenario. The following is the simplest Docker container that could work. The application is
  # composed of only a single container
  ##

### ESB
  config.vm.define "esb", autostart: true do |esb|
    esb.vm.provider "docker" do |docker|
      docker.image = "massimodanieli/wso2esb"

      docker.ports = %w(9443:9443)

      docker.vagrant_vagrantfile = __FILE__
    end
  end
### APi Manager
config.vm.define "am", autostart: true do |apim|
    apim.vm.provider "docker" do |docker|
      docker.image = "massimodanieli/wso2apim"

      docker.ports = %w(9445:9443)

      docker.vagrant_vagrantfile = __FILE__
    end
  end


end
