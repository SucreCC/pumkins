---
title: Hexo deploy
sticky: true
date: 2023-12-25 20:02:00
layout: categories
categories:
- [Blog]
tags:
- Sucre
- Hexo
- Configuration
- deploy
---

Deployments for pumkins



<!-- more -->

# Adjust the timezone

``` Bash
yum -y install ntpdate
timedatectl set-timezone European/Dbulin #set EU/Dub
ntpdate time.nist.gov
timedatectl list-timezones # list all timezones
```

# Install aaPanel


``` Bash
yum install -y wget && wget -O install.sh http://www.aapanel.com/script/install_6.0_en.sh && bash install.sh
```

# Add website
After install aaPanel, we need login in aaPanel, if not find the link and account use below command.
``` Bash
bt 14
```
Website --> Add site --> fill Domain name, if you need SSL you can also choose "Apply for SSL".

![img.png](/assets/blog/img1.png){height="500" width="800"}
 

# Install Git, Node.js and Npm

``` Bash
#git
yum install git

# node.js
curl -sL https://rpm.nodesource.com/setup_12.x | sudo bash -
sudo yum install nodejs
```

# Clone code from github to a folder in your server

``` Bash
makedir /www/source_code

cd /www/source_code

git clone xxxx 

cd your_blog

npm install hexo-cli -g

npm install

hexo g
```

# Move the static files to your website folder

move the file from public folder to "/www/wwwroot/your_website folder'


# visit your domain or ip without port number


# Create a Corn in aaPanel

![img.png](/assets/blog/img2.png)



```
cd /www/source_code/your_blog
git pull
hexo g
cd public
rm -rf  /www/wwwroot/your_website/*
mv ./*  /www/wwwroot/your_website/
```
