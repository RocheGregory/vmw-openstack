# Fuel 7.0 with vCenter/VDS Plugins 

Assuming you have an Up & Running vCenter 6.0 with bunch of ESX 6.0 and an fully operationnal Fuel 7.0 Master node with at least 2 Fuel Slave nodes. (My lab is nested without any issues. If it's also your case, don't forget to set the VSS or VDS in promiscous mode for physical ESX.)

## vCenter Preparation

1. Create a datacenter with a cluster, example with 'Openstack' Cluster within 'Showroom' datacenter
![](docs/vcenter-cluster-openstack.png)

2. Create a VDS like the 'dvSwitch' below and attach hosts of 'Openstack' Cluster
![](docs/vcenter-dvswitch.png)

## vCenter Preparation

1. Configure the network tab and specify the VLAN range, for each neutron network there is a dedicated portgroup the VLAN ID
![](docs/fuel-network-settings.png)

2. Download and install VDS plugin into Fuel Master node, verify installed plugins
```bash
[root@fuel ~]# fuel plugins --install fuel-plugin-vmware-dvs-1.1-1.1.0-1.noarch.rpm
```
```bash
[root@fuel ~]# fuel plugins
id | name                   | version | package_version
---|------------------------|---------|----------------
1  | fuel-plugin-vmware-dvs | 1.1.0   | 3.0.0
```

3. Create a dedicated Fuel env for vCenter with QEMU + vCenter options and attach 2 nodes
  * One with controller+cinder+cinder-vmware+base-os roles
  * One with only compute-vmware role
   
![](docs/fuel-nodes.png)

4. Configure the vCenter plugin, like the example below
![](docs/fuel-vcenter-conf-plugin.png)
![](docs/fuel-vcenter-conf-plugin-nova-glance.png)

5. Deploy the env
![](docs/fuel-deployment.png)

6. Example of corresponding PORTGROUP to neutron network, automatically created by plugin
![](docs/vcenter-new-portgroup.png)

## Consume openstack as usual
  * Creation of a new network: creation of a new PORTGROUP in VDS with a VLANID in the range
  * Spawn a VM in neutron network: the VM VNIC is attached to the corresponding PORTGROUP by vCenter

[Openstack saved oconfiguration files for this examples](scripts/vmw-fuel-dvs.tgz)

