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
  config.vm.synced_folder "..", "/home/vagrant/evolveum", type: "virtualbox"

  # Add Google Chrome repository
  # config.vm.provision :shell, inline: "wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub|sudo apt-key add -"
  # config.vm.provision :shell, inline: "sudo sh -c 'echo \"deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main\" > /etc/apt/sources.list.d/google.list'"

  # Update repositories
  config.vm.provision :shell, inline: "sudo apt update -y"

  # Upgrade installed packages
  # config.vm.provision :shell, inline: "sudo apt upgrade -y"

  # Install ansible
  config.vm.provision :shell, inline: "sudo apt-get install -y ansible"

  # Add desktop environment
  # config.vm.provision :shell, inline: "sudo apt install -y --no-install-recommends ubuntu-desktop"
  # config.vm.provision :shell, inline: "sudo apt install -y --no-install-recommends virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11"
  # Add `vagrant` to Administrator
  config.vm.provision :shell, inline: "sudo usermod -a -G sudo vagrant"

  # Add Google Chrome
  # config.vm.provision :shell, inline: "sudo apt install -y google-chrome-stable"

  # Add Chromium
  # config.vm.provision :shell, inline: "sudo apt install -y chromium-browser"

  # Add Firefox
  # config.vm.provision :shell, inline: "sudo apt install -y firefox"

  # Restart
  # config.vm.provision :shell, inline: "sudo shutdown -r now"

  # Install openJDK 11, evolveum and start midpoint
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "ansible/setup-midpoint.yml"
  end
end
