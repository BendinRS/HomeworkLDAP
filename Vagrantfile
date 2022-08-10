Vagrant.configure(2) do |config|
    config.vm.define "ldap" do |vmconfig|
      vmconfig.vm.box = 'centos/7'
      vmconfig.vm.hostname = 'ldap'
      vmconfig.vm.provider "virtualbox" do |vbx|
        vbx.memory = "2048"
        vbx.cpus = "2"
        vbx.customize ["modifyvm", :id, '--audio', 'none']
        end
        vmconfig.vm.provision "shell", run: "always", inline: <<-SHELL
        sudo apt-get update
        SHELL

      end
    end
