---
title: Known limits
excerpt: 'Requirements and limits to respect'
updated: 2023-11-14
---

## IPs used by services

When a service is spawned in a subnet, it is using some IPs from the subnet CIDR. The following table provides the number of IPs used by each services. If the subnet has a 'small' number of available IPs this can have impact ! Since if you use all the L3 services, the total number of IPs used is 7, we advise to use at least `/28` mask.

| Used IPs by the service:| in DHCP allocation pool |	outside of allocation pool (gateway_ip) |
| :---: | :---: | :---: |
| DHCP |	2 | |	
| Public Cloud Gateway | 1	| 1 |
| Public Cloud Load Balancer (Octavia)	| 3 | |	



## We want your feedback!

We would love to help answer questions and appreciate any feedback you may have.

If you need training or technical assistance to implement our solutions, contact your sales representative or click on [this link](https://www.ovhcloud.com/en/professional-services/) to get a quote and ask our Professional Services experts for a custom analysis of your project.

Are you on Discord? Connect to our channel at <https://discord.gg/ovhcloud> and interact directly with the team that builds our services!
