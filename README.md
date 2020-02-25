# Fully L3 & Automated BGP fabric

## Introduction 

This repository provides Ansible playbook and templates to deploy a fully L3 fabric based on BGP (using [FreeRangeRouting](https://github.com/FRRouting/frr)) on the free test Lab "[Cumulus In The Cloud](https://cumulusnetworks.com/products/cumulus-in-the-cloud/)" platform.

Of course, you can re-use this project in any Linux based platform/topology by customizing the **hosts** and **host_vars** files.

## The topology
Assuming you are playing with "[Cumulus In The Cloud/CITC](https://cumulusnetworks.com/products/cumulus-in-the-cloud/)" platform, ~~you'll maybe have a hard time finding the actual interfaces used on the spines/leafs (I had to look into the deployment source code of CITC).~~
~~To save you some time, here is the detailed physical topology:~~, you'll find the following diagram (provided by Cumulus) when launching the simulation (This is new since the beginning of 2020) :

![alt text](https://github.com/jpmondet/FullyAutomatedBGPfabric/raw/master/new_citc_topo.jpg "CITC topology") 


*Note that servers are using **Ubuntu 18.04.3 LTS**  & spine/leaf are using **Cumulus Linux 3.7.8** at this moment [02/02/2020]*


## How-to

From the `oob-mgmt-server` : 

```bash
git clone https://github.com/jpmondet/FullyAutomatedBGPfabric.git
```
```bash
cd FullyAutomatedBGPfabric
```
```bash
ansible-playbook deploy_network.yml 
```

And *Voilà*, you can start to play with BGP and your new network ! :-)

### Options 

  - **Fully IPv4**

    By default, the playbook assigns IPv4 addresses on interfaces and negociates IPv4 Address Family during BGP sessions establishment. 

  - **Fully IPv6**

    By using the option `IPv6`, the playbook will activate **Link-Local** IPv6 addresses on interfaces and will negociate IPv6 Address Family during BGP sessions establishment.

```bash
ansible-playbook deploy_network.yml -e "option=ipv6"
```

  - **RFC 5549**

    By using the option `RFC5549`, the playbook will activate **Link-Local** IPv6 addresses on interfaces and will negociate IPv**4** Address Family during BGP sessions establishment.

```bash
`ansible-playbook deploy_network.yml -e "option=5549"`
```



