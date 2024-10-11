Vagrant.configure("2") do |config|
  config.vm.box = "archlinux/archlinux"
  
  # Port forwarding for Flask
  config.vm.network "forwarded_port", guest: 5000, host: 8080

  # Provisioning
  config.vm.provision "shell", inline: <<-SHELL
    sudo pacman -Syu --noconfirm git nano vim python python-virtualenv python-pip
    cd /vagrant
    python -m venv flask_venv
    source flask_venv/bin/activate
    pip install Flask
  SHELL

  # Upload hello.py file
  config.vm.provision "file", source: "./hello.py", destination: "/home/vagrant/hello.py"
end
