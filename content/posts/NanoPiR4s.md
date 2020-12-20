---
title: "NanoPi R4S 上手体验"
date: 2020-12-20T19:21:35+08:00
draft: false
---

![](https://oss.qust.me/img/20201220194933.png)

在购买 NanoPi R4s 之前，我其实已经拥有了 NanoPi R2s。是的 R2s 很好用，价格也非常便宜，你只用花不到 200 元就能购买一台拥有 2 个 1000M 网口，性能也还过得去的体积非常小的路由器。前些天浏览新闻看到 R4s 曝光的消息，这俩天看到淘宝正好上架了，我还是按捺不住入手了一台。

## 基本配置

![](https://oss.qust.me/img/20201220202048.jpg)

很容易看出因为 CPU 的大小和俩个 USB 3.0 接口让 R4s 的体积的直接大了不少，R4s 因为是直接 PCIe 接的 1000M 网口理论效率应该也能高一点，我也总结了下俩个的一些基本配置可以参看下。

|     R2s R4s 对比      |                  R2s                   |                          R4s                           |
| :-------------------: | :------------------------------------: | :----------------------------------------------------: |
|          CPU          |  28nm Rockchip RK3328 4核 A53 1.5Ghz   | 28 nm Rockchip RK3399 2.0Ghz 双核 A72 + 4核 1.5Ghz A53 |
|         内存          |                  1GB                   |                       1GB / 4GB                        |
|         网口          | 1个原生 1000M + 1 USB 3.0 转接 1000 M  |             1个原生 1000M + 1 PICe 1000 M              |
|       USB 接口        |            1个 USB 2.0 接口            |                   2 个 USB 3.0 接口                    |
|         供电          | micro USB 供电（有 Type C 口版本可选） |                         Type C                         |
|         尺寸          |              55.6 x 52 mm              |                     66 mm x 66 mm                      |
|       系统卡槽        |                micro SD                |                        micro SD                        |
| 单核 Geekbench 5 跑分 |                  105                   |                          206                           |
| 多核 Geekbench 5 跑分 |                  325                   |                          615                           |
|        CPU TDP        |                   5W                   |                           7W                           |
|       带壳价格        |               200 元左右               |               1GB 359元 / 4GB 449 元左右               |

## 安装系统

默认的后台地址：192.168.2.1 

默认用户名：root

默认密码：password

### 准备 

* micro SD 卡一张
* 下载安装 [Etcher](https://www.balena.io/etcher/) （烧录工具， Mac Win Linux 都支持，非常好用）
* 下载 R4S 固件 [Github链接](https://github.com/LewiVir/NanoPi-R4S) 

 Official 是来自于 friendly 的源，Lean 的则是来自于 Lean 的，我个人推荐目前用 Lean 的版本功能丰富很多。下载 Release 出的内容比较多，选择  **openwrt-rockchip-armv8-friendlyarm_nanopi-r4s-ext4-sysupgrade.img.gz** 下载就可以。注意选择自己对应的内存版本。目前的固件可能还不是很稳定，可以参看那个项目的 issue。

### 烧录系统

1. 电脑插上 micro SD 卡

2. 打开 Etcher ，先选从 Github 下载的 固件（不需要解压），再选择你插入的 SD 卡

   ![](https://oss.qust.me/img/20201220210337.jpg)

3. 点 Flash 烧录（Mac 可能需要输入下密码）

4. 烧录完成后拔下 micro SD 卡插上 NanoPi R4S 的卡槽，插电开机即可。

![](https://oss.qust.me/img/20201220211920.JPG)

插上电源和网线理论上就能正常使用了。

## USB 无线网卡

我有带着一个体积小性能好便携路由器的需求，但 NanoPi R4s 又不带 Wifi 功能，只好选择再买个 USB 无线网卡。

![](https://oss.qust.me/img/20201220213131.jpeg)

从左到右依次是 网件 A6210AC（MT7612U 芯片）、未知品牌（RT3070芯片）、GRiS （RTL8822BU芯片）、未知品牌（RTL 8811CU/AU）的无线网卡。

买这么多个因为该 openwrt 的 USB 无线网卡驱动目前还不完善，我测试了下这四个中只有 **网件 A6210AC（MT7612U 芯片）**、**未知品牌（RT3070芯片）** 这俩个芯片插上去就能直接使用（不能热插拔，插上去需要重启后即可配置使用）。

![](https://oss.qust.me/img/20201220215929.jpg)

网件 A6210AC（MT7612U 芯片）这款我个人非常推荐，淘宝上卖的价格非常便宜 79 元左右，支持 USB 3.0，也支持 5Ghz，连接速度和稳定性都不错。

## 配置代理

我个人比较推荐使用 OpenClash，目前使用也很方便。

* 选择 服务-配置文件订阅-添加

![](https://oss.qust.me/img/20201220221127.jpg)

* 配置文件名随便填即可；订阅地址可以是你的 Clash 地址也可以是别的地址，如果是 V2ray、SS 等地址记得钩一下在线转换，这会给你的订阅转换成 Clash 格式的。最后点下保存配置。（图中的配置是瞎编的链接不用尝试）

![](https://oss.qust.me/img/20201220221302.jpg)

* 开关在 OpenClash 的主界面，你可以选择你刚添加的配置文件 点开启用，这时候应该就能正常使用了。

![](https://oss.qust.me/img/20201220222622.jpg)

控制面板也和其他平台的 Clash 类似，可以点开 Web 版查看选择节点、模式等操作。

当然固件也是带有 Hello World、PassWall 等传统的 V2ray 、ss、ssr、trojan 等订阅，选择节点的服务，你可以在里面选择添加订阅地址，或者直接添加节点使用。

## 总结

* NanoPi R4s 固件暂时还不太稳定，如果你不着急也可以再等等。
* NanoPi R4s 和 R2s 最大的提升其实是 CPU 性能，和 USB 速度；R2s 这对于大部分人完全足够使用。R2s 代理我测过大概能跑 300M+ ，我会觉得还缺了点，但到了 R4s 正好能弥补这个遗憾。另外就是 USB 3.0 接口了，对于想用 USB 无线网卡上网以及外界存储设备的人来说还是非常有必要的。
* 1Gb 版本的当路由器完全够用，你不必选择 4Gb 版本。
* R4s 价格偏高，体积偏大了点，发热也大了不少，没更高需求建议买 Type C 口的 R2s ，性价比会高很多。

我会把 NanoPi R4s 当作便携的高性能路由器使用，出门能挂在移动电源上，然后配合 USB 无线网卡非常不错。