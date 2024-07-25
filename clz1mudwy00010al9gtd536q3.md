---
title: "How to Turn Off Lock Screen Blur Effect in Ubuntu: A Step-by-Step Guide"
seoTitle: "Disable Lock Screen Blur in Ubuntu"
seoDescription: "Disable Ubuntu lock screen blur with a simple GNOME extension setup. Follow our easy step-by-step guide"
datePublished: Wed Jul 24 2024 18:30:00 GMT+0000 (Coordinated Universal Time)
cuid: clz1mudwy00010al9gtd536q3
slug: how-to-turn-off-lock-screen-blur-effect-in-ubuntu-a-step-by-step-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1721933580868/24fa7f42-d472-4d40-9018-8fdaa1b1c520.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1721933628509/a33527d0-7d2f-4b04-8fed-55438003cb36.png
tags: ubuntu, gnome, gnome-customize

---

Hello, Ubuntu users! As you know, the default setting on Ubuntu blurs the lock screen, giving it a modern look. However, if you want a clear view of the lock screen wallpaper, this short article will guide you on how to remove the blur effectively and quickly.

Before removing the blur effect, the image below shows how my blurred lock screen wallpaper looks now.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721933014645/3f4d18f3-d776-481f-836e-f9eaf60bd566.png align="center")

To remove the blur effect, we'll use a GNOME extension. So, before getting started, let's install the GNOME extension manager first with the following command:

```bash
sudo apt install gnome-shell-extensions gnome-shell-extension-manager
```

After installing the GNOME extensions manager, open it and search for the **Control Blur on Lock Screen** extension package. Download it. See the image below for reference.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721932243946/5178bb5f-d26d-4be7-b5d0-6034023efae9.png align="center")

After installation, go to the Installed tab and enable the package we downloaded. Then, click on the settings of the package. It should look something like this:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721932535649/2d345309-8f01-4141-af31-59ca63670af2.png align="center")

Now, here you can adjust the **Adjust Sigma** option to control the blur effect on the lock screen. If you want to completely remove the blur, set the value to 0.

After setting this up, just lock the screen, and you'll see it works immediately.

Now let's see how my wallpaper looks without the blur. Here's the image:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1721933181013/e90e14a8-a5b6-4e02-81bc-315fb45e8c09.png align="center")

---

I hope this article helped you set up your lock screen wallpaper without the blur effect. Please provide any feedback or suggestions for improvement. Thanks!