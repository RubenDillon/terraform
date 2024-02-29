Here you will find everything about Terraform (Tf) that could be useful in a KVM (libvirt) environment.

Libvirt integration
=

To Check if Virtualization is enabled on your linux environment:
```
egrep -c '(svm|vmx)' 
```

/proc/cpuinfo should return the number of processors, greater than 0.

```
lscpu 
```

Should grep for 'Virtualization'. VT is turned on if you see VT-x and full in the output.

Intall libvirt: (fedora...) 
```
sudo dnf install virt-top libguestfs-tools virt-manager
```

Start libvirtd 
```
sudo systemctl enable --now 
```

libvirtd Additional tools 
```
yum module install virt yum install virt-install virt-viewer
```

Verify 
```
virt-host-validate
```

Download terraform 
```
wget https://releases.hashicorp.com/terraform/0.13.4/terraform_0.13.4_linux_amd64.zip Unzip and copy terraform executable in /usr/local/sbin (in Path)
```

Check terraform version 
```
terraform version
```

Download terraform libvirt provider 
```
mkdir -p ~/.local/share/terraform/plugins
```
Go to above directory 
```
mkdir registry.terraform.io
```
Go to above directory 
```
mkdir dmacvicar
```
Go to above directory 
```
mkdir libvirt
```
Go to above directory 
```
mkdir 0.6.2
```
Go to above directory 
```
mkdir linux_amd64
```
Go to above directory

Download libvirt terraform plugin Go to https://github.com/dmacvicar/terraform-provider-libvirt/releases and get the latest version (.tar.gz). Unzip it. 
```
tar -xvzf file
```
Build the example
```
Mkdir ~/examples
```

Go to ~/examples

```
terraform init
```

Copy the files from this git (main.tf, cloud_init.cfg and network_config.cfg) 

Ensure you update ssh public key in cloud_init.cfg.

Do terraform init again and followed by terraform apply

Verify vm creation with 'virsh list' and dhcp with 'virsh net-dhcp-leases vm_network'.Get ip address and do 'ssh developer@' to login to the vm.


Documentation used to create this git
=

  - https://github.com/gitsridhar/libvirt-terraform/tree/main
  - https://dev.to/ruanbekker/terraform-with-kvm-2d9e[
  - https://www.youtube.com/watch?v=MdeJn1k2b8Y
  - https://registry.terraform.io/providers/multani/libvirt/latest/docs
  -  https://github.com/opentofu/registry/tree/main
  -  https://github.com/dmacvicar/terraform-provider-libvirt
  -  https://yping88.medium.com/building-and-installing-terraform-provider-for-libvirt-a08a29f93135
