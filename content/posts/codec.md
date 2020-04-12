---
title: "Codec"
date: 2020-04-12T21:47:48+08:00
draft: false
toc: false
images:
tags: 
  - untagged
---

# 视频与编码

你我中的绝大多数从出生开始就一直伴随着“视频”以及视频技术的飞速发展，我是95后我依然很清晰的记得小学时的露天电影：白色的幕布，硕大的放映机🎥，每次放映的师傅来还会带好几盘很大的胶卷盒，伴随着机械的声音光打到了白色的布上，特别期待的电影🎬也就这样开始了。我也记得以前的CRT电视：从黑白的到彩色的，动画片一定要放学后准时收看否则你就再也看不到了，电视还会因信号不好莫名的变得不清楚全是雪花点。到后来用上了电脑、手机、网络电视，我们已经能随时享受到 4k 高清HDR的 Netflix、YouTube、BiliBili，但视频所给我们带来的兴奋与快乐始终没有改变。

## 模拟视频与数字视频

![](https://oss.qust.me/img/20200219233901.jpg)

我们常常把信号分为两种：模拟信号和数字信号。模式信号指：模拟信号是指时间上和数值上均连续的信号，数字信号是指：数字信号是指时间上和数值上均离散的信号。李永乐老师讲解过[模拟信号与数字信号的区别](https://www.bilibili.com/video/av25762796)感兴趣的可以看看。回归到电影、视频领，像🎞️胶片电影(光敏材料记录)、以前的CRT电视📺（连续的电信号）、VHS录像带📼这些都是模拟信号的视频。而如今我们通过网络上看到的所有视频，电脑手机存的这些影片都是数字视频，它们都是摄像机采集通过编码数字化，计算机用0和1存储传播然后又解码后呈现到我们的屏幕上。

#### Film 胶片电影

![](https://oss.qust.me/img/20200220172739.jpg)

"If I can't shoot on film I'll stop making movies" 如果不能使用胶片的话那么我将放弃拍电影。这是昆汀在电台里所说的，包括不久前上映的《好莱坞往事》也都是用35mm的胶片进行拍摄的里面也有很多致敬胶片电影的片段，即使观看昆汀也更愿意看胶片放映而不是数字，他更喜欢那种一秒种24张照片的魔法。像昆汀这样坚持拍摄胶片的导演还有挺多的，比如诺亚的《婚姻故事》、诺兰的《敦刻尔克》、《星际穿越》等一系列电影。

![](https://oss.qust.me/img/20200221105831.png)

电影从19世纪末诞生的那一刻开始就来自于胶片，从无声电影到旁边电影到有声电影，从黑白电影到彩色电影再到3D电影，胶片也从8mm、到16mm、32mm到 IMAX 70mm。我们从胶片到数字，直到今天胶片电影任然占据着电影工业很重要的一部分。数字电影拍摄制作会快很多也会便宜很多，而胶片又更具有“艺术性”的优势，我个人并不会在意一部电影是数字的还是用胶片拍摄的，它像是一种工具，看是否被电影和导演所需要。

![](https://oss.qust.me/img/20200221160908.jpg)

像《乔布斯》这部电影里，在乔布斯不同年纪分别就采用了 16mm胶片、32mm胶片、以及数码的形式呈现时代的变化。

![](https://oss.qust.me/img/20200221164320.jpg)

近年来你能看到很多像 NOMO 这样模拟复古胶片的相机App，很多音乐MV、Vlog 里都插入了 Super 8mm 胶片相机拍摄的镜头，过去的胶片又在以不同的形式流行。

如果你感兴趣可以看看这几个视频：

* 如果你想查看一部电影所使用的相机，镜头等信息可以在 [IMDB 查看 Technical Specifications](https://www.imdb.com/title/tt7131622/technical?ref_=tt_ql_dt_6) 
* [从1878到2018年电影的改革](https://youtu.be/FhjPi5o2quE)
* [如何使用 Super 8mm 胶片相机进行拍摄](https://youtu.be/TRqAxhykP_4)
* [关于相机 CMOS 的以及胶片的大小](https://youtu.be/rUOYXjH6y7w)
* Vox 写的：[数字还是胶片电影界里最大的争论](https://www.vox.com/2016/1/5/10714588/film-digital-35mm-70mm-explainer)

#### CRT 显像管电视

![](https://oss.qust.me/img/20200221184849.jpg)

相比电影，电视的出现和普及要晚很多，从20世纪40年代开始商业化，在美国5、60年代开始逐渐普及。直到2008年LCD电视的销量才超越 CRT 显像管电视，而各国从模拟信号逐渐转变为数字信号的时间则要更晚一些。

![](https://oss.qust.me/img/20200221234550.jpg)

**电视节目的录制**：**摄像管**是CCD出现之前的一类用于摄像的阴极射线管CRT。这就是传统CRT电视信号的来源，摄像管逐行扫描图像将光信号转变成模拟电信号。

![](https://oss.qust.me/img/20200222125553.png)

**电视节目的传输**：模拟电信号包含着同步信息，亮度、色度将通过电磁波或不同的介质输送到千家万户。无论是使用 NTSC 制式（北美大部分国家的信号制式） 还是 PAL（我国和欧洲东南亚大多数国家使用的制式）它们的原理都是基本都是这样。只是扫描方式、颜色信息处理、以及帧率的差别。

![](https://oss.qust.me/img/20200222170622.gif)

**电视节目的播放**：在 CRT 显像管电视里模拟电信号又通过电子枪发射的电子束打到屏幕上形成亮点，电磁线圈驱使电子束横向扫描让我们看见亮线，最终竖向扫描亮线形成了一帧的画面，然后25/30帧的画面形成了我们电视里看到的一秒钟的视频。

![](https://oss.qust.me/img/20200222171817.svg)

![](https://oss.qust.me/img/20200222225845.gif)

我本以为 NTSC 或 PAL 只是以前的电视信号制式，对我们大多数人应该没什么影响，但我发现我自己的 sony 微单里也有 PAL 和 NTSC 的选择我才发现事情并没有这么简单。电视 NTSC 制式是每秒30帧的视频，而 PAL 则是每秒25帧的视频，恰巧的是全球使用 PAL 制式的点国家的交流电都是50Hz的，而使用 NTSC 制式的国家都是60HZ的交流电。其实这并不是巧合，“使场刷新率与电源匹配可以避免互调（也称为跳动），跳动会在屏幕上产生滚动条。刷新速率与交流电的频率偶然的帮助了显像管摄像机记录早期的现场电视广播，因为交流电频率正好符合电动摄像机的速度来捕获每一帧的画面”（引用自 wikipedia）

![](https://oss.qust.me/img/20200222231058.jpg)

![](https://oss.qust.me/img/20200222231107.jpg)

很多相机、GoPro 都内置了 NTSC/PAL 拍摄的选择，切换后你会发现视频的帧率倍数都会改变。PAL 模式会是 25p、50p、100p 这样，NTSC 模式则是 30p、60p、120p。如果帧率与当地交流电的灯光的频率相符，拍摄的素材一般则不会有灯光闪烁的问题，当你出国拍摄素材的时候请记得选择与当地交流电频率相符（50Hz PAL，60Hz NTSC）。

![](https://oss.qust.me/img/20200222231802.jpg)

如果你在 YouTube 上观察不同地区的 YouTuber 的视频你也会发现这个非常有趣的现象：除了24帧是因为电影大家会一样以外，绝大部分的 YouTuber 拍摄的帧率都是和当地的 NTSC/PAL 相符。

有很多我只说了了个大概（也可能说的不太对），如果感兴趣可以看看：

* [彩色CRT电视上面并不是像素点](https://youtu.be/Ea6tw-gulnQ)
* [模拟信号视频是如何工作的](https://youtu.be/r38nVmxBfvM)
* [视频是如何发明的](https://youtu.be/rjDX5ItsOnQ)
* [慢放镜头下的电视](https://youtu.be/3BJU2drrtCM)
* [NTSC wikipedia](https://en.wikipedia.org/wiki/NTSC)
* 李永乐老师：[电视机的显像原理](https://youtu.be/Sq6LE1OKuPU)

## 数字视频编码

![](https://oss.qust.me/img/20200223161154.jpg)

从上个世纪末计算机逐渐开始普及，视频（电影）从拍摄、到剪辑、到传播以及呈现都发生了转向数字化的改变，视频编码则是在这其中每一步都凸显的尤为关键。

视频编码（视频编解码器，这里就简称视频编码）的英文名叫 codec 是 encoder 和 decoder 的缩写，我们拍摄、剪辑、转码的时候会将图像的光信号处理后 encoder；在播放的时候又会 decoder 将视频呈现出来。

视频编码与我们平常见到的 .mp4、 .flv 等视频的拓展名并没有必然的联系，这些拓展名格式像一个容器或者说“container”里面往往包含了不同编码的视频、不同编码的音频、图片、字幕、等等都可以。

目前大家接触到比较多的视频编码大体有下面5种：

### H.264/AVC

无论是叫 H.264 或者是 AVC 或者  MPEG-4 Part 10, Advanced Video Coding 都是指的这一个。

这是在2003年就由MPEG（Moving Picture Experts Group 动态影像专家组）发布了的至今为止已经有17年历史的视频编码，也是迄今为止最流行最通用的视频编码。H.264 的适应范围非常广，我们不同系统的电脑、浏览器、手机、电视、数码相机、流媒体、播放器、剪辑软件等几乎都有在使用这种编码。

### H.265/HEVC

无论是叫 H.265 还是 HEVC （High Efficiency Video Coding ）或者  MPEG-H Part 2 指的都是这个编码。

H.265 可以说是 H.264 的继任者，H.265 主要解决了 H.264 的两个问题：

1. H.265 的效率要高很多，一般相同的画质 H.265 比 H.264 节省了大约一倍的带宽（1080p 下节省了57%左右，4k UHD 更是节省了大约64%的带宽 ），这对于一众流媒体视频网站的诱惑力可以说是十分巨大的，因为视频网站往往有一半甚至更多的开销得花费在带宽上面。不过还是有缺点的，播放 H.265 编码的视频内容的设备需要更好的性能，目前很多设备往往也并不支持 H.265 视频的播放，这时候就要在服务端放两份一份 H.264 的一份 H.265 的然后分发给不同的客户端。
2. 目前4K已经比较普遍，很多专业设备甚至手机都能拍摄8k的内容，很多8k的电视也已经开卖。而 H.264 最高只支持4k已经不太适合更高质量视频的拍摄、制作、和播放了，H.265 支持8k恰好能满足当前的需求。

最大的坏处是收费，并且更贵了。

### VP9

无论是 H.264 还是 H.265 都有一个非常大的问题就是收费，并且非常昂贵，厂商随随便便一用一年就是几百万刀的钱进去了。Google 就想我又有技术又有钱我为啥不自己造个轮子，受这“剥削”干嘛。于是2009年 Google 就花了106.5万刀收购了 On2（视频编码公司）然后很快就推出了 VP8 供大家免费使用，但这个时候天下早已经是 H.264 的，VP8 本身的编码效率也不够好，除了 YouTube 和几家浏览器开始支持外并没有特别大规模的被使用。

索性2010年 Google 就直接又推出了 VP9，目标是直接干 H.265，YouTube、Netflix 等视频网站巨头也都相继支持，主流浏览器除了 Safari 也都支持（这就是你的 Safari 看 YouTube 没有 1080p 以上选项的根本原因），Android 更是从 4.4 就开始支持了。Netflix 曾经做过详细的对比 VP9 相比较 H.265 在1080p往上的分辨率 VP9 还是拥有不小的优势。

### AV1

虽然 Google 的 VP9 效果还不错，但是其它几家巨头并不太买单，毕竟在 Google 手里的项目他们也不太放心，苹果就始终未支持 VP9/VP8，很多买了 Apple TV 估计也会因此困恼无法观看4k的 YouTube。然后苹果、亚马逊、思科、 谷歌、英特尔、 微软、Mozilla 以及 Netflix 等共同组建了 Alliance for Open Media（开发媒体联盟）在2018年推出了 AV1（AOMedia Video 1）来共同对抗 H.265。谷歌也贡献出了自己的VP9作为基础，AV1比起VP9又节省了约20%的带宽，依然免版权费。

![](https://oss.qust.me/img/20200225233004.jpg)

不过最重要的是这个联盟的号召力，图上N个公司都加入了这个联盟，像 Netflix 、YouTube 很多也都直接开始分发 AV1 编码的视频了，其它也都陆陆续续开始支持 AV1 了。

### Apple ProRes

![](https://oss.qust.me/img/20200226000444.png)

与上述几种帧间编码的视频编码不同，多用于专业相机拍摄的编码 Apple ProRes 属于帧内编码。“帧内压缩只参考本帧数据，压缩率小；帧间压缩要参考其他帧数据，压缩率大” 。Apple ProRes 这种帧内编码的视频编码的体积会比帧间编码的大很多很多，像一般的数码相机、微单都很少使用这种，因为体积过于庞大。

不过 Apple ProRes 这种帧内编码的好处也是有的，这种编码往往会使用更大的体积保存更多的信息；因为是帧内编码不需要计算出其它的帧在剪辑的时候也会对性能的要求低很多很多，即使配置低的电脑剪辑高分辨率的视频也会流畅很多。

有很多专业级别的拍摄设备都会有自己家类似 Apple ProRes 的编码，甚至有些会记录“无损”的数据，记录更高的质量，方便后期处理。这些专业的拍摄设备一般用户不会接触到，网络视频传播基本也不会使用帧内编码的这类，因为体积实在太大了，非常不利于传播。

如果你对这些感兴趣可以看看：

* [H.264 vs H.265 H.265 会主宰市场吗？](https://medium.com/advanced-computer-vision/h-264-vs-h-265-a-technical-comparison-when-will-h-265-dominate-the-market-26659303171a)
* [【省带宽、压成本专题】深入解析 H.265 编码模式，带你了解 Apple 全面推进 H.265 的原因](https://www.jianshu.com/p/70a45e0e9876)
* [视频编码的终结？](https://netflixtechblog.com/the-end-of-video-coding-40cf10e711a2)
* [HEVC (H.265) 是啥，我们需要关注什么？](https://blog.frame.io/2018/09/24/hevc-format-wars/)
* [aomedia 官网](https://aomedia.org/)
* [2016年 Netflix 在 Android 上分发 VP9 内容](https://variety.com/2016/digital/news/netflix-offline-downloads-codecs-vp9-1201932502/)
* [AVC 编码详解](https://mpeg.chiariglione.org/standards/mpeg-4/advanced-video-coding)
* [HEVC 授权价格](http://x265.org/hevc-advance-reduces-proposed-license-fees/)
* [HEVC VP9 未来的视频编码](https://headjack.io/blog/hevc-vp9-vp10-dalaa-thor-netvc-future-video-codecs/)

### 视频的拍摄

![](https://oss.qust.me/img/20200229014326.jpg)

拍摄：大部分设备我们都是没法选择视频录制的编码的，不过 iPhone 可以所以 iPhone 为例。在 设置-相机-格式 可以选**高效**（H.265 即 HEVC）或者 **兼容性最佳**（H.264 即 AVC），可以在两个对比图中看出视频编码对体积的影响真的很大。（4k 60fps 只能选择高效即使是兼容最佳模式，个人认为是如果记录 H.264 编码的视频体积会过于庞大对用户非常不友好）

选择高效自然会碰见兼容性问题，你可以参考广告导演 flypig 微博：[iPhone 拍下来的素材在 Final Cut Pro X 里花屏](https://weibo.com/1639529981/Ivpa9pBB7?type=comment) ，碰见这种问题一般你可以选择将 H.265 的素材转成 H.254 或者坚持自己的系统或者剪辑软件是不是最新的。

拍摄、剪辑、和导出上传我自然是门外汉了（别的也是），推荐你们可以看看影视飓风的这几期视频，讲的很清楚。

* [完全解析：编码与封装](https://www.bilibili.com/video/av4101573/)
* [高画质的背后——视频的封装与编码](https://www.bilibili.com/video/av25783076/)
* [422，420，10bit，8bit？这些究竟是什么](https://www.bilibili.com/video/av29270929/)

### 视频的分发

相同的电影剧集，看起来清晰不清晰除了和分辨率、码率有关，视频的编码也是非常重要的一部分，也常常被我我们所忽视。

国际上比较主流的视频网站都采用了多种视频编码来应对不同平台和不同的内容甚至不同的网络环境，下面是我个人总结的一些（可能会不完整）

* Netflix 

  ![](https://oss.qust.me/img/20200229150321.jpg)

  Netflix 目前正在使用 4 种不同的编码，分别是

  H.264(AVC)：这是 Netflix 使用较多的一种编码格式，在 Safari、iOS、电视客户端等都在使用。

  H.265(HEVC)：Netflix 一般仅为 4k 的内容提供 H.265 的编码，并且一般只有在能看 4k 的客户端上使用此编码。我这里说的是 4k 的内容并不是你看 4k 的时候才会使用 H.265 编码，举个例子：你在 firetv 4k 或者 Windows edge 浏览器上观看 《爱尔兰人》等有 4k 版本的内容，即使你观看的分辨率是 480p、或者720p 都会是 H.265 编码的。

  AV1：Netflix 在前几天宣布 Android 上正式开始使用这种编码，在这之前一直使用的是VP9，不过只有在使用流量省数据的选项下才会采用。

  VP9: Netflix 目前在 Android、Chrome 等谷歌系的一直使用这种编码。这里也很容易解释为啥你在 iOS 下载相同的内容和 Android 下载的体积不一样（iOS 客户端下载的普遍体积更小）

* YouTube 

  ![](https://oss.qust.me/img/20200229150131.jpg)

  YouTube 目前主要使用 VP9、H.264、以及 AV1 视频编码，不过值得注意的是 1080p 以上的内容 YouTube 都不会使用 H.264 编码，这也导致了 Apple 全系产品目前没法观看 YouTube 4k，不过 YouTube 已经开始支持 AV1 编码了，AV1 也有苹果的一部分参与，未来几年内应该能解决这个问题。

像 Apple TV+、Disney+ 也都采用了 H.265 在 4k 内容上，并且码率还要比 Netflix 的 16Mbps 要高些许，相比国内爱奇艺、bilibili 只使用 H.264 并且码率也要低很多很多，差距确实十分明显。

![](https://oss.qust.me/img/20200229151855.jpg)

如果你也使用 firetv 想看详细播放内容详细信息可以开启开发者模式：

“遥控器：在方向盘上，按住“ 中央”按钮一秒钟；然后（仍然按住居中），也按下“ 向下”按钮。按住两个按钮约3-4秒。然后释放两个按钮，然后按遥控器的菜单按钮。（如果这不起作用，请尝试同时按住“ Center”和“ Down”，而不要交错放置。）”

## 尾巴

胶片电影时我们的视频时一秒24张照片的魔法，到电视我们的视频是“不稳定”的模拟电信号，到如今我们的视频又是网络中的数字信号。好的内容不会因为传播记录方式而改变，但却能让更多人看到更多更好的内容。

文章写杂乱，很多说的很糙很杂，如果有不对欢迎您指正。
