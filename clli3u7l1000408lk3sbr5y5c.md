---
title: "Day 20,21 [ Docker CheatSheet, Docker Interview Questions for DevOps Engineer]"
datePublished: Sat Aug 19 2023 14:18:34 GMT+0000 (Coordinated Universal Time)
cuid: clli3u7l1000408lk3sbr5y5c
slug: day-2021-docker-cheatsheet-docker-interview-questions-for-devops-engineer
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692454050246/473c9144-293b-4bd4-adfe-17d25cb97cf0.png

---

# **Container Management CLIs**

![](https://miro.medium.com/v2/resize:fit:875/0*wxIwUKubVAa8V8o3.png align="left")

# **Inspecting The Container**

![](https://miro.medium.com/v2/resize:fit:875/0*t_5fRfbXa-B2lMtd.png align="left")

# **Interacting with Container**

![](https://miro.medium.com/v2/resize:fit:875/0*0GGU8k1s3kAncHGo.png align="left")

# **Image Management Commands**

![](https://miro.medium.com/v2/resize:fit:875/0*d6sdX-L2FAZVM8Yj.png align="left")

# **Image Transfer Commands**

![](https://miro.medium.com/v2/resize:fit:875/0*TaY-meNaUbV9Wsk5.png align="left")

# **Builder Main Commands**

![](https://miro.medium.com/v2/resize:fit:875/0*MFN3mZWgdVjoHSDX.png align="left")

# **The Docker CLI**

## **Manage imagesdocker build**

`docker build`

```plaintext
docker build [options] .
  -t "app/container_name"    # name
```

Create an `image` from a Dockerfile.

`docker run`

```plaintext
docker run [options] IMAGE
  # see `docker create` for options
```

Run a command in an `image`.

# **Manage containers**

`docker create`

```plaintext
docker create [options] IMAGE
  -a, --attach               # attach stdout/err
  -i, --interactive          # attach stdin (interactive)
  -t, --tty                  # pseudo-tty
      --name NAME            # name your image
  -p, --publish 5000:5000    # port map
      --expose 5432          # expose a port to linked containers
  -P, --publish-all          # publish all ports
      --link container:alias # linking
  -v, --volume `pwd`:/app    # mount (absolute paths needed)
  -e, --env NAME=hello       # env vars
```

# **Example**

```plaintext
$ docker create --name app_redis_1 \
  --expose 6379 \
  redis:3.0.2
```

Create a `container` from an `image`.

`docker exec`

```plaintext
docker exec [options] CONTAINER COMMAND
  -d, --detach        # run in background
  -i, --interactive   # stdin
  -t, --tty           # interactive
```

# **Example**

```plaintext
$ docker exec app_web_1 tail logs/development.log
$ docker exec -t -i app_web_1 rails c
```

Run commands in a `container`.

`docker start`

```plaintext
docker start [options] CONTAINER
  -a, --attach        # attach stdout/err
  -i, --interactive   # attach stdin
docker stop [options] CONTAINER
```

Start/stop a `container`.

`docker ps`

```plaintext
$ docker ps
$ docker ps -a
$ docker kill $ID
```

Manage `container`s using ps/kill.

# **Images**

`docker images`

```plaintext
$ docker images
  REPOSITORY   TAG        ID
  ubuntu       12.10      b750fe78269d
  me/myapp     latest     7b2431a8d968
$ docker images -a   # also show intermediate
```

Manages `images`.

`docker rmi`

```plaintext
docker rmi b750fe78269d
```

Deletes `images`

**Also, see**

* [**Getting Started**](http://www.docker.io/gettingstarted/) *(*[***docker.io***](http://docker.io)*)*
    

# **Dockerfile**

## **Inheritance**

```plaintext
FROM ruby:2.2.2
```

# **Variables**

```plaintext
ENV APP_HOME /myapp
RUN mkdir $APP_HOME
```

# **Initialization**

```plaintext
RUN bundle install
WORKDIR /myapp
VOLUME ["/data"]
# Specification for mount point
ADD file.xyz /file.xyz
COPY --chown=user:group host_file.xyz /path/container_file.xyz
```

# **Onbuild**

```plaintext
ONBUILD RUN bundle install
# when used with another file
```

# **Commands**

```plaintext
EXPOSE 5900
CMD    ["bundle", "exec", "rails", "server"]
```

# **Entrypoint**

```plaintext
ENTRYPOINT ["executable", "param1", "param2"]
ENTRYPOINT command param1 param2
```

Configures a container that will run as an executable.

```plaintext
ENTRYPOINT exec top -b
```

This will use shell processing to substitute shell variables, and will ignore any `CMD` or `docker run` command line arguments.

# **Metadata**

```plaintext
LABEL version="1.0"
LABEL "com.example.vendor"="ACME Incorporated"
LABEL com.example.label-with-value="foo"
LABEL description="This text illustrates \
that label-values can span multiple lines."
```

# **See also**

* [**https://docs.docker.com/engine/reference/builder/**](https://docs.docker.com/engine/reference/builder/)
    

# **docker-compose**

# **Basic example**

```plaintext
# docker-compose.yml
version: '2'services:
  web:
    build: .
    # build from Dockerfile
    context: ./Path
    dockerfile: Dockerfile
    ports:
     - "5000:5000"
    volumes:
     - .:/code
  redis:
    image: redis
```

# **Commands**

```plaintext
docker-compose start
docker-compose stop
docker-compose pause
docker-compose unpause
docker-compose ps
docker-compose up
docker-compose down
```

# **Reference**

# **Building**

```plaintext
web:
  # build from Dockerfile
  build: .
# build from custom Dockerfile
  build:
    context: ./dir
    dockerfile: Dockerfile.dev
# build from image
  image: ubuntu
  image: ubuntu:14.04
  image: tutum/influxdb
  image: example-registry:4000/postgresql
  image: a4bc65fd
```

# **Ports**

```plaintext
ports:
    - "3000"
    - "8000:80"  # guest:host
# expose ports to linked services (not to host)
  expose: ["3000"]
```

# **Commands**

```plaintext
# command to execute
  command: bundle exec thin -p 3000
  command: [bundle, exec, thin, -p, 3000]
# override the entrypoint
  entrypoint: /app/start.sh
  entrypoint: [php, -d, vendor/bin/phpunit]
```

# **Environment variables**

```plaintext
# environment vars
  environment:
    RACK_ENV: development
  environment:
    - RACK_ENV=development
# environment vars from file
  env_file: .env
  env_file: [.env, .development.env]
```

# **Dependencies**

```plaintext
# makes the `db` service available as the hostname `database`
  # (implies depends_on)
  links:
    - db:database
    - redis
# make sure `db` is alive before starting
  depends_on:
    - db
```

# **Other options**

```plaintext
# make this service extend another
  extends:
    file: common.yml  # optional
    service: webapp
volumes:
    - /var/lib/mysql
    - ./_data:/var/lib/mysql
```

# **Advanced features**

# **Labels**

```plaintext
services:
  web:
    labels:
      com.example.description: "Accounting web app"
```

# **DNS servers**

```plaintext
services:
  web:
    dns: 8.8.8.8
    dns:
      - 8.8.8.8
      - 8.8.4.4
```

# **Devices**

```plaintext
services:
  web:
    devices:
    - "/dev/ttyUSB0:/dev/ttyUSB0"
```

# **External links**

```plaintext
services:
  web:
    external_links:
      - redis_1
      - project_db_1:mysql
```

# **Hosts**

```plaintext
services:
  web:
    extra_hosts:
      - "somehost:192.168.1.100"
```

# **sevices**

To view list of all the services runnning in swarm

```plaintext
docker service ls
```

To see all running services

```plaintext
docker stack services stack_name
```

to see all services logs

```plaintext
docker service logs stack_name service_name
```

To scale services quickly across qualified node

```plaintext
docker service scale stack_name_service_name=replicas
```

# **clean up**

To clean or prune unused (dangling) images

```plaintext
docker image prune
```

To remove all images which are not in use containers, add — a

```plaintext
docker image prune -a
```

To Purne your entire system

```plaintext
docker system prune
```

To leave swarm

```plaintext
docker swarm leave
```

To remove swarm ( deletes all volume data and database info)

```plaintext
docker stack rm stack_name
```

To kill all running containers

```plaintext
docker kill $(docker ps -q )
```

# Day 21 — Docker Interview Questions for DevOps Engineer

Now that I am almost pulling the curtains for the DOCKER topic in the 90 days challenge, here’s the final nail in the coffin. The most exciting part for those who have interviews lined up!

The Docker Interview Questions Blog. Along with the answers!

1. **What is Docker?**
    
    Docker is an open-source platform that allows you to automate the deployment and management of applications within lightweight, isolated containers.
    
2. **Why and when to use Docker?**
    
    We use Docker:
    
    * Package applications and dependencies to containers making them isolated which makes it easier to deploy and run consistently across different environments.
        
    * Docker supports scaling allowing multiple containers to run on a single host machine.
        
    * Docker integrates well with CI/CD pipeline allowing to automate through the stages.
        
    * Docker Hub, registry, allows us to share and discover images publicly.
        
    * Docker is valuable when we want to achieve application isolation, portability, scalability, simplified deployment, CI/CD automation, microservices architecture, reproducible environments, and collaboration in software development and deployment.
        
3. **What are the disadvantages of using docker?**
    
    * Docker introduces additional security considerations like kernel sharing, tampered images, and secret sharing.
        
    * Docker can add complexity when managing distributed systems with multiple containers and networking requirements.
        
    * Docker containers are designed to be ephemeral, which means they are not intended for long-term storage or managing stateful applications.
        
    * Although Docker containers have lower resource overhead compared to virtual machines, there is still a slight performance impact due to the additional layer of abstraction and the shared kernel.
        
4. **What is the basic architecture behind Docker?**
    
    Docker is built on the client-server model.
    
5. **Explain the Docker architecture.**
    
    Docker architecture consists of three main components:
    
    * Docker Engine: It is the runtime that runs and manages containers. It includes the Docker daemon (dockerd) running on the host machine and the Docker CLI (docker) used for interacting with the Docker daemon.
        
    * Docker Images: They are read-only templates used to create Docker containers.
        
    * Docker Containers: They are lightweight and isolated runtime environments created from Docker images.
        
6. **Explain the terminology: Docker Compose, Docker File, Docker Image, Docker Container?**
    
    Docker Compose is a tool that allows you to define and manage multi-container applications. A Dockerfile is a text file that contains instructions for building a Docker image. It specifies the base image, environment variables, software dependencies, configuration settings, and commands to be executed during the image build process. A Docker image is a read-only template or snapshot that serves as the basis for creating Docker containers. A Docker container is a lightweight, isolated, and executable instance of a Docker image.
    
7. **Can you tell the difference between Docker and Hypervisor?**
    
    Docker and a hypervisor are both technologies used for virtualization.
    
    ![](https://miro.medium.com/v2/resize:fit:875/0*VZpbWnegwR4G2T7M.jpeg align="left")
    
8. **What is the difference between an Image, a Container, and an Engine?**
    
    Image: An image is a lightweight, standalone, and executable software package that includes everything needed to run a piece of software.
    
    Container: A container is an instance of an image that runs as a separate and isolated process on a host operating system.
    
    Engine: The engine often referred to as a container runtime or container engine, is responsible for managing the lifecycle of containers. The engine interacts with the underlying operating system’s kernel to create and manage isolated environments for containers, including resource allocation, networking, and storage.
    
9. **What is a Docker namespace?**
    
    In Docker, namespaces are a key feature of the Linux kernel that enables process isolation and provide separate and independent environments for various system resources. Docker leverages namespaces to create lightweight and isolated containers. Some commonly used Docker namespaces are pid, net, mnt, uts, ipc.
    
10. **What is a Docker registry?**
    
    A Docker registry is a central repository for storing and distributing Docker images. The most commonly used Docker registry is Docker Hub.
    
11. **What is the difference between the Docker command COPY vs ADD?**
    
    COPY command copies files or directories from the host machine to the container. ADD command also copies files or directories from the host machine to the container, but it has additional features like handling automatic extraction of compressed archives (such as tar, gzip, and bzip2) and retrieving files from remote URLs.
    
12. **What is the Difference between the Docker command CMD vs RUN?**
    
    CMD command specifies the default command to be executed when a container is run and can be overwritten. Whereas, RUN executes commands during the image build process.
    
13. **What is an ENTRYPOINT?**
    
    The ENTRYPOINT instruction in a Dockerfile is used to specify the command or script that should be executed when a container is run from the Docker image. It sets the primary command that will be executed within the container.
    
14. **How is ENTRYPOINT different from the CMD command of Docker?**
    
    ENTRYPOINT gets executed post-container launch and cannot be overwritten. But a new command can be attached(appended).
    
15. **Why do we use EXPOSE in the docker file?**
    
    The EXPOSE instruction in a Dockerfile is used to specify the ports on which a container will listen for connections. It does not publish or expose those ports to the host or the outside world. It is more like a documentation mechanism to inform users of the intended network ports used by the container.
    
16. **How Will you reduce the size of the Docker image?**
    
    * Choosing lightweight base images.
        
    * Installing only necessary dependencies.
        
    * Combining multiple RUN commands in the docker file into a single command.
        
    * Removing temporary and unnecessary files.
        
17. **In what real scenarios have you used Docker?**
    
    This you can explain from your project experience. I have used Docker in a few real scenarios:
    
    * While working with CI/CD pipeline, to automate the build, testing, and deployment of applications. Docker containers provide a lightweight and portable unit that can be easily deployed to various platforms.
        
    * During the migration of applications to the cloud and supports hybrid cloud deployments. Docker’s portability and consistency helps in achieving flexibility and scalability in cloud deployments.
        
18. **How to implement CI/CD in Docker?**
    
    Explain the full process to the interviewer.
    
    The full implementation can be understood through the documentation from docker: [**CI/CD in Docker**](https://docs.docker.com/language/java/configure-ci-cd/).
    
19. **What is the lifecycle of a docker container?**
    
    The stages of the lifecycle of a docker container are as follows:
    
    * Create: The container is created based on an image, but not running.
        
    * Start: The container is started using the docker start command.
        
    * Run: The container is running and continues to execute the commands or services specified in the image.
        
    * Pause/Unpause: Pausing a container temporarily suspends its processes while unpausing resumes its execution without starting the container from scratch.
        
    * Stop: The container is gracefully stopped using the docker stop command.
        
    * Remove: The container is removed using the docker rm command.
        
20. **Will data on the container be lost when the docker container exits?**
    
    By default, no data is preserved when the container exits.
    
21. **If so, how do you preserve data when the container exits?**
    
    * Docker volumes are a way to store and manage persistent data independently of the container’s lifecycle.
        
    * With bind mounts, data is stored on the host’s file system and remains available even after the container exits.
        
    * By using external storage solutions like NAS.
        
22. **How do you view running containers?**
    
    By using the command:
    
    1. ```plaintext
         docker ps
        ```
        
    2. **What is the command to run the container under a specific name?**
        
        By using — name with the docker run command:
        
        ```plaintext
        docker run --name container_name image_name
        ```
        
    3. **How do you save a docker?**
        
        There are multiple ways to save or export a docker:
        
        * We can use the docker save command to save the container or image as a tar file.
            
    
    ```plaintext
        docker save imagename > image.tar
    ```
    
    * We can use the docker export command to export the container or image as a tar file.
        
    
    ```plaintext
        docker export image_name > image.tar
    ```
    
    1. **How do you create a docker container based on an existing container?**
        
        By using the docker commit command:
        
        ```plaintext
        docker commit existing_container new_container
        ```
        
    2. **What is the command to import an already existing docker image?**
        
        By using the docker load command, we can import an already existing command which was saved using the docker save command:
        
        ```plaintext
        docker load -i <image.tar>
        ```
        
    3. **What is the command to delete a container?**
        
        We use the docker rm command:
        
        ```plaintext
        docker rm container1_id container2_id
        ```
        
        To delete all stopped containers, we can use the prune command:
        
        ```plaintext
        docker container prune
        ```
        
    4. **What is the command to remove all stopped containers, unused networks, build caches, and dangling images?**
        
        The command is:
        
        ```plaintext
        docker system prune -f
        ```
        
        \-f is used to bypass the confirmation prompt.
        
    5. **How can you monitor Docker containers and collect metrics for performance analysis?**
        
        By using the docker stats command, the real-time performance metrics for running containers can be obtained. It provides information on CPU usage, memory consumption, network I/O, and more.
        
    6. **How do you share Docker images with others?**
        
        * We can use Docker Hub or any container registry as the central repository to share the docker images with our team members.
            
        * Or else we can export the docker image as a tar file and share it with others.
            
    7. **How do you remove a docker image and docker volume?**
        
        To delete an image:
        
        ```plaintext
        docker rmi image_name
        ```
        
        To delete a volume:
        
        ```plaintext
        docker volume rm volume_name
        ```
        
    8. **How do you link multiple Docker containers together?**
        
        * By using the docker network.
            
        * By setting environment variables.
            
        * By using docker-compose.
            
    9. **Explain the purpose of Docker Compose. How is it used?**
        
        Docker Compose is a tool that allows you to define and manage multi-container Docker applications. It simplifies the process of running multiple containers together, enabling you to define their configuration, dependencies, and network connections in a declarative YAML file.
        
        The main purposes of Docker Compose are to define services, manage dependencies, create networks, simplify configurations, and help in development workflows.
        
        To use Docker Compose, you define your application stack in a docker-compose.yaml file, and then use commands like docker-compose up and docker-compose down to manage the lifecycle of the containers.
        
    10. **Can we use JSON instead of YAML while developing a docker-compose file in Docker?**
        
        Yes. By using:
        
        ```plaintext
        docker-compose -f docker-compose.json up
        ```
        
    11. **What features are provided by Docker Enterprise Edition instead of Docker Community Edition?**
        
        Docker Enterprise Edition provides certified Docker images and plugins. It also provides Active Directory or LDAP user integration, continuous vulnerability and security scans, and container app and image management features.
        
    12. **What are the security best practices when working with Docker?**
        
        * Use officially certified images.
            
        * Regularly update images.
            
        * Do not provide all privileges to non-root use. Limit the privileges.
            
        * Secure the docker host.
            
        * Keep logging and monitoring the container activities.
            
        * Don’t store secure keys and configuration in a file or directory. Store them as environment variables.
            
        * Perform up-to-date security checks and keep updating the security vulnerabilities.
            
    
    In this blog, I have put my heart to collect interview questions on Docker. If you have any questions or would like to share your experiences, feel free to leave a comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.