Vagrant.configure("2") do |config|
  # Imagen base de Ubuntu
  config.vm.box = "ubuntu/bionic64"

  # IP estática
  config.vm.network "private_network", ip: "127.0.0.1"

  # Recursos
  config.vm.provider "virtualbox" do |vb|
    vb.memory = 512
    vb.cpus = 1
  end

  # Sincronizar carpeta local con /var/www/html
  config.vm.synced_folder "./public_html", "/var/www/html"

  # Script de provisión para instalar Apache
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
    sudo systemctl enable apache2
    sudo systemctl start apache2
  SHELL
end
