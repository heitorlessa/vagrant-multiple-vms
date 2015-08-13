# Multiple VMs with Vagrant

This is a simple yet flexible Vagrantfile that parses a .yml file (servers.yml) in this example, where you should be able to pass the following:

  - name: VM Name 
  - box: Vagrant box (i.e hashicorp/precise32)
  - ram: Amount of memory you want to assign to this box
  - ip: defines if public network will be used, it accepts 'dhcp' or 'i.p.addr.ess'
  - playbook: path to Ansible playbook to use as a provisioner

### Credits

**Full credits to [Scott](http://blog.scottlowe.org/2014/10/22/multi-machine-vagrant-with-yaml/) where I 'hacked' the code from.**

### Installation

Make sure you already have [Vagrant installed](http://www.vagrantup.com/downloads.html), then format 'servers.yml' as following and ensure Vagrantfile is sitting alongside with this YAML file:

```sh
- name: nodejs
  box: hashicorp/precise32
  ram: 128
  ip: dhcp
  # playbook: "provisioning/vagrant/vagrant_server.yml"
# - name: openvpn-client01
#   box: hashicorp/precise32
#   ram: 128
#   playbook: "provisioning/vagrant/vagrant_client.yml"
#   ip: 172.16.100.14
```

**Note that '#' still applies as comments. The above will create a Vagrant VM called 'nodejs' with the above requirements and will ask what adapter you want to use for the public_network**

Vagrant official reference:

* [Managing multiple machines](http://docs.vagrantup.com/v2/multi-machine/)

### Development

Can't find Chef or Puppet or another particular option (Port forward)?? Great! 

Feel free to contribute by either forking or PR :)

License
----
MIT
