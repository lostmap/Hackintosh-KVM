MAC address generator:
./mac-addr-generator.sh 

uuid generator:
uuidgen

macOS-libvirt-NG.xml:
sed -i "s/CHANGEME/$USER/g" macOS-libvirt-NG.xml

run in virt-manager (GUI):
virsh --connect qemu:///system define macOS-libvirt-NG.xml

run via CLI:
./boot-macOS-NG.sh

if device busy:
sudo ip link delete tap0

inet fix:
sudo ip tuntap add dev tap0 mode tap
sudo ip link set tap0 up promisc on
sudo ip link set dev virbr0 up
sudo ip link set dev tap0 master virbr0

*
virsh net-start default

virsh net-autostart default
