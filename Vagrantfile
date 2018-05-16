Vagrant.configure("2") do |config|

  config.vm.box = "centos/7"

  config.vm.provider :libvirt do |libvirt|
    libvirt.cpus = 2
    libvirt.memory = 4096
  end

  config.vm.define "tower0" do |tower0|
    tower0.vm.hostname = "tower0.example.com"
    tower0.vm.network "private_network", ip: "10.0.0.10"
    tower0.vm.provision :ansible_local do |ansible_local|
      ansible_local.playbook = "site.yml"
      ansible_local.become = true
      ansible_local.raw_arguments = [
        "--extra-vars=vars.yml"
      ]
    end
  end

  config.vm.define "tower1" do |tower1|
    tower1.vm.hostname = "tower1.example.com"
    tower1.vm.network "private_network", ip: "10.0.0.11"
  end

  config.vm.define "tower2" do |tower2|
    tower2.vm.hostname = "tower2.example.com"
    tower2.vm.network "private_network", ip: "10.0.0.12"
  end

  config.vm.define "postgresql0" do |postgresql0|
    postgresql0.vm.hostname = "postgresql0.example.com"
    postgresql0.vm.network "private_network", ip: "10.0.0.100"
  end

  config.vm.define "postgresql1" do |postgresql1|
    postgresql1.vm.hostname = "postgresql1.example.com"
    postgresql1.vm.network "private_network", ip: "10.0.0.101"
  end

end
