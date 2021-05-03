---
title: "红米 AX6 刷 openwrt 教程｜软路由杀手来了🥷"
date: 2021-05-03T18:55:43+08:00
draft: false
---

# 红米 AX6 刷 openwrt 教程｜软路由杀手来了🥷

我用过很多路由器（有时候必须得装一下才能让人信服），比如最近热门的 NanoPi R2s、R4S、斐讯 N1、AX86U，最近甚至一直都是用的 Mac mini 安装 Surge Mac 版本来当软路由。但我必须得说红米 AX6 无论是官方固件作为 AP Mesh Wi-Fi 的信号还是刷 openwrt 处理「网络数据」都是性价比非常非常高的选择，这方面性能上其实完全不输软路由。<!--more-->

该教程主要参考：

[li4621180](https://www.right.com.cn/forum/space-uid-191571.html)：https://www.right.com.cn/forum/thread-4111331-1-1.html

[yyjdelete](https://www.right.com.cn/forum/space-uid-90558.html)：https://www.right.com.cn/forum/forum.php?mod=viewthread&tid=4060726&extra=page%3D1%26filter%3Dtypeid%26typeid%3D64

## 警告⚠️

* 如果你操作错误等情况可能会变砖得返厂，我不会对此负责

* 目前教程也会比较麻烦，你旁边有**得有一台别的 openwrt 路由器**作为辅助

* 固件不是特别稳定 Wi-Fi 因为驱动原因暂时比官方的要差不少，如果你是觉得你是新手可以再等等
* 暂时还没刷会官方的教程（以后肯定会有）

## 准备

一台电脑（Mac Windows 均可）

另外一台已经是 openwrt 的路由器（打开了 SSH，用来当服务器）

Windows 需要安装 [Putty](https://www.putty.org/) 和 [WinSCP](https://winscp.net/eng/download.php)｜Mac 使用命令行即可

## 第一步｜降级并恢复出厂设置

![截屏2021-05-03 下午12.44.44](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-03%20%E4%B8%8B%E5%8D%8812.44.44.jpg)

[红米 ax6 1.0.16 固件](http://cdn.cnbj1.fds.api.mi-img.com/xiaoqiang/rom/ra69/miwifi_ra69_firmware_a7244_1.0.16.bin) [红米 ax6 1.0.18 固件](http://cdn.cnbj1.fds.api.mi-img.com/xiaoqiang/rom/ra69/miwifi_ra69_firmware_45a77_1.0.18.bin)，下载其中一个即可（推荐下载 1.0.16 ）；打开路由器后台选择 系统升级—手动升级—然后选择下载好的固件，等待重启。

然后最好再恢复下出厂设置。

## 第二步｜准备 openwrt 服务

![IMG_1734](https://oss.qust.me/img/IMG_1734.JPG)

我这里准备的是一台刷了 openwrt 的 k2p，只需要接上电源有 Wi-Fi 信号即可（后续会让红米 AX 6 Wi-Fi 连接上此 openwrt 路由器）。 

### 创建 lua 文件

![截屏2021-05-03 下午4.04.00](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-03%20%E4%B8%8B%E5%8D%884.04.00.jpg)

ssh 连接上 openwrt 的路由器，然后使用 nano 创建 /usr/lib/lua/luci/controller/admin/xqsystem.lua 这样一个文件。

```
nano /usr/lib/lua/luci/controller/admin/xqsystem.lua
```

如果你的系统没有 nano 你可以使用 vi 或 vim 

```
vim /usr/lib/lua/luci/controller/admin/xqsystem.lua
```

文件内容填写下面的保存即可。

```
module("luci.controller.admin.xqsystem", package.seeall)


function index()
    local page   = node("api")
    page.target  = firstchild()
    page.title   = ("")
    page.order   = 100
    page.index = true
    page   = node("api","xqsystem")
    page.target  = firstchild()
    page.title   = ("")
    page.order   = 100
    page.index = true
    entry({"api", "xqsystem", "token"}, call("getToken"), (""), 103, 0x08)
end

local LuciHttp = require("luci.http")

function getToken()
    local result = {}
    result["code"] = 0
    result["token"] = "; nvram set ssh_en=1; nvram commit; echo -e 'admin\nadmin' | passwd root; sed -i 's/channel=.*/channel=\"debug\"/g' /etc/init.d/dropbear; /etc/init.d/dropbear start;"
    LuciHttp.write_json(result)
end
```

输入完成后你可以 cat /usr/lib/lua/luci/controller/admin/xqsystem.lua  检查一下。

![截屏2021-05-03 下午4.08.15](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-03%20%E4%B8%8B%E5%8D%884.08.15.jpg)

### 修改该 openwrt 路由器的 Lan 地址，并关闭 DHCP

![截屏2021-05-03 下午4.16.28](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-03%20%E4%B8%8B%E5%8D%884.16.28.jpg)

登陆 openwrt 的后台，在 网络-接口-Lan 选择编辑，IPv4 地址修改为 169.254.31.1。

![截屏2021-05-03 下午4.18.02](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-03%20%E4%B8%8B%E5%8D%884.18.02.jpg)

在 DHCP 服务器 — 高级设置里取消勾选 动态 DHCP（也就是关闭 DHCP，这会让你需要手动设置网络 IP 才能连接上该 openwrt 路由器）然后**保存 并 应用**。然后重启该 openwrt 路由器

### 验证

![截屏2021-05-03 下午4.27.07](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-03%20%E4%B8%8B%E5%8D%884.27.07.jpg)

想再次连接到 openwrt 路由器，你需要讲电脑的网络 Wi-Fi 设置为手动 IPv4 （IP 地址填写：169.254.31.3；子网掩码：255.255.255.0；路由器：169.254.31.1）。

然后浏览器访问：http://169.254.31.1/cgi-bin/luci/api/xqsystem/token，如果得到下面的结果，则证明你设置成功。

![截屏2021-05-03 下午4.33.46](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-03%20%E4%B8%8B%E5%8D%884.33.46.jpg)

## 第三步｜红米 AX 6 破解 SSH

将电脑的网络设置回自动获取 DHCP，然后最好将电脑用网线和 红米 AX6 连接（因为红米 ax6 解锁 Wi-Fi 可能会掉线）。

### 获取后台 STOK

![截屏2021-05-03 下午4.43.49](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-03%20%E4%B8%8B%E5%8D%884.43.49.jpg)

登陆小米路由器后台后，浏览器地址栏 stok= 后面的一段内容即是（选中部分），准备好备用。

### 第一次请求

```
http://192.168.31.1/cgi-bin/luci/;stok=<STOK>/api/misystem/extendwifi_connect?ssid={SSID}&password={Wi-Fi密码}
```

* \<STOK> 替换为上面的值

* {SSID} 替换为 openwrt 路由器的 Wi-Fi 名

* {Wi-Fi密码} 替换为 openwrt 路由器的 Wi-Fi 密码

<> 和 {} 均需要替换

我的替换后如下（我的 Wi-Fi 没有密码，你的如果有秘密填上密码即可）

```
http://192.168.31.1/cgi-bin/luci/;stok=b3ee3b3d1baa28c0b208a46a47c84a03/api/misystem/extendwifi_connect?ssid=OPENWRT_DEE_5G&password=
```

将替换好的值复制到浏览器请求，如果显示 code 0 则成功。

（贴图）

<!--显示1646的请检查下第一步的DHCP是否关闭,  1619的请检查第一步IP是否设置正确或者路由器B下仍有其他设备, 1655的请再来一次, 有小概率会连接失败
如果一直失败请改下路由器B的SSID/密码/信道/换着连下2.4G和5G(不要开二合一)-->

### 第二次请求

```
http://192.168.31.1/cgi-bin/luci/;stok=<STOK>/api/xqsystem/oneclick_get_remote_token?username=xxx&password=xxx&nonce=xxx
```

\<STOK> 替换为小米路由器后台获得的值即可，其它均不用改变

将替换好的值复制到浏览器请求，如果显示 code 0 则成功

贴图



## 第四步｜验证 SSH 并备份

ssh 连接小米路由器**ssh root@192.168.31.1** 密码是 admin，如果能 ssh 连接上则证明上述步骤均完成。

链接成功后进行备份

```
mkdir /tmp/syslogbackup/
dd if=/dev/mtd9 of=/tmp/syslogbackup/mtd9
```

浏览器请求该地址下载备份

http://192.168.31.1/backup/log/mtd9

## 第五步｜刷入 openwrt 固件

### 下载固件备用

下载固件：https://pan.baidu.com/s/1NVDSw79g4V18JpucMsBMkw
提取码：fmaw

### ssh 连接 红米 ax  设置env

ssh 连接上后复制👇下面执行

```
nvram set flag_last_success=0
nvram set flag_boot_rootfs=0
nvram set flag_boot_success=1
nvram set flag_try_sys1_failed=0
nvram set flag_try_sys2_failed=0
nvram set boot_wait=on
nvram set uart_en=1
nvram set telnet_en=1
nvram set ssh_en=1
nvram commit
```

### scp 固件 qsdk 固件并刷入

scp 下载好的  xiaomimtd12.bin 到 红米 AX6 的 /tmp 下面

```
scp xiaomimtd12.bin root@192.168.31.1:/tmp
```

并在红米 AX6 上执行

```
mtd write /tmp/xiaomimtd12.bin rootfs
```

断电重启红米 AX6，**此时红米 AX 6 的后台地址已经变为 192.168.1.1**

### 重新分区

scp 下载好的  a6minbib.bin 到 红米 AX6 的 /tmp 下面

```
scp a6minbib.bin root@192.168.1.1:/tmp
```

并在 红米AX6 上执行

```
. /lib/upgrade/platform.sh
switch_layout boot; do_flash_failsafe_partition a6minbib "0:MIBIB
```

拔电源重启路由器

### openwrt刷入到rootfs_1分区

scp 下载好的 openwrt-ipq807x-generic-xiaomi_ax6-squashfs-nand-factory.bin 到 红米 AX6 的 /tmp

```
scp openwrt-ipq807x-generic-xiaomi_ax6-squashfs-nand-factory.bin root@192.168.1.1:/tmp
```

在红米 AX6 上执行刷入

```
ubiformat /dev/mtd13 -y -f /tmp/openwrt-ipq807x-generic-xiaomi_ax6-squashfs-nand-factory.bin
fw_setenv flag_last_success 1
fw_setenv flag_boot_rootfs 1
```

红米 AX6 执行命令重启

```
reboot
```

重启后完成，系统应该已经是 openwrt 系统了。

## one more thing ｜安装 Clash

该固件并不会自带 clash ，或别的代理软件，需要手动安装。

```
wget https://github.com/vernesong/OpenClash/releases/download/v0.40.7-beta/luci-app-openclash_0.40.7-beta_all.ipk
opkg install luci-app-openclash_0.40.7-beta_all.ipk
```

因为 libcap 安装比较麻烦，所以上面 openclash 安装的是去年10月初的版本。

**如果你想安装最新**的可以修改

vim /etc/opkg.conf 将 /etc/opkg.conf 的内容修改为以下内容

```
dest root /
dest ram /tmp
lists_dir ext /var/opkg-lists
option overlay_root /overlay
#option check_signature
arch all 100
arch aarch64_cortex-a53_neon-vfpv4 200
arch aarch64_cortex-a53 300
```

 vim /etc/opkg/distfeeds.conf 将 /etc/opkg/distfeeds.conf 的内容修改为以下内容

```
src/gz openwrt_19.07_base https://mirrors.cloud.tencent.com/lede/releases/19.07-SNAPSHOT/packages/aarch64_cortex-a53/base/
src/gz openwrt_19.07_freifunk https://mirrors.cloud.tencent.com/lede/releases/19.07-SNAPSHOT/packages/aarch64_cortex-a53/freifunk/
src/gz openwrt_19.07_luci https://mirrors.cloud.tencent.com/lede/releases/19.07-SNAPSHOT/packages/aarch64_cortex-a53/luci/
src/gz openwrt_19.07_packages https://mirrors.cloud.tencent.com/lede/releases/19.07-SNAPSHOT/packages/aarch64_cortex-a53/packages/
src/gz openwrt_19.07_routing https://mirrors.cloud.tencent.com/lede/releases/19.07-SNAPSHOT/packages/aarch64_cortex-a53/routing/
src/gz openwrt_19.07_telephony https://mirrors.cloud.tencent.com/lede/releases/19.07-SNAPSHOT/packages/aarch64_cortex-a53/telephony/
```

## 总结

我家是 500M 的联通宽带，vmess 协议 ws+tls 轻松跑满 500M 的宽带，CPU 占用也才 20-30%。如果拿 MTK 7621 芯片的 k2p 测试的速度是 30Mbps。红米 AX6 采用的是高通 IPQ8071A 芯片，4 核心 A53 1.4GHz 的 CPU 外加上双核 1.7GHz NPU，在进行计算任务的时候依靠 NPU，红米 AX6 在这方面真的暴打很多软路由。

不足的是现在刷机还比较麻烦，并且目前的固件不是很稳定，还只适合尝鲜阶段不适合日常使用。期待下吧，毕竟这款 CPU+NPU 实在是太强了。

