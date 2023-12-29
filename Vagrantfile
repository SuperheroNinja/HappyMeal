$script = <<-SCRIPT
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
sudo echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt-cache policy docker-ce
sudo apt install docker-ce -y
sudo newgrp docker
sudo usermod -aG docker vagrant
SCRIPT

Vagrant.configure("2") do |happymeal|
    happymeal.vm.define     "happymeal"
    happymeal.vm.hostname   = "happymeal"
    happymeal.vm.box        = "generic/ubuntu2204"
    happymeal.vm.provider "qemu" do |qe|
        qe.arch = "x86_64"
        qe.machine = "q35"
        qe.memory = "8G"
        qe.cpu = "max"
        qe.net_device = "virtio-net-pci"
    end
    
    happymeal.vm.provision "shell", inline: $script
    
    # Add more forwarded ports by copying the below line
    # Run "vagrant reload" after adding ports if your VM is 
    # already provisioned
    happymeal.vm.network "forwarded_port", guest: 80, host: 8080
    happymeal.vm.network "forwarded_port", guest: 90, host: 8081
    
    # Fixes: SMB is asking for credentials on Mac
    #        if synced_folder is not disabled
    happymeal.vm.synced_folder ".", "/vagrant", disabled: true
  end


