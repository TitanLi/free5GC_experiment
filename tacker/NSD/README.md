# free5GC
## create VNFD
```shell
$ openstack vnf descriptor create --vnfd-file amf.yaml amf
$ openstack vnf descriptor create --vnfd-file hss.yaml hss
$ openstack vnf descriptor create --vnfd-file smf.yaml smf
$ openstack vnf descriptor create --vnfd-file upf.yaml upf
$ openstack vnf descriptor create --vnfd-file pcrf.yaml pcrf
$ openstack vnf descriptor create --vnfd-file mongodb.yaml mongodb
$ openstack vnf descriptor create --vnfd-file webui.yaml webui
```
## create ns
```shell
$ openstack ns descriptor create --nsd-file nsd.yaml ns
$ openstack ns create --nsd-name ns free5gc
```
## mongoDB
```shell
$ sudo apt-get install mongodb
$ sudo sed -i 's/bind_ip = 127.0.0.1/bind_ip = 0.0.0.0/g' /etc/mongodb.conf
$ sudo /etc/init.d/mongodb restart
```