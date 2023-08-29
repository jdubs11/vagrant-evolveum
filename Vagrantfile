Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-22.04"

  config.vm.provider :virtualbox do |v|
    v.gui = true
    v.name = "midpoint-vm"
    v.memory = 12288
    v.cpus = 4
  end

  # Set hostname
  config.vm.hostname = "midpoint-vm"

  config.vm.network "forwarded_port", guest: 8080, host: 8080  # midpoint

  # Currently "ubuntu/bionic64" on VirtualBox requires `type: "virtualbox"`
  # to make synced folder works.
  config.vm.synced_folder ".", "/home/vagrant/evolveum", type: "virtualbox"

  # Update repositories
  config.vm.provision :shell, inline: "sudo apt update -y"

  # Install ansible
  config.vm.provision :shell, inline: "sudo apt-get install -y ansible"

  config.vm.provision :shell, inline: "sudo usermod -a -G sudo vagrant"

  # Install openJDK 11, evolveum and start midpoint
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible/setup-midpoint.yml"
  end
end
