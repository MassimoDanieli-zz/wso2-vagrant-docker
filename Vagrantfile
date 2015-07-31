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

