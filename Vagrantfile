Vagrant.configure(2) do |config|
    config.vm.define "ipaserver.bendin.local" do |vmconfig|
      vmconfig.vm.box = 'centos/7'
      vmconfig.vm.hostname = 'ipaserver.bendin.local'
      vmconfig.vm.provider "virtualbox" do |vbx|
        vbx.memory = "4500"
        vbx.cpus = "3"
        vbx.customize ["modifyvm", :id, '--audio', 'none']
        end
        vmconfig.vm.provision "shell", run: "always", inline: <<-SHELL
        echo "Go ansible"
        SHELL

      end
    end
