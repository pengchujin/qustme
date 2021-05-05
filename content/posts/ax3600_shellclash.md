---
title: "AX3600 ShellClash 教程｜官方固件使用代理"
date: 2021-05-05T15:32:18+08:00
draft: false
---

小米 AX3600 采用的是高通 IPQ8071A 4核心 1.4GHz A53 的 CPU，外加上双核主频高达 1.7GHz 的 NPU，这让这款路由器的跑「加密解密」类的代理性能特别特别的好。开启 SSH 和 安装 ShellClash 都不会影响固件正常的更新升级，也会影响官方固件的功能， 如果你有这方面的需求会是非常棒的选择。<!--more-->

这个教程会教你解锁小米 AX3600 的 SSH，并使用 ShellClash「基于命令行的 Clash」进行代理。

该教程主要参考了：

* [[AX3600] 小米ax3600获取root权限【简单快速】【修复丢ssid】](https://www.right.com.cn/forum/thread-4046020-1-1.html)
* [在路由器上安装及使用 ShellClash 的教程](https://juewuy.github.io/post/clash-for-miwifi-an-zhuang-ji-shi-yong-jiao-cheng/)

你基本不需要任何准备，有台能上网的电脑甚至手机都可以，最好用网线连接到小米 AX3600 路由器。

提前下载好文件（旧版固件和脚本）：链接: https://pan.baidu.com/s/15QsNvM9qwgTVtk8zF843eA 提取码: 8rcu

## 开启 AX3600 SSH

### 降级

下载 AX3600 1.0.17 的固件，在路由器后台选择本地「固件升级」，就会清除现有数据降级，等待降级完成后重新设置好路由器即可。

### 获取后台 STOK

![截屏2021-05-03 下午4.43.49](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-03%20%E4%B8%8B%E5%8D%884.43.49.jpg)

登陆小米路由器后台后，浏览器地址栏 stok= 后面的一段内容即是（选中部分），准备好备用。



### 获取 SSH

```
http://192.168.31.1/cgi-bin/luci/;stok=<STOK>/api/misystem/set_config_iotdev?bssid=Xiaomi&user_id=longdike&ssid=-h%3B%20nvram%20set%20ssh_en%3D1%3B%20nvram%20commit%3B%20sed%20-i%20's%2Fchannel%3D.*%2Fchannel%3D%5C%22debug%5C%22%2Fg'%20%2Fetc%2Finit.d%2Fdropbear%3B%20%2Fetc%2Finit.d%2Fdropbear%20start%3B
```

将 <STOK>  替换为上一步的值，替换完成后复制到浏览器打开。

### 修改默认 SSH 密码为 admin

```
http://192.168.31.1/cgi-bin/luci/;stok=<STOK>/api/misystem/set_config_iotdev?bssid=Xiaomi&user_id=longdike&ssid=-h%3B%20echo%20-e%20'admin%5Cnadmin'%20%7C%20passwd%20root%3B
```

将 <STOK>  替换为上上一步的值，替换完成后复制到浏览器打开。

### 备份

现在应该可以通过 ssh 连接到 小米 AX3600 了，终端里执行（密码是 admin）

```
ssh root@192.168.31.1
```

在小米 AX3600 上执行

```
mkdir /tmp/syslogbackup/
dd if=/dev/mtd9 of=/tmp/syslogbackup/mtd9
```

浏览器请求该地址下载备份 http://192.168.31.1/backup/log/mtd9

### 固化 SSH

在电脑上将下载好的 fuckax3600 上传到小米 AX3600 的根目录（fuckax3600 路径下执行） 

```
scp fuckax3600 root@192.168.31.1:/tmp
```

然后在小米 AX3600 上执行

```
/tmp/fuckax3600 unlock
```

系统会自动重启

SSH 重新连接上小米 AX3600 后，执行

```
/tmp/fuckax3600 hack
/tmp/fuckax3600 lock
```

这会设置永久的 ssh、telnet、uart 权限，也会计算出默认的秘密，记得保存

备注：如果升级后丢失 SSH 权限，你也可以 telnet 连接上 AX3600 后执行，即可恢复 SSH。

```
sed -i 's/channel=.*/channel="debug"/g' /etc/init.d/dropbear
/etc/init.d/dropbear start
```

## 安装使用 ShellClash

SSH 连接上小米 AX3600 执行安装

```
sh -c "$(curl -kfsSl https://cdn.jsdelivr.net/gh/juewuy/ShellClash@master/install.sh)" && source /etc/profile &> /dev/null
```

安装完成后 clash 命令即可进行配置，Clash 后台可以通过 [http://clash.razord.top](http://clash.razord.top/) 或者 [https://yacd.haishan.me](https://yacd.haishan.me/) 或者[http://app.tossp.com](http://app.tossp.com/)  进行管理调配。



## 总结

得益于小米 AX3600 超强的 CPU + NPU 组合，跑代理速度是真不错。ShellClash 这种方案虽然没有图形化 UI 操作方便，但好在不需要刷麻烦也不稳定的 openwrt 固件，直接小米官方固件也能享受到网络「加速」的福利。