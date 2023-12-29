Vagrant.configure("2") do |config|
    config.vm.box = "generic/ubuntu2204"
    
    # Asking for credentials if this is not disabled
    config.vm.synced_folder ".", "/vagrant", disabled: true

    # Making sure it works
    config.vm.provision "shell", inline: "echo hello"
    config.vm.network "forwarded_port", guest: 80, host: 8080

    config.vm.provider "qemu" do |qe|
        qe.arch = "x86_64"
        qe.machine = "q35"
        qe.cpu = "max"
        qe.net_device = "virtio-net-pci"
    end
  end
