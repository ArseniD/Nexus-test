# -*- mode: ruby -*-
# vi: set ft=ruby :

BOX_IMAGE = "sbeliakou/centos-7.4-x86_64-minimal"


Vagrant.configure("2") do |config|

  config.ssh.username = "root"
  config.ssh.password = "vagrant"
  config.vm.box = BOX_IMAGE

  config.vm.define :jenkins do |jenkins_config|
    jenkins_config.vm.hostname = "jenkins"
    jenkins_config.vm.network :private_network, ip: "10.0.0.10"
    jenkins_config.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.name = "jenkins"
    end

    jenkins_config.vm.provision "shell", path: "provision_jenkins.sh"
    jenkins_config.vm.provision "file", source: "setting_nexus.xml", destination: "/opt/setting_nexus.xml"

  end


  config.vm.define :nexus do |nexus_config|
    nexus_config.vm.hostname = "nexus"
    nexus_config.vm.network :private_network, ip: "10.0.0.11"
    nexus_config.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.name = "nexus"
    end

    nexus_config.vm.provision "shell", path: "provision_nexus.sh"

  end

end
