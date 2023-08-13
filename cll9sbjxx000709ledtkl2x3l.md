---
title: "Day 17 Task: Docker Project for DevOps Engineers."
datePublished: Sun Aug 13 2023 18:33:58 GMT+0000 (Coordinated Universal Time)
cuid: cll9sbjxx000709ledtkl2x3l
slug: day-17-task-docker-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691951505363/a8f23d07-c40c-40ff-bcd7-c4ed19c81f95.png
tags: ubuntu, docker, devops, 90daysofdevops, trainwithshubham

---

In this blog, let’s learn about what a Dockerfile is and use the dockerfile to create a container.

# **1\. Dockerfile**

Dockerfile is a text file used to define a set of instructions to build a Docker image. When we use the Docker command-line interface (CLI) to build an image, it reads the instructions from the Dockerfile and executes them to create the image.

The name of the docker file will always be *dockerfile* and nothing else.

A dockerfile will have instructions written in the following format:

```plaintext
keyword argument
```

A dockerfile will always start with FROM and FROM can only be used once. A RUN keyword can be used multiple times. But wait, what are these keywords? To understand that I have created the dockerfile format:

```plaintext
FROM <baseimage>
RUN <installedsoftware_or_runcommands>
ENV <environmentvariable>
WORKDIR <dafault_directory>
COPY <argument>
ADD <argument>
CMD <argument>
ENTRYPOINT <argument>
EXPOSE <argument>
VOLUME <argument>
```

Let us understand what these keywords are.

## **🐳 FROM**

FROM is the mandatory keyword. FROM specifies the Base Image that the Docker images are to be built from according to our customization. Docker images are never built from scratch, they are built on base images. Below is an example of how to use the keyword FROM:

```plaintext
FROM ubuntu
```

## **⚙️ RUN**

RUN is a keyword that can be repeated multiple times. It is used to provide the Linux commands like installing a package, uninstalling, upgrading a package, creating a directory, or permitting users. Below is an example of how to use the keyword RUN:

```plaintext
RUN apt-get update
```

## **🌐 ENV**

ENV is a keyword used for environment variables. It defines variables and values that can be used in dockerfile. Below is an example of how to use the keyword ENV:

```plaintext
ENV abc=hello
```

## **📂 WORKDIR**

WORKDIR is used to specify the default directory where the commands will be executed. Below is an example of how to use the keyword WORKDIR:

```plaintext
WORKDIR /path/to/workdir
```

If the WORKDIR is not specified, it will be created automatically by the Docker compiler and the default will be the ROOT directory (`/`).

## **📦 COPY**

COPY is used to copy files from the host machine to the container directory.

## **➕ ADD**

ADD is used to copy files from the host machine to the container directory and it can also copy TAR files and unzip them on the container directory.

## **🖥️ CMD**

By using the keyword CMD, we will provide the commands or name of the script that *should run when the container is launched.* This can be overwritten by the user.

## **🏁 ENTRYPOINT**

The commands get executed post-container launch while using the keyword ENTRYPOINT. It cannot be overwritten and a new command can be appended.

## **🌐 EXPOSE**

The keyword EXPOSE specifies the port number that needs to be exposed on the container.

## **💾 VOLUME**

The keyword VOLUME is used to inform users of the Docker image that certain directories within the container should be treated as volumes when running a container based on that image.

# **2\. Task: Create a Dockerfile for a simple web application (e.g., a Node.js or Python app).  
🏗️ Build the image using the Dockerfile and run the container.  
👀 Verify that the application is working as expected by accessing it in a web browser.  
🚀 Push the image to a public or private repository (e.g., Docker Hub).**

I have used the following repository for the task: [https://github.com/Azure-Samples/nodejs-docs-hello-world.git](https://github.com/Azure-Samples/nodejs-docs-hello-world.git)

Using the git clone command, clone the repository to your machine. Then get into the directory of the cloned repository.

## **Create a Dockerfile for a simple web application (e.g., a Node.js or Python app).**

Using the command vim open the dockerfile “vim dockerfile”. And the following code is present in the file.

```plaintext
FROM node:14
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
EXPOSE 3000
CMD ["npm", "start" ]
```

`FROM node:14`: Use a base image with Node.js pre-installed

`WORKDIR /app`: Set the working directory inside the container

`COPY package*.json ./`: Copy package.json and package-lock.json to the working directory

`RUN npm install`: Install application dependencies

`COPY . .`: Copy the application code to the working directory

`EXPOSE 3000`: Expose the port that the application listens on

`CMD ["npm", "start"]`: Specify the command to run the application

![](https://miro.medium.com/v2/resize:fit:875/1*6qkYNzrpxBSqKxudFfiOIA.jpeg align="left")

## **🏗️ Build the image using the Dockerfile and run the container.**

To build the image, save the Dockerfile in a directory alongside your application code and run the following command in that directory:

```plaintext
docker build . -t sample_application
```

![](https://miro.medium.com/v2/resize:fit:875/1*adoNnzeIFtvSMn7X9utl2Q.jpeg align="left")

Once the image is built, run the container using the following command:

```plaintext
docker run -p 3000:3000 sample_application
```

![](https://miro.medium.com/v2/resize:fit:875/1*YQ5vK_dF6wVUKz9A4zgUIA.jpeg align="left")

## **👀 Verify that the application is working as expected by accessing it in a web browser.**

Edit the inbound rules for the EC2 instance in AWS. Open port 3000 for your IP for all traffic.

Connect to your application on the Internet (browser) using:

```plaintext
Public_IPv4_address:3000
```

![](https://miro.medium.com/v2/resize:fit:875/1*pUdPqDQ6ucMa5w5PVKHCuA.jpeg align="left")

The application is running!

## **🚀 Push the image to a public or private repository (e.g., Docker Hub).**

To push the image to a repository, an account on Docker Hub, or another container registry. If you have already not signed up, sign up and log in to the docker hub.

In your CLI, log in to the docker hub using the following command and enter your username and password.

![](https://miro.medium.com/v2/resize:fit:875/1*cENakXmBFYAqO8sDgwNHeA.jpeg align="left")

Once you have logged in, tag the image with the repository’s name and push it using the following commands:

```plaintext
docker tag sample_application mudit097/sample_nodejs:latest
docker push mudit097/sample_nodejs:latest
```

![](https://miro.medium.com/v2/resize:fit:875/1*V64eWAxPSK-Krvn0Th-3_A.jpeg align="left")

Verify it in the docker hub. My docker push seems a success.

![](https://miro.medium.com/v2/resize:fit:875/1*icXqCeGaOnfwd0achU5XDA.jpeg align="left")

Well, this was it for this blog. Until then, keep reading my blogs and connect with me on LinkedIn and let’s have a conversation.

#Day17 #90DaysofDevops