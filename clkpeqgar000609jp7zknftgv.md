---
title: "Day 11 — Advanced Git & GitHub for DevOps Engineers"
datePublished: Sun Jul 30 2023 12:18:15 GMT+0000 (Coordinated Universal Time)
cuid: clkpeqgar000609jp7zknftgv
slug: day-11-advanced-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690719440132/28146667-9d2b-4747-bf79-78e717b72d92.webp

---

# **1\. 🌟 Greetings, Adventurers! 🌟**

Welcome back to Day 11 of our exhilarating #90DaysOfDevOps adventure! Today’s expedition takes us deep into the realm of Git mastery, where we’ll uncover the hidden treasures of Git Stash and Cherry-pick techniques. Moreover, we shall unravel the art of resolving merge conflicts, an invaluable skill for seamless collaboration in your quests. Prepare yourselves to grasp the secrets of Stashing and Applying Changes, attaining virtuosity in the Rebase command, and honing the craft of effective commit messages. As we traverse further, behold the wondrous magic of Cherry-picking and unleashing the full potential of features in your noble projects. Together, let’s embark on this thrilling journey of version control, elevating your DevOps experience to unparalleled heights! 🚀😊”

# **2\. 🔒 What is Git Stash?**

Imagine you are working on a coding project, and suddenly your team asks you to fix a critical bug in another part of the code. You don’t want to commit your incomplete changes, as it might create issues in the main codebase. 🐛

Here comes Git Stash to the rescue! 🎉

Git Stash is a powerful feature that allows you to temporarily store your unfinished changes in a safe, hidden box. When you use the “git stash” command, Git saves your current changes and reverts your workspace to a clean state, as if you never started making those changes. 📦

This means you can switch to the bug fix task or any other task without worrying about your incomplete changes interfering with your work. The changes you stashed away are stored and can be easily retrieved later. Once you’ve fixed the bug or completed the other task, you can simply unstash your changes and continue where you left off, with all your work intact! 🧩

It’s like having a secret compartment for your code changes, allowing you to work on multiple tasks simultaneously and keeping your codebase organized and free from half-baked changes. 🧹

# **3\. 🍒 What is Cherry-pick?**

In Git, “cherry-pick” is a useful operation that allows you to select and apply specific commits from one branch to another.

Imagine you have two branches in your project, and there’s a bug fix or a cool feature in one branch that you want to add to another branch without merging the whole branch. 🐞

Here’s where cherry-pick comes to the rescue! 🎉

You can cherry-pick the specific commit from one branch and apply it to another branch. It’s like plucking a cherry from one tree and placing it on another tree! 🍒🌳

Cherry-pick is a nifty tool to selectively bring in changes from one branch to another, making it easier to manage code and collaborate with your team. 👩‍💻👨‍💻

# **4\. 🔄 How to resolve merge Conflicts?**

Merge conflicts can happen when you try to combine different branches, and Git doesn’t know which changes to keep. This can occur when you’re merging or rebasing branches that have gone in different directions.

When a conflict occurs, Git will let you know which files have conflicts. You can use the “git status” command to see the list of conflicted files. 😮

Next, you can use the “git diff” command to see the differences between the conflicting versions and understand what needs to be resolved. 👀

Now comes the fun part! You get to manually edit the conflicting parts in the files, choosing which changes to keep and which to discard. Once you’ve made the necessary adjustments, you use the “git add” command to tell Git that you’ve resolved the conflicts. 🛠️

After resolving all the conflicts, you can continue with the merge or rebase process with confidence! 🚀

By resolving merge conflicts, you can ensure that your code is in sync and ready to be shared with the rest of the team. 👩‍💻👨‍💻

# **5\. 📋 Task 1: Stashing and Applying Changes**

In this task, our focus will be on branches, and we’ll explore how to utilize the “git stash” command to save changes temporarily without committing them. Simply follow these steps: 🌟

1. Create a new branch 🌿 using the below command:
    

```plaintext
git checkout -b dev
```

![](https://miro.medium.com/v2/resize:fit:875/0*t5FrGhvaDv7bbqTA.png align="left")

2\. Make some changes to the files 📝 in the **dev** branch.

![](https://miro.medium.com/v2/resize:fit:875/0*Hx4jPWUWG-w9_3l6.png align="left")

3\. In the middle of your work, your team urgently requests you to handle an important task in the main branch. To handle this situation without losing your progress, you can utilize the “**git stash**” command to save your changes without committing them.

![](https://miro.medium.com/v2/resize:fit:875/0*IWq8fiWTW1xLV1Oe.png align="left")

4\. Use following the command to switch to the **main** branch and proceed with important tasks.

![](https://miro.medium.com/v2/resize:fit:875/0*fMNQsUtWqJftIo3X.png align="left")

5\. Now that our crucial task is completed, let’s switch 🔙 to the dev branch to continue our work. We’ll use the “git stash pop” command to retrieve the changes we stashed earlier and apply them on top of the new commits.

![](https://miro.medium.com/v2/resize:fit:875/0*5i6RIQy95TDDHShJ.png align="left")

![](https://miro.medium.com/v2/resize:fit:875/0*1mlmGfjX-ApEFCh1.png align="left")

# **6\. 📋 Task 2: Rebase and Commit Messages**

In this task, we’ll be working on the day-10 version01.txt file in the development branch and carrying out a rebase operation. Follow these steps:

1. 📝 Open the `version01.txt` file in the development branch. add the line: "**After bug fixing, this is the new feature with minor alteration.**" Commit this change with the message: “**Added feature 2.1 in the development branch.**”
    

![](https://miro.medium.com/v2/resize:fit:875/0*Whr8LYnFl0-EOqi6.png align="left")

2\. 📝 Add another line in version01.txt: “**This is the advancement of the previous feature.**” Commit this change with the message: “**Added feature2.2 in the development branch.**”

![](https://miro.medium.com/v2/resize:fit:875/0*4jWI0b2wODaiGNg7.png align="left")

3\. 📝 Add one more line in version01.txt: “**Feature 2 is completed and ready for release.**” Commit this change with the message: “**Feature2 completed.**”

![](https://miro.medium.com/v2/resize:fit:875/0*lRsk6cZ1vTb8NBLr.png align="left")

4\. 🚀 Create a prod branch and use **git rebase** to include all the commits from the dev branch into the prod branch.

![](https://miro.medium.com/v2/resize:fit:875/0*EtlQbrZpGZX2B6FJ.png align="left")

# **7\. 📋 Task 3: Cherry-picking and Optimizing Features**

In this task, we’ll learn about cherry-picking a specific commit from one branch to another and making additional changes to it. Follow these steps:

1. 🚀 Switch to the production branch. And cherry-pick the commit “Added feature2.2 in development branch” using the below command.
    

```plaintext
git cherry-pick <commit-hash>
```

![](https://miro.medium.com/v2/resize:fit:875/0*O7J-JY038z2KxVuW.png align="left")

2\. ✏️ Add the following lines after “This is the advancement of the previous feature” in the version01.txt file:

```plaintext
Added few more changes to make it more optimized.
```

3\. 📝 Commit this change with the message “Optimized the feature.”

![](https://miro.medium.com/v2/resize:fit:875/0*6kvCl711CvBA9JHM.png align="left")

# **8\. 🎉 Conclusion 🎉**

Congratulations on completing Day 11 of the #90DaysOfDevOps challenge! During this exciting session, we explored some advanced Git techniques, such as stashing, cherry-picking, and rebasing, and we’re going to celebrate your accomplishments!

Git Stash proved to be an invaluable tool, allowing us to temporarily save changes without committing them. Cherry-Pick, on the other hand, empowered us to transfer selective commits between branches, making it a breeze to manage our codebase effectively. And let’s not forget about mastering conflict resolution, a crucial skill that enhances collaboration and teamwork.

The comprehensive step-by-step guide covered everything you need to know about stashing and applying changes, as well as how to use rebase to maintain a clean and organized commit history. With the power of cherry-picking, we were able to optimize and fine-tune features, which undoubtedly will boost our development productivity.

By incorporating these powerful Git tools into our workflows, we can streamline processes and make collaboration among team members seamless and efficient.

As you continue on your DevOps journey, I encourage you to keep exploring and practicing with Git, as it holds immense potential for DevOps engineers like yourself. Stay excited and motivated, for there are more challenges ahead that will only help you grow stronger as a developer and a team player! 💪😊🚀