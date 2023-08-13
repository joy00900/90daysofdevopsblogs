---
title: "Day 16. Introduction to Docker for DevOps Engineers."
datePublished: Sun Aug 13 2023 09:55:29 GMT+0000 (Coordinated Universal Time)
cuid: cll99srm7000r09l8eof5be0e
slug: day-16-introduction-to-docker-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691920383947/f7cd426e-ae77-408f-a167-8d0b944bcad2.jpeg

---

In this blog, I will discuss the open-source tool — Docker. Docker is used to automate the deployment, scaling, and management of applications using containerization.

But, **what are Containers?**

# **1\. Containers**

Containers are lightweight, isolated environments that package an application along with its dependencies, to run seamlessly on any infrastructure. They can be run on any machine that has Docker Installed.

## **1.1 Container Images**

Container Images or just Images are static files that cannot be edited. They are read-only files that have all the information needed to run an application.

## **1.2 Docker**

Docker is an open-source platform that allows you to automate the deployment, scaling, and management of applications using containerization.

## **1.2.1 Docker Architecture**

The Docker architecture, as in from the official website [Docker Architecture](https://docs.docker.com/get-started/overview/), is:

![](https://miro.medium.com/v2/resize:fit:875/1*8-PpGcZPiu2A3tdf2fw_Fw.jpeg align="left")

Docker uses Client-Server architecture.

The Docker client talks to the Docker daemon, which does the actual work of building, running, and distributing your containers. They can be on the same computer or different computers, and they communicate using a special language called a REST API. Docker Compose is an additional tool that helps you manage applications made up of multiple containers.

In simple words, *The Docker client* is a tool that you use to give instructions to Docker, like building and running containers. *The Docker daemon* is present in the Docker host. When you give a command to pull the image, the daemon fetches the image through the run command and runs it.

The registry from which the image needs to be pulled, information is provided by the image itself.

Let us install Docker in a Linux OS and play around with it to understand how it works.

## **1.2.2 Docker Installation**

First, we need to update the apt-get for security vulnerabilities. Then we install the Docker package.

```plaintext
sudo apt-get update
sudo apt-get install docker.io
docker ps
```

![](https://miro.medium.com/v2/resize:fit:875/1*nC0WwjIHyFgSTCusbaOmqg.png align="left")

You can see that the “docker ps” is throwing an error: “Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get “http://%2Fvar%2Frun%2Fdocker.sock/v1.24/containers/json": dial unix /var/run/docker.sock: connect: permission denied”, which means that the current user is not added to the group docker.

So let’s add the user to docker and then reboot.

```plaintext
sudo usermod -aG docker $USER
```

![](https://miro.medium.com/v2/resize:fit:875/1*Sk9XdFZP1n5f2vCWuetr9g.png align="left")

Then by executing the “docker ps” command we can observer that we can see that the error is gone.

![](https://miro.medium.com/v2/resize:fit:875/1*NgW7qIt7wpT6FonwnkWhqw.jpeg align="left")

Now let us complete some tasks which are part of the #90DaysofDevops Challenge.

# **2\. Tasks**

**2.1 Task 1: Use the** `docker run` **command to start a new container and interact with it through the command line/**

For example, let’s run hello-world.

```plaintext
docker run hello-world
```

![](https://miro.medium.com/v2/resize:fit:875/1*KoLKffAIj8xZsIKrCtdqBw.png align="left")

The above docker run command shows that the docker image installation is successful.

Let’s pull an MYSQL package from the DockerHub and interact with it in the terminal.

**DockerHub** is the public registry where docker images are available, powered by Docker. There are many other registries available like **Amazon Elastic Container Registry, Google Container Registry, JFrog Artifactory, etc.**

Also if you just want to pull the image we use docker pull to image. The docker run command pulls and builds the image.

```plaintext
docker pull mysql
docker run -it -e MYSQL_ROOT_PASSWORD=password mysql bash
```

\-it stands for interactive terminal

\-e stands for eb=nvironment variable

MYSQL\_ROOT\_PASSWORD stores the password.

Bash indicates that we can interact with the terminal via bash.

![](https://miro.medium.com/v2/resize:fit:875/1*LKxUnjiCVdU-mYaM2rK1yQ.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*fpjVYFK5OAkfU5cWuRkrvA.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*beDTEIWGadNIQzwzLIll0Q.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*1V8_Ro43mL962hQLCHoKGw.png align="left")

We can see that the output of the docker pull command that the tag: latest is being considered. This means that if the version is not specified, docker pulls the latest image from the registry.

We can exit the interactive terminal using the exit command.

**2.2 Task 2: Use the** `docker inspect` **command to view detailed information about a container or image**

To list the container and its information we use the docker ps command.

![](https://miro.medium.com/v2/resize:fit:875/1*xfE7kTNrHDOvKmxPypqOJA.png align="left")

The `docker inspect` the command is used to obtain detailed information about Docker objects such as containers, images, networks, and volumes. It is in the JSON format.

```plaintext
docker inspect container_id
```

![](https://miro.medium.com/v2/resize:fit:875/1*JesFS0wDmWjPCHdWhk7nVg.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*OqFQJdgECJW-eNldrJGP5g.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*cVE5Dv8Zz8YTt6sxe7vpRg.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*ixc3992DX6AeHOYpkOtUpg.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*BvKNNBkcVrIE1thPilk3yQ.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*kn0qXdr9FaiknraoUM4QpQ.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*Yxx085cTZZpK1pq2Uc9YiA.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*7AfYDT3FPOeroHdfAnjOmw.png align="left")

**2.3 Task 3: Use the** `docker port` **command to list the port mappings for a container.**

Since previously I had not bound the container to any port, first, let’s bind to the port and then use the docker port command.

```plaintext
docker run -p 3306:3306 -e MYSQL_ROOT_PASSWORD=password -d mysql
docker ps
docker port container_ID_thathasbeenmappedtoport
```

![](https://miro.medium.com/v2/resize:fit:875/1*xSZA9H44ZLDgQ869EF7hEg.png align="left")

The docker port command can display the port mappings for only running containers. Hence we have run the image in detached mode (-d).

The docker port output shows the port mappings, i.e., the exposed ports of the container to the corresponding host bindings.

**2.4 Task 4: Use the** `docker stats` **command to view resource usage statistics for one or more containers.**

The docker stats command is used to display real-time resource usage statistics for running containers. It provides information such as CPU usage, memory consumption, network I/O, and block I/O of each container.

```plaintext
docker stats
```

![](https://miro.medium.com/v2/resize:fit:875/1*KGG5CMWs6FvWgDsIiKiZ6Q.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*0BJhqHUjNzLLklnco7siqQ.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*5pEkMAY3Sp8TJm_M7OKtoQ.png align="left")

**2.5 Task 5: Use the** `docker top` **command to view the processes running inside a container**

The docker top command is used to display running processes inside the container. This command does not provide real-time updates. For that one needs to use the docker stats command.

```plaintext
docker top container_id
```

![](https://miro.medium.com/v2/resize:fit:875/1*naiDWEqoY1GNgnFcvFs_hw.png align="left")

**2.6 Task 6: Use the** `docker save` **command to save an image to a tar archive**

We use the docker save command to save one or more docker images to a tar archive.

```plaintext
docker save -o image.tar image:tag
```

* o specifies the path and filename for generated tar archive.
    

![](https://miro.medium.com/v2/resize:fit:875/1*ZI4W-ukj8l-O_rleb36r_g.png align="left")

**2.7 Task 7: Use the** `docker load` **command to load an image from a tar archive**

The docker load command restores the saved images into your local Docker environment, making them available for use.

```plaintext
docker load -i image.tar
```

* i specify the tar archive file to load the docker images from.
    

![](https://miro.medium.com/v2/resize:fit:875/1*4BAwePSAOSiFqfvG56CmWg.png align="left")

Well, this was it for this blog. Until then, keep reading my blogs and connect with me on LinkedIn and let’s have a conversation.

To help me improve my blog and correct my mistakes, I am available on LinkedIn as [Harsh Rajotya](https://www.linkedin.com/in/harsh-rajotya/) . Do reach me and I am open to suggestions and corrections.

#Day16 #90DaysofDevops