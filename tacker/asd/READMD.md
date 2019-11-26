sudo vim /etc/resolv.conf 
vim /etc/hosts
sudo vim /etc/hosts
vim install.sh
. install.sh 
vim install/etc/free5gc/free5gc.conf
vim install/etc/free5gc/freeDiameter/amf.conf 
sudo sh -c 'echo 1 > /proc/sys/net/ipv4/ip_forward'
sudo iptables -t nat -A POSTROUTING -o ens3 -j MASQUERADE
sudo iptables -I INPUT -i uptun -j ACCEPT
. free5gc-amfd 
vim free5gc-stage-1/install/etc/free5gc/free5gc.conf 
vim free5gc-stage-1/install/etc/free5gc/freeDiameter/amf.conf 
vim free5gc-stage-1/install/etc/free5gc/freeDiameter/amf.conf 
history
exit
./free5gc-stage-1/free5gc-amfd