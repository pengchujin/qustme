---
title: "家庭网络小米 Mesh 组网指南｜ShellClash 抛弃软路由全家开心 Netflix"
date: 2021-05-07T12:51:42+08:00
draft: false
---

<img src="https://oss.qust.me/img/%E5%9B%BE%E5%83%8F5-7-21%20%E4%B8%8B%E5%8D%881.42.JPG" alt="图像5-7-21 下午1.42" style="zoom:150%;" />

上图是我家目前的搭配方案，下面我会和你慢慢解释让你理解学会，如何用小米、红米 AX 系列路由器就能组建稳定强大的无线网络，电视等设备观看 Netflix 秒加载 4k。<!--more-->

## 弱电箱

![IMG_1822](https://oss.qust.me/img/IMG_1822.JPG)

一般最近十几年建的房子都会有「弱电箱」，你拉宽带附带的光猫一般都塞在这里面，也是你家网络的入口。

### 简介下什么是光猫

简单来说光猫就是把从运营商拉来的光纤（图中白色的线）转换为我们日常网线的网络，运营商会直接装宽带的时候带给你。

**光猫拨号还是路由拨号？光猫改桥接？**

其实是一个问题，目前为了方便，大部分运营商直接将你宽带账号和密码放在光猫里直接 PPPoE 拨号，你插上网线或者无线路由器就能直接使用。这样会方便很多，也基本不会影响速度。

改成桥接也就是让你的路由器拨号，这样的好处是理论上减少了一层 Nat 可能能快一点点，路由器拨号速度可能更快一点点，路由器功能更丰富端口转发更方便一点，还有如果你宽带提供了公网 IP 的话这样做也会方便很多。不过有些地区的运营商是默认不允许用户改桥接让路由器拨号的，因为拿给你的光猫后台你没法进行修改。

**为什么不用光猫的 Wi-Fi？**

最近几年很多光猫都带了无线 Wi-Fi 功能，你可以直接使用，但体验糟糕。出于成本原因，这些 Wi-Fi 信号一般都会非常差，很多甚至都没 5GHz Wi-Fi。所以我个人建议不使用光猫的 Wi-Fi ，最好进光猫后台将 Wi-Fi 关了还能减少无线的干扰。

### 弱电箱里选择什么路由器

弱电箱一般空间都很小，你应该选择一个能放进去的路由器；弱电箱的位置一般都是靠进门并且一般都是嵌入墙体的，对于 Wi-Fi 来说位置非常差，所以你选择主路由器的时候可以不带 Wi-Fi 功能。

这个路由器直接关系你家所有设备网络的稳定性，最好选择能功能丰富，稳定性好一点的。比如 DHCP 功能至少能设置网关、DNS，这会让你的整体网络灵活很多。**最好有多个网口**，很多人家都会将客厅和房间布置网线，这样能直接接上路由器，免得再购买交换机。

**交换机呢？** 

如果你路由器的网口不够用，一般情况你就得买交换机来拓充更多网口。

![ubnt-erx](https://oss.qust.me/img/ubnt-erx.jpg)

我用的是 ubnt-erx 路由，体积小巧，还有 5 个网口，手机 App 也方便查看每个网口速度等信息，可以自行设置 DHCP 的 Router/网关、DNS。（缺点可能是设置功能太复杂，对新手不友好）

## Mesh 路由器

![IMG_1823](https://oss.qust.me/img/IMG_1823.JPG)

首先你得明白一个基本常识，**路由器 Wi-Fi 信号穿墙后信号好是伪命题**，想 Wi-Fi 信号好最好的办法就是多整几台无线路由器。最好使用有线 AP Mesh。

Mesh 本身是编织网的意思，Mesh 路由器最大的好处是让你家的 Wi-Fi 信号像一张紧致的网。 使用体验是无感的，你从一个房间走到另一个房间，Wi-Fi 自动连接到信号更好的 Mesh 路由器上。这个过程你察觉不到，游戏不会掉线，视频也不会卡顿一下，聊天刷微博也不会因此突然加载。

**有线 Mesh 还是 无线 Mesh？**

如果条件允许，当然推荐你 Mesh 节点路由器直接网线连接到弱电箱的路由器。这会大大提升网络的速度、和降低延迟、也提升稳定性。实在没有埋网线，直接一台路由器无线 Mesh 也能解决基本信号覆盖困扰。

**小米的 Mesh 设置很简单无脑**

![截屏2021-05-07 下午5.17.11](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-07%20%E4%B8%8B%E5%8D%885.17.11.jpg)

第一台路由器你只用有线连接上弱电箱路由器，在上网设置中将工作模式切换到中继即可，你可以在这时候设置你的 Wi-Fi 名和密码。（不要合并双频 Wi-Fi 一点历史经验，希望大家都不合并，分开 2.4GHz 和 5GHz Wi-Fi 会好很多）

第二台、第三台后面的你都不用设置，新的路由器或者恢复出厂设置的路由器，插上网线（连接弱电箱路由器的网线）和电源自动就能设置，非常非常方便。

## 小米 Mesh 使用 ShellClash 全家开心 Netflix

你只用任意一台小米路由器安装了 ShellClash 即可，推荐使用 [小米AX3600 ShellClash 教程](https://qust.me/)。实现效果都一样，你家任何连接上的设备都能打开观看 Netflix。

### 如果你是主路由安装 ShellClash

![截屏2021-05-07 下午5.36.53](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-07%20%E4%B8%8B%E5%8D%885.36.53.jpg)

你几乎不用做更多的设置，很方便，不过这样欠缺灵活性。（下面会说）

### 如果你是 Mesh 节点安装 ShellClash（推荐网线连接）

<img src="https://oss.qust.me/img/%E5%9B%BE%E5%83%8F5-7-21%20%E4%B8%8B%E5%8D%881.42.JPG" alt="图像5-7-21 下午1.42" style="zoom:150%;" />

安装好 ShellClash 后，有线连接主路由，并在后台将工作模式设置为有线中继模式。这个时候你会重新获得小米路由后台的地址，我的是 192.168.88.38 你的可能是 192.168.31.X  记住它就行。

### 修改防火墙允许 lan 转发

ssh root@192.168.88.38 连接上你的路由器，我的是 192.168.88.38 你的刚设置完有告诉你。

修改防火墙配置文件，vi 编辑工具不会操作可以查一下（按字母 i 是进入编辑，按 esc 推出编辑，输入 :wq 是保存）

```
vi /etc/config/firewall
```

将 name 为  lan 的 forward 选中那里**改成 ACCEPT**，保存。

![截屏2021-05-07 下午5.48.03](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-07%20%E4%B8%8B%E5%8D%885.48.03.jpg)

然后重启防火墙（下面的命令）

```
/etc/init.d/firewall restart
```

![截屏2021-05-07 下午5.50.20](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-07%20%E4%B8%8B%E5%8D%885.50.20.jpg)

再输入 clash 命令 按 1 重启 clash。

### 配置主路由的 DHCP，让安装了 ShellClash 的路由器接管。

![截屏2021-05-07 下午5.52.31](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-07%20%E4%B8%8B%E5%8D%885.52.31.jpg)



将主路由 lan 的 DHCP 进行修改：router 也叫网关改为上面你安装了 ShellClash Mesh 的 AP，DNS 同样第一个改为 Mesh IP，第二个你可以改为 1.1.1.1 或者你喜欢的 DNS，保存并重新连接网络即可。

![截屏2021-05-07 下午6.10.21](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-07%20%E4%B8%8B%E5%8D%886.10.21.jpg)

如果你主路由器是小米路由器。在常用设置-局域网设置里：同样是修改默认网关，和两个 DNS。这个时候你应该所有连接整个 Mesh 的设备都能享受 Netflix 了。

## Clash  Web 控制面板

![截屏2021-05-07 下午6.17.09](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-07%20%E4%B8%8B%E5%8D%886.17.09.jpg)

局域网任何设备打开 http://yacd.haishan.me/ ，添加 http://192.168.88.38:9999 我的是 192.168.88.38 你的换成你安装 ShellClash 的小米 IP 即可。

![截屏2021-05-07 下午6.18.58](https://oss.qust.me/img/%E6%88%AA%E5%B1%8F2021-05-07%20%E4%B8%8B%E5%8D%886.18.58.jpg)

打开它你就能非常便利的切换选择规则了。

## 总结

我是真的退休了 Mac mini + Surge 接管网络方案，小米的 AP Mesh 性价比极高，又能实现非常棒的全家 Netflix 效果，真心推荐。

我个人认为我的这套方案稳定性、可拓展性、和性价比都不错，也只用一台设备安装 ShellClash。你想部分局域网能 2.5G 连接 Nas ，替换或者添加 AX6000 AX9000 AP Mesh 即可。想更便宜也可以选择性价比更高的红米 AX5 做覆盖。