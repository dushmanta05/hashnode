---
title: "Generating and Adding GPG Keys to Your GitHub Account"
seoTitle: "Generating and Adding GPG Keys to Your GitHub Account"
seoDescription: "Learn how to generate GPG keys and add them to your GitHub account with this comprehensive guide."
datePublished: Tue Mar 26 2024 00:21:29 GMT+0000 (Coordinated Universal Time)
cuid: clu7mt4ac000608l99ydfcd0t
slug: generating-and-adding-gpg-keys-to-your-github-account
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1761110516695/52d90cd1-dc69-4926-9ef0-6be23b2a8554.png
tags: github, gpg-key

---

While adding SSH to your GitHub account, you must've come across the `Add GPG keys` option. In this article, let's understand what GPG keys are in brief and how to add GPG keys to your GitHub account.

**What are GPG keys?**  
In short, GPG (GNU Privacy Guard) is a cryptography software used to encrypt and decrypt data for secure communication over the internet. There are mainly two types of GPG keys: public keys and private keys. Public keys are used for encryption and verification, while private keys are kept secret and used for decryption and signing. You can read more about it [here](https://gnupg.org/).

**Benefits of adding GPG keys**  
Adding GPG keys to GitHub has its benefits. Unlike SSH, which is used for authentication, GPG keys are used to verify your signing commits. This means GPG helps encrypt your commits by attaching a digital signature to them, which can be verified, ensuring the commits' authenticity and integrity.

To add GPG keys to your GitHub account, follow these steps:

Recommendation: Before starting out, I recommend using `Git Bash` to generate the GPG keys smoothly and avoid potential errors.

1. **Installing GnuPG**
    
    If you're using Git Bash, then it should be installed already, but make sure to check again.
    
    Check if GnuPG is installed or not by running the following command:
    
    ```bash
    gpg --version
    ```
    
    If GnuPG is not installed, you can download and install GnuPG tools from [here](https://www.gnupg.org/download/)
    
2. **Check if GPG key already exists**
    
    Run the following command to see if you already have any existing GPG keys on your device:
    
    ```bash
    gpg --list-secret-keys --keyid-format=long
    ```
    
    If a key already exists, you'll see output in the terminal similar to this:
    
    ```yaml
    /home/dushmanta/.gnupg/pubring.kbx
    ----------------------------------
    sec   rsa3072/1A2B3C4D5E6F7G8H 2024-03-07 [SC]
          4D5805B4263EDF0CBF30DCC10A323E973124C0C9
    uid                 John Doe <john.doe@example.com>
    ssb   rsa3072/94793836B747D40A 2024-03-07 [E]
    ```
    
    In this output, "1A2B3C4D5E6F7G8H" in the "sec" line is the key ID, which will be used to generate the public key further.
    
    If you have multiple GPG keys, choose the key ID you want to use for GitHub, and you can skip to step no. 5.
    
3. **Generating GPG keys**
    
    If you don't have any GPG keys, open your terminal and run the following command to generate one:
    
    ```bash
    gpg --full-generate-key
    ```
    
    This will prompt you to make several choices to generate the key.
    
    ```yaml
    Please select what kind of key you want:
       (1) RSA and RSA (default)
       (2) DSA and Elgamal
       (3) DSA (sign only)
       (4) RSA (sign only)
      (14) Existing key from card
    ```
    
    By default, you can choose option 1 or another according to your needs.
    
    ```yaml
    RSA keys may be between 1024 and 4096 bits long.
    What keysize do you want?
    # Choose according to your need or press Enter to use the default 3072
    
    Please specify how long the key should be valid.
             0 = key does not expire
          <n>  = key expires in n days
          <n>w = key expires in n weeks
          <n>m = key expires in n months
          <n>y = key expires in n years
    Key is valid for?
    
    # Choose according to your requirement (let's choose 0)
    
    Key does not expire at all
    Is this correct? (y/N)
    
    # Choose y
    ```
    
    Then, it will ask for some basic information to create a user ID to identify your key.
    
    ```yaml
    GnuPG needs to construct a user ID to identify your key.
    
    Real name: John Doe
    Email address: john.doe@example.com # give the email you've used for GitHub
    Comment: GPG key for GitHub
    ```
    
    Then, a prompt will be given if you want to change any information or save.
    
    ```yaml
    Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit?
    # Select O to save your changes
    ```
    
    After that, it'll ask for a passphrase to protect the key (remember the passphrase, as it will be used every time you commit). Once entered, the key will be generated, and you'll see something like this:
    
    ```yaml
    pub   rsa3072 2024-03-14 [SC]
          441F9580CF1B5238C3F0B2FCA369A9BFD11F6F60
    uid                      John Doe (Example) <john.doe@example.com>
    sub   rsa3072 2024-03-14 [E]
    ```
    
4. **Retrieving the keys**
    
    After successfully generating your GPG keys, you can retrieve the key ID using the following command:
    
    ```bash
    gpg --list-secret-keys --keyid-format=long
    ```
    
    The result will look something like this:
    
    ```yaml
    sec   rsa3072/A369A9BFD11F6F60 2024-03-14 [SC]
          441F9580CF1B5238C3F0B2FCA369A9BFD11F6F60
    uid                 [ultimate] John Doe (Example) <john.doe@example.com>
    ssb   rsa3072/F038B8C5AD80A86D 2024-03-14 [E]
    ```
    
    In this output, the key ID is highlighted in the "sec" line, next to "rsa3072/". This key ID, such as "A369A9BFD11F6F60," will be used in the next step to generate the public key for export.
    
5. **Exporting the keys**
    
    After obtaining the key ID, use the following command to generate the public key:
    
    ```bash
    gpg --armor --export <Key ID> # Here Key Id is A369A9BFD11F6F60
    ```
    
    This command will generate the public key, which you'll need to add to GitHub. The public key generated will look like this:
    
    ```yaml
    -----BEGIN PGP PUBLIC KEY BLOCK-----
    # Public key value
    -----END PGP PUBLIC KEY BLOCK-----
    ```
    
6. **Adding the public key to GitHub**
    
    After the successful generation of the public key:
    
    1. Go to GitHub and navigate to Settings &gt; SSH and GPG keys.
        
    2. Click on 'New GPG key' and paste the public GPG key that was generated.
        
    3. Remember to include the 'Begin' and 'End' GPG public key block lines along with the public key value when pasting.
        
    
    And voila! You've successfully added the GPG key to your GitHub account.
    

I hope this article helped you successfully generate GPG keys and add them to your GitHub account. Thank you for reading the article, and please do share your feedback or suggestions on the article. Have a good day.