---
title: "Day 5 Advanced Linux Shell Scripting for DevOps Engineers with User management"
datePublished: Sat Jul 22 2023 00:15:02 GMT+0000 (Coordinated Universal Time)
cuid: clkd9dk5a000009mf4ra43lt7
slug: day-5-advanced-linux-shell-scripting-for-devops-engineers-with-user-management

---

![](https://miro.medium.com/v2/resize:fit:875/0*S_5N5zxqche6i3it align="center")

1. # **Write a bash script create** [**directories.sh**](http://directories.sh) **that when the script is executed with three given arguments (one is the directory name and second is the start number of directories and third is the end number of directories ) it creates a specified number of directories with a dynamic directory name.**
    

```plaintext
#!/bin/bash
#############################################################
#Purpose: This script will create 90 directories at once
#############################################################

#Intializing variables
Name_of_dir=$1
start_no=$2
end_no=$3

#Command to create directories
eval mkdir $Name_of_dir{$start_no..$end_no}
```

Here, the “eval” command takes arguments as input to the command and stores it as one single command.

Execution,

```plaintext
./directories.sh day 1 90
```

Here,

day, — First argument

1, — Second argument

2, — Third Argument

![](https://miro.medium.com/v2/resize:fit:875/0*lSDE3MJ7Ypgar7ZO align="left")

1. # **create a Script to backup all your work done till now**
    

```plaintext
##########################################################################
#Purpose: This script will take backup
##########################################################################

#Creating Variables 
src=/home/ubuntu/day5
dest=/home/ubuntu/backups
time=$(date +"%Y-%m-%d-%H-%M-%S")
backupfile=$dest/$time.tgz

#Taking Backup
echo "Taking backup on $time"
tar zcvf $backupfile --absolute-names $src

if [ ${?} -eq 0 ]
then
        echo "Backup Complete"
else
        exit 1
fi
```

Above, the script will take backups.

![](https://miro.medium.com/v2/resize:fit:608/0*gY9EtohF6kv0uggg align="left")

1. # [**Read**](http://3.Read) **About Cron and Crontab, to automate the backup Script**
    

```plaintext
crontab -e
```

Enter the below code in the last line of crontab,

```plaintext
* * * * * sh /home/ubuntu/day5/backup.sh
```

![](https://miro.medium.com/v2/resize:fit:833/0*cUXrIHIMc9NmeVun align="left")

first \*, — represents minutes

second \*, — represents hours

third \*, — represents day of month

fourth \*, — represents month

fith \*, — day of week

1. # [**Read**](http://4.Read) **about User Management**
    

User management is a very important part of a DevOps engineer’s journey.

User management includes some basic tasks, like

* Creating Users
    
* Deleting Users
    
* Password reset
    
* Adding user in a group
    

1. # **Create 2 users and just display their Usernames**
    

```plaintext
##########################################################################
#Purpose: This script will take two argument as username and create user
##########################################################################

#Creating variables
user1=$1
user2=$2

#Creating Users
echo "Adding Users $user1 and $user2"
useradd -p test -m $user1
useradd -p test -m $user2

if [ ${?} -eq 0 ]
then
        echo "Users added successfully"
else
        exit 1
fi
```

![](https://miro.medium.com/v2/resize:fit:688/0*ws6aZ_7ZedkD25Ak align="left")