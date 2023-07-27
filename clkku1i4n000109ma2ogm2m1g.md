---
title: "Understanding package manager and systemctl #Day7"
datePublished: Thu Jul 27 2023 07:27:54 GMT+0000 (Coordinated Universal Time)
cuid: clkku1i4n000109ma2ogm2m1g
slug: understanding-package-manager-and-systemctl-day7
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690442812798/36d84eee-2392-4534-a8df-22fab78b4eb1.jpeg

---

# **1\. What is Package Manager in Linux?**

A package manager in Linux is a software tool that automates the process of installing, upgrading, configuring, and removing software packages on a Linux system. It provides a convenient way to search for and install software from a central repository of pre-built and pre-configured software packages.

# **2\. What is a Package?**

In Linux, a package refers to a collection of files that are bundled together to perform a specific function, such as a program or application. The package typically includes the executable file, any libraries or dependencies required by the program, documentation, and other supporting files.

Linux distributions, such as Ubuntu or Debian, use package management systems that automate the installation, removal, and updating of packages. These systems typically use a package manager (such as apt or yum) to manage the packages.

Packages are often distributed in a compressed format, such as .deb or .rpm files, which can be easily installed using the package manager. The package manager handles the installation process, ensuring that all dependencies are met and any necessary configuration files are created.

# **3\. Different Kinds of Package Managers**

Package Managers differ based on the packaging system but the same packaging system may have more than one package manager.

There are several package managers available in Linux, and the most commonly used ones are:

**1.Advanced Packaging Tool (APT):**

APT is the default package manager used in Debian-based distributions such as Ubuntu, Linux Mint, and Debian. It manages packages by downloading them from repositories over the internet.

**2\. Yellowdog Updater Modified (YUM):**

YUM is a package manager used in Red Hat-based distributions such as CentOS, Fedora, and Red Hat Enterprise Linux. It manages packages by downloading them from repositories over the internet.

**3.DNF (Dandified Packaging Tool):**

This is a package manager that installs, updates and removes packages on RPM-based Linux distributions. It is a more advanced version of the YUM manager and is intended to be the replacement for YUM in RPM-based systems.

**4\. Dpkg(Debian Package Management System):**

This is a base package management system for the Debian Linux family, it is used to install, remove, store, and provide information about `.deb` packages.

**5\. RPM (Red Hat Package Manager):**

This is the Linux Standard Base packing format and a base package management system created by RedHat.

# **4\. Installation of Docker on Ubuntu**

To update all the packages in the system use the following command:

```plaintext
 sudo apt-get update
```

Install Docker using the following command:

```plaintext
 sudo apt install docker.io -y
```

Install all the dependency packages using the following command:

```plaintext
 #Install the snapd for Docker
 sudo apt install snapd -y

 sudo snap install docker
```

![](https://miro.medium.com/v2/resize:fit:875/1*vqHPDVULX2954xGbUUDiww.png align="left")

Before testing Docker, check the version installed using the following command:

```plaintext
 docker --version
```

![](https://miro.medium.com/v2/resize:fit:875/1*3DL65faVN5nHZ86Vs2OAZw.png align="left")

To check the docker status use the following command

```plaintext
 sudo systemctl stop docker

 # CTRL + C -> To exit from prompt
```

![](https://miro.medium.com/v2/resize:fit:875/1*ExWFlUTxFLa0TL3JVlhjrA.png align="left")

To stop a docker service

```plaintext
 sudo systemctl status docker

 # CTRL + C -> To exit from prompt
```

![](https://miro.medium.com/v2/resize:fit:875/1*2RTcWG_Y3ENHd8J0jZMYxQ.png align="left")

# **5\. Installation of Jenkins on Ubuntu**

Installation of Java as per the prerequisite

```plaintext
 sudo apt-get install openjdk-11-jdk -y
```

Adding the repository to the system

```plaintext
 curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
   /usr/share/keyrings/jenkins-keyring.asc > /dev/null
 echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
   https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
   /etc/apt/sources.list.d/jenkins.list > /dev/null
```

After both commands have been entered, run apt update so that apt will use the new repository.

```plaintext
 sudo apt-get update
```

Finally, install Jenkins and check the status:

```plaintext
 sudo apt-get install jenkins
```

```plaintext
 sudo systemctl status jenkins
```

![](https://miro.medium.com/v2/resize:fit:875/1*ogIUCOOn36qKRYJoI3Hafw.png align="left")

# **6\. Installation of Docker in CentOS**

Update Docker Package Database

```plaintext
 sudo yum check-update
```

Install the Dependencies

```plaintext
 sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```

Add the Docker Repository to CentOS

```plaintext
 sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

Install Docker On CentOS Using Yum

```plaintext
 sudo yum install docker
```

Manage Docker Service

```plaintext
 #Start Docker:
 sudo systemctl start docker

 #Enable Docker:
 sudo systemctl enable docker

 #Check the status of the service with:
 sudo systemctl status docker
```

# **7\. systemctl & systemd**

Systemd is a system and service manager for Linux operating systems. It is responsible for starting and stopping system services and managing system resources. Systemd was introduced as a replacement for the traditional SysVinit system initialization process and has become the standard for many modern Linux distributions.

Systemctl is a command-line tool that is part of the systemd suite of tools. It is used to control and manage services that are managed by systemd. With systemctl, you can start, stop, restart, enable, and disable services, as well as view the status of running services and get information about services that are installed on your system.

# **8\. systemctl Commands**

```plaintext
#Starting a Service 
sudo systemctl start <service_name>

#Stopping a Service 
sudo systemctl stop  <service_name>

#Restart a Service 
sudo systemctl restart  <service_name>

#Reload a Service
sudo systemctl reload  <service_name>

#Enabling a Services 
sudo systemctl enable  <service_name>

#Disabling a Services 
sudo systemctl disable  <service_name>

#Checking the Status
systemctl status  <service_name>
```

# **9\. service Commands**

```plaintext
#Start a service
sudo service <service-name> start 

#Stop a service
sudo service <service-name> stop

#Restart a service
sudo service <service-name> restart

#Reload the configuration of a service
sudo service <service-name> reload

#Enable a service to start automatically at boot time
sudo service <service-name> enable

#Disable a service from starting automatically at boot time
sudo service <service-name> disable
```

# **10\. Difference between systemctl & service**

Systemctl is the newer command for systems that boot with systemd instead of init. Systemctl is a combination of service and chkconfig for those newer systems. If you accidentally use a service on a systemd-based system, the arguments will be swapped (ie: service httpd restart will become systemctl restart httpd). They serve the same function, but they interact with different systems.

“Service” is the legacy command, which normally works with classical init. Although on systems which use systemd it’s actually more of a wrapper over the actual systemd native means of managing services, namely systemctl.

You use service on init systems other than systemd. You use systemctl on systemd.

Thank You,

Harsh Rajotya