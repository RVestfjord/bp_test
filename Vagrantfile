Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.network "private_network", type: "dhcp"
  
  config.vm.provision "shell" do |s|
    s.binary = true
    s.inline = " yum install -y epel-release; \
                 yum install -y ansible python-pip python wheel; \
                 ansible-playbook playbook.yml"
  end
end
