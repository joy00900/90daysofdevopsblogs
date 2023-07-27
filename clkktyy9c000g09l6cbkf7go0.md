---
title: "Day 6 File Permissions and Access Control Lists"
datePublished: Thu Jul 27 2023 07:25:55 GMT+0000 (Coordinated Universal Time)
cuid: clkktyy9c000g09l6cbkf7go0
slug: day-6-file-permissions-and-access-control-lists
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690442447286/b035446a-1271-4887-a329-e498e23b5690.webp

---

# **1\. Understanding File Permissions and Changing Access Rights in Linux**

As Linux users, we often come across various files and directories each with specific permissions that determine who can access, modify, or execute them. we will explore file permissions in Linux and learn how to change them using the `chown` and `chmod` commands. We'll also create a simple file and observe the changes after modifying its permissions.

File Permissions in Linux: An Overview In Linux, each file and directory has three sets of permissions assigned to three defined categories of users:

1. **Owner: The user who created the file or directory.**
    
2. **Group: The group that owns the file or directory.**
    
3. **Others: All users with access to the system but do not fall under the owner or group category.**
    

The three permissions are:

* **Read (r):** Allows users to view the contents of a file or the list of files in a directory.
    
* **Write (w):** Allows users to modify the content of a file or create, delete, or rename files within a directory.
    
* **Execute (x):** Allows users to run an executable file or access a directory (required to navigate into the directory).
    

Changing Ownership with `chown` The `chown` command is used to change the ownership of files and directories.

```plaintext
chown new_owner:group file_or_directory
```

Changing Group Permissions with `chgrp` The `chgrp` command is used to change the group ownership of files and directories.

```plaintext
chgrp new_group file_or_directory 
```

Changing Group Permissions with `chgrp` The `chgrp` command is used to change the group ownership of files and directories.

```plaintext
chgrp new_group file_or_directory
```

Changing Permissions with `chmod` The `chmod` command allows us to modify the access permissions of files and directories.

```plaintext
chmod permissions file_or_directory
```

Here, permissions can be represented either in numeric mode (e.g., 644, 755) or symbolic mode (e.g., u+r, g-w, o+x).

Task: Creating a Simple File and Modifying Permissions Let’s go through a practical example to understand how file permissions work. Follow these steps:

Open your terminal.

Create a new text file named `my_file.txt` using the following command:

```plaintext
touch my_file.txt
```

3\. Use the `ls -ltr` command to view the details of the newly created file

```plaintext
ls -ltr my_file.txt
```

The output will display the file details, including its permissions, owner, group, size, and modified time.

4\. Now, let’s change the user permissions of the file. For this example, we’ll add execute permission for the owner

```plaintext
chmod u+x my_file.txt
```

5\. Check the file details again using `ls -ltr my_file.txt`. You will notice that the permissions for the owner have been modified, and the "x" (execute) permission is now added

6\. To change the group permissions or others’ permissions, you can use similar `chmod` commands with `g` or `o` instead of `u`

# **2\. File Permissions in Linux**

* **/sbin:** Holds system binaries used by system administrators for maintenance.
    
* **/etc:** Stores configuration files (etc: extended text configuration).
    
* **/dev:** Contains device files representing hardware devices.
    
* **/proc:** Provides process information, updated on each system reboot.
    
* **/var:** Holds variable files, including logs.
    
* **/tmp:** Contains temporary files cleared on system reboot.
    
* **/usr:** Contains user programs, binaries, libraries, and documentation files.
    
* **/home:** Stores user home directories.
    
* **/boot:** Contains boot loader files (kernel, grub, etc.).
    
* **/lib:** Contains system libraries supporting binaries in /bin and /sbin.
    
* **/opt:** Holds optional add-on application-related files.
    
* **/mnt:** A mount directory used for temporarily mounting foreign devices.
    
* **/media:** For mounting removable devices.
    
* **/srv**: Contains server-specific service data.
    

Basic Symbols in Linux

* “.”: Represents the current directory.
    
* “..”: Represents one level above the current directory.
    
* “/”: Denotes the root of the filesystem (all directories/files are nested under it).
    
* “~”: Represents the home directory of the currently logged-in user.
    
* “-”: Navigates back to the previous working directory.
    
* “\*”: Stands for “everything.”
    
* “&”: Runs a command in the background.
    
* “&&”: Allows running two commands together.
    
* “”: Allows continuing commands in a new line.
    
* “#”: Denotes comments, not processed by the shell.
    
* “|”: Represents “Piping,” redirecting output to another command.
    
* “&gt;”: Redirects output into a file (overwriting it).
    
* “&lt;”: Reads file contents into a command’s input.
    
* “&gt;&gt;”: Appends text or command output to the end of a file.
    

Understanding File Permissions:

File permissions are divided into three categories, each assigned to specific user types:

1. Owner (user): The user who created the file.
    
2. Group: The group that owns the file.
    
3. Others: All users with access to the system but not included in the group or owner category.
    

File permissions use symbols and numerical values to represent access rights:

* “r” (Read) — 4
    
* “w” (Write) — 2
    
* “x” (Execute) — 1
    
* “-” (Null) — 0
    

Common Linux File Types:

* “-” (Regular file): e.g., text files, images, binaries.
    
* “d” (Directory).
    
* “c” (Character device file): Communicates with hardware devices character by character.
    
* “b” (Block device file): Communicates with hardware devices in blocks.
    
* “s” (Local socket file used for inter-process communication).
    
* “p” (Named Pipe).
    
* “l” (Symbolic link).
    

Changing File Permissions

* chmod: Used to modify permissions. For example, adds execute permission for the owner.
    

```plaintext
chmod u+x my_file.txt
```

* chown: Used to change ownership. For example changes the file’s owner and group.
    

```plaintext
chown user:group my_file.txt
```

* chgrp: Used to change group permissions. For example changes the file's group.
    

```plaintext
chgrp group my_file.txt
```

For Example

```plaintext
touch my_file.txt          # Create a new file
ls -ltr my_file.txt        # View file details and permissions

```

![](https://miro.medium.com/v2/resize:fit:875/1*leZDTgt0l6NzfOyZ694j9A.png align="left")

```plaintext
chmod u+x my_file.txt      # Give owner execute permission
ls -ltr my_file.txt        # Check the updated permissions
```

![](https://miro.medium.com/v2/resize:fit:599/1*2YBOoGqDZFLsdOOn4gNWeA.png align="left")

# **3\. Understanding Access Control Lists (ACL) in Linux**

Access Control Lists (ACLs) provide a more granular and flexible way of managing access rights to files and directories. Standard file permissions in Linux allow for three levels of access (owner, group, and others), but ACLs extend this by enabling specific permissions for multiple users and groups. we will delve into ACLs, explore their usage, and try out the commands `getfacl` and `setfacl`

What are Access Control Lists (ACL)?

ACLs are an extension to the traditional file permissions in Linux. They allow for defining additional access rules on files and directories, granting or denying specific permissions to individual users or groups beyond the standard owner, group, and others.

Understanding `getfacl` Command The `getfacl` command is used to view the ACLs of a file or directory.

```plaintext
getfacl file_or_directory
```

The output will display the existing ACL entries, if any, including the permissions for each user and group.

Understanding `setfacl` Command The `setfacl` command is used to modify the ACLs of a file or directory.

```plaintext
setfacl options file_or_directory
```

We can use various options with `setfacl` to grant or revoke permissions for specific users or groups. For example:

* `setfacl -m u:user:permissions file_or_directory`: Adds permissions for a specific user.
    
* `setfacl -m g:group:permissions file_or_directory`: Adds permissions for a specific group.
    
* `setfacl -x user file_or_directory`: Removes all ACL entries for a particular user.
    
* `setfacl -b file_or_directory`: Removes all ACL entries for the file or directory.