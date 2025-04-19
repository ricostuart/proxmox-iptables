# Add to /etc/network/interfaces
auto vmbr0
iface vmbr0 inet static
        address 10.32.0.2/24
        gateway 10.32.0.1
        bridge-ports enp3s0
        bridge-stp off
        bridge-fd 0
        post-up iptables -t nat -A PREROUTING -p tcp -d 10.32.0.2 --dport 443 -j REDIRECT --to-ports 8006



# proxmox-iptables
iptables 8006 to 443

/sbin/iptables -F
/sbin/iptables -t nat -F
/sbin/iptables -t nat -A PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports 8006
