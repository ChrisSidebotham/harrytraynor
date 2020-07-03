---
layout: post
title:  "Installing Windows Apps through a Package Manager"
date:   2020-03-12 18:00:00 +0000
categories: Powershell Intune
---
If you are familiar with operating systems like Ubuntu or RHEL, you have probably used something like the following to install an application. 

```powershell
apt install git
```

This has many advantages, some being quickly updating and managing all the applcaitions on a system. 

Now Windows has had many different tools over the years to install applications, whether thats from an end user perspective or orchestrated from an administrator. Apple has had tools like Homebrew and u untill recently I didnt realise Windows has one too.

**Enters Chocolatey**

![Chocolatey Logo](/assets/chocolatey.png)

Installing Chocolatey is as easy as running this bit of Powershell.

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force;
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072;
iwr https://chocolatey.org/install.ps1 -UseBasicParsing | iex
```

Once that has finished doing its thing, you should be able to run commands like below to install apps on Windows with speed!

```powershell
choco install vlc -y
```

The extent of how this can be used is great for remote management too with InTune on Azure for example. This [link](https://www.prajwaldesai.com/automate-intune-application-deployment-using-chocolatey/) shows you how to deploy through InTune using this method and how easy it is to do that.

**Disclaimer**: I would say hopefully I have been living under a rock and I just haven't heard about this before. But a lot of places I visit don't take advantage of it. Fingers crossed!
