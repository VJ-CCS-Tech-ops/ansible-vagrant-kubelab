## Setup

This exercise utilises Vagrant for the lab environment setup. Vagrant allows for the build and creation of virtual environments that are defined as configuration parameters in a "VagrantFile" and as a result, are reproducible and portable. More information on Vagrant can be found at the link below.

### Pre-requisites

* VirtualBox - (https://www.virtualbox.org/wiki/Downloads)
* Vagrant - (https://www.vagrantup.com/)
* Git - (https://git-scm.com/downloads)

This exercise has been tested with the following setups:

---
* Windows 10 Enterprise Host
* VirtualBox Version 5.2.22 r126460
* Vagrant Version 2.2.4
* Git version 2.19.1.windows.1

---

* macOS Mojave 10.14.6 Host
* VirtualBox Version 6.0.12 r133076 (Qt5.6.3)
* Vagrant Version 2.2.5
* Git version 2.23.0
---


This setup should in fact work fine on Linux or other versions of Mac and Windows too, but hasn't been tested by us. If you're confident it will work, feel free to give it a try on a platform of your choosing.

### Networking

The VagrantFile included in this repository will create 2x Virtual Machines. One named "Master" and one named "Worker". The communication between these machines relies on the presence of a "Host-Only" network adapter that is installed by default with VirtualBox. This adapter acts as a "private" network that allows communication between guest Virtual Machines and the host. This will be the basis for communication between nodes in our Kubernetes cluster. All communication between master and worker nodes will occur via this Host-Only virtual network.

To find out the specific details of the Host-Only adapter on your system, run the following:

```
#> C:\Program Files\Oracle\VirtualBox\VBoxManage.exe list hostonlyifs

Name:            VirtualBox Host-Only Ethernet Adapter
GUID:            49d645a0-e5b7-4589-bfe0-2126b15890c9
DHCP:            Disabled
IPAddress:       192.168.56.1
NetworkMask:     255.255.255.0
IPV6Address:
IPV6NetworkMaskPrefixLength: 0
HardwareAddress: 0a:00:27:00:00:09
MediumType:      Ethernet
Wireless:        No
Status:          Up
VBoxNetworkName: HostInterfaceNetworking-VirtualBox Host-Only Ethernet Adapter
```

Each Virtual Machine will also have a single NAT interface but this can largely be ignored as it's only used for pulling packages from the Internet.

### Steps

* Download the pre-requisites listed above.

MASTER_ADDRESS = '192.168.56.50'
WORKER_ADDRESS = '192.168.56.100'
```
* Run the command:

```
#> vagrant up
```
...to begin box provisioning. Once the provisioning is complete, login to the nodes using vagrant ssh:

```
#> vagrant ssh worker
```
```
#> vagrant ssh master
```

If at any time you wish to power down the boxes but retain the changes you've made so far, run:
```
#> vagrant halt
```

If at any time you wish to destroy the boxes and recreate them in their default states, run:
```
#> vagrant destroy
```
```
#> vagrant up
```


