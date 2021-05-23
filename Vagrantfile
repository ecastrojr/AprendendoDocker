BOX_IMAGE = "generic/ubuntu2004"
NODE_COUNT = 2

Vagrant.configure("2") do |config|
    config.vm.define "manager" do |subconfig|
        subconfig.vm.box = BOX_IMAGE
        subconfig.vm.hostname = "manager"
    end

    (1..NODE_COUNT).each do |i|
      config.vm.define "worker#{i}" do |subconfig|
        subconfig.vm.box = BOX_IMAGE
        subconfig.vm.hostname = "worker#{i}"
      end
     end

  config.vm.provider :libvirt do |libvirt|
      libvirt.cpus = 2
      libvirt.memory = 4096
  end
end    
