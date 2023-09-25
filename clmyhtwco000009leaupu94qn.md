---
title: "Jenkins Pipeline |Jenkinsfile | Declarative and Scripted Pipelines"
datePublished: Mon Sep 25 2023 06:14:15 GMT+0000 (Coordinated Universal Time)
cuid: clmyhtwco000009leaupu94qn
slug: jenkins-pipeline-jenkinsfile-declarative-and-scripted-pipelines
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695622367732/bd30501a-b937-4c63-aafe-055cd6956b86.png
tags: aws, devops, jenkins, 90daysofdevops, trainwithshubham

---

In this blog, I will discuss the Jenkins Pipeline and the types of pipelines: Declarative and Scripted Pipelines. Also, as a starter, I will create an example Pipeline Job.

Let’s start!

# **1\. Jenkins Pipeline**

According to the official documentation of Jenkins, “ [Jenkins Pipeline](https://www.jenkins.io/doc/book/pipeline/) is a suite of plugins that supports implementing and integrating *continuous delivery pipelines* into Jenkins. “

Pipelines allow for defining a series of steps that will be executed whenever the change of code like building, testing, and deploying takes place.

Pipelines enable modeling simple-to-complex delivery Pipelines as a Code. The definition of a Jenkins Pipeline is written into a text file called Jenkinsfile.

Jenkins Pipelines are written in a domain-specific language (DSL) called Declarative Pipeline. This DSL makes it easy to define complex pipelines without writing a lot of code.

# **2\. Why Pipelines?**

* They are easy to use.
    
* They are scalable.
    
* They are flexible.
    
* They are secure.
    
* Automate the software development process.
    
* Improve the quality of your code.
    
* Increase the speed of your deployments.
    
* Improve collaboration.
    

# **3\. Pipeline Concepts**

# **3.1 Pipeline**

A Pipeline is a user-defined model of a CD pipeline. This is a vital part of Declarative Pipeline Syntax.

# **3.2 Node**

A node is a machine part of the Jenkins environment and capable of executing a Pipeline. This is a key part of Scripted Pipeline Syntax.

# **3.3 Stage**

A stage in a pipeline is a logical grouping of steps that are executed together. Stages are typically used to group related tasks, such as building, testing, and deploying code.

# **3.4 Step**

A step in a pipeline is a single action that is executed as part of a stage. Steps are typically used to perform tasks such as building, testing, and deploying code.

Now let us know the types of Pipelines. There are two types: Declarative Pipelines and Scripted Pipelines.

# **4\. Declarative Pipeline**

Declarative Pipeline is based on a set of declarative statements that define the structure and behavior of your pipeline. These statements are grouped into sections, which are executed in order.  
Declarative Pipeline is a new syntax for writing Jenkins Pipelines. It is designed to be more concise and easier to read than the Scripted Pipeline syntax.

# **4.1 Syntax**

```plaintext
pipeline {
    agent any #1
    stages {
        stage('Build') { #2
            steps {
                //#3
            }
        }
        stage('Test') { #4
            steps {
                //#5
            }
        }
        stage('Deploy') { #6
            steps {
                //#7
            }
        }
    }
}
```

#1 Execute this Pipeline or any of its stages, on any available agent.

#2 Defines the “Build” stage.

#3 Perform some steps related to the “Build” stage.

#4 Defines the “Test” stage.

#5 Perform some steps related to the “Test” stage.

#6 Defines the “Deploy” stage.

#7 Perform some steps related to the “Deploy” stage.

# **5\. Scripted Pipeline**

Scripted Pipeline is based on a Groovy script that defines the structure and behavior of the pipeline. The script is executed in order, and it can contain a variety of steps, including building, testing, and deploying code.  
Scripted Pipeline is a syntax for writing Jenkins Pipelines. It is the original syntax for Pipelines, and it is still supported in Jenkins.

# **5.1 Syntax**

```plaintext
node { #1
    stage('Build') { #2
        //#3
    }
    stage('Test') { #4
        // #5
    }
    stage('Deploy') { #6
        // #7
    }
}
```

#1 Execute this Pipeline or any of its stages, on any available agent.

#2 Defines the “Build” stage. ‘stage’ blocks are optional in Scripted Pipeline syntax.

#3 Perform some steps related to the “Build” stage.

#4 Defines the “Test” stage.

#5 Perform some steps related to the “Test” stage.

#6 Defines the “Deploy” stage.

#7 Perform some steps related to the “Deploy” stage.

# **6\. Difference between Declarative and Scripted Pipelines**

![](https://miro.medium.com/v2/resize:fit:875/0*mUP81spFQjZMvXZt.jpeg align="left")

# **7\. Jenkinsfile**

A Jenkinsfile is a text file that contains the definition of a Jenkins Pipeline. It is typically stored in the root directory of the project that it is used to automate.

The following is an example of a Jenkinsfile:

```plaintext
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage('Deploy') {
      steps {
        sh 'scp -r target/*.jar localhost:/opt/app'
      }
    }
  }
}
```

This is the foundation of “Pipeline-as-code”; treating the CD pipeline as a part of the application to be versioned and reviewed like any other code.

Now let us complete tasks as we now know the basics of the Pipelines.

# **8\. Tasks**

# **8.1 Task 1: Create a Jenkins Pipeline Project using declarative pipeline syntax to print “Hello World”**

1) Create a Jenkins Pipeline named “HelloWorld Example1”

![](https://miro.medium.com/v2/resize:fit:875/0*rCbReYUYQdXlmCqg.png align="left")

2) Go to the Dashboard &gt; Configure &gt; Pipeline &gt; Select Definition as “Pipeline Script” &gt; And enter the following command.

```plaintext
pipeline {
    agent any
```

```plaintext
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
    }
}
```

![](https://miro.medium.com/v2/resize:fit:875/0*ELZJT0cna_vPyCnE.png align="left")

3) Click on Save and Build the Pipeline.

4) In the Pipeline Dashboard, you can see the Stage View as well. Our job is successful.

![](https://miro.medium.com/v2/resize:fit:875/0*nxV5TyWDLUHZvcYw.png align="left")

5) This is the Console Output. It says SUCCESS. Also, you can observer that the “HELLO WORLD” is printed.

![](https://miro.medium.com/v2/resize:fit:875/0*ILkOwrwBUvQa1nVO.png align="left")

# **8.2 Task 2: Perform the same task which you did in Task 1, but using a Jenkinsfile.**

1. Create a file named Jenkinsfile in your repository. Write down the below contents into the file and commit the changes. Copy the repository link for further usage.
    

![](https://miro.medium.com/v2/resize:fit:875/0*WbiAxRSwUGyrgihY.png align="left")

2) Now in Jenkins, create a new Pipeline name “HelloWorldExample2”

![](https://miro.medium.com/v2/resize:fit:875/0*GV8pGV3XT9WraUhc.png align="left")

3) Go to Dashboard &gt; Configuration &gt; Pipeline &gt; Select Definition “Pipeline script from SCM” &gt; Select “Git” for SCM &gt; Paste the repository URL which you previously copied and paste in the Repositories Section &gt; Select the branch name where the Jenkinsfile is located &gt; Click on Save

![](https://miro.medium.com/v2/resize:fit:875/0*B0Ez-7XRi_WWb0hD.png align="left")

4) Now build the pipeline. The stage view appears. Our build is successful.

![](https://miro.medium.com/v2/resize:fit:875/0*CGgp60Mikg54qKG1.png align="left")

When we see the Console Output, we can see that Jenkinsfile is being obtained from GitHub. And then the build progressed.

![](https://miro.medium.com/v2/resize:fit:875/0*Jl-TexTvbqzsoEpj.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*MJ7sOjOJR8NyLcDV.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*qTaFCHOpgMlEuonl.png align="left")

And we have successfully built the Pipeline Project for the “Hello-World” example.

In this blog, I have discussed Jenkins Pipelines, Jenkinsfile, types of Jenkins pipelines, and an example of how to run a Jenkins Pipeline job. If you have any questions or would like to share your experiences, feel free to leave a comment below. Don’t forget to read my blogs and connect with me on LinkedIn and let’s have a conversation.

To help me improve my blog and correct my mistakes, I am available on LinkedIn as [Mudit Mathur](https://www.linkedin.com/in/mudit--mathur/). Do reach me and I am open to suggestions and corrections.

#Day26 #90daysofdevops