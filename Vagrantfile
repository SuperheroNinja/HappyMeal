$script = <<-SCRIPT
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
apt-cache policy docker-ce
sudo apt install docker-ce -y
SCRIPT

Vagrant.configure("2") do |config|
    config.vm.box = "generic/ubuntu2204"
    
    # Asking for credentials if this is not disabled
    config.vm.synced_folder ".", "/vagrant", disabled: true

    # Making sure it works
    config.vm.provision "shell", inline: $script
    config.vm.network "forwarded_port", guest: 80, host: 8080

    config.vm.provider "qemu" do |qe|
        qe.arch = "x86_64"
        qe.machine = "q35"
        qe.cpu = "max"
        qe.net_device = "virtio-net-pci"
    end
  end


