# Vmware
# -----------------------------------------------------------

# Vagrant.configure("2") do |config|
#   # Provisiing MongoDB
#   config.vm.define "mongodb" do |mongodb|
#     mongodb.vm.box = "spox/ubuntu-arm"
#     mongodb.vm.network "private_network", ip: ""
#     mongodb.vm.provider "vmware_fusion" do |vb|
#       config.vm.synced_folder "env/", "/home/vagrant/env" 
#     end
#     mongodb.vm.provision "shell", inline: <<-SHELL
#       systemctl disable apt-daily.service
#       systemctl disable apt-daily.timer
#       sudo apt remove unattended-upgrades -y
#     SHELL
#     mongodb.vm.provision "shell", path: "env/mongodb/script.sh"
#   end

#   # Provisioning NodeJS App
#   config.vm.define "nodeapp" do |nodeapp|
#     nodeapp.vm.box = "spox/ubuntu-arm"
#     nodeapp.vm.network "private_network", ip: ""
#     nodeapp.hostsupdater.aliases = ["nology.training"]
#     nodeapp.vm.provider "vmware_fusion" do |vb|
#       nodeapp.vm.synced_folder "app/", "/home/vagrant/app/"
#       nodeapp.vm.synced_folder "env/", "/home/vagrant/env"
#     end
#     nodeapp.vm.provision "shell", inline: <<-SHELL
#       systemctl disable apt-daily.service
#       systemctl disable apt-daily.timer
#       sudo apt remove unattended-upgrades -y
#     SHELL
#     nodeapp.vm.provision "shell", inline: "echo 'export DB_PATH=' >> /etc/profile.d/myvars.sh", run: "always"
#     nodeapp.vm.provision "shell", path: "env/nodeapp/script.sh"
#   end
# end

# Virtual Box4
# ------------------------------------------------------------

Vagrant.configure("2") do |config|
  # Provisiing MongoDB
  config.vm.define "mongodb" do |mysqldb|
    mysqldb.vm.box = "generic/ubuntu2010"
    mysqldb.vm.network "private_network", ip: ""
    mysqldb.vm.provider "virtualbox" do |vb|
      config.vm.synced_folder "env/", "/home/vagrant/env" 
    end
    mysqldb.vm.provision "shell", path: "env/mongodb/script.sh"
  end

  # Provisioning NodeJS App
  config.vm.define "nodeapp" do |nodeapp|
    nodeapp.vm.box = "generic/ubuntu2010"
    nodeapp.vm.network "private_network", ip: ""
    nodeapp.hostsupdater.aliases = ["nology.training"]
    nodeapp.vm.provider "virtualbox" do |vb|
      nodeapp.vm.synced_folder "app/", "/home/vagrant/app/"
      nodeapp.vm.synced_folder "env/", "/home/vagrant/env"
    end
    nodeapp.vm.provision "shell", inline: "echo 'export DB_PATH=' >> /etc/profile.d/myvars.sh", run: "always"
    nodeapp.vm.provision "shell", path: "app0916/env/nodeapp/script.sh"
  end
end
