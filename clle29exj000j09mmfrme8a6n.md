---
title: "Day 20 — Docker Interview Questions for DevOps Engineer"
datePublished: Wed Aug 16 2023 18:23:20 GMT+0000 (Coordinated Universal Time)
cuid: clle29exj000j09mmfrme8a6n
slug: day-20-docker-interview-questions-for-devops-engineer
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692209207610/fed2d129-56e7-485d-ad81-64a280f4641c.png
tags: ubuntu, docker, devops, 90daysofdevops, trainwithshubham

---

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
    
    ![](https://miro.medium.com/v2/resize:fit:875/1*sPFJiV5skvHlPGjeCVfwpQ.jpeg align="left")
    
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
        
    * During the migration of applications to the cloud and supports hybrid cloud deployments. Docker’s portability and consistency help in achieving flexibility and scalability in cloud deployments.
        
18. **How to implement CI/CD in Docker?**
    
    Explain the full process to the interviewer.
    
    The full implementation can be understood through the documentation from docker: [CI/CD in Docker](https://docs.docker.com/language/java/configure-ci-cd/).
    
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
    
    ```plaintext
    docker ps
    ```
    
23. **What is the command to run the container under a specific name?**
    
    By using — name with the docker run command:
    
    ```plaintext
    docker run --name container_name image_name
    ```
    
24. **How do you save a docker?**
    
    There are multiple ways to save or export a docker:
    
    * We can use the docker save command to save the container or image as a tar file.
        
    
    ```plaintext
    docker save imagename > image.tar
    ```
    
    * We can use the docker export command to export the container or image as a tar file.
        
    
    ```plaintext
      docker export image_name > image.tar
    ```
    
25. **How do you create a docker container based on an existing container?**
    
    By using the docker commit command:
    
    ```plaintext
    docker commit existing_container new_container
    ```
    
26. **What is the command to import an already existing docker image?**
    
    By using the docker load command, we can import an already existing command which was saved using the docker save command:
    
    ```plaintext
    docker load -i <image.tar>
    ```
    
27. **What is the command to delete a container?**
    
    We use the docker rm command:
    
    ```plaintext
    docker rm container1_id container2_id
    ```
    
    To delete all stopped containers, we can use the prune command:
    
    ```plaintext
    docker container prune
    ```
    
28. **What is the command to remove all stopped containers, unused networks, build caches, and dangling images?**
    
    The command is:
    
    ```plaintext
    docker system prune -f
    ```
    
    \-f is used to bypass the confirmation prompt.
    
29. **How can you monitor Docker containers and collect metrics for performance analysis?**
    
    By using the docker stats command, the real-time performance metrics for running containers can be obtained. It provides information on CPU usage, memory consumption, network I/O, and more.
    
30. **How do you share Docker images with others?**
    
    * We can use Docker Hub or any container registry as the central repository to share the docker images with our team members.
        
    * Or else we can export the docker image as a tar file and share it with others.
        
31. **How do you remove a docker image and docker volume?**
    
    To delete an image:
    
    ```plaintext
    docker rmi image_name
    ```
    
    To delete a volume:
    
    ```plaintext
    docker volume rm volume_name
    ```
    
32. **How do you link multiple Docker containers together?**
    
    * By using the docker network.
        
    * By setting environment variables.
        
    * By using docker-compose.
        
33. **Explain the purpose of Docker Compose. How is it used?**
    
    Docker Compose is a tool that allows you to define and manage multi-container Docker applications. It simplifies the process of running multiple containers together, enabling you to define their configuration, dependencies, and network connections in a declarative YAML file.
    
    The main purposes of Docker Compose are to define services, manage dependencies, create networks, simplify configurations, and help in development workflows.
    
    To use Docker Compose, you define your application stack in a docker-compose.yaml file, and then use commands like docker-compose up and docker-compose down to manage the lifecycle of the containers.
    
34. **Can we use JSON instead of YAML while developing a docker-compose file in Docker?**
    
    Yes. By using:
    
    ```plaintext
    docker-compose -f docker-compose.json up
    ```
    
35. **What features are provided by Docker Enterprise Edition instead of Docker Community Edition?**
    
    Docker Enterprise Edition provides certified Docker images and plugins. It also provides Active Directory or LDAP user integration, continuous vulnerability and security scans, and container app and image management features.
    
36. **What are the security best practices when working with Docker?**
    
    * Use officially certified images.
        
    * Regularly update images.
        
    * Do not provide all privileges to non-root use. Limit the privileges.
        
    * Secure the docker host.
        
    * Keep logging and monitoring the container activities.
        
    * Don’t store secure keys and configuration in a file or directory. Store them as environment variables.
        
    * Perform up-to-date security checks and keep updating the security vulnerabilities.
        

In this blog, I have put my heart to collect interview questions on Docker. If you have any questions or would like to share your experiences, feel free to leave a comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.

To help me improve my blog and correct my mistakes, I am available on LinkedIn as [**Harsh Rajotya**](https://www.linkedin.com/in/harsh-rajotya/)**.** Do reach me and I am open to suggestions and corrections.

#Day21 #90daysofdevops