Vagrant.configure("2") do |config|
  servers=[
    {
      :hostname => "control",
      :box => "ubuntu/focal64",
      :ip => "192.168.57.10",
      :ssh_port => '2200'
    },
    {
      :hostname => "node1",
      :box => "ubuntu/focal64",
      :ip => "192.168.57.11",
      :ssh_port => '2201'
    },
    {
      :hostname => "node2",
      :box => "ubuntu/focal64",
      :ip => "192.168.57.12",
      :ssh_port => "2202"
    }
  ]

  servers.each do |machine|
    config.vm.define machine[:hostname] do |node|
      node.vm.box = machine[:box]
      node.vm.hostname = machine[:hostname]
      node.vm.network :private_network, ip: machine[:ip]
      node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
      # node.vm.provision "shell", path: "provision.sh"
      node.vm.provider :virtualbox do |vb|
        vb.customize ["modifyvm", :id, "--memory", 2048]
        vb.customize ["modifyvm", :id, "--cpus", 2]
      node.vm.disk :disk, size: "10GB", primary: true
      end
    end
  end
end













# Vagrant.configure("2") do |config|
#   config.vm.box = "ubuntu/focal64"

#   (1..3).each do |i|
#     config.vm.define "vm#{i}" do |node|

#       node.vm.hostname = "vm#{i}"

#       node.vm.network "forwarded_port", guest: 22, host: 2222 + i, id: "ssh"

#       node.vm.network "private_network", ip: "192.168.57.#{10 + i}", netmask: "255.255.255.0"

#       node.vm.provision "shell", path: "provision.sh"

#       # node.vm.provision "ansible" do |ansible|
#       #   ansible.playbook = "playbook.yml"
#       #   ansible.inventory_path = "hosts"
#       # end
#     end
#   end
# end
