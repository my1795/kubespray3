Vagrant.configure("2") do |config|
  config.vm.box = "geerlingguy/ubuntu2004"

  ip_prefix = '192.168.37.1'

  config.vm.define "ansible" do |ansible|
    ansible.vm.hostname = "ansible"
    ansible.vm.network "private_network", ip: "#{ip_prefix}0"
    
    ansible.vm.provision "shell", inline: "cp /vagrant/keys/id_rsa /home/vagrant/.ssh/id_rsa"
    ansible.vm.provision "shell", inline: "chmod 600 /home/vagrant/.ssh/id_rsa && chown vagrant:vagrant /home/vagrant/.ssh/id_rsa"

    ansible.vm.provision "shell", inline: "apt-get update && apt-get install -y python3-pip"

    ansible.vm.provider :virtualbox do |v|
      v.memory = 2048
      v.cpus = 2
      v.linked_clone = true
    end
  end

  (0..0).each do |i|
    config.vm.define "ctrl-node-0#{i}" do |ctrl|
      ctrl.vm.hostname = "ctrl-node-0#{i}"
      ctrl.vm.network "private_network", ip: "#{ip_prefix}0#{i}"

      ctrl.vm.provision "shell", inline: "cat /vagrant/keys/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys"

      ctrl.vm.provider :virtualbox do |v|
        v.memory = 2048
        v.cpus = 2
        v.linked_clone = true
      end
    end
  end

  (0..1).each do |i|
    config.vm.define "worker-node-0#{i}" do |worker|
      worker.vm.hostname = "worker-node-0#{i}"
      worker.vm.network "private_network", ip: "#{ip_prefix}1#{i}"

      worker.vm.provision "shell", inline: "cat /vagrant/keys/id_rsa.pub >> /home/vagrant/.ssh/authorized_keys"

      worker.vm.provider :virtualbox do |v|
        v.memory = 4096
        v.cpus = 2
        v.linked_clone = true
      end
    end
  end
end
