# OpenStack
* OS:Ubuntu 18.04

1. Install OpenStack Cluster(Controller、Compute1)
2. 新增Ubuntu Image
3. 新增Public Network
4. 新增Flavor: 2 Core, 2GB Mem, 20 GB Disk
5. 新增Project Network Subnet
6. 新增Key
7. 新增Security Group(TCP,UDP,ICMP)
8. 新增VM
9. 更改free5gc.conf(s1ap=SubnetIP,460,99)
10. 更改amf.conf(ListenOn=SubnetIP)
11. 執行
> 開啟路由功能
```shell
$ sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
$ sudo iptables -t nat -A POSTROUTING -o ens3 -j MASQUERADE
$ sudo iptables -I INPUT -i uptun -j ACCEPT
```
12. 執行
```shell
$ . free5gc-amfd
```
13. 設定eNodeB
14. 重啟eNodeB
15. 新增Security Group
- Other Protocol
- Ingress
- IP Protocol => -1
- Remote => CIDR
- CIDR => 0.0.0.0/0
16. 進階應用
> 抓取來自eNodeB封包(Controller)
```shell
$ tcpdump -i eno1 src 192.168.2.254
```
> 可用來更新數值
```shell
$ sudo echo 'nameserver 8.8.8.8' > /etc/resolv.conf
$ sed -i "s/mongodb:\/\/localhost/mongodb:\/\/mongodb/g" free5gc-stage-1/install/etc/free5gc/free5gc.conf
$ sudo sh -c "echo '10.10.0.16 mongodb' >> /etc/hosts"
```

# free5GC_experiment
example:

|VNF    |Subnet    |floating IP |
|-------|----------|------------|
|AMF    |10.30.0.17|192.168.2.61|
|HSS    |10.30.0.13|192.168.2.62|
|SMF    |10.30.0.11|192.168.2.63|
|UPF    |10.30.0.3 |192.168.2.64|
|PCRF   |10.30.0.18|192.168.2.65|
|mongodb|10.30.0.25|192.168.2.66|
|webUI  |10.30.0.25|192.168.2.66|

deploy:

|VNF    |Subnet    |floating IP  |
|-------|----------|-------------|
|AMF    |10.10.0.11|192.168.2.111|
|HSS    |10.10.0.12|192.168.2.112|
|SMF    |10.10.0.13|192.168.2.113|
|UPF    |10.10.0.14|192.168.2.114|
|PCRF   |10.10.0.15|192.168.2.115|
|mongodb|10.10.0.16|192.168.2.116|
|webUI  |10.10.0.17|192.168.2.117|

# install
```bash
$ ./example/install.sh
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

# AMF
```shell
$ sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
$ sudo iptables -t nat -A POSTROUTING -o ens3 -j MASQUERADE
$ sudo iptables -I INPUT -i uptun -j ACCEPT
```