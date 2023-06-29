Vagrant.configure("2") do |config|
  # Web Server VM
  config.vm.define "web" do |web|
    web.vm.box = "ubuntu/focal64"
    web.vm.network "private_network", ip: "192.168.33.11"
    web.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end

  # Database Server VM
  config.vm.define "database" do |database|
    database.vm.box = "ubuntu/focal64"
    database.vm.network "private_network", ip: "192.168.33.12"
    database.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
  end

  # Control VM
  config.vm.define "control" do |control|
    control.vm.box = "ubuntu/focal64"
    control.vm.network "private_network", ip: "192.168.33.10"
    control.vm.provision "ansible" do |ansible|
      ansible.playbook = "playbook.yml"
    end
    control.vm.provision "ansible_local" do |ansible_local|
      ansible_local.playbook = "playbook-control.yml"
      ansible_local.limit = "all"
      ansible_local.inventory_path = "inventory.ini"
    end
  end
end