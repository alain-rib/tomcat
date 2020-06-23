Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"
  config.vbguest.auto_update = false
  config.vm.network "private_network", ip: "192.168.33.21"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
    vb.cpus = 2
  end   
  config.vm.provision "ansible_local" do |ansible|
    ansible.compatibility_mode = "2.0"
    ansible.extra_vars = { ansible_python_interpreter:"/usr/bin/python3.6" }
    ansible.become = true
    ansible.playbook = "playbook.yml"
    ansible.galaxy_role_file = "requirements.yml"
    ansible.galaxy_roles_path = "/etc/ansible/roles"
    ansible.galaxy_command = "sudo ansible-galaxy install --role-file=%{role_file} --roles-path=%{roles_path} --force"
  end
end
