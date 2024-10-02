# Ubuntu Grub Boot Repair/Restore

[ref](https://help.ubuntu.com/community/Boot-Repair)

```bash
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt update
sudo apt install -y boot-repair && boot-repair

sudo chroot "/mnt/boot-sav/sda5" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda5" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda5" apt-get install -y mdadm
sudo chroot "/mnt/boot-sav/sda5" mdadm --assemble --scan
sudo chroot "/mnt/boot-sav/sda5" apt-get purge --allow-remove-essential -y grub-com*
sudo chroot "/mnt/boot-sav/sda5" apt-get purge --allow-remove-essential -y grub2-com*
sudo chroot "/mnt/boot-sav/sda5" apt-get purge --allow-remove-essential -y shim-signed
sudo chroot "/mnt/boot-sav/sda5" apt-get purge --allow-remove-essential -y grub-common:*
sudo chroot "/mnt/boot-sav/sda5" apt-get purge --allow-remove-essential -y grub2-common:*

sudo chroot "/mnt/boot-sav/sda5" apt-get install -y grub-efi
```
