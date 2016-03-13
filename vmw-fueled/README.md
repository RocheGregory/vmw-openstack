# Fuel 7.0 with vCenter/VDS Plugins 

Assuming you have an Up & Running vCenter 6.0 with bunch of ESX 6.0 and an fully operationnal Fuel Master with at least 2 Fuel Slaves. My lab is a nested one without any issues. If it's also you case, don't forget to set the VSS or VDS for physical ESX in promiscous mode.

## vCenter Preparation

1. Create a datacenter with a cluster, example with 'Openstack' Cluster within 'Showroom' datacenter
![](docs/vcenter-cluster-openstack.png)

2. Create a VDS like the 'vdSwitch' below and attach hosts of 'Openstack' Cluster
![](docs/vcenter-dvswitch.png)

3. Download and install VDS plugin into Fuel Master node, verify installed plugins
```bash
[root@fuel ~]# fuel plugins --install fuel-plugin-vmware-dvs-1.1-1.1.0-1.noarch.rpm
[root@fuel ~]# fuel plugins
```

4. Create a dedicated Fuel env for vCenter with QEMU + vCenter options and attach 2 nodes
..* One with controller+cinder+cinder-vmware+base-os roles
..* One with only compute-vmware role
![](docs/fuel-nodes.png)

5. Configure the vCenter plugin, like the example below
![](docs/fuel-vcenter-plugin.png)
![](docs/fuel-conf-plugin-nova-glance.png)

6. Deploy the env
![](docs/fuel-deployment.png)

