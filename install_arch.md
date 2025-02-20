To install Arch Linux from an ISO, follow these steps:

### **1. Download Arch Linux ISO**
Download the latest ISO from the official website:  
➡️ [https://archlinux.org/download/](https://archlinux.org/download/)

---

### **2. Create a Bootable USB**
**On Linux/macOS:**
Run this command to write the ISO to a USB drive (replace `/dev/sdX` with your USB device):
```sh
sudo dd if=archlinux-*.iso of=/dev/sdX bs=4M status=progress && sync
```

**On Windows:**  
Use tools like **Rufus** or **balenaEtcher** to create a bootable USB.

---

### **3. Boot into the Arch ISO**

---

### **4. Set Up Network (Optional for WiFi)**
Check internet connection:
```sh
ping archlinux.org -c 3
```
For **WiFi**, use:
```sh
iwctl
station wlan0 connect "SSID"
```

---

### **5. Partition the Disk**
Check disks:
```sh
lsblk
```
Partition using `fdisk` or `cfdisk`, e.g.:
```sh
cfdisk /dev/sdX
```
Suggested partitions:
- **EFI (512MB, type `EFI System`)** → `/boot`
- **Root (Rest of disk, type `Linux filesystem`)** → `/`

Format partitions:
```sh
mkfs.fat -F32 /dev/sdX1  # For EFI
mkfs.ext4 /dev/sdX2      # Root
```

---

### **6. Mount Partitions**
```sh
mount /dev/sdX2 /mnt
mkdir /mnt/boot
mount /dev/sdX1 /mnt/boot
```

---

### **7. Install Base System**
```sh
pacstrap /mnt base linux linux-firmware
```

---

### **8. Generate fstab**
```sh
genfstab -U /mnt >> /mnt/etc/fstab
```

---

### **9. Chroot into System**
```sh
arch-chroot /mnt
```

---

### **10. Set Up Basics**
- **Set Timezone**:
  ```sh
  ln -sf /usr/share/zoneinfo/Region/City /etc/localtime
  hwclock --systohc
  ```
- **Set Locale**:
  ```sh
  echo "en_US.UTF-8 UTF-8" > /etc/locale.gen
  locale-gen
  echo "LANG=en_US.UTF-8" > /etc/locale.conf
  ```
- **Set Hostname**:
  ```sh
  echo "myhostname" > /etc/hostname
  ```

---

### **11. Set Up Bootloader**
For **UEFI (GRUB)**:
```sh
pacman -S grub efibootmgr
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
grub-mkconfig -o /boot/grub/grub.cfg
```

---

### **12. Set Root Password**
```sh
passwd
```

---

### **13. Reboot**
Exit chroot:
```sh
exit
umount -R /mnt
reboot
```

Remove the USB and enjoy your Arch Linux install! 🚀
