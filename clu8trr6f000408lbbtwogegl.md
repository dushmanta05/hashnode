---
title: "How to Sign your Git Commits with GPG Keys"
seoTitle: "Git Commit Signing with GPG Keys: A Comprehensive Guide"
seoDescription: "Learn how to sign Git commits with GPG keys with  this comprehensive guide."
datePublished: Tue Mar 26 2024 20:24:09 GMT+0000 (Coordinated Universal Time)
cuid: clu8trr6f000408lbbtwogegl
slug: how-to-sign-your-git-commits-with-gpg-keys
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1711484516805/7acb48b1-ff23-45d6-9bcb-5671f2f84f12.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1711484572717/fe2e1ec2-3aa4-436e-a51d-81941820f9d9.png
tags: github, git, gpg, gpg-key

---

Although we can push our code to a GitHub remote repository using SSH, the commits are not truly verified, which means that the commits don't have any cryptographic verification. You might wonder, "What do you mean by my commits not being verified? I do commits and push to my account." Technically, yes, you do, but without cryptographic verification, we can't guarantee that the commits were altered since they were made or tampered codes were introduced to the repository.

To overcome this issue and ensure the authenticity of the commits, cryptographic verification such as GPG sign-in can be used. In this article, we'll explore how to sign our commits using GPG keys.

**Prerequisite:** Before starting, it's helpful if you know how to generate GPG keys and add them to your GitHub account. If not, don't worry; I've got that covered in detail in [this article](https://dushmanta.hashnode.dev/generating-and-adding-gpg-keys-to-your-github-account). Please feel free to check it out and add the GPG keys to your GitHub account.

After successfully adding your GPG keys to your GitHub account, the next step involves specifying the GPG key and setting the `gpgsign` option to true in your global Git configuration.

**Retrieve the GPG key:**

* First, let's retrieve the GPG key ID, which is associated with the public key added to GitHub
    
* Run the following command to list all the GPG keys available:
    
    ```bash
    gpg --list-secret-keys --keyid-format=long
    ```
    
* The result will look something like this:
    
    ```yaml
    sec   rsa3072/A369A9BFD11F6F60 2024-03-14 [SC]
          441F9580CF1B5238C3F0B2FCA369A9BFD11F6F60
    uid                 [ultimate] John Doe (Example) <john.doe@example.com>
    ssb   rsa3072/F038B8C5AD80A86D 2024-03-14 [E]
    ```
    
    In this output, the key ID is highlighted in the "sec" line, next to "rsa3072/". Here the key ID is "A369A9BFD11F6F60."
    
* Note: If you've got multiple GPG keys, then make sure to identify the one used to generate the public key for your GitHub account.
    

**Update Git configuration:**

Now that we have the required GPG key, let's configure the global Git config

1. **Adding the GPG key as the sign-in key:**  
    To add your GPG key as the signing key, execute the following command:
    
    ```bash
    git config --global user.signingkey A369A9BFD11F6F60
    # Replace 'A369A9BFD11F6F60' with your own GPG key ID
    ```
    
2. **Enabling the Git sign:**
    
    Next, enable Git signing with GPG keys by running:
    
    ```bash
    git config --global commit.gpgsign true
    ```
    
3. **Signing a Git commit:**  
    Now that we've enabled commit sign-in with GPG keys, each time you commit a message, you'll be prompted to enter the passphrase associated with your GPG key. This passphrase is set during the GPG key generation process.
    

Now, when you push your commit to the remote repository, you can verify your commits, and a verified badge will appear next to them, indicating their authenticity, as shown in the image below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1711484479324/69244991-0803-4269-b0b4-30479cb9f6ab.png align="left")

**Note:** Ensure you select the correct GPG key ID while setting the sign-in key. If you encounter an error message like `Signing failed: If there is no secret key,` it may indicate that your GPG key has expired or does not exist. In such cases, consider generating a new GPG key and following the setup steps outlined above.

I trust this article has been helpful in guiding you through the process of signing your Git commits. If you have any feedback or suggestions, please feel free to share them. Thank you for reading.