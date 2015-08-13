
VAGRANTFILE_API_VERSION = "2"

require 'yaml'

servers = YAML.load_file('servers.yml')

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  servers.each do |servers|
    config.vm.define servers["name"] do |srv|
      srv.vm.box = servers["box"]
      case servers["ip"]
	when "dhcp"
	 srv.vm.network "public_network"
	else
	 srv.vm.network "public_network", ip: servers["ip"]
      end
      srv.vm.provider :virtualbox do |vb|
        vb.name = servers["name"]
        vb.memory = servers["ram"]
      if servers["playbook"]
        srv.vm.provision :ansible do |ansible|
          ansible.playbook = servers["playbook"]        
      end
      end
      end
    end
  end
end
