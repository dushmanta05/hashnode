---
title: "Git Guide: Pushing Code to Remote Feature Branches and Best Practices"
seoTitle: "Git Push to Remote Branches and Best Practices for Branch Naming"
seoDescription: "Learn how to push code to main branch, feature branch and other remote branch with best practice for naming GitHub branches to avoid confusion and error."
datePublished: Sun Sep 17 2023 19:58:44 GMT+0000 (Coordinated Universal Time)
cuid: clmnvrdhx000009mc5kmxfmnr
slug: git-guide-pushing-code-to-remote-feature-branches-and-best-practices
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1694979390507/e5713df7-9378-4a95-baf3-14e552afd7c4.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1711414121808/d1bf90ad-66e0-4e23-9ad6-17199c3c769d.avif
tags: github, git

---

In the world of Git, we mainly develop code within our local feature branches. Unlike our code, Git branches don't automatically sync with the remote repository when we hit the `git push` command. However, we need to be careful when pushing code using the feature branch name to avoid Git fatal errors.

In this guide, we'll explore how to push code to the remote repository and discuss best practices to prevent common issues.

**Prerequisite:** You should have a basic understanding of `git` and the `git push`.

Throughout this guide, I'll reference the main / master branch as the `main` branch and the other branches as `feature` or `feature-branch`.

Before we dive in, let's just revise `git push` in brief:

When setting up git in our repository and before the first push, we need to establish an upstream connection between our local and remote repositories. This connection allows us to easily pull and push between the local and remote repositories.

The syntax is: `git push <options> <repository> <branch-name>`

Here, we'll use the `-u` or `--set-upstream` option in `<options>` to set the remote repository as upstream. The `<repository>` is the name of the remote repo and by default, the name is `origin`. The `<branch-name>` specifies the local branch you're pushing from, which is typically `main` (or `master` previously) So, the basic push command to set `origin` as upstream for the **local main** branch is: `git push -u origin main`

Now, let's dive into the specifics of pushing code.

### **Pushing from the Local Main Branch to the Remote Main Branch**

* The default `git push` primarily occurs between the **main** branches of your local and remote repositories.
    
* The syntax to push the **local main** branch to the **remote main** branch is: `git push -u origin main`
    
* Once you've set up the upstream, you can use `git push` and `git pull` seamlessly without writing the branch names.
    

**P.S.** Remember, it's best practice not to push directly to the **main** to avoid disruptions to the main code base? (Hey, you don't want to be the culprit who broke the main code base, right?)

### **Pushing from a Local Feature Branch to the Remote Main Branch**

Suppose you want to add a new feature and have created a local branch called **feature**. To push the **local feature** branch to the `remote main` (although not a best practice), follow these steps:

* Switch to the `feature` branch:
    
    1. If it doesn't exist: `git checkout -b feature` (this creates and switches to the **feature branch**).
        
    2. If it already exists: `git checkout feature` (simply switch to it).
        
* Push your commits to remote
    
    1. Syntax: `git push <repository> <local-feature>:<remote-branch>`
        
    2. If you want to push the local feature branch itself without specifying the branch to push, you can use `git push origin feature`. This command will push the entire branch and create a branch named **feature** in the remote repository. If a branch named **feature** already exists in the remote, it will simply push the new code to the remote feature branch.
        
    3. if we want to push it to `main` branch then we can use the command written in the syntax above `git push origin feature:main`
        

### **Pushing from a Local Main Branch to a Remote Feature Branch**

* To push from the **local main** branch to a **remote feature** branch, ensure you pull any changes and merge the **local feature** branch into the **local main** if necessary.
    
* Use the following syntax: `git push <repository> <local-main>:<remote-feature>`
    
* Now, for example, you can use `git push origin main:feature-branch`. if `feature-branch` doesn't exist remotely, this command creates it; if it exists, it pushes your new code.
    

### **Pushing from a Local Feature Branch to a Local Remote Branch**

* If you wish to push your code to a **remote feature** branch from your **local feature** repository without merging to the **local main** branch or pushing to the **remote main** branch use this syntax: `git push <repository> <local-feature-branch>:<remote-feature-branch>`
    
* `<repository>` usually defaults to `origin<local-feature-branch>` could be `local-feature` and `remote-feature-branch` might be `remote-feature`, so, it could look like this: `git push origin local-feature:remote-feature`
    

You may wonder if you can do this without switching branches, and yes, you can.

Now, let's explore common errors and best practices.

### **Error I Faced**

Even if you follow all the steps correctly, Git can sometimes throw errors due to branch naming conventions, especially when dealing with the Bash command line.

I once encountered an error at work because of a branch named `dushmanta's-branch.` When I tried to push it with the command `git push origin dushmanta:dushmanta's-branch` the single quote caused issues in the git bash. To resolve this, I had to wrap the branch names in double quotes, similar to how we wrap commit messages:

* `git push origin "dushmanta:dushmanta's-branch"`
    
* Alternatively, you can wrap the branch name which has the single quote: `git push origin dushmanta:"dushmanta's-branch"`
    
* If you prefer using single quotes, you can escape the single quote in the branch name using `\` (forward slash), like this: `git push origin dushmanta:'db'\''s-branch'` (Here the branch name's single quote `'` is preceded by `\`, which then again is wrapped by `''`, making the escaping expression `'\''` and the branch name is wrapped by single quotes), you can also wrap the entire branch expression: `git push origin 'dushmanta:db'\''s-branch'`.
    

### **Best Practices**

While GitHub permits special characters like `', ", !, %, &, $, @` to include in branch names, it's best to avoid them to prevent issues in git commands. Here are some tips for better branch names:

* Use lowercase letters for branch names to maintain consistency. Git treats `feature` and `Feature` as different branches, which can be confusing.
    
* Stick to letters and numbers in branch names, avoiding special characters that can cause problems with Git tools and systems.
    
* Use **hyphens (-)** or **underscores (\_)** to separate words in branch names, making them more readable. Avoid special characters.
    
* Avoid using reserved words like `master`, `develop`, and `head` to prevent confusion.
    
* Prefix branch names with descriptive terms like `bug-fix`, `feature`, `hotfix`, `chore`, or `release` to indicate their purpose. For example, use names like `feature/user-auth`, `bug-fix/issue-101`, `release/2.0.1`, etc.
    
* Maintain a consistent naming convention across your projects.
    

I hope this helps you navigate the world of git push. Feel free to share your thoughts and suggestions for improvements in the comments. Thank you for reading! Have a good day!