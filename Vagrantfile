# Vagrantfile para configurar un servidor con Apache y un directorio compartido
Vagrant.configure("2") do |config|
  # Configuración de la VM
  config.vm.box = "ubuntu/bionic64" # Puedes cambiar esto a otra versión si lo prefieres

  # Configuración de recursos de la VM
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"     # Asigna 512 MB de RAM
    vb.cpus = 2           # Asigna 2 cores de CPU
  end

  # Mapeo de puerto: el puerto 8080 de la máquina host se redirige al puerto 80 de la VM
  config.vm.network "forwarded_port", guest: 80, host: 8080

  # Provisión para instalar Apache
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y apache2
  SHELL

  # Configuración del directorio compartido
  config.vm.synced_folder "./html", "/var/www/html", owner: "www-data", group: "www-data"

  # Configuración de nombre de la VM (opcional)
  config.vm.hostname = "servidor-apache"
end
