BOX_NAME = "bento/ubuntu-16.04"

K8S_MASTER_NUM = 3
K8S_NODE_NUM = 3

Vagrant.configure("2") do |config|
    config.ssh.insert_key = false

    config.vm.provider "virtualbox" do |v|
        v.memory = 1024
        v.cpus = 2
    end

    #k8s masters configuration
    (1..K8S_MASTER_NUM).each do |i|
      config.vm.define "master-#{i}" do |master|
        master.vm.box = BOX_NAME
        master.vm.network "private_network", ip: "192.168.50.#{i}"
        master.vm.hostname = "master-#{i}"
      end
    end

    #k8s nodes configuration
    (1..K8S_NODE_NUM).each do |i|
        config.vm.define "node-#{i}" do |node|
            node.vm.box = BOX_NAME
            node.vm.network "private_network", ip: "192.168.50.#{i + 10}"
            node.vm.hostname = "node-#{i}"
        end
    end

end
