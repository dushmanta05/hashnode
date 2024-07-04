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

<iframe src="https://app.warp.dev/block/embed/ErEHThUEggAcW9zmEEDKSv" style="width:1922px;height:698px;border:0;overflow:hidden"></iframe>

You can also pass any directory path to see its folder structure. Run the `pwd` command to get the path of any folder, and by passing that path, you can generate the folder structure from anywhere. See the example below:

<iframe src="https://app.warp.dev/block/embed/goQijC6MaO6p4rRMuN0vCT" style="width:1922px;height:698px;border:0;overflow:hidden"></iframe>

## Customize the output:

The `tree` command creates a tree structure of all files, folders, and hidden files. Sometimes, the structure can look very long and cluttered. For example, if you have a `node_modules` folder in your project, you know how many folders and files it contains. Or if you have a `.git` folder, the tree will look huge with unnecessary information. You might wonder if you can customize this. Of course, you can. You can also specify how many nested folders you want to include in the structure, show only folders, and much more. Let's explore how we can achieve this.

### **Displaying all files and directories, including hidden:**

Use the `-a` flag to see all the folders and files, including hidden files:

```bash
tree -a
```

<iframe src="https://app.warp.dev/block/embed/Y4K9XOoNa2hEKBcML0e0SZ" style="width:1922px;height:774px;border:0;overflow:hidden"></iframe>

### **Limit the depth of the directory.**

To limit the number of nested directories you want to include in the tree structure, you can specify the number preceded by the `-L` flag. This will ignore folder files nested more deeply than the specified number:

```bash
tree -L 2
```

This command will include up to 2 levels of nested folders and their files in the folder structure.

<iframe src="https://app.warp.dev/block/embed/V3FOkVR6mpA0SF4rCjURa3" style="width:1922px;height:527px;border:0;overflow:hidden"></iframe>

### **Including only directories:**

With the `-d` flag, you can ignore files and list only the directories in the folder structure:

```bash
tree -d
```

<iframe src="https://app.warp.dev/block/embed/yWoKiTvcpHSiV2rl8py3ng" style="width:1922px;height:470px;border:0;overflow:hidden"></iframe>

### **Ignoring specific folders:**

If you want to ignore specific folders or files from the structured output, use the `-I` flag followed by the folder or file name. For example, to ignore the `node_modules`, `.git` folder and `.env` file:

```bash
tree -I 'node_modules|.git|.env'
```

You can add more patterns if you want; even deeply nested files or folders can be ignored. Just make sure to specify the file or folder paths correctly.

<iframe src="https://app.warp.dev/block/embed/CAJVYZCH2VnEKCAftYVWKv" style="width:1922px;height:641px;border:0;overflow:hidden"></iframe>

### **Sorting files by last modification time:**

Using the `-t` flag, you can sort the files by their last modification time. The most recently modified files and directories will appear first within each directory.

```bash
tree -t
```

<iframe src="https://app.warp.dev/block/embed/lpki50hthn9ONyntGR4RNR" style="width:1922px;height:698px;border:0;overflow:hidden"></iframe>

### **Colorized output:**

By default, the outputs are colorized. If you're not seeing it, you can generate a colorized structure using the `-C` flag, making it easier to distinguish between files and directories:

```bash
tree -C
```

<iframe src="https://app.warp.dev/block/embed/8J7Ozu9DWNnldLEV98Swya" style="width:1922px;height:698px;border:0;overflow:hidden"></iframe>

### **Showing the full path for each file:**

With the `-f` flag, you can see the folder structure, where each file and folder is shown in the full path format (relative path):

```bash
tree -f
```

<iframe src="https://app.warp.dev/block/embed/yBK5oeCHDKLXwvWaEcLC3I" style="width:1922px;height:698px;border:0;overflow:hidden"></iframe>

### **Displaying file sizes:**

With the `-s` flag, you can get the file size of each file along with the structure:

```bash
tree -s
```

<iframe src="https://app.warp.dev/block/embed/ROVMfBGJ3UGQOHo58teVgi" style="width:1922px;height:698px;border:0;overflow:hidden"></iframe>

### **Displaying human-readable file sizes:**

While the above method shows file sizes, they are not in a human-readable format. To make it human-readable, use the `-h` flag:

```bash
tree -h
```

<iframe src="https://app.warp.dev/block/embed/8UFCHTdvYNHJ75NkRbwEKG" style="width:1922px;height:698px;border:0;overflow:hidden"></iframe>

### **Display the owner:**

You can also display the owner of the files using the `-u` flag:

```bash
tree -u
```

<iframe src="https://app.warp.dev/block/embed/0BSRHlvpz87MOCBGCSZiQc" style="width:1922px;height:698px;border:0;overflow:hidden"></iframe>

You can combine these flags for your desired output. For example, if you want a colorized structure with 2 levels of folder depth, ignoring `node_modules`, `.git`, and `.env` files, with human-readable file sizes, you can achieve it with:

```bash
tree -C -L 2 -I 'node_modules|.git|.env' -h
```

<iframe src="https://app.warp.dev/block/embed/2z1OfaPFs501R8QCQm3n21" style="width:1922px;height:470px;border:0;overflow:hidden"></iframe>

## Saving the Folder Structure:

Using certain commands, you can also save these tree-like structures in text, HTML, JSON, and XML files.

### Text File:

To save the output to `output.txt`, you can run the following command:

```bash
tree > output.txt
# or
tree -o output.txt
```

The `output.txt` file will look like this:

```bash
.
├── node_modules
│   ├── module1
│   └── module2
├── output1.txt
├── output.html
├── output.json
├── output.txt
├── output.xml
├── package.json
├── public
│   ├── assets
│   │   └── images
│   │       └── logo.png
│   ├── index.html
│   └── styles.css
├── README.md
└── src
    ├── App.js
    ├── components
    │   ├── common
    │   │   └── Button.js
    │   ├── Footer.js
    │   └── Header.js
    ├── index.js
    └── utils
        └── helpers
            ├── helper1.js
            └── helper2.js

12 directories, 17 files
```

### HTML File:

To save the output to `output.html`, use:

```bash
tree -H . -o output.html
```

The `output.html` will show the structure in HTML format like the below:

```xml
<!DOCTYPE html>
<html>
<head>
 <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
 <meta name="Author" content="Made by 'tree'">
 <meta name="GENERATOR" content="tree v2.1.1 © 1996 - 2023 by Steve Baker, Thomas Moore, Francesc Rocher, Florian Sesser, Kyosuke Tokoro">
 <title>Directory Tree</title>
 <style type="text/css">
  BODY { font-family : monospace, sans-serif;  color: black;}
  P { font-family : monospace, sans-serif; color: black; margin:0px; padding: 0px;}
  A:visited { text-decoration : none; margin : 0px; padding : 0px;}
  A:link    { text-decoration : none; margin : 0px; padding : 0px;}
  A:hover   { text-decoration: underline; background-color : yellow; margin : 0px; padding : 0px;}
  A:active  { margin : 0px; padding : 0px;}
  .VERSION { font-size: small; font-family : arial, sans-serif; }
  .NORM  { color: black;  }
  .FIFO  { color: purple; }
  .CHAR  { color: yellow; }
  .DIR   { color: blue;   }
  .BLOCK { color: yellow; }
  .LINK  { color: aqua;   }
  .SOCK  { color: fuchsia;}
  .EXEC  { color: green;  }
 </style>
</head>
<body>
	<h1>Directory Tree</h1><p>
	<a href="./">.</a><br>
	├── <a href="./node_modules/">node_modules</a><br>
	│   ├── <a href="./node_modules/module1/">module1</a><br>
	│   └── <a href="./node_modules/module2/">module2</a><br>
	├── <a href="./output.html">output.html</a><br>
	├── <a href="./output.txt">output.txt</a><br>
	├── <a href="./package.json">package.json</a><br>
	├── <a href="./public/">public</a><br>
	│   ├── <a href="./public/assets/">assets</a><br>
	│   │   └── <a href="./public/assets/images/">images</a><br>
	│   │   &nbsp;&nbsp;&nbsp; └── <a href="./public/assets/images/logo.png">logo.png</a><br>
	│   ├── <a href="./public/index.html">index.html</a><br>
	│   └── <a href="./public/styles.css">styles.css</a><br>
	├── <a href="./README.md">README.md</a><br>
	└── <a href="./src/">src</a><br>
	&nbsp;&nbsp;&nbsp; ├── <a href="./src/App.js">App.js</a><br>
	&nbsp;&nbsp;&nbsp; ├── <a href="./src/components/">components</a><br>
	&nbsp;&nbsp;&nbsp; │   ├── <a href="./src/components/common/">common</a><br>
	&nbsp;&nbsp;&nbsp; │   │   └── <a href="./src/components/common/Button.js">Button.js</a><br>
	&nbsp;&nbsp;&nbsp; │   ├── <a href="./src/components/Footer.js">Footer.js</a><br>
	&nbsp;&nbsp;&nbsp; │   └── <a href="./src/components/Header.js">Header.js</a><br>
	&nbsp;&nbsp;&nbsp; ├── <a href="./src/index.js">index.js</a><br>
	&nbsp;&nbsp;&nbsp; └── <a href="./src/utils/">utils</a><br>
	&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; └── <a href="./src/utils/helpers/">helpers</a><br>
	&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; ├── <a href="./src/utils/helpers/helper1.js">helper1.js</a><br>
	&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp; └── <a href="./src/utils/helpers/helper2.js">helper2.js</a><br>
<br><br><p>

12 directories, 14 files

</p>
	<hr>
	<p class="VERSION">
		 tree v2.1.1 © 1996 - 2023 by Steve Baker and Thomas Moore <br>
		 HTML output hacked and copyleft © 1998 by Francesc Rocher <br>
		 JSON output hacked and copyleft © 2014 by Florian Sesser <br>
		 Charsets / OS/2 support © 2001 by Kyosuke Tokoro
	</p>
</body>
</html>
```

### XML File:

To save the output to `output.xml`, use:

```bash
tree -x -O output.xml
```

The `output.xml` file will look like this:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<tree>
  <directory name=".">
    <directory name="node_modules">
      <directory name="module1"></directory>
      <directory name="module2"></directory>
    </directory>
    <file name="output.html"></file>
    <file name="output.txt"></file>
    <file name="output.xml"></file>
    <file name="package.json"></file>
    <directory name="public">
      <directory name="assets">
        <directory name="images">
          <file name="logo.png"></file>
        </directory>
      </directory>
      <file name="index.html"></file>
      <file name="styles.css"></file>
    </directory>
    <file name="README.md"></file>
    <directory name="src">
      <file name="App.js"></file>
      <directory name="components">
        <directory name="common">
          <file name="Button.js"></file>
        </directory>
        <file name="Footer.js"></file>
        <file name="Header.js"></file>
      </directory>
      <file name="index.js"></file>
      <directory name="utils">
        <directory name="helpers">
          <file name="helper1.js"></file>
          <file name="helper2.js"></file>
        </directory>
      </directory>
    </directory>
  </directory>
  <report>
    <directories>12</directories>
    <files>15</files>
  </report>
</tree>
```

### JSON File:

To save the output to `output.json`, use:

```bash
tree -J -o output.json
```

The `output.json` file will look like this:

```json
[
  {"type":"directory","name":".","contents":[
    {"type":"directory","name":"node_modules","contents":[
      {"type":"directory","name":"module1"},
      {"type":"directory","name":"module2"}
    ]},
    {"type":"file","name":"output.html"},
    {"type":"file","name":"output.json"},
    {"type":"file","name":"output.txt"},
    {"type":"file","name":"output.xml"},
    {"type":"file","name":"package.json"},
    {"type":"directory","name":"public","contents":[
      {"type":"directory","name":"assets","contents":[
        {"type":"directory","name":"images","contents":[
          {"type":"file","name":"logo.png"}
        ]}
      ]},
      {"type":"file","name":"index.html"},
      {"type":"file","name":"styles.css"}
    ]},
    {"type":"file","name":"README.md"},
    {"type":"directory","name":"src","contents":[
      {"type":"file","name":"App.js"},
      {"type":"directory","name":"components","contents":[
        {"type":"directory","name":"common","contents":[
          {"type":"file","name":"Button.js"}
        ]},
        {"type":"file","name":"Footer.js"},
        {"type":"file","name":"Header.js"}
      ]},
      {"type":"file","name":"index.js"},
      {"type":"directory","name":"utils","contents":[
        {"type":"directory","name":"helpers","contents":[
          {"type":"file","name":"helper1.js"},
          {"type":"file","name":"helper2.js"}
        ]}
      ]}
    ]}
  ]}
,
  {"type":"report","directories":12,"files":16}
]
```

You can also use different flags along with the output command according to your needs. For example:

```bash
tree -C -L 2 -I 'node_modules|.git|.env' -J -o output.json
```

The output will look like this:

```bash
[4.0K]  .
├── [   0]  output.txt
├── [   0]  package.json
├── [4.0K]  public
│   ├── [4.0K]  assets
│   ├── [   0]  index.html
│   └── [   0]  styles.css
├── [   0]  README.md
└── [4.0K]  src
    ├── [   0]  App.js
    ├── [4.0K]  components
    ├── [  18]  index.js
    └── [4.0K]  utils

6 directories, 7 files
```

---

I hope this article helps you learn the `tree` command, customize its output, and save the structure in different formats. I would appreciate any feedback and suggestions for improvement. Thank you!