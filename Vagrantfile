# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|


(1..2).each do |i|
config.vm.define "master#{i}", primary: true do |master|
  master.vm.box = "ubuntu/xenial64"
  master.vm.synced_folder ".", "/vagrant", disabled: true
  master.vm.hostname = "master#{i}"
  master.vm.network :private_network, ip: "192.168.1.1#{i}"
  master.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
  end
  master.vm.provision "docker" do |dock|
  end
end
end



    (1..2).each do |i|
    config.vm.define "slave#{i}" do |slave|
      slave.vm.box = "ubuntu/xenial64"
      slave.vm.synced_folder ".", "/vagrant", disabled: true
      slave.vm.hostname = "slave#{i}"
      slave.vm.network :private_network, ip: "192.168.1.2#{i}"
      slave.vm.provider "virtualbox" do |vb|
        vb.memory = "1024"
      end
      slave.vm.provision "docker" do |docknode|
      end
  end

end

end
