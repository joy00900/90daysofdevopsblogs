---
title: "Day 3 Task: Basic Linux Commands"
datePublished: Mon Jul 17 2023 11:26:15 GMT+0000 (Coordinated Universal Time)
cuid: clk6s5hyp000x09l0evuu87pg
slug: day-3-task-basic-linux-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690442059092/82a4b0d2-1563-4528-9145-43f397142dc8.webp
tags: ubuntu, aws, command-line, 90daysofdevops, trainwithshubham

---

# **1.** **Introduction** **🌟**

Welcome back to Day 3 of the thrilling **#90DaysOfDevOps** challenge! Today, we’ll explore the wonders of Linux commands, like magical keys unlocking every DevOps engineer’s potential! With these tools, navigating your Linux system becomes as easy as exploring a map. 🚀🗺️💻 Get ready for a tech-packed journey! Together, we’ll unravel the mysteries of essential Linux commands, discovering hidden treasures that elevate your skills. Excitement fills the air as we dive into this epic DevOps adventure! Let’s go! 🌟💻

# **2\. Viewing the content of a file 👀**

To view the contents of a file in Linux, you can use the **“cat”** command. For example, let’s say you have a file named **“example.txt”** To view what’s written in this file, open your terminal and write **cat example.txt**:

![](https://miro.medium.com/v2/resize:fit:875/1*0rEFgtlGn1UzwVFfrEz_EQ.png align="left")

Also we can use **“less”** or **“more”** instead of **“cat”** to view files as they offer better text navigation. “Cat” shows all content at once, while **“less”** and **“more”** allow scrolling and analyzing large files more easily.

# **3\. Changing the access permissions of files 🔒**

Changing the access permissions of files in Linux is done using the **“chmod”** command, which stands for **“change mode.” 🚪**

In Linux, every file has three types of permissions: read (r), write (w), and execute (x). These permissions can be set for three different categories of users: the file’s owner (u), the group (g) the file belongs to, and others (o) who are not the owner or part of the group.

To change the permissions, we use a combination of letters and symbols. For example:

* **“chmod u+rwx example.txt”** grants read, write, and execute permissions to the file owner.
    
* **“chmod go-r example.txt”** revokes read permission from the group and others.
    

Here’s an example:

![](https://miro.medium.com/v2/resize:fit:875/1*rR5DOg5Psvf32F9PYLzvyw.png align="left")

Let’s say we have a script file named [“](https://text.sh/)[text.sh](http://text.sh)[”](https://text.sh/) that we want to make executable only for the owner and read-only for others. We would use the following command:

```plaintext
chmod u+x,go-w text.sh
```

In this command:

* “u+x” adds execute permission to the owner.
    
* “go-w” removes written permission from the group and others.
    

After running this command, the owner of [“](https://text.sh/)[text.sh](http://text.sh)[”](https://text.sh/) will be able to execute it, while the group and others will only have read access.

# **4\. Checking the command history 📜**

To check the commands you have run in the current terminal session in Linux, you can use the **“history”** command. 📜

![](https://miro.medium.com/v2/resize:fit:875/1*rR5DOg5Psvf32F9PYLzvyw.png align="left")

# **5\. Removing a directory/folder 🗑️**

Removing a directory or folder in Linux is done using the **“rmdir”** or **“rm”** command. 🗑️

The **“rmdir”** command is used specifically to remove empty directories. For example:

![](https://miro.medium.com/v2/resize:fit:875/1*uUWllwZtbZSzSoulxzHpdg.png align="left")

The **“rmdir”** removes an empty **“example1”** directory, while **“rm -r”** deletes directories with content and files. For example

![](https://miro.medium.com/v2/resize:fit:875/1*PIiYoiRQLHoB9KKps5GLqw.png align="left")

Be cautious with **“rm -r”** to delete **“demo”** and its contents without confirmation, leading to permanent data removal. Double-check directories to avoid accidental data loss. Use commands responsibly! 🛡️🗑️🔍🧹

# **6\. Creating and viewing the content of bikes.txt 📄**

To create a **“bikes.txt”** file in Linux, you can use the “touch” command. 📄

For example:

![](https://miro.medium.com/v2/resize:fit:875/1*fpBfu5j-ibRFHpYCFH2pHg.png align="left")

This command will create an empty file named **“bikes.txt”** in the current directory.

Next, to view the content of the **“bikes.txt”** file, you can use the **“cat”** command. 🐱

For example:

![](https://miro.medium.com/v2/resize:fit:875/1*ogJoRdqUJHwjlt1DoPm80A.png align="left")

# **7\. Adding content to bikes.txt (One bike per line) 🏍️**

To add content to the **“bikes.txt”** file, you can use a text editor or the **“echo”** command to append each fruit on a new line. Here’s an example using the **“echo”** command:

![](https://miro.medium.com/v2/resize:fit:875/1*1r9ltPNKwlxAohpJyuz1Tw.png align="left")

This command adds each fruit on a separate line in the **“bikes.txt”** file. You can then use the **“cat”** command to view the contents of the file:

![](https://miro.medium.com/v2/resize:fit:875/1*pOhQIsjaCSizU9QC-DKJ_A.png align="left")

# **8\. Showing the top three bikes from bikes.txt 🔝**

To display only the top three bikes from the **“bikes.txt”** file, you can use the **“head”** command with the **“-n”** option, specifying the number of lines you want to see. In this case, we want to see the first three lines, which represent the top three bikes in the file.

![](https://miro.medium.com/v2/resize:fit:875/1*HecX3nFElQhtxBGA-qXMnw.png align="left")

# **9\. Showing the bottom three bikes from bikes.txt🔻**

To display only the bottom three bikes from the **“bikes.txt”** file, you can use the **“tail”** command with the **“-n”** option, specifying the number of lines you want to see from the end of the file. In this case, we want to see the last three lines, which represent the bottom three bikes in the file.

![](https://miro.medium.com/v2/resize:fit:875/1*FqWwe_Xm1CqMYbvQM1PJ_Q.png align="left")

# **10\. Creating and viewing the content of Colors.txt🌈**

To create a new file called **“Colors.txt”** in Linux, you can use the **“touch”** command followed by the desired filename. This command will create an empty file named **“Colors.txt”** in the current directory. Now, to view the content of the file, you can use the **“cat”** command:

![](https://miro.medium.com/v2/resize:fit:875/1*xdgeN8PQacyUG1QB7VUF-A.png align="left")

# **11\. Adding content to Colors.txt (One color per line)**

To add the specified content to the **“Colors.txt”** file with each color on a separate line, you can use the following command:

![](https://miro.medium.com/v2/resize:fit:875/1*VJet6R2LIeMY7M1ZP6ujMw.png align="left")

🌈🎨 This command will add the colors Red, Green, Pink , Black, White, Orange, Purple, to the **“Colors.txt”** file, with each color on its line. If you view the content of the file using the `cat` command:

![](https://miro.medium.com/v2/resize:fit:875/1*VXJe2qZr4jfsEzf7UNG72Q.png align="left")

# **12\. Finding the difference between bikes.txt and Colors.txt 🏍️🌈🔄**

To find the difference between the contents of two files, such as **“bikes.txt”** and **“Colors.txt”** you can use the **“diff”** command. Here’s an example:

![](https://miro.medium.com/v2/resize:fit:875/1*nx-2GpRzFDUSw3zgsHiZyg.png align="left")

This command will compare the contents of **“bikes.txt”** and **“Colors.txt”** files. If there are any differences between the two files, the `diff` command will show them in the output.

With the `diff` command, you can easily spot the variations between two files and manage your data more efficiently.

# **13\. Conclusion 🎉**

In conclusion, we explored essential **Linux** commands that empower **DevOps Engineers**:

1\. View file content using **“cat,”** **“less,”** or **“more.”**  
2\. Change file permissions with **“chmod.”**  
3\. Check command history with **“history.”**  
4\. Remove directories using **“rmdir”** or **“rm.”**  
5\. Create and view file content using **“touch”** and **“cat.”**  
6\. Add content to files with **“echo.”**  
7\. Display top or bottom lines of a file using **“head”** and **“tail.”**  
8\. Compare file contents with **“diff.”**

Mastering these commands enhances file navigation, access control, and data management. Congratulations on completing Day 3 of the #90DaysOfDevOps challenge! 🌟🚀💻