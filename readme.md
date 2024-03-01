Here you will find everything about Terraform (Tf) / OpenTofu (Ot) that could be useful in a KVM (libvirt) environment.

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

Download terraform / openTofu
```
wget https://releases.hashicorp.com/terraform/0.13.4/terraform_0.13.4_linux_amd64.zip Unzip and copy terraform executable in /usr/local/sbin (in Path)
```

Check terraform version / Tofu version
```
terraform version
tofu version
```

If you clone or copy the files from this git, and you use the current main.tf we need only to initialize terraform / tofu to automatically deploy any provider needed.

```
terraform init
```

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
