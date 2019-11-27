# NSD
```shell
$ vim mongodb.yaml
$ vim amf.yaml
$ vim hss.yaml
$ vim smf.yaml
$ vim pcrf.yaml
$ vim upf.yaml
$ vim free5gc.yaml
$ openstack vnf descriptor create --vnfd-file mongodb.yaml mongodb
$ openstack vnf descriptor create --vnfd-file amf.yaml amfd
$ openstack vnf descriptor create --vnfd-file hss.yaml hssd
$ openstack vnf descriptor create --vnfd-file smf.yaml smfd
$ openstack vnf descriptor create --vnfd-file pcrf.yaml pcrfd
$ openstack vnf descriptor create --vnfd-file upf.yaml upfd
$ openstack ns descriptor create --nsd-file free5gc.yaml free5gc-nsd
$ openstack ns create --nsd-name free5gc-nsd free5gc
```