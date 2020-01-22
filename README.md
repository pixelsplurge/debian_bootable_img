# debian_bootable_img
### Weston on Debian 9 Stretch screenshot.
![](https://github.com/pixelsplurge/debian_bootable_img/blob/master/weston_screenshot.png)

Developing Debian 9 Stretch based minimal (under 400mb zipped) raw image

With Wayland/Weston interface

Image is Grub 2 bootable

Network enabled

DD write direct to device (usb, sda ect)

Mounted locally read/write in chroot environment

Mounted with Qemu.

### Download Link due to image size ~370mb (too large for github).
[Download ext4fs-weston-img.zip](https://pixelsplurge.com/?mode=download)

### Howto

First unzip
### To mount with QEMU

(These instruction are appropriate for Fedora 27, please adjust accordingly)

$`su -c "qemu-kvm -m 2048 -name deb-min -drive format=raw,file=/path/to/ext4fs.img -vga std -usbdevice tablet"`

Login: user password: user

Login: root password: root

### To start Weston/Wayland session after login:

$`weston-launch`

### DD write to usb or sd drive

$`su -c "dd if=/path/to/ext4fs.img of=/dev/sdX bs=8M status=progress oflag=direct"`

### Remaster with chroot

$`mkdir tmp`

$`su`

#`mount -o loop,rw ./ext4fs.img ./tmp`

#`mount --bind /dev ./tmp/dev`

#`mount --bind /dev/pts ./tmp/dev/pts`

#`mount --bind /proc ./tmp/proc`

#`mount --bind /sys ./tmp/sys`

#`mount --bind /etc/resolv.conf ./tmp/etc/resolv.conf`

#`chroot ./tmp`
#### On complete
#`exit`

#`umount ./tmp/dev`

#`umount ./tmp/dev/pts`

#`umount ./tmp/proc`

#`umount ./tmp/sys`

#`umount ./tmp/etc/resolv.conf`

#`umount ./tmp`
