---
title: "Advance Git & GitHub concepts for DevOps Engineers. Day 10"
datePublished: Thu Jul 27 2023 12:22:54 GMT+0000 (Coordinated Universal Time)
cuid: clkl4kvch000c09mp2g6i95w9
slug: advance-git-github-concepts-for-devops-engineers-day-10

---

![](https://miro.medium.com/v2/resize:fit:875/1*QAXSXmrvPUGnXfqDKWawPA.jpeg align="left")

# **Git branching :**

Git branching allows you to create separate lines of development within a repository. It enables isolated work on features, bug fixes, or experiments. Branches have their own commit history and can be easily switched between. Branching facilitates parallel development and collaborative workflows through pull requests. It also helps with version control and managing different releases.

![](https://miro.medium.com/v2/resize:fit:521/0*gS3S_4otm0irVVvB align="left")

```plaintext
  #Creating a Branch
  git branch <branch>

  #List all of the branches in your repository. 
  git branch --list.

  #Delete the specified branch.
  git branch -d <branch>

  #Force delete the specified branch, even if it has unmerged changes.
  git branch -D <branch>

  #Rename the current branch to ＜branch＞.
  git branch -m <branch>

  #List all remote branches. 
  git branch -a

  #jump into that branch
  git checkout <branch>
  git switch <branch>
```

let’s understand with an real life example:

Imagine you are a writer working on a book. The main branch represents the final published version of the book, while each branch represents a different draft or version of the book.

* You start with the main branch, which contains the completed and polished chapters of your book.
    
* When you want to experiment with a new plot twist or character development, you create a new branch. This branch allows you to make changes without affecting the main story.
    
* You can switch between branches to work on different ideas independently. Each branch has its own set of changes and revisions.
    
* Once you are satisfied with a particular branch, you can merge it back into the main branch, incorporating the changes into the final version of the book.
    
* If an experiment doesn’t work out, you can simply discard the branch, just like crumpling up a piece of paper and throwing it away, without impacting the main storyline.
    

A branch is not a folder:

It’s natural to think of a Git branch as a folder.

It’s not.

When you create a branch, you’re not creating a clean environment, even though it might seem like you are. A branch inherits all of the data that its parent contains. If the parent branch is the main branch, then your new branch contains the common history of your project. But if the parent branch is another branch off of main, then your new branch contains the history in main plus the history of the other branch.

# **Git revert:**

undoes a previous commit by creating a new commit that inverses the changes introduced by the original commit. This keeps a record of the undo operation in the commit history, making it safe for collaborative workflows. It is commonly used for reverting changes in shared branches.

![](https://miro.medium.com/v2/resize:fit:875/0*8tGpwXKffw2htcoM align="left")

# **Git reset :**

`git reset` is a command in Git that allows you to move the current branch pointer to a different commit. It is primarily used to undo changes or manipulate the commit history.

When you run `git reset`, you can specify the commit to which you want to reset the branch pointer.

# **What are git rebase and git merge?**

1. `git rebase`: It is a command used to incorporate changes from one branch onto another by moving or replaying commits. When you perform a rebase, Git identifies the common ancestor of the two branches, detaches the commits from the current branch, and reapplies them on top of the target branch. This results in a linear commit history, with the changes from both branches appearing in chronological order. Rebase is commonly used to keep a clean and linear commit history.
    

![](https://miro.medium.com/v2/resize:fit:281/0*TCYbPVIwBbP-80LR align="left")

`git merge`: It is a command used to combine the changes from one branch into another. When you perform a merge, Git creates a new "merge commit" that represents the combination of changes from the merged branches. The merge commit has multiple parents, preserving the commit history of both branches. Git automatically identifies the common ancestor of the branches and applies the changes on top of the target branch. Merge is commonly used to integrate feature branches or branches with divergent histories.

![](https://miro.medium.com/v2/resize:fit:625/0*h7FdmDoiBPQc7K7y.png align="left")

**TASK:**

1. Step 1: Create a new branch called “dev” and switch to it.
    

```plaintext
 git checkout -b dev
```

Step 2: Create a text file called “version01.txt” with the content “This is the first feature of our application”

```plaintext
 echo "This is the first feature of our application" > Devops/Git/version01.txt
```

Step 3: Add and commit the changes with the commit message “Added new feature”

```plaintext
 git add Devops/Git/version01.txt
 git commit -m "Added new feature"
```

Step 4: Push the changes to the remote repository.

```plaintext
 git push origin dev
```

Step 5: Add new commits to the “dev” branch with the specified content in “version01.txt”

```plaintext
 echo "This is the bug fix in development branch" >> Devops/Git/version01.txt
 git add Devops/Git/version01.txt
 git commit -m "Added feature2 in development branch"

 echo "This is gadbad code" >> Devops/Git/version01.txt
 git add Devops/Git/version01.txt
 git commit -m "Added feature3 in development branch"

 echo "This feature will gadbad everything from now." >> Devops/Git/version01.txt
 git add Devops/Git/version01.txt
 git commit -m "Added feature4 in development branch"
```

Step 6: Restore the file to a previous version where the content should be “This is the bug fix in the development branch”.

```plaintext
 git log
```

Note the commit hash of the commit where the content is “This is the bug fix in the development branch”.

To use git revert:

```plaintext
 git revert <commit-hash>
```

This will create a new commit that undoes the changes made in the specified commit.

To use git reset:

```plaintext
 git reset <commit-hash>
```

This will reset the branch to the specified commit, erasing the changes made in the subsequent commits.

After reverting or resetting, you can add and commit the changes with an appropriate commit message, and push the changes to the remote repository.

```plaintext
 git add Devops/Git/version01.txt
 git commit -m "Restored file to previous version"
 git push origin dev
```

You have now created a branch, made changes to a file, committed the changes, pushed them to the remote repository, and restored the file to a previous version using Git commands. Git provides powerful version control features that help developers effectively manage their codebase and collaborate with their teams.