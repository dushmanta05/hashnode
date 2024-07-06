---
title: "How to View, Customize and Save Tree-Like Directory Structure in Linux"
seoTitle: "View, Customize and Save Linux Directory Trees"
seoDescription: "Learn how to view, customize, and save tree-like directory structures in Linux using the `tree` command"
datePublished: Thu Jul 04 2024 04:16:15 GMT+0000 (Coordinated Universal Time)
cuid: cly6r87vo000108lebez9gq33
slug: how-to-view-customize-and-save-tree-like-directory-structure-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1720110170770/faa6fab3-a008-4de5-81c1-92911455d2a2.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1720110192199/49bb44c2-c459-44bc-a4de-71c0379528e9.png
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
# or
tree /path/name
```

The output will look something like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720274494263/ce0f0a4c-4b1f-4b7f-86e0-5f9d38243b85.png align="center")

You can also pass any directory path to see its folder structure. Run the `pwd` command to get the path of any folder, and by passing that path, you can generate the folder structure from anywhere. See the example below:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720274584418/18ea6a9c-642e-4753-b9f2-dcecdc2b7b23.png align="center")

## Customize the output:

The `tree` command creates a tree structure of all files, folders, and hidden files. Sometimes, the structure can look very long and cluttered. For example, if you have a `node_modules` folder in your project, you know how many folders and files it contains. Or if you have a `.git` folder, the tree will look huge with unnecessary information. You might wonder if you can customize this. Of course, you can. You can also specify how many nested folders you want to include in the structure, show only folders, and much more. Let's explore how we can achieve this.

### **Displaying all files and directories, including hidden ones:**

Use the `-a` flag to see all the folders and files, including hidden files:

```bash
tree -a
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720274716721/df099132-17fe-4c64-84d2-c8aa532c8c2d.png align="center")

### **Limit the depth of the directory.**

To limit the number of nested directories you want to include in the tree structure, you can specify the number preceded by the `-L` flag. This will ignore folder files nested more deeply than the specified number:

```bash
tree -L 2
```

This command will include up to 2 levels of nested folders and their files in the folder structure.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720274888451/dcc8ee19-cd6b-4dcf-993c-b5368bdb3b8a.png align="center")

### **Including only directories:**

With the `-d` flag, you can ignore files and list only the directories in the folder structure:

```bash
tree -d
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720274999648/e33ed8b1-07ec-485d-a3d9-568d53d9733b.png align="left")

### **Ignoring specific folders:**

If you want to ignore specific folders or files from the structured output, use the `-I` flag followed by the folder or file name. For example, to ignore the `node_modules`, `.git` folder and `.env` file:

```bash
tree -I 'node_modules|.git|.env'
```

You can add more patterns if you want; even deeply nested files or folders can be ignored. Just make sure to specify the file or folder paths correctly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720275125143/a406829b-e76e-4b7d-9301-1170e7864436.png align="center")

### **Sorting files by last modification time:**

Using the `-t` flag, you can sort the files by their last modification time. The most recently modified files and directories will appear first within each directory.

```bash
tree -t
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720275218960/43adeadf-bbda-4908-b3b2-71281f0388e0.png align="center")

### **Colorized output:**

By default, the outputs are colorized. If you're not seeing it, you can generate a colorized structure using the `-C` flag, making it easier to distinguish between files and directories:

```bash
tree -C
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720275306109/a8a6ed91-f18a-4219-95c9-9b1a822f548a.png align="center")

### **Showing the full path for each file:**

With the `-f` flag, you can see the folder structure, where each file and folder is shown in the full path format (relative path):

```bash
tree -f
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720276089377/dc13b58f-26d3-411f-8c22-99865bfda12b.png align="center")

### **Displaying file sizes:**

With the `-s` flag, you can get the file size of each file along with the structure:

```bash
tree -s
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720276686549/0d3151c8-dd16-482f-8995-367c7f9981ec.png align="center")

### **Displaying human-readable file sizes:**

While the above method shows file sizes, they are not in a human-readable format. To make it human-readable, use the `-h` flag:

```bash
tree -h
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720276662329/a65cfa3d-e996-427e-94a4-8d0f2a663a34.png align="center")

### **Display the owner:**

You can also display the owner of the files using the `-u` flag:

```bash
tree -u
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720276639519/69067f65-a329-496d-b019-1f7d11899130.png align="center")

You can combine these flags for your desired output. For example, if you want a colorized structure with 2 levels of folder depth, ignoring `node_modules`, `.git`, and `.env` files, with human-readable file sizes, you can achieve it with:

```bash
tree -C -L 2 -I 'node_modules|.git|.env' -h
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1720276612513/15d7e58d-0f8e-4086-a718-c0e5cb5bce3d.png align="center")

## Saving the Folder Structure:

Using certain commands, you can also save these tree-like structures in text, HTML, JSON, and XML files.

### Text File:

To save the output to `output.txt`, you can run the following command:

```bash
tree > output.txt
# or
tree -o output.txt
```

### HTML File:

To save the output to `output.html`, use:

```bash
tree -H . -o output.html
```

### XML File:

To save the output to `output.xml`, use:

```bash
tree -x -O output.xml
```

### JSON File:

To save the output to `output.json`, use:

```bash
tree -J -o output.json
```

You can also use different flags along with the output command according to your needs. For example:

```bash
tree -C -L 2 -I 'node_modules|.git|.env' -J -o output.json
```

---

I hope this article helps you learn the `tree` command, customize its output, and save the structure in different formats. I would appreciate any feedback and suggestions for improvement. Thank you!