---
title: "Day 19 Docker Volume & Docker Network | Docker for DevOps"
datePublished: Tue Aug 15 2023 18:41:20 GMT+0000 (Coordinated Universal Time)
cuid: cllcngpsg000709mt54r7hzim
slug: day-19-docker-volume-docker-network-docker-for-devops
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692124762491/afb13097-b948-43c9-b1d0-ebc64dd55e6f.png
tags: ubuntu, docker, devops, 90daysofdevops, trainwithshubham

---

Until now, I have learned how to create a docker-compose.yml file and push it to the repository. Let’s move forward and delve deeper into other Docker-compose.yml concepts like Docker Volume and Docker Network.

# **1\. Docker Volumes 📦**

Before I explain Docker Volumes, here is the link to the official documentation of [Docker Volumes](https://docs.docker.com/storage/volumes/).

In simple terms, volumes are the preferred way to store and keep data that is created or used by Docker containers.

When you run containers with Docker, they can generate or rely on certain data, such as configuration files, databases, or application outputs. Volumes provide a convenient and reliable method to persist this data. By using volumes, it is ensured that the data remains available even if the containers are stopped, restarted, or removed. It acts as a separate storage space specifically for container data, making it easy to manage and share data between containers as needed.

There is a concept called Bind Mounts. Bind mounts are a way to access and share files or directories between the host machine and a Docker container. Unlike volumes, which are managed by Docker and stored within the Docker environment, bind mounts link specific locations on the host file system directly to the container.

# **2\. Why Volumes over Bind Mount? 🔄**

Volumes have several advantages over bind mounts:

* Volumes are easier to back up or migrate than bind mounts.
    
* You can manage volumes using Docker CLI commands or the Docker API.
    
* Volumes work on both Linux and Windows containers.
    
* Volumes can be more safely shared among multiple containers.
    
* Volume drivers let you store volumes on remote hosts or cloud providers, encrypt the contents of volumes, or add other functionality.
    
* New volumes can have their content pre-populated by a container.
    
* Volumes on Docker Desktop have much higher performance than bind mounts from Mac and Windows hosts.
    
* Unlike a bind mount, you can create and manage volumes outside the scope of any container.
    

![](https://miro.medium.com/v2/resize:fit:628/0*jPvP4BT0OGR9dMkb.png align="center")

# **3\. Commands related to Docker Volumes ⌨️**

# **Create a volume:**

```plaintext
docker volume create my-vol
```

# **List volumes:**

```plaintext
docker volume ls
```

# **Inspect a volume:**

```plaintext
docker volume inspect my-vol
```

# **Remove a volume:**

```plaintext
docker volume rm my-vol
```

# **Attach a Volume to a Container:**

```plaintext
docker run -v myvolume:/path/in/container myimage
```

# **Detach a Volume from a Container:**

To detach a volume from a running container, you need to stop and remove the container. The volume will still exist and can be attached to other containers if needed.

```plaintext
docker container stop imagename
docker container rm imagename
```

# **4\. Docker Network 🌐**

Docker networking allows containers to communicate with each other and with external networks.

It provides a way for containers to establish connections, share information, and collaborate within a Docker environment.

# **5\. Commands related to Docker Network ⌨️**

# **Create a Network:**

```plaintext
docker network create mynetwork
```

# **List Networks:**

```plaintext
docker network ls
```

# **Inspect a Network:**

```plaintext
docker network inspect mynetwork
```

# **Connect a Container to a Network:**

```plaintext
docker run --network mynetwork myimage
```

# **Disconnect a Container from a Network:**

```plaintext
docker network disconnect mynetwork mycontainer
```

# **Remove a Network:**

```plaintext
docker network rm mynetwork
```

# **6\. Tasks 📋**

# **6.1 Task 1: Create a multi-container docker-compose file that will bring UP and bring DOWN containers in a single shot (Example — Create application and database container) 🚀**

Let us set up a multi-container Docker Compose file that brings up an application container and a database container, allowing you to start and stop them together.

For that, the docker-compose needs to be installed. I have given a detailed explanation of the installation of docker-compose in the blog: [Docker Compose Installation](https://snehaksuresh.hashnode.dev/docker-compose-docker-for-devops#heading-task-1-learn-how-to-use-the-docker-composeyml-file-to-set-up-the-environment-configure-the-services-and-links-between-different-containers-and-also-to-use-environment-variables-in-the-docker-composeyml-file).

So let us start with the docker-compose.yml file:

```plaintext
version : "3.3"
services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
    depends_on:
      - db
  db:
    image: mysql
    ports:
      - "3306:3306"
    environment:
      - "MYSQL_ROOT_PASSWORD=test@123"
```

In this example, I have defined two services: `web` and `db`. The `web` service represents the application container and the `db` service represents the database container.

![](https://miro.medium.com/v2/resize:fit:875/0*6bH_zE19A_Q--OPh align="left")

Now using docker-compose up we can start both containers:

```plaintext
docker-compose up
```

![](https://miro.medium.com/v2/resize:fit:875/0*MSKJfnCT_ffynMkD align="left")

Use the `docker-compose scale` command to increase or decrease the number of replicas for a specific service. You can also add [`replicas`](https://stackoverflow.com/questions/63408708/how-to-scale-from-within-docker-compose-file) in deployment file for *auto-scaling*.

```plaintext
docker-compose up --scale web=4
```

**To scale down you can use:**

```plaintext
docker-compose up --scale=2
```

**To down the docker-compose:**

```plaintext
docker compose down
```

# **6.2 Task 2: Learn how to use Docker Volumes and Named Volumes to share files and directories between multiple containers. 📂**

**To create a docker volume:**

```plaintext
sudo docker volume create --name myvol_1
```

![](https://miro.medium.com/v2/resize:fit:875/0*MBpHxCJNfKgzn0Id align="left")

**To mount the volume in a container:**

```plaintext
docker run -d -v myvol_1:/app/data <image_id>
```

![](https://miro.medium.com/v2/resize:fit:875/0*rzMczV105tpMV_rI align="left")

For shared volumes, include it in the docker-compose.yaml file:

![](https://miro.medium.com/v2/resize:fit:875/0*d83_6YCUk8ttG4h2 align="left")

To list all the volumes, you can use:

```plaintext
docker volume ls
```

![](https://miro.medium.com/v2/resize:fit:875/0*Up2JJ9k83zkBZ-Xt align="left")

**To inspect volumes, use:**

```plaintext
docker volume inspect <vol_name>
```

![](https://miro.medium.com/v2/resize:fit:875/0*vWwiC6owcG115xXJ align="left")

By using the docker exec command, I have verified that the data in both the containers is same:

```plaintext
docker exec -it <cont_ID> <command_oryou_can_start_bash>
```

I have used ls for the listing of all directories.

![](https://miro.medium.com/v2/resize:fit:875/0*SOlwyG-zOmTsJn6Z align="left")

Since I have completed my task, and no more need the docker volume I am going to delete the volumes:

```plaintext
docker volume rm volume_name
```

![](https://miro.medium.com/v2/resize:fit:875/0*XtWhdw0Z_hoJtP5Z align="left")

In conclusion, Docker volumes provide a way to persist and share data between containers in a Docker environment. They offer several advantages over bind mounts. When using Docker volumes, you can either create anonymous volumes or named volumes. Anonymous volumes are created automatically by Docker, while named volumes are explicitly defined in the Dockerfile or Docker Compose file.

In this blog, we explored the key features and common use cases of Docker Volumes. If you have any questions or would like to share your experiences, feel free to leave a comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversations.

#Day19 #90daysofdevops