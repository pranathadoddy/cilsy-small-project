Vagrant.configure("2") do |config|
  config.vm.provision "shell", inline: "apt-get update -y  "
 
  config.vm.define "webserver" do |webserver|
    webserver.vm.provision "shell", inline: "sudo apt-get install git -y"
    webserver.vm.provision "shell", path: "shell/install-webserver.sh"
    webserver.vm.box = "ubuntu/xenial64"
    webserver.vm.network "private_network",ip: "192.168.100.4"
      webserver.vm.provider "virtualbox" do |v|
        v.memory = 512
        v.cpus = 2
     end
  end

  config.vm.define "database" do |database|
    database.vm.box = "ubuntu/xenial64"
    database.vm.provision "shell", path: "shell/install-databaseserver.sh"
    database.vm.network "private_network",ip: "192.168.100.2"
      database.vm.provider "virtualbox" do |v|
        v.memory = 512
        v.cpus = 2
     end
  end
end
