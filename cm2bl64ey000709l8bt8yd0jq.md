---
title: "Quick Guide: Set Up Golang on Your Ubuntu and Debian System"
seoTitle: "Golang Setup on Ubuntu & Debian"
seoDescription: "Learn how to set up Golang on Ubuntu/Debian systems with this easy step-by-step guide"
datePublished: Wed Oct 16 2024 08:04:20 GMT+0000 (Coordinated Universal Time)
cuid: cm2bl64ey000709l8bt8yd0jq
slug: quick-guide-set-up-golang-on-your-ubuntu-and-debian-system
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1729065779008/fe682c89-3e28-483f-8494-7b073c88769d.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1729065838440/d928badc-a9ce-4f92-a7de-37610074686d.png
tags: ubuntu, linux, go, golang, debian

---

**Go** or **Golang** is an open-source, high-level programming language created at Google by *Robert Griesemer*, *Rob Pike*, and *Ken Thompson*. Recently, it has become very popular for building scalable applications due to its simplicity, efficiency, and scalability. In this article, let's explore how to install the Golang package on Ubuntu/Debian systems.

We can install *Golang* in two ways: first, by manually installing the latest official package from the [Go](https://go.dev/dl/) website, and second, through Debian’s *apt* package manager. I recommend manually installing the latest package because the *apt* package may not always provide the newest version.

### Manual Installation:

To manually install the latest version (or any other version) of *Go*, follow these steps:

#### Remove any existing Go installation:

```bash
sudo rm -rf /usr/local/go
```

#### Download the latest binary package:

Next, download the latest *Go* package using the following command. I'm downloading the latest version available as of now (go 1.23.2) for x86-64. You can download a different version by specifying the version you need according to your device specs from the [official Go download](https://go.dev/dl/) page. Just replace the version name along in the command.

```bash
wget https://go.dev/dl/go1.23.2.linux-amd64.tar.gz
# wget https://go.dev/dl/<version>
```

#### Extract the archive:

Next, we need to extract the downloaded *Go* binary to the `usr/local/` folder. We can do this with the following command:

```bash
sudo tar -C /usr/local -xzf go1.23.2.linux-amd64.tar.gz
```

#### Add Go to the PATH:

Now we need to add *Go* to the *PATH*, so the system can recognize *Go* commands from any directory on our device. We can add it to the *PATH* with the following command:

```bash
export PATH=$PATH:/usr/local/go/bin
```

#### Apply the changes:

Next, to apply all these changes, run the following command:

```bash
source ~/.profile
```

#### Verify Installation:

Now we can check if *Go* has been installed by verifying the version with the following command:

```bash
go version
```

This command should display the *Go* version we installed.

### Install with the apt Package:

You can also install *Go* using the apt package, though this method may not always provide the latest version of *Go*. However, one advantage of this method is that you don't have to update manually, as it will be handled automatically through the `apt` repository.

#### Check available Go version:

First, check which version of *Go* is available with the `apt` package using the following command:

```bash
apt show golang
```

Currently, the apt `golang` package is at version 1.22, as shown in the image below. This version is not the latest, as mentioned earlier.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1729060167538/62cf8795-269a-4945-904f-17f590fc478b.png align="center")

#### Install Go:

Next, install the *Go* package with the following command:

```bash
sudo apt install golang
```

#### Verify installation:

Run the following command to check the installed *Go* version:

```bash
go version
```

---

### Creating Your First Program in Go:

After successfully installing *Go*, let's create a "Hello, World!" program to ensure *Go* runs correctly.

Create a `hello.go` file with the following code:

```go
package main
import "fmt"

func main() {
    fmt.Println("Hello, World!")
}
```

Next, in the terminal, run the file with:

```bash
go run hello.go
```

If *Go* is installed correctly, you'll see the output "Hello, World!"

---

And voilà! You’ve successfully installed *Go* on your system.

I hope this guide helped you install *Go* on your Ubuntu/Debian device. If you have any questions or suggestions for improvement, feel free to leave a comment below. Thank you for reading!