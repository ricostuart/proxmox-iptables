# proxmox-iptables
iptables 8006 to 443

iptables -t nat -A PREROUTING -p tcp --dport 443 -j REDIRECT --to-ports 8006
