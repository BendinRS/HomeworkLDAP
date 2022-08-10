Vagrant.configure(2) do |config|
    config.vm.define "ipaserver" do |vmconfig|
      vmconfig.vm.box = 'centos/7'
      vmconfig.vm.hostname = 'ipaserver'
      vmconfig.vm.provider "virtualbox" do |vbx|
        vbx.memory = "2048"
        vbx.cpus = "2"
        vbx.customize ["modifyvm", :id, '--audio', 'none']
        end
        vmconfig.vm.provision "shell", run: "always", inline: <<-SHELL
        echo "Go ansible"
        SHELL

      end
    end
