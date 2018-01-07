# Fully L3 & Automated BGP fabric


*Work in progress...*



## Introduction 

This repository provides Ansible playbook and templates to deploy a fully L3 fabric based on BGP (using [FreeRangeRouting](https://github.com/FRRouting/frr)) on the free test Lab "[Cumulus In The Cloud](https://cumulusnetworks.com/products/cumulus-in-the-cloud/)" platform.

Of course, you can re-use this project in any Linux based platform/topology by customizing the **hosts** and **host_vars** files.

## The topology
Assuming you are playing with "[Cumulus In The Cloud/CITC](https://cumulusnetworks.com/products/cumulus-in-the-cloud/)" platform, you'll maybe have a hard time finding the actual interfaces used on the spines/leafs (I had to look into the deployment source code of CITC).
To save you some time, here is the detailed physical topology: 

![alt text](https://github.com/jpmondet/FullyAutomatedBGPfabric/raw/master/topoCICT.png "CICT topology") 

## How-to

From the `oob-mgmt-server` : 

```bash
git clone https://github.com/jpmondet/FullyAutomatedBGPfabric.git
```
```bash
cd FullyAutomatedBGPfabric
```
```bash
ansible-playbook generate-network.yml -i hosts 
```

And *Voilà*, you can start to play with BGP ! :-)

### Options [/!\ For now Only IPv4 is supported]
  - Fully IPv4
    By default, the playbook assigns IPv4 addresses on interfaces and negociates IPv4 Address Family during BGP sessions establishment. 

  - Fully IPv6
    By using the option `IPv6`, the playbook will activate **Link-Local** IPv6 addresses on interfaces and will negociate IPv6 Address Family during BGP sessions establishment.

`ansible-playbook generate-network.yml -i hosts -e "option=IPv6"`

  - RFC 5549
    By using the option `RFC5549`, the playbook will activate **Link-Local** IPv6 addresses on interfaces and will negociate IPv**4** Address Family during BGP sessions establishment.

`ansible-playbook generate-network.yml -i hosts -e "option=RFC5549"`




