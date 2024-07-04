---
title: "How to View, Customize and Save Tree-Like Directory Structure in Linux"
seoTitle: "View, Customize and Save Linux Directory Trees"
seoDescription: "Learn how to view, customize, and save tree-like directory structures in Linux using the `tree` command"
datePublished: Thu Jul 04 2024 04:16:15 GMT+0000 (Coordinated Universal Time)
cuid: cly6r87vo000108lebez9gq33
slug: how-to-view-customize-and-save-tree-like-directory-structure-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720066530032/0b6e4af9-c116-464d-b62a-0422ac5c9998.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1720066564035/fec2a914-c48d-463e-a080-ef8d1f446441.png
tags: ubuntu, linux

---

You've probably seen images or GitHub repositories showing project folders in a tree-like structure, with sub-directories as branches and files as leaves. These layouts are visually appealing and provide a clear view of the folder structure. They are especially useful for organizing projects by grouping files based on their function or purpose. This makes it easier to understand the project, its composition, module functions, and their respective roles.

While IDEs like VS Code allow us to visualize folder structures, it's not easy to copy or fully view the entire structure. However, using the `tree` package in the Linux command terminal, you can easily view and manage your folder structure.

In this article, let's explore how to install and use the `tree` command to view your folder's structure directly in your terminal. We'll also look at different flag options that let you customize your folder structure output according to your needs. Additionally, we'll explore how to save these structures into `Text`, `HTML`, `XML`, and `JSON` files.

## Installation

You can install the `tree` package from your terminal by following this guide. Make sure to use the correct command for your Linux distribution.

**Debian / Ubuntu / Mint**

```bash
sudo apt-get install tree
```

**RHEL / CentOS / Fedora**

```bash
sudo dnf install tree
```

**Arch Linux**

```bash
sudo pacman -Syu tree
```

**OpenSUSE**

```bash
sudo zypper install tree
```

**Alpine Linux**

```bash
sudo apk add tree
```

## Using the `tree` Command

After successfully installing the `tree` package, you can now use the `tree` command to view the folder structure directly in your terminal.

To see the folder structure of any directory, open the terminal from that directory and simply run the `tree` command:

```bash
tree
```

The output will look something like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1719973227341/50909c0c-c3df-4976-815a-cd52f6b1d831.png align="center")

You can also pass any directory path to see its folder structure. Run the `pwd` command to get the path of any folder, and by passing that path, you can generate the folder structure from anywhere. See the example below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720017452970/dad5ea51-cbea-42c8-8a30-f6b14ceed6ae.png align="center")

## Customize the output:

The `tree` command creates a tree structure of all files, folders, and hidden files. Sometimes, the structure can look very long and cluttered. For example, if you have a `node_modules` folder in your project, you know how many folders and files it contains. Or if you have a `.git` folder, the tree will look huge with unnecessary information. You might wonder if you can customize this. Of course, you can. You can also specify how many nested folders you want to include in the structure, show only folders, and much more. Let's explore how we can achieve this.

### **Displaying all files and directories, including hidden:**

Use the `-a` flag to see all the folders and files, including hidden files:

```bash
tree -a
```

### **Limit the depth of the directory.**

To limit the number of nested directories you want to include in the tree structure, you can specify the number preceded by the `-L` flag. This will ignore folder files nested more deeply than the specified number:

```bash
tree -L 2
```

This command will include up to 2 levels of nested folders and their files in the folder structure.

### **Including only directories:**

With the `-d` flag, you can ignore files and list only the directories in the folder structure:

```bash
tree -d
```

### **Ignoring specific folders:**

If you want to ignore specific folders or files from the structured output, use the `-I` flag followed by the folder or file name. For example, to ignore the `node_modules`, `.git` folder and `.env` file:

```bash
tree -I 'node_modules|.git|.env'
```

You can add more patterns if you want; even deeply nested files or folders can be ignored. Just make sure to specify the file or folder paths correctly.

### **Sorting files by last modification time:**

Using the `-t` flag, you can sort the files by their last modification time. The most recently modified files and directories will appear first within each directory.

```bash
tree -t
```

### **Colorized output:**

By default, the outputs are colorized. If you're not seeing it, you can generate a colorized structure using the `-C` flag, making it easier to distinguish between files and directories:

```bash
tree -C
```

### **Showing the full path for each file:**

With the `-f` flag, you can see the folder structure, where each file and folder is shown in the full path format (relative path):

```bash
tree -f
```

### **Displaying file sizes:**

With the `-s` flag, you can get the file size of each file along with the structure:

```bash
tree -s
```

### **Displaying human-readable file sizes:**

While the above method shows file sizes, they are not in a human-readable format. To make it human-readable, use the `-h` flag:

```bash
tree -h
```

### **Display the owner:**

You can also display the owner of the files using the `-u` flag:

```bash
tree -u
```

You can combine these flags for your desired output. For example, if you want a colorized structure with 2 levels of folder depth, ignoring `node_modules`, `.git`, and `.env` files, with human-readable file sizes, you can achieve it with:

```bash
tree -C -L 2 -I 'node_modules|.git|.env' -h
```

## Saving the Folder Structure:

Using certain commands, you can also save these tree-like structures in text, HTML, JSON, and XML files.

### Saving in a `text` file

To save the output to `output.txt`, you can run the following command:

```bash
tree -0 output.txt
```

### Saving in an `HTML` file

To save the output to `output.html`, use:

```bash
tree -H -o output.html
```

### Saving in an `XML` file

To save the output to `output.xml`, use:

```bash
tree -x -O output.xml
```

### Saving in JSON Format

To save the output to `output.json`, use:

```bash
tree -J -o output.json
```

You can also use different flags along with the output command according to your needs. For example:

```bash
shCopy codetree -C -L 2 -I 'node_modules|.git|.env' -h -o output.txt
```

---

I hope this article helps you learn the `tree` command, customize its output, and save the structure in different formats. I would appreciate any feedback and suggestions for improvement. Thank you!