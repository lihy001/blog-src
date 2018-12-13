---
title: title #文章標題
date: 2016-06-01 23:47:44 #文章生成時間
categories: [test] #文章分類目錄 可以省略
type: categories
tags: #文章標籤 可以省略
     - 标签1
     - 标签2
description: #你對本頁的描述 可以省略
---

### CentOS7配置静态IP后出现2个IP



#### 一、问题出现

   使用VM装系统CentOS-7-x86_64-Minimal-1804，网络连接方式为桥接方式，

   配置/etc/sysconfig/network-script/ifcfg-ens33

``` TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=static
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=no
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6_ADDR_GEN_MODE=stable-privacy
NAME=ens33
UUID=7437d24d-6261-4669-b966-ac0979ed2038
DEVICE=ens33
ONBOOT=yes
ZONE=public
IPADDR0=10.82.17.165
GATEWAY=10.82.17.1
NETMASK=255.0.0.0
DNS1=10.82.1.4
DNS2=10.82.1.6
```

 执行` ip addr `  出现

![](C:\Users\lihy\Pictures\29381f30e924b89982bda97062061d950b7bf6f1.jpg)



#### 二、解决问题

网络查找，是由于NetWorkManager 和 network同时对网卡作用导致的，

停止NetWorkManager， ` systemctl stop NetWorkManager `

禁止NetWorkManager自启, ` systemctl disable NetworkManager `

执行 ` ip addr `，上图中的ens33只有1个Ip了

