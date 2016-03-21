# VMware vRA and Openstack as Endpoint 

Some of you ask me to talk about vRA and Openstack integration. I'm not favorable to daisy chain CMP.
There is a risk to desynchronize all that stuff. Anyway I explain in this topic how to.

 1. Create some floating IP in advance, so vRA could discover them during the next data collection
 ![](docs/1-prepare-floating-ip.png)

 2. Identity the openstack URL in order to create OS Endpoint
 ![](docs/2-identify-url.png)

 3. Identify network in within you want spawn VMs
 ![](docs/3-identify-networks.png)

 4. Create the OS endpoint in vRA
 ![](docs/4-create-os-endpoint.png)

 5. Spicify OS URL, the account and the projet
 ![](docs/5-spicify-url-account-project.png)

 6. Dont't forget to modify your Fabric Group
 ![](docs/6-modify-fabric-group.png)

 7. And add the OS resource
 ![](docs/7-add-openstack.png)

 8. Lauch data collection and verify its status
 ![](docs/8-launch-data-collection.png)

 9. Now you should creat a blueprint based on OS image
 ![](docs/9-create-blueprint.png)

 10. Select some properties corresponding to your needs
 ![](docs/10-select-properties.png)

 11. Publish the blueprint and modify the entitlement, assuming your are familiar with that
 ![](docs/11-publish-blueprint.png)

 12. Now create a new request to launch a new VM deployment
 ![](docs/12-blueprint-available.png)

 13. Check the new request
 ![](docs/13-new-request.png)

 14. The request is submitted, everything seems to be under control...
 ![](docs/14-submitted-request.png)

 15. Yeah! VM is deployed
 ![](docs/15-vm-deployed.png)

 16. Now associate a floating IP to the VM from items menu
 ![](docs/16-floating-ip.png)

 17. A quick check in Horizon
 ![](docs/17-horizon.png)

 18. And initiate a ssh connexion with verification
 ![](docs/18-the-proof.png)
