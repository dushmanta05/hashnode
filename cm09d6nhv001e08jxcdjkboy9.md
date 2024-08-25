---
title: "Simple Steps to Configure Git for a Specific Repo with a Different User"
seoTitle: "Configure Git: Different User for Specific Repo"
seoDescription: "Learn how to configure Git for a specific repository with a different user, including GPG key setup for enhanced security"
datePublished: Sun Aug 25 2024 09:25:51 GMT+0000 (Coordinated Universal Time)
cuid: cm09d6nhv001e08jxcdjkboy9
slug: simple-steps-to-configure-git-for-a-specific-repo-with-a-different-user
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1724577874103/5f767259-159d-489c-9ee1-bee79c6a1c96.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1724577904867/164e0978-5d4c-45fb-b565-2d0a4fd28894.png
tags: github, git, gitlab

---

Have you ever needed to set up different Git settings for a specific repository on your system that isn't your main account? By default, Git uses global configuration settings for all repositories, but sometimes you need a unique setup for certain repositories. In this article, we'll explore how to configure Git for a different account in a specific repository and how to add a separate GPG key for that account for security.

Before we begin, I assume you already have a global Git configuration with a different email. Now, let's focus on the specific repository where you want to change the Git settings.

First, let's see what the current Git configuration looks like by running the following command:

```bash
git config --list
```

The output will look something like this:

```bash
user.email=global@user.com
user.name=Global User
user.signingkey=<Your GPG Signing Key> # If you've added GPG key to the config
commit.gpgsign=true # If you've setup GPG signing
init.defaultbranch=main # If you've setup default branch to main
```

To add a different configuration for a specific repository, open the terminal in that folder and make the following changes:

First, let's add Git to that repository if you haven't already.

```bash
npm init
```

Next, if we check the Git configuration by running the `git config --list` command, it will show the global user's Git settings.

```bash
user.email=global@user.com
user.name=Global User
user.signingkey=<Your GPG Signing Key>
commit.gpgsign=true
init.defaultbranch=main
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
```

Now, let's change the user email and name to the new ones for this specific repository.

#### Set the local user email:

Run the following command to set the user email for that repository:

```bash
git config user.email "your-email@example.com"
```

#### Set the local user name:

Run the following command to set the user name for that repository:

```bash
git config user.name "Your Name"
```

After making these changes, let's check the updated configuration by running the same command:

```bash
user.email=global@user.com
user.name=Global User
user.signingkey=<Your GPG Signing Key>
commit.gpgsign=true
init.defaultbranch=main
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
user.email=your-email@example.com
user.name=Your Name
```

As you can see, the user email and name appear at the bottom of the config. If you try this outside of the repository, they won't show because they are configured specifically for this repository.

Also, if you have GPG signing enabled for the global user, you can turn it off to avoid any issues by running the following command:

```bash
git config commit.gpgsign false
```

If you don't plan to use the GPG signing key, this configuration will allow you to make commits with the new user name and email.

If you want to know what will happen if you don't turn off GPG signing and want to add GPG signing, please follow the next steps.

#### Configuring GPG Keys:

Before diving in, let's learn what GPG keys do.

GPG keys add an extra layer of security. Each time you commit, you sign the commits with your password. These GPG keys are linked to your GitHub or GitLab account, which verifies the commit by checking the valid signature and adds a verified badge to your commits.

Now, when you generate a GPG key, you set an email address with that key. If you don't turn off GPG signing in your specific repository, you'll always sign the commit locally. However, after you push, GitHub/GitLab will not recognize this signature as valid and won't show the verified badge because this new email address is not included in the existing GPG key.

Now, based on your needs, if the new user email is added to the same GitHub/GitLab account as the global user email or if it's a different account, you can add GPG keys with the following steps according to your requirement:

#### Different GitHub or GitLab accounts:

If you have a different account from the global Git configured account for GitHub or GitLab, you need to generate a new GPG key and add it to GitHub or GitLab.

To generate a new GPG key and add it to GitHub, you can check out my blog on [Generating and Adding GPG Keys to Your GitHub Account](https://dushmanta.hashnode.dev/generating-and-adding-gpg-keys-to-your-github-account).

After you successfully add the GPG key to your GitHub or GitLab account, retrieve the GPG key ID and add it to your current repository by running the following command:

```bash
git config user.signingkey <Your-GPG-Key-ID>
```

This will successfully add your GPG key to your Git configuration. To sign all your commits with this GPG key, enable GPG signing by running the following command:

```bash
git config commit.gpgsign true
```

#### Same GitHub or GitLab account:

If the new user you configured is associated with the same GitHub/GitLab account as the global Git user, you can follow the steps above to add a new GPG key. Alternatively, you can follow this article [Guide to Adding Multiple Email to Your Existing GPG Key for Git](https://dushmanta.hashnode.dev/guide-to-adding-multiple-email-to-your-existing-gpg-key-for-git) to add this new user to the existing GPG key and .

After updating, don't forget to enable GPG signing by setting `gpg.sign` to true with the following command:

```bash
git config commit.gpgsign true
```

Once you have successfully updated the configuration, running the `git config --list` command will show something like this:

```bash
user.email=dushmanta.behera@hyscaler.com
user.name=Dushmanta Behera
user.signingkey=<Your GPG Signing Key>
commit.gpgsign=true
init.defaultbranch=main
core.repositoryformatversion=0
core.filemode=true
core.bare=false
core.logallrefupdates=true
user.name=Dushmanta
user.email=dushmanta0511@gmail.com
# Below will show if you've added a new GPG keys
user.signingkey=<Your GPG Signing Key>
commit.gpgsign=true
```

If you've updated the existing GPG keys, the last two lines won't appear because they are already included in the global GPG key.

And that's it! Now you're ready to make commits with the new user for the specific repository, with GPG signatures for your commits.

---

I hope this article helps you configure Git for a specific repository with a distinct user. Please share your feedback or any suggestions for improvements. Thank you.