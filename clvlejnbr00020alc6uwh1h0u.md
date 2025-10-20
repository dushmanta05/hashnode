---
title: "Easy Guide to Configuring a Git Repository with a Custom Branch Name"
seoTitle: "Git Repository Custom Branch Configuration"
seoDescription: "Learn how to configure a Git repository with a custom branch name like 'main' instead of 'master'"
datePublished: Mon Apr 29 2024 20:18:39 GMT+0000 (Coordinated Universal Time)
cuid: clvlejnbr00020alc6uwh1h0u
slug: easy-guide-to-configuring-a-git-repository-with-a-custom-branch-name
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1760945786765/2b86ed87-a6bb-4121-938f-a58b9a9cbf3f.png
tags: git

---

Greetings, fellow code wizards! In this article, let's explore how to configure a Git repository with a custom branch name other than `master`.

If you've used Git before, you probably know that when you create a Git repository, the default branch name is usually `master`. However, nowadays, hardly anyone uses `master` as the main / default branch. In reality, most of us prefer to use `main` as the branch name. Even platforms like **GitHub** and **GitLab** use `main` as the default branch when creating a repository. It's a bit puzzling why Git still sticks with `master` as the default branch name when `main` has become the standard across the software industry, but that's just how it is.

Let's now explore how we can set up a git repository with `main` as the default branch name or choose any other custom branch name as the default one.

**Note:** Before diving in, please ensure that your `Git` version is **2.28.0** or higher, as this feature was added in that release. (If you're using **Ubuntu**, follow [this link](https://gist.github.com/dushmanta05/d03e6eef3c77d76bf8d65b5d892e52b6) for the command to upgrade `Git` to the latest version.)

**Configuring Branch on Initialization:**

We can set up the branch name directly when initializing a Git repository using the `--initial-branch` or `-b` parameter, like in the following example:

```bash
git init --initial-branch <branch-name>
# or
git init -b <branch-name>
```

For example, if we want to initialize the branch name as `development`, the command would be:

```bash
git init --initial-branch development
# or
git init -b development
```

**Configuring Default Branch for All Repositories:**

We can also set up the default setting to use a custom-named branch for all repositories. This way, we won't need to specify it every time we create a git repository, especially if we want to keep the main branch consistent across all repositories.

This can be achieved by setting `init.defaultBranch` globally using the command below:

```bash
git config --global init.defaultBranch <branch-name>
```

For example, if we want to set the default branch as `main` for all new git repositories we create, we can do this by using the following command:

```bash
git config --global init.defaultBranch main
```

Now, every time we create a new git repository using the `git init` command, the default branch will be named `main` by default.

I hope this article helps you set a custom branch name when starting a git repository. Please share your feedback and suggestions for improvement. Thank you. Happy coding!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714421006957/109292dd-d943-4ea9-b3ef-a88692490899.gif align="center")