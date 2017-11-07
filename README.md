# Vagrant Swarm

A (very) simple Vagrant file to help set up an experimental docker swam environment with 2 masters and two slaves.
Options (no of masters/slaves, memory allocated to the machines are easily configurable).

## Getting Started

```shell
git clone git@github.com:pkaramol/vagrant-swarm.git
cd vagrant-swarm
vagrant up
```

This will init a private network consisting of 2 master swam nodes on IPs `192.168.1.11`, `192.168.1.12` and two slave nodes on IPs `192.168.1.21`, `192.168.1.22`.

Master / slave distinction is only semantic (hostnames) and resource (RAM) based for the time being.
Swarm initiation and boostrapping needs to be taken care of by you; here is a way that you could do this:

```shell
$ vagrant ssh master1
ubuntu@master1:~$ docker swarm init --advertise-addr 192.168.1.11

Swarm initialized: current node (i2l6veyx68wppvp0de1lzpwl0) is now a manager.

To add a worker to this swarm, run the following command:

    docker swarm join --token <token_value> 192.168.1.11:2377

To add a manager to this swarm, run 'docker swarm join-token manager' and follow the instructions.

```

The above process will make `master1` the __leader__ of the swarm.

Then, login to all other three nodes typing the above command, e.g.:

```shell
vagrant ssh master2
ubuntu@master2:~$  docker swarm join --token <token_value> 192.168.1.11:2377
This node joined a swarm as a worker.
```

You can (if you like) promote node with hostname `master2` so that it actually becomes a master by logging in to the leader node (`master1`) and typing:

```shell
ubuntu@master1:~$ docker node promote master2
```


### Prerequisites

Has been tested with `vagrant 2.0.0`, `virtualbox 5.0.40_Ubuntu r115130` on `Ubuntu 16.04.3 LTS`
