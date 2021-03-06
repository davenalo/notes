Arch: sudo pacman -S qemu (optionally "qemu-arch-extra" for more architectures)
Debian/Ubuntu: sudo apt install qemu
Fedora: sudo dnf install qemu

To create a virtual image use:

qemu-img create -f qcow2 Image.img 10G

(create is to create an image, -f qcow2 sets the format to qcow2, Image.img is our final file and 10G is it's size)

Launching the VM:

qemu-system-x86_64 -enable-kvm -cdrom OS_ISO.iso -boot menu=on -drive file=Image.img -m 2G
> flag -m 2G se refiere a la memoria ram

(-enable-kvm enables KVM, -cdrom selects an iso to load as a cd, -boot menu=on enables a boot menu, -drive file= selects a file for the drive, -m sets the amount of dedicated RAM)
(Remember! Ctrl + Alt + G to exit capture, Ctrl + Alt + F to fullscreen!)

That doesn't run so good, what can we do to improve it?

Basic performance options

 -cpu host (sets the CPU to the hosts' CPU)
 -smp 2 (sets the numbers of cores)
 >creo que no son cores, sino hilos. "los hilos que se van a usar por cada núcleo, pero les llaman cpu", hay que mirarlo bien, pero es lo mismo en virtual mmachine manager, te pone "cuantas cpus? tienes 8 disponibles" por ejemplo.

Basic Graphics Acceleration

the -vga option can be used to specify one of various vga card emulators:

"qxl" offers 2D acceleration but requires kernel modules "qxl" and "bochs_drm" to be enabled:

-vga qxl

"virtio" works much better and supports some 3D emulation:

-vga virtio -display sdl (or gtk) ,gl=on

•Site: https://denshi.org

- el vídeo es: https://www.youtube.com/watch?v=AAfFewePE7c

--

otros recursos:

https://www.unixmen.com/gnome-boxes-a-front-end-tool-for-qemu-and-kvm/

https://www.qemu.org/

--

From Mental Outlaw: https://www.youtube.com/watch?v=wxxP39cNJOs

sudo pacman -S qemu virt-manager virt-viewer dnsmasq vde2 bridge-utils openbsd-netcat libguestfs

non systemd systems needs libvirt-openrc too (or other init system) and needs extra configuration

systemctl start libvirtd
systemctl enable libvirtd

Already on wm manager: enable XML edition, be sure QEMU/KVM is connected