---
title: Hexo deploy
sticky: true
date: 2023-12-25 20:02:00
layout: categories
categories:
- [Blog]
tags: 
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

Website --> Add site --> fill Domain name, if you need SSL you can also choose "Apply for SSL"

![img.png](/assets/blog/img1.png){height="500" width="800"}

