# Docker Swarm 1.12 on Vagrant
This mean of this project if to demonstrate capabilites of docker swarm 1.12 on a real environment

## Description
- Vagrant will setup 3 boxes based on Ubuntu trusty64, install the lastest version of docker.
- The cluster is mabe by 3 machines, 1 master and 2 simple swarm nodes (please edit Vagrant file to setup more nodes)
- On going on the address `192.168.33.10:3000` you will see a simple interface of [docker-swarm-visualizer](https://github.com/ManoMarks/docker-swarm-visualizer)

## run the environment
To start using the cluster just use `vagrant up`

## Clean the environment
To delete every thing made by this project just run the following command `vagrant destroy`
