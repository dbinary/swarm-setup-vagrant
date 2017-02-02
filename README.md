# Requirements

- Virtualbox
- Vagrant

# How to run

## Create virtual machines

```
$ vagrant up --driver=virtualbox
```

## Setup swarm manager

- SSH into manager vm

```
$ vagrant ssh manager
```

- Create a new swarm

```
$ docker swarm init --advertise-addr 192.168.70.10
```

The output includes the commands to join new nodes to the swarm

- Now connects to worker1 & worker2 and run the previous command

# Results

- Manager (192.168.70.10)
- Worker1 (192.168.70.11)
- Worker2 (192.168.70.12)
