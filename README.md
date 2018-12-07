# EDCI-SoftRoCE_Experiment_Env
Build SoftRoCE Experiment Environment on VirtualBox VMs

## Install VirtualBox and Vargant
* [VirtualBox](https://www.virtualbox.org/wiki/Downloads) - A desktop virtualization system.
* [Vagrant](https://www.vagrantup.com/downloads.html) - A script tool for managing VirtualBox VMs.

## Source for building one VM and SoftRoCE packages
https://github.com/haggaie/rdma-experiment

## Replace the Vagrant script for building two VMs
```shell=
# Build SoftRoCE Server and SoftRoCE Client
Vagrant.configure("2") do |config|
    
  config.vm.define "softroce_server" do |softroce_server|    
    softroce_server.vm.box = "ubuntu/bionic64"
    softroce_server.vm.network "private_network", type: "dhcp"
    softroce_server.vm.provision "shell", path: "provision/setup-vm.sh"    
  end
  
  config.vm.define "softroce_client" do |softroce_client|    
    softroce_client.vm.box = "ubuntu/bionic64"
    softroce_client.vm.network "private_network", type: "dhcp"
    softroce_client.vm.provision "shell", path: "provision/setup-vm.sh"    
  end
  
end
```
## Login SoftRoCE Server VM and get its IPs
```shell=
vagrant ssh softroce_server
ifconfig
```

## Login SoftRoCE Client VM and get its IPs
```shell=
vagrant ssh softroce_client
ifconfig
```

## How to configure SoftRoCE and test SoftRoCE communication
https://www.systutorials.com/docs/linux/man/8-rxe_cfg/  
https://zhengjingwei.github.io/2018/01/27/Soft-RoCE-setup/

