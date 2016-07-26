# Docker Swarm 1.12 on Vagrant
This mean of this project if to demonstrate capabilites of docker swarm 1.12 on a real environment

## Description
- Vagrant will setup 3 boxes based on Ubuntu trusty64, install the lastest version of docker.
- The cluster is mabe by 3 machines, 1 master and 2 simple swarm nodes
- On going on the address `192.168.33.10:3000` you will see a simple interface of [docker-swarm-visualizer](https://github.com/ManoMarks/docker-swarm-visualizer)
- You can increase the number of boxes by just changing the value `NB_NODES=2 #MAX = 9` in Vagrant file

## Run the environment
To start using the cluster just use `vagrant up`

## How to use it
- To start using your new cluster, just connect to the master `vagrant ssh master`
- Run whatever docker service you want `sudo docker service create ...`
- See [docker Swarm 1.12 documentation](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/) to have more specifics

## Running an Example
- This example will just start an HelloWorld Container [Image can be found here](https://github.com/tutumcloud/hello-world)
- Connect to the master node `vagrant ssh master`
- Run the docker command `sudo docker service create --replicas 4 --name helloworld -p 8081:80 tutum/hello-world`
- Go on the URL `192.169.33.10:8081` and you will see "Hello World"
![alt tag](https://raw.githubusercontent.com/marco565/docker-swarm-112-on-vagrant/master/doc-images/helloworld-result.png)

- Go back on the UI of swarm `192.169.33.10:3000` and you will see 4 containers
![alt tag](https://raw.githubusercontent.com/marco565/docker-swarm-112-on-vagrant/master/doc-images/swarm-result.png)

## Clean the environment
To delete every thing made by this project just run the following command `vagrant destroy`
