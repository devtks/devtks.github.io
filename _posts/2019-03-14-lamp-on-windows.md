---
layout: post
title: PHP Dev Environment LAMP stack (Linux, Apache, MySql, PHP) on Windows Tuto
gh-repo: devtks/devtks.github.io
gh-badge: [star, fork, follow]
tags: [tuto]
---

When working on Windows it might be challenging to find or setup a good dev environment or project that requires stack like LAMP. This tutorial will show you how to quickly setup a full virtual machine containing all you need for your lamp stack.

Why not XAMPP?

- Shipped with its unchangeable php version
- Hard to work on multiple project requiring different php version
- Every devs dont share the same dev env
- Cant be share/distribute between devs
- xdebug act very weird on xampp sometime

## Requirements

You need multiple tools on your machine

- VirtualBox( prefered) but can work with VMware too (https://www.virtualbox.org/)
- Vagrant (which is a wrapper to virtual box/vmware) https://www.vagrantup.com/
- HeidiSQL\* (free mysql client not as heavy as workbench) https://www.heidisql.com/download.php
- Git\* (https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- Putty (https://www.putty.org/)
  \*optional

**What it will give you?**
Ability to download and launch on the fly different machines containing all the environment you need pre-setup

For example on my machine right now i have two boxes (LAMP env)

![img](/img/tuto-lamp/my-machines.png)

> Warning: Before you start make sure you shut down any running instance of XAMPP

This tuto is using scotch/box because it appears to be the most downloaded and easy one to setup

![img](/img/tuto-lamp/scotch-box.png)

## Steps:

- Install all the tools above
- Create a folder where you are going to put work on your project (ex: c:\MyPhpProjects)
- Navigate to that folder via cmd and enter the following command (my project being the name of the project ex: learnsphere)

```
git clone https://github.com/scotch-io/scotch-box my-project
```

- Navigate into your new folder

![img](/img/tuto-lamp/cd-into-folder.png)

```
vagrant up
```

- This should take a little while (it actually download the box for you and starting it)

- To have any realtime feedback you can open your virtual box and you should see your machine being added and running

- ![real-time](/img/tuto-lamp/real-time.png)

* If everything works you should be able to navigate to http://192.168.33.10

- You have now a full LAMP/LEMP stack running on your machine
- Navigate to your folder and you will see different docs and config files (all your project files goes into public you will work into that)

![code-location](/img/tuto-lamp/code-location.png)

## Connection to MySQL

**Step**

- Open HeidiSQl (indicate your putty path for ssh)

![heidiSql](/img/tuto-lamp/heidiSql.png)

- ![db-info](../img/tuto-lamp/db-info.png)

Then you can create db and do whatever you want

![dbs-list](../img/tuto-lamp/dbs-list.png)

Usefull links:
https://box.scotch.io/docs/ (box the tuto was based from)
https://app.vagrantup.com/boxes/search (all the possible boxes available to us)
https://www.vagrantup.com/docs/cli/ (vagrant command)
