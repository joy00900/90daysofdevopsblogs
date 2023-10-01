---
title: "Jenkins Agents | Master & Agent(Slave) Nodes"
datePublished: Sun Oct 01 2023 16:26:41 GMT+0000 (Coordinated Universal Time)
cuid: cln7oclei000609l39uj709wx
slug: jenkins-agents-master-agentslave-nodes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696177519037/afc602dc-c53a-4e0b-b4f3-f4f4658cf81c.png
tags: aws, jenkins, 90daysofdevops, trainwithshubham

---

# **Jenkins Master (Server)**

Jenkins Master (Server) is the primary node that manages and distributes the software development processes across various worker nodes. It is responsible for coordinating the build process, managing plugins, and scheduling jobs. The Jenkins Master node serves as the central point of control for all tasks and workflows, and it provides a web interface for managing and monitoring the build process.

# **Jenkins Agent**

Jenkins Agent, also known as Jenkins Node is a worker node that executes the tasks and builds assigned by the Jenkins Master. It works as a distributed system where the Jenkins Master assigns tasks to Jenkins Agents, which then execute the tasks on the machines they are running on.

Jenkins Agents are often used to distribute builds and tests across multiple machines, allowing for parallel execution of tasks and faster build times. Jenkins Agents can be configured to run on a variety of machines, including physical machines, virtual machines, and containers to include any necessary tools and dependencies required for the tasks assigned by the Jenkins Master.

![](https://miro.medium.com/v2/resize:fit:875/0*9aEoFaMvd9YXmPqI align="left")

# **Project: Deploy a web app through Jenkins master to Jenkins worker node**

# **Set Up Jenkins-Master & Jenkins-Agent**

1. Create a 2 EC2 instance in AWS and connect both servers.
    

* jenkins-master
    
* jenkins-agent
    

![](https://miro.medium.com/v2/resize:fit:875/0*q_p26x1b8T6C6Uv9 align="left")

2\. Now clear up the unwanted images from the jenkins-server

```plaintext
 docker rmi <image-name> --force
```

3\. Generate SSH key on the jenkins-master using “ssh-keygen” command.

```plaintext
ssh-keygen
```

![](https://miro.medium.com/v2/resize:fit:875/0*ut1rzvOMFTRwi8c0 align="left")

4\. Now go to that folder and copy the id\_[rsa.pub](http://rsa.pub/) which is public key.

```plaintext
 cd .ssh
 ls
 cat id_rsa.pub
```

5\. Then on the jenkins-agent server, paste the public key from the jenkins-master in the authorized\_keys file.

```plaintext
 cd .ssh
 ls
 vi authorized_keys
```

![](https://miro.medium.com/v2/resize:fit:875/0*b4rp8SCPFGZ8AaLw align="left")

6\. Now from the jenkins-master we can connect the jenkins-agent server

```plaintext
 # inside ssh dir
 ssh ubuntu@<Public-IPv4-addr>

 # if we exit we will be back to jenkins-server.
```

![](https://miro.medium.com/v2/resize:fit:875/0*IZ6aNTCfP8zjh1i5 align="left")

7\. Make sure to install Java in the agent server.

```plaintext
 sudo apt-get update
 sudo apt-get install openjdk-11-jre
```

![](https://miro.medium.com/v2/resize:fit:875/0*UPH30jn0omEmS45S align="left")

8\. Now go to the Jenkins Dashboard and click on Manage Jenkins.

9\. Now click on Manage Nodes & Clouds, and click on “+ New Node”

![](https://miro.medium.com/v2/resize:fit:875/0*KsqP9KcOPtEHxDpL align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*IPbcEfhpktWLl4Zf align="left")

10\. Add details of the second agent node(make sure to fill in the Labels)

```plaintext
Node name: agent-node
✅ Permanent node

Name: agent
Desc: This is our agent which will run Node JS application

Number of executaion: 1 (cpu)
Remote root directory: /home/ubuntu/jenkins-agent
Labels: dev-server
Usage: Only build jobs with label expression matching this node
Launch method: launch agents via SSH
Host: <Public-IPv4-addr-agent>

Credentials:
Kind: SSH username with private key
ID: jenkins-ssh-key
Description: jenkins-ssh-key
Username: ubuntu
Private Key: <Private-key-master-node>
Host Key Verification Strategies: Non verifying verification strategy (SSH check with keys)
```

![](https://miro.medium.com/v2/resize:fit:726/0*oX88FlMNYisMTFIs align="left")

![](https://miro.medium.com/v2/resize:fit:621/0*GOirv-KmhkGTbLd2 align="left")

![](https://miro.medium.com/v2/resize:fit:746/0*0JFMq0xv5inuMBeF align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*8nHvivUUWBol8mpt align="left")

11\. Now click “OK” and Node will be connected and online.

![](https://miro.medium.com/v2/resize:fit:875/0*hsT13_YQY8O4w25P align="left")

12\. Installed docker-compose for future requirements.

```plaintext
sudo apt-get install docker.io docker-compose
sudo usermod -aG docker $USER
sudo restart
```

![](https://miro.medium.com/v2/resize:fit:875/0*omOKhPHKJCb36LUx align="left")

# **Set Up Node Application**

1. Now create a new item with the pipeline, and named it(node-pipeline)
    

![](https://miro.medium.com/v2/resize:fit:801/0*-d2g-jkfpHjZ7ROM align="left")

2\. Now give it a description “This is a declarative pipeline for Node JS App” Put the GitHub repo

![](https://miro.medium.com/v2/resize:fit:875/0*qlzCTIlVr8r6l_k_.jpeg align="left")

3\. Build Triggers ✅ GitHub hook triggers for GITScm polling.

![](https://miro.medium.com/v2/resize:fit:588/0*SUpxqOBYeweGBM1W align="left")

4\. Now we have to pass the pipeline script in the pipeline to test the script.

```plaintext
 pipeline {
     agent { label "dev-server" }
     stages{
         stage("Clone Code"){
             steps{
                 git url: "https://github.com/mudit097/node-todo-cicd.git", branch: "master"
             }
         }
         stage("Build and Test"){
             steps{
                 sh "docker build . -t node-app-test-new"
             }
         }
         stage("Push to Docker Hub"){
             steps{
                 echo "Docker Hub will receive the image"
             }
         }
         stage("Deploy"){
             steps{
                 sh "docker-compose down && docker-compose up -d"
             }
         }
     }
 }
```

5\. Now go to Manage Jenkins &gt; Manage Plugin and install the “Environment Injector” and Download and install after restart Jenkins. It will store all the environment variables where we can pass the credentials.

![](https://miro.medium.com/v2/resize:fit:875/0*OlXY7PwfD_DAiZPx align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*Ta12U_P5GvmjnDC9 align="left")

6\. Now go to Manage Jenkins &gt; Credentials &gt; System &gt; Global Credentials &gt; globals &gt; + Add Credentials

![](https://miro.medium.com/v2/resize:fit:875/0*AwsRYbLtZ2lExef9.png align="left")

```plaintext
 Kind: username with password
 username: <DockerHub_Username>
 password: <DockerHub_Password>
 ID: dockerHub
 Desc: This is my Docker Hub Credentials
```

![](https://miro.medium.com/v2/resize:fit:875/0*TV_IpBFVU1Knu2rX.png align="left")

7\. Now configure the pipeline for pushing the image into the docker hub.

```plaintext
 pipeline {
     agent { label "dev-server" }
     stages{
         stage("Clone Code"){
             steps{
                 git url: "https://github.com/LondheShubham153/node-todo-cicd.git", branch: "master"
             }
         }
         stage("Build and Test"){
             steps{
                 sh "docker build . -t node-app-test-new"
             }
         }
         stage("Push to Docker Hub"){
             steps{
                 withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                 sh "docker tag node-app-test-new ${env.dockerHubUser}/node-app-test-new:latest"
                 sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                 sh "docker push ${env.dockerHubUser}/node-app-test-new:latest"
                 }
             }
         }
         stage("Deploy"){
             steps{
                 sh "docker-compose down && docker-compose up -d"
             }
         }
     }
 }
```

![](https://miro.medium.com/v2/resize:fit:875/0*YKmHsK5qDuWRlnAF.jpeg align="left")

8\. Click on Save, and your project will be tied to Jenkins-agent.

![](https://miro.medium.com/v2/resize:fit:875/0*pjx-hgXvM4Sdvxvs.jpeg align="left")

9\. Now, build your project.

![](https://miro.medium.com/v2/resize:fit:875/0*miyA56dcYAQ42DA0 align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*eDNlVqHW3Ffi779D align="left")

10\. Open 8000 port on jenkins-agent, now the app can be accessed from the browser.

![](https://miro.medium.com/v2/resize:fit:875/0*SLTX62z-5s0c8FAq align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*IAiNcyY6Y450m5BM align="left")

11\. Our application image is also pushed to DockerHub

![](https://miro.medium.com/v2/resize:fit:875/0*GXKUylPGz55ml2_N.jpeg align="left")

# **Set Up the Node app using Pipeline Script from SCM**

1. We can build the application using the Pipeline script from SCM by passing the GitHub URL where “Jenkinsfile” is present in the repository.
    
2. Now in the pipeline script, use “Pipeline script from SCM”
    
3. SCM: Git
    
4. Repository: &lt;URL-of-Git-Repo&gt;
    
5. Script Path: Jenkinsfile
    

![](https://miro.medium.com/v2/resize:fit:875/0*WdHJoubUNXvNyVgq.jpeg align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*ivA0g6iX4DBrfj-D align="left")

Now the application is up & running and there is a new step added by Jenkins, Declarative Checkout SCM to verify that Jenfinsfile is available in the GitHub repo. Once the file is verified, then further steps proceed.

![](https://miro.medium.com/v2/resize:fit:875/0*iCLUdRy9k2JpDUEc align="left")

Congratulation!! The whole CI CD pipeline for this Node JS application is done including pushed images into the GitHub.