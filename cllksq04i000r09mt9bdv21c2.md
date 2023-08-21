---
title: "Day-23 : Jenkins Freestyle Project for DevOps Engineers"
datePublished: Mon Aug 21 2023 11:30:41 GMT+0000 (Coordinated Universal Time)
cuid: cllksq04i000r09mt9bdv21c2
slug: day-23-jenkins-freestyle-project-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692617341110/e71fdc3e-7224-4190-b7c5-b5fbf3800665.jpeg
tags: aws, devops, jenkins, 90daysofdevops, trainwithshubham

---

In the previous blog, I explained what CI/CD is. Here’s the link to my blog: [CI/CD](https://muditm12.hashnode.dev/day-22-getting-started-with-jenkins#heading-1-cicd). If you haven’t already installed Jenkins on your server, here are the steps to [Install Jenkins on your system](https://muditm12.hashnode.dev/day-22-getting-started-with-jenkins#heading-32-installing-jenkins).

# **1\. 🏗️ What is a Build Job?**

A build job in Jenkins is a repeatable process that automates the building, testing, and deploying of software. It is a collection of steps that are executed in a specific order to create a finished product. Jenkins build jobs can be configured to run on a schedule, or they can be manually triggered.

Many different types of build jobs can be created in Jenkins, including:

* Freestyle projects: These are the most basic type of build job, and they allow you to define the steps that are executed in the build process.
    
* Pipelines: Pipelines are a more advanced type of build job that allows you to define the steps in the build process using a declarative syntax.
    
* Multi-configuration projects: These allow you to create multiple builds of the same project, each with different configurations.
    
* Folders: Folders can be used to organize your build jobs.
    
* Multibranch pipelines: These allow you to create pipelines that are based on branches in a Git repository.
    
* Organization folders: These allow you to organize your build jobs by organization.
    

In this blog, I am going to do a Freestyle Project. Let’s learn what a freestyle project is.

# **2\. 🎨 What are Freestyle Projects?**

A freestyle project in Jenkins is a type of build job that allows you to define the steps that are executed in the build process. Freestyle projects are the most basic type of build job in Jenkins, and they are a good starting point for building more complex pipelines.

Here are a few tasks that you could complete when working with a freestyle project in Jenkins:

* Build a software project. Freestyle projects can be used to build web applications, mobile applications, desktop applications, and more.
    
* Run automated tests. Freestyle projects can be used to run automated tests against your software project.
    
* Deploy your software project. Freestyle projects can be used to deploy software projects to a production environment.
    
* Collect metrics about your build process. Freestyle projects can be used to collect metrics about your build process. This information can be used to improve the efficiency and effectiveness of your build process.
    
* Integrate with other tools. Freestyle projects can be integrated with other tools, such as version control systems, continuous integration servers, and continuous delivery servers.
    

Let’s complete today’s tasks which include deploying a Django Todo List application.

# **3\. 📝 Tasks**

# **3.1.✅ Task 1**

1. Create a new Jenkins freestyle project named ToDoApp.
    
2. Configure the project. In the Source Code Management section &gt; Select Git &gt; Enter the GitHub Repository Link and the branch name.
    
3. Repo link I have used: [Django Todo App](https://github.com/joy00900/django-todo-cicd).
    

![](https://miro.medium.com/v2/resize:fit:875/0*sS3QRcbeKqE5H8Te align="left")

In the Build Steps section &gt; Select Add Build Steps &gt; Select Execute Shell &gt; And type the commands required for your activity.

```plaintext
docker build -t todoapp .   
docker run -d --name django-todo-app -p 8000:8000 todoapp:latest
```

![](https://miro.medium.com/v2/resize:fit:875/0*-kdELTW9emdUyU65 align="left")

1. Click on Save and Build your project.
    
2. Once the project is built successfully, a green tick can be observed beside the build number.
    

![](https://miro.medium.com/v2/resize:fit:875/0*XxA4PJGZcIqzY6IY align="left")

1. We can see the console output and steps of the activity.
    

![](https://miro.medium.com/v2/resize:fit:875/0*K_lOu2x2hHZTh-iC align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*ayU_I8kjWxOGJwBr align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*toK-tmqLZ-TYU9Zs align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*cXWiCSm5gFdmAixP align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*jWVdH6fmIJqyABoB align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*NSYpgLizAZw05hCq align="left")

In the final line of the Console Output, we can observe that Finished: Success is printed. That means our build is successful.

I have verified that the ToDo list application is accessible on host\_IP:8000.

![](https://miro.medium.com/v2/resize:fit:875/0*PqLuxPT2-pFNWq7g.jpeg align="left")

# **3.2. ✅ Task 2**

In task 2, we need to create a Jenkins project to run the “docker-compose up -d” command to start the multiple containers defined in the compose file. Set up a cleanup step in the Jenkins project to run the “docker-compose down” command to stop and remove the containers defined in the compose file.

So in the Add build steps of the configuration section, write in the following command and go ahead and build the project.

```plaintext
docker-compose down
docker-compose up -d
```

![](https://miro.medium.com/v2/resize:fit:875/0*yaxGNbPl-_3dvVRj align="left")

And in the Console Output, we can check the status.

![](https://miro.medium.com/v2/resize:fit:875/0*1mko8praTezso569 align="left")

Yeah, the build is successful!

In this blog, I have done a freestyle project on Jenkins to deploy a Django application on Docker. If you have any questions or would like to share your experiences, feel free to leave a comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.