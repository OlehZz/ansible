Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/bionic64"
  #config.vm.box_check_update = false
  #config.ssh.insert_key = false

  # 1 VM
  config.vm.define "ansible" do |subconfig|
    # setup
    subconfig.vm.provider "virtualbox" do |vb|
      vb.name = "ansible"
      vb.memory = "2048"
  end
    # hostname
    subconfig.vm.hostname = "ansible"
    # network
    subconfig.vm.network "private_network", ip: "192.168.53.3"
    # install
#    subconfig.vm.provision "ansible", type: "shell", inline: "apt-get install -y ansible"
  end

  # 2 VM
  config.vm.define "web-server" do |subconfig|
    # name
    subconfig.vm.provider "virtualbox" do |vb|
      vb.name = "web-server"
      vb.memory = "2048"
    end
    # hostname
    subconfig.vm.hostname = "web-server"
    # network
    subconfig.vm.network "private_network", ip: "192.168.53.4"
    # install
#    subconfig.vm.provision "mysql", type: "shell", inline: "apt-get install -y mysql-server"
  end
  
  # update system (for both)
  config.vm.provision "update", type: "shell", inline: "apt-get update && apt-get upgrade -y"
end
