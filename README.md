Tutorial I used to migrate our VMs to NetworkManager if interested:
https://askubuntu.com/questions/1442352/migrate-ubuntu-server-from-netplan-to-networkmanager-without-disconnection-poss


Before beginning, make sure to modify your $HOME/.ssh/config file to have the following:
```
Host cn*
    StrictHostKeyChecking no
```

This will make sure Ansible does not require you to have previously connected to your node before provisioning.

To change hostname, simply do
`hostnamectl hostname {name}` e.g. `hostnamectl hostname cn01`

This can also be automated with the ansible `hostname` module.

To modify a node's IP, you just do
`sudo nmcli con modify enp0s8 ipv4.address 10.10.10.11/24` (change IP to whatever you would like)
`sudo nmcli dev reapply enp0s8`

I recommend ascending IP for each node: 10.10.10.10 for login, 10.10.10.11 for cn01, 10.10.10.12 for cn02

