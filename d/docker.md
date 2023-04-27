# Docker

Docker uses containers to deploy images. Containers run instances of images that can be used to deploy the application

Containers are completely isolated environments, like using different machines but they all use the same OS kernel. Docker shares the kernel, which means it can run any OS on top of the kernel - except Windows

Main purpose of Docker to package applications, ship and run them as much as you want

#### Containers vs. Virtual Machines&#x20;

Each VM has its own OS inside it, which takes much more processing power, consumes higher disk space, and boots up much more slowly than Docker containers. Docker also has less isolation between services.

It isn’t either/or though - Docker containers are often provisioned on virtual machines

#### Common Docker commands&#x20;

* `docker run {container}` - start a container&#x20;
* `docker ps` - list all running containers
* `docker ps -a` - list all containers including those that are stopped&#x20;
* `docker stop {container}` - stop a container (provide id or name to stop it)&#x20;
* `docker rm {container}` - remove a stopped container permanently&#x20;
* `docker images` - list images&#x20;
* `docker rmi {image}` - remove images (make sure no containers are running off this image before deleting)&#x20;
* `docker pull {image}` - download an image (and not run it)

You can add parameters to these commands.

`-p` specifies port eg.

`docker run -p 38282:8080 {image}`

`-e` sets an environment variable

`docker run -e APP_COLOR=blue {image}`

To find what is in an environment variable of a container that’s already running:

&#x20;`docker inspect {container}`

To build an image from a Dockerfile, go to the file containing the Dockerfile and run:

&#x20;`docker build -t {file}`



These parameters can be stacked, for example, if you wanted to run a container named blue-app using image example/simple-webapp and also wanted to set the environment variable APP\_COLOR to blue, make the application available on port 38282 on the host with the application listening on port 8080 you would use:

`docker run -p 38282:8080 --name blue-app -e APP_COLOR=blue -d example/simple-webapp`

#### Create your own image

Do if:&#x20;

1. Cannot find a component or service that you want to use as part of your app&#x20;
2. You want to containerise your existing application

To do this, make a list of instructions you’d need to complete to run your application, eg. downloading python/pip dependencies. Then translate this into the Dockerfile. Docker images should be small and lightweight.

Every Docker image must be based on another image, either an OS or another image based on an OS. All official OS releases are on Docker Hub. All Dockerfiles must start with a `FROM` instruction stating this OS or image of an OS.

#### CMD vs. Entrypoint&#x20;

Unlike virtual machines, containers are not meant to hold an OS, but are meant to run a specific task or process eg. an instance of a web/application server or database. Once that task or process is complete it exits.

* CMD - defines the program run within the container when it starts
* Entrypoint - don’t have to write the definition of the program, so command line can just take parameters for the program in the container

Eg.

`docker run ubuntu-sleeper sleep` 10 Vs. `docker run ubuntu-sleeper 10`

Use them together to specify a default value for the parameter in case the user does not enter one eg.

`FROM ubuntu`&#x20;

`ENTRYPOINT [“sleep”]`&#x20;

`CMD [“5”]`

#### Networking

When you install Docker it creates three networks automatically - bridge, none, and host Bridge is the default that a container gets attached to, but you can use the network cmd line parameter to change this eg. Docker run ubuntu –network=host

* _Bridge_

Bridge is a private, internal network. To make these containers accessible to outside, map them to ports on the host network, or associate the container with the host network. A bridge network allows containers connected to the same bridge network to communicate, while providing isolation from containers which are not connected to that bridge network.

* _None_

In the none network the containers run in an isolated network with no links out. If you want to completely disable the networking stack on a container, you can use the --network none flag when starting the container. Within the container, only the loopback device is created.

* _Host_

If you use the host network mode for a container, that container’s network stack is not isolated from the Docker host

Host mode networking can be useful to optimize performance, and in situations where a container needs to handle a large range of ports, as it does not require network address translation (NAT), and no “userland-proxy” is created for each port. Info on a container’s network can be found with the docker inspect command

Can create a user-defined network based on one of these networks. Eg. `docker network create --driver bridge --subnet 182.18.0.1/24 --gateway 182.18.0.1 wp-mysql-network`

Containers can connect to each other using their container name thanks to an internal DNS.

To see networks on system: `docker network ls`

#### Docker storage

When Docker is installed it creates a storage structure `/var/lib/docker`. All docker data is stored here by default. Docker has a cache which is used when building images with some of the same layers as each other (ie. repeated lines in image Dockerfiles) such as download python.

You can add a persistent volume to a container to persist data created by the container eg. Docker volume create data\_volume Then mount it to the image with -v&#x20;

`docker run -v data_volume:/var/lib/mysql mysql`

Even if the container is destroyed, the data is saved

`–mount` is preferred for this though as you have to then supply each variable separately and more clearly.

#### Docker compose

Compose is used when setting up a more complicated application that runs multiple services. A YAML file can be made to specify what needs to be done. This is easier to implement and maintain as all details of the application will be stored in the compose configuration YAML file.

Link running services together with –link, however this is deprecated and may be removed soon. It can be done better with a docker compose as below.

Example of a docker compose file:

`services:`&#x20;

&#x20;     `redis:`&#x20;

&#x20;        `image: redis:alpine`&#x20;

&#x20;     `clickcounter:`&#x20;

&#x20;        `image: kodekloud/click-counter`&#x20;

&#x20;         `ports: - 8085:5000`&#x20;

`version: '3.0'`
