Vagrant.configure('2') do |config|

  config.vm.hostname = 'wharehauora-server'
  config.vm.box      = 'centos/7'
  config.vm.network :private_network, ip: "10.10.10.10"
  config.vm.network :forwarded_port, guest: 3000, host: 3000
  
  config.vm.provider 'virtualbox' do |v|
    v.memory = 2048
    v.cpus = 2
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.verbose = true
    ansible.version = "2.3.1.0"
    ansible.install_mode = "pip"
    ansible.playbook = "wharehauora.yml"
    ansible.inventory_path = "inventory"
    ansible.limit = "all"
  end
end
