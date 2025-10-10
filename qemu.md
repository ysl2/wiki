# qemu

> Install qemu on Debian and boot with virt-manager.
>
> Ref: <https://christitus.com/vm-setup-in-linux/>

1. Check virtualization

   ```bash
   egrep -c '(vmx|svm)' /proc/cpuinfo
   ```

   If the output is zero then go to bios settings and enable VT-x (Virtualization Technology Extension) for Intel processor and AMD-V for AMD processor.

1. Install

   ```bash
   sudo apt install qemu-kvm qemu-system qemu-utils python3 python3-pip libvirt-clients libvirt-daemon-system bridge-utils virtinst libvirt-daemon virt-manager -y
   ```

1. Check service status

   ```bash
   sudo systemctl status libvirtd.service
   ```

1. Set network

   ```bash
   sudo virsh net-start default
   sudo virsh net-autostart default
   sudo virsh net-list --all
   ```

1. Add into user group

   ```bash
   sudo usermod -aG libvirt $USER
   sudo usermod -aG libvirt-qemu $USER
   sudo usermod -aG kvm $USER
   sudo usermod -aG input $USER
   sudo usermod -aG disk $USER
   ```

1. Boot

   ```bash
   sudo virt-manager
   ```
