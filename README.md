# update + cài qemu: @dilosuke 
`sudo apt update && sudo apt install qemu-system -y`

tạo disk 128gb:
`qemu-img create -f qcow2 /home/user/Android/Sdk/disk.qcow2 128G`

cài win:
`qemu-system-x86_64 -M q35 -usb -device qemu-xhci -device usb-tablet -device usb-kbd -cpu host,+pae -smp sockets=1,cores=16,threads=2 -m 49152M -drive file=/home/user/Android/Sdk/disk.qcow2,aio=threads,cache=writeback,if=none,id=hda -device ahci,id=hdaahci -device ide-hd,drive=hda,bus=hdaahci.0 -cdrom /home/user/Downloads/win.iso -vga std -device ich9-intel-hda -device hda-duplex -device virtio-net-pci,netdev=n0 -netdev user,id=n0 -accel kvm -device virtio-serial-pci -device intel-iommu`

cài mạng:
`qemu-system-x86_64 -M q35 -usb -device qemu-xhci -device usb-tablet -device usb-kbd -cpu host,+pae -smp sockets=1,cores=16,threads=1 -m 49152M -drive file=/home/user/Android/Sdk/disk.qcow2,aio=threads,cache=writeback,if=none,id=hda -device ahci,id=hdaahci -device ide-hd,drive=hda,bus=hdaahci.0 -cdrom /home/user/Downloads/virtio.iso -vga std -device ich9-intel-hda -device hda-duplex -device virtio-net-pci,netdev=n0 -netdev user,id=n0 -accel kvm -device virtio-serial-pci -device intel-iommu`
