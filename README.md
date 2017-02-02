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

## Setup swarm workers

- Now connects to worker1 & worker2 and type the following command

```
$ docker swarm join \
    --token TO_BE_REPLACED_WITH_TOKEN_GENERATED IN PREVIOUS STEP \
    192.168.70.10:2377
```

# Results

- Manager (192.168.70.10)
- Worker1 (192.168.70.11)
- Worker2 (192.168.70.12)
