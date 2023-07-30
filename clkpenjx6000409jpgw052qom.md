---
title: "Day 10 — Advanced Git & GitHub for DevOps Engineers Part 2"
datePublished: Sun Jul 30 2023 12:16:00 GMT+0000 (Coordinated Universal Time)
cuid: clkpenjx6000409jpgw052qom
slug: day-10-advanced-git-github-for-devops-engineers-part-2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690719325070/466f61ab-7092-494b-8a7f-a6bebf9e6227.webp

---

# **📋 Task 1: Branching, Committing, and Restoring**

🌟 In this task, we’ll explore how to create a new branch 🌿, make changes with various messages 📝, and restore a file to an earlier version ⏪. Just follow these simple steps:

1. 🚀 Create a new branch named “dev” from the main branch and verify the change using the command “git checkout dev”.
    

```plaintext
git checkout -b dev
```

![](https://miro.medium.com/v2/resize:fit:875/0*DpNJ2SkXzKt7LK0q.png align="left")

2\. 📝 Create a new text file named version01.txt and fill it with the following content:

```plaintext
"This is the first feature of our application."
```

![](https://miro.medium.com/v2/resize:fit:875/0*7mPLo8Oczqi-vvNZ.png align="left")

3\. 📂 Use the “git add” command followed by the file names to prepare the tracking changes. Then commit this change with the message “Added new feature.”

![](https://miro.medium.com/v2/resize:fit:875/0*wMakQoSGm0NUobgA.png align="left")

4\. 📤 Push the `dev` branch to the remote repository using the command:

```plaintext
git push origin dev
```

![](https://miro.medium.com/v2/resize:fit:875/0*gCKNKIu2pdGXIz4S.png align="left")

5\. 🔄 Make additional commits to the dev branch by updating the version01.txt file and commit this change with the message “Making the following changes: …”.

```plaintext
This is the bug fix in the development branch
```

![](https://miro.medium.com/v2/resize:fit:875/0*A0A76X_ZSFvrmUTQ.png align="left")

6\. 🔄 Perform this step two additional times, including the provided content, and commit each change with relevant messages.

```plaintext
This is gadbad code.
```

![](https://miro.medium.com/v2/resize:fit:875/0*rHuitiohMAy8Dkli.png align="left")

7\. Again for adding feature4

```plaintext
This feature will goodbad everything from now.
```

![](https://miro.medium.com/v2/resize:fit:875/0*U_67TB-0wWyPldJZ.png align="left")

8\. Adding feature 5

![](https://miro.medium.com/v2/resize:fit:875/0*59QTRV8aCTfQJV4x.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*CTwWAJUQXZTCnLQk.png align="left")

9\. 🔙 Revert the version01.txt file to a previous state with the content “This is the bug fix in the development branch.”

10\. 📜 Using the “git log — oneline” command, find the &lt;commit&gt; information and identify the commit you want to reset to.

![](https://miro.medium.com/v2/resize:fit:875/0*j6ziJe42j9zOc6TF.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*aQvIihVv1pXAKtEL.png align="left")

# **📋 Task 2: Branching, Merging, and Rebasing**

In this task, we will explore the concepts of branches, merging, and rebasing. To get started, follow these steps:

1. 🚀 Let’s merge the “dev” branch with the “main” branch. First, check the commits on the “dev” branch by using “git checkout dev” 👩‍💻. Then, switch back to the “main” branch and check its commits as well 🌿. Now, execute the “git merge dev” command to combine the commits and observe the results.
    

![](https://miro.medium.com/v2/resize:fit:875/0*T1Ltnihgx8fYNfXE.png align="left")

2\. Now, execute the “git merge dev” command to combine the commits and observe the results.

![](https://miro.medium.com/v2/resize:fit:875/0*KCLPGp4W-0ZcP8Yq.png align="left")

3\. 🔄 As a practice, perform a `git rebase` operation to see the difference it makes. Describe the differences you observe 🔄.

![](https://miro.medium.com/v2/resize:fit:875/0*4V_FFHl2KQsZv1hQ.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*3ErMfXMTT6jFQMCY.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*n4Jksalq8nqJwoFI.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*tO9IqlYeFJYpMZRM.png align="left")

In this sequence of commands, developers start by checking out the “dev” branch in Git. They then create a new text file called “version01.txt” with specific content. The changes to this file are staged and committed with an appropriate commit message. After inspecting the commit history on the “dev” branch, they switch to the “main” branch and perform a rebase.

During the rebase, the commits from the “dev” branch are moved on top of the existing commits in the “main” branch, resulting in an updated, linear commit history on the “main” branch. This process demonstrates how branches interact, and how Git’s merge and rebase commands can be used to manage code development seamlessly.

Note: Git merge combines changes and preserves the original commit history, while Git rebase moves commits to create a cleaner, linear commit graph, making project tracking easier.

# **🎉 Conclusion 🎉**

Congratulations on completing Day 10 of the #90DaysOfDevOps challenge! Today, we explored advanced Git techniques such as branching, merging, and reverting, essential for efficient collaboration and version control in software projects. Get ready for Day 11, where we’ll dive deeper into Git and GitHub for DevOps Engineers in the second part of this topic. Stay tuned for more exciting learning ahead! 🚀👩‍💻