Vagrant.configure(2) do |config|
  config.vm.box = "centos/7"

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
    ansible.sudo = "true"
  end


  config.vm.provider "virtualbox" do |v|
    v.memory = 256
  end

  config.vm.define "inetRouter" do |inetRouter|
    inetRouter.vm.network "private_network", ip: '192.168.255.1', adapter: 2, netmask: "255.255.255.252", virtualbox__intnet: "router-net"
    inetRouter.vm.hostname = "inetRouter"
  end

  config.vm.define "centralRouter" do |centralRouter|
    centralRouter.vm.network "private_network", ip: '192.168.255.2', adapter: 2, netmask: "255.255.255.252", virtualbox__intnet: "router-net"
    centralRouter.vm.network "private_network", ip: '192.168.0.1', adapter: 3, netmask: "255.255.255.240", virtualbox__intnet: "dir-net"
    centralRouter.vm.network "private_network", ip: '192.168.255.13', adapter: 4, netmask: "255.255.255.252", virtualbox__intnet: "router-net2"
    centralRouter.vm.hostname = "centralRouter"
  end    

  config.vm.define "centralServer" do |centralServer|
    centralServer.vm.network "private_network", ip: '192.168.0.2', adapter: 2, netmask: "255.255.255.240", virtualbox__intnet: "dir-net"
    centralServer.vm.hostname = "centralServer"
  end    

  config.vm.define "inetRouter2" do |inetRouter2|
    inetRouter2.vm.network "private_network", ip: '192.168.255.14', adapter: 8, netmask: "255.255.255.252", virtualbox__intnet: "router-net2"
    inetRouter2.vm.hostname = "inetRouter2"
  end
end     