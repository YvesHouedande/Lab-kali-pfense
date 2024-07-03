Vagrant.configure("2") do |config|
  # Configuration de la machine pfSense
  config.vm.define "pfsense" do |pfsense|
    pfsense.vm.box = "ksklareski/pfsense-ce"
    pfsense.vm.box_version = "1.0.0"
    pfsense.vm.hostname = "pfsense"

    # Configuration des interfaces réseau pour pfSense

    # Interface privée sur le réseau 192.168.222.0/24
    pfsense.vm.network "private_network", ip: "192.168.222.1", virtualbox__intnet: true

    # Port forwarding pour accéder à l'interface web de pfSense depuis l'hôte
    pfsense.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  end

  # Configuration de la machine Kali Linux
  config.vm.define "kali" do |kali|
    kali.vm.box = "kalilinux/rolling"
    kali.vm.hostname = "kali"

    # Interface privée pour se connecter à pfSense
    kali.vm.network "private_network", ip: "192.168.222.2", virtualbox__intnet: true

    # Provisioning de fichiers depuis la machine hôte vers la VM Kali
  end
end
