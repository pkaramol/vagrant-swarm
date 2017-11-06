# Vagrant Swarm

A (very) simple Vagrant file to help set up an experimental docker swam environment with 2 masters and two slaves.
Options (no of masters/slaves, memory allocated to the machines are easily configurable).

## Getting Started

```
git clone git@github.com:pkaramol/vagrant-swarm.git
cd vagrant-swarm
vagrant up
```

This will init a private network consisting of 2 master swam nodes on IPs 192.168.1.11, 192.168.1.12 and two slave nodes on IPs 192.168.1.21, 192.168.1.22.
Master / slave distinction is only semantic (hostnames) and resource (RAM) based for the time being.
Swarm initiation and boostrapping needs to be taken care of by you.

### Prerequisites

Has been tested with `virtualbox 5.0.40_Ubuntu r115130` on `Ubuntu 16.04.3 LTS`
