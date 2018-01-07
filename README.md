# Fully L3 & Automated BGP fabric


*Work in progress...*



## Introduction 

This repository provides Ansible playbook and templates to deploy a fully L3 fabric based on BGP (using [FreeRangeRouting](https://github.com/FRRouting/frrFreeRangeRouting)) on the free test Lab "[Cumulus In The Cloud](https://cumulusnetworks.com/products/cumulus-in-the-cloud/)" platform.

Of course, you can re-use this project in any Linux based platform/topology by customizing the **hosts** and **host_vars** files.

## The topology
Assuming you are playing with "[Cumulus In The Cloud/CITC](https://cumulusnetworks.com/products/cumulus-in-the-cloud/)" platform, you'll, maybe, have a hard time finding the actual interfaces used on the spines/leafs (I found it in the deployment source code of CITC) so here is the detailed physical topology : 

*image to add here*


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

And *Voila*, you can start to play with BGP ! :-)

### Options 
  - Fully IPv4
  - Fully IPv6
  - RFC 5549




