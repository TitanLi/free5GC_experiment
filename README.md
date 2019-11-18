# free5GC_experiment
|VNF    |Subnet    |floating IP |
|-------|----------|------------|
|AMF    |10.30.0.17|192.168.2.61|
|HSS    |10.30.0.13|192.168.2.62|
|SMF    |10.30.0.11|192.168.2.63|
|UPF    |10.30.0.3 |192.168.2.64|
|PCRF   |10.30.0.18|192.168.2.65|
|mongodb|10.30.0.25|192.168.2.66|
|webUI  |10.30.0.25|192.168.2.66|

# install
```bash
$ ./deploy/install.sh
```

# UPF
```shell
$ ip tuntap add mode tun dev uptun
$ ip addr add 45.45.0.1/16 dev uptun
$ ip link set dev uptun up
$ sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
$ iptables -F
$ iptables -X
$ iptables -Z
$ iptables -t nat -A POSTROUTING -o ens3 -j MASQUERADE
$ iptables -I INPUT -i uptun -j ACCEPT
```