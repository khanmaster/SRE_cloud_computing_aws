Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/xenial64"
    config.vm.network "private_network", ip: "192.168.10.100"

    # Synced app folder- path of your host machine 
    config.vm.synced_folder "app", "/home/ubuntu/app" #- path of your VM/destination
    # Provisioning
    config.vm.provision "shell", path: "provision.sh", privileged: false
end

