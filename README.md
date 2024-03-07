Tutorial I used to migrate our VMs to NetworkManager:
https://askubuntu.com/questions/1442352/migrate-ubuntu-server-from-netplan-to-networkmanager-without-disconnection-poss

To change hostname, simply do
`hostnamectl hostname {name}` e.g. `hostnamectl hostname cn01`

To modify a node's IP, you just do
`sudo nmcli con modify enp0s8 ipv4.address 10.10.10.11/24` (change IP to whatever you would like)
`sudo nmcli dev reapply enp0s8`

