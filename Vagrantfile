VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.box_check_update = false
  config.vm.network "public_network",
    use_dhcp_assigned_default_route: true
  config.vm.network "forwarded_port", guest: 5000, host: 5000
  config.vm.hostname = "webapp"
  config.vm.provision :"ansible_local" do |ansible|
#    ansible.install = true
    ansible.playbook = "playbook.yml"
#    ansible.install_mode = "pip"
#    ansible.version = "2.2.1.0"
  end

end
