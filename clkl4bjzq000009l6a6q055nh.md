---
title: "Deep Dive in Git & GitHub for DevOps Engineers part 1 #Day 9"
datePublished: Thu Jul 27 2023 12:15:40 GMT+0000 (Coordinated Universal Time)
cuid: clkl4bjzq000009l6a6q055nh
slug: deep-dive-in-git-github-for-devops-engineers-part-1-day-9
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690460097699/0090907d-a7de-42c7-b991-147363574b12.webp

---

# **1\. Introduction**

Welcome to Day 9 of #90DaysOfDevOps! Today, we’ll explore Git and GitHub. Git is a version control system, allowing devs to track code changes. GitHub is a web-based platform that hosts Git repositories, fostering collaboration. They empower DevOps teams, automate workflows, and enhance code quality. Embrace these tools for successful software delivery! Happy coding! #DevOps #Git #GitHub

# **2\. What is GIT and Why it is important?**

**Git :** Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency. git also used for source code management.

Git is used to tracking changes in the source code, enabling multiple developers to work together on non-linear development. With Git, you can keep a record of who made changes to what part of a file, and you can revert back to earlier versions of the file if needed. Git also makes it easy to collaborate with others, as you can share changes and merge the changes made by different people into a single version of a file

# **3\. What is the difference Between Main Branch and Master Branch?**

There is no difference between main and master branch in git. Main or Master branch is a default branch when you create a repository. GitHub now use main as a it’s default branch. while others still use master branch as a default branch.

# **4\. Explanation of the difference between Git and GitHub**

**Git:**

Git is indeed a distributed version control system that allows users to track changes in any set of files. It was created by Linus Torvalds in 2005 and has become the standard version control system for software development. Git enables multiple developers to work on the same project simultaneously without interfering with each other’s work. It efficiently handles branching, merging, and tracking changes, making it a powerful tool for collaborative software development.

It’s important to note that while Git is typically used for coordinating work among programmers, it is not limited to code. It can be used for version controlling any set of files, including text documents, configuration files, graphics, and more.

Git is installed and maintained on your local system, and it operates primarily through the command-line interface (CLI). There are also various graphical user interfaces (GUIs) available that provide a more visual way to interact with Git, but fundamentally, Git is a command-line tool.

**GitHub:**

GitHub is a cloud-based platform that provides hosting for Git repositories. It is one of several services that offer Git repository hosting, and it’s one of the most popular ones. GitHub allows users to create remote repositories for their projects, which are stored on GitHub’s servers.

While Git itself is primarily a command-line tool, GitHub provides a graphical user interface (GUI) on top of Git. This web-based interface allows users to perform many Git operations through a visual and user-friendly interface. It simplifies tasks like creating and managing repositories, branching, pull requests, code reviews, issue tracking, and more.

GitHub’s collaborative features make it an excellent platform for open-source projects and team-based development, as it allows multiple developers to work together on a project and easily contribute their changes. It also provides additional features like continuous integration, code reviews, project management tools, and integrations with other development tools.

# **5\. How to create a new repository on GitHub?**

**step 1:** Sign in to your GitHub account using your username and password.

**step 2:** Once you are signed in, click on the “+” icon in the top-right corner of the GitHub homepage. From the dropdown menu, select “New repository.” or, go to repositories and click on ‘new’ in the top right corner.

![](https://miro.medium.com/v2/resize:fit:875/1*CYe_ack7Y2Us6y0_LZ71Nw.png align="left")

**Step 3:** Set up the repository: Now Add the repository name and other details like whether you want to keep it public(publically accessible) or private repo.

![](https://miro.medium.com/v2/resize:fit:875/1*ISQGHjNQQXjQNKna-jz9dg.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/1*oppDr8CkHOLia02BYMt7NA.png align="left")

Then click on ‘create repository’

you have successfully created a repository.

# **6\. Difference between local & remote repository**

Git local repository is the one on which we will make local changes, typically this local repository is on our computer.

Git remote repositories are hosted on a server that is accessible for all team members.

# **7\. How to connect local to remote repository?**

A git remote command is used to make the remote connections such as connecting a Git local repository with GitHub remote repository.

1.git remote add origin [github.com/YOUR-USERNAME/YOUR-REPOSITORY](http://github.com/YOUR-USERNAME/YOUR-REPOSITORY)

2.git push origin master