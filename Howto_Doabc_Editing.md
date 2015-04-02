# Introduction #

转载请注明以下信息

文章转载自：鲁夫的爱 [http://opengg.me/ ](.md)

本文标题：存个档, 破解优酷和土豆的播放器

本文地址：http://opengg.me/751/crack-youku-tudou-player/



# Details #
## 需要准备的软件 ##
  1. [wget](http://gnuwin32.sourceforge.net/packages/wget.htm) 或其他下载工具
  1. [Swftools](http://swftools.org/download.html)
  1. Sothink SWF Decompiler 或其他swf反编译工具
  1. [notepad++](http://notepad-plus-plus.org/download/) 或其他文本编辑器
  1. [Yogda](http://opengg.me/wp-content/uploads/2012/03/Yogda.1.0.564.zip)
  1. [HxD](http://mh-nexus.de/en/hxd/) 或其他十六进制编辑器
  1. [wamp](http://www.wampserver.com/en/) 或其他web 服务器
  1. 可能会用到 Adobe Flash Pro
## 下载swf 文件 ##
`wget "http://static.youku.com/v1.0.0224/v/swf/player.swf"`
## 解压swf文件 ##
似乎是从flash 6 开始, swf 文件都可以用zlib 压缩了, 我们用Swftools 自带的 swfcombine 解压出来, 以方便修改. 详见[Swftools faq](http://wiki.swftools.org/wiki/FAQ).
`swfcombine -d player.swf -o player.fws.swf`
## 反编译优酷播放器 ##
用Sothink SWF Decompiler 打开player.fws.swf, 在右侧export 栏中就能看到播放器内的图片等元素, 还能看到反编译出来的源代码. 我们只关心源代码, 于是去掉Shape 和 Image 等其他选项, 只选择Action, 导出到一个文件夹里.
## 阅读源代码 ##
导出的源代码非常完整, 可以看到播放器的用户数据收集和广告获取等模块如何工作, 进而可以得出对策.
分析与修改的主要策略有二:

  1. 自顶向下, 直接在逻辑里去掉对模块或函数的调用;
  1. 自下而上, 针对具体的网络行为, 以url 的参数为关键字查找, 去掉子函数内对应的语句.

自顶向下的修改, 能把功能删得比较干净, 但一个函数往往会被调用很多次, 可能需要改很多地方. 自下而上的修改则比较直接而方便. 具体采用哪种策略, 可以根据工作量来权衡, 尽量选择修改最少的方法.

对优酷播放器主要用前一种策略, 对土豆播放器主要用后一种策略.

## 修改播放器 ##
直接用Sothink SWF Decompiler 反编译出来的代码进行编译可能会出错, 我们通过hex 编辑器修改player.fws.swf 文件来修改播放器的行为.

修改的原理是, 先分析出源代码编译出来的指令, 在hex 编辑器里查找这些指令, 修改它们, 从而修改播放器的行为.

在这里我们用到两个免费的软件: avm2静态分析工具yogda 和hex编辑器HxD.
然后为了进行在线调试, 需要把播放器放到web 服务器的www 目录里, 我使用的是wamp, 安装在D盘 .
  1. 先把player.fws.swf 复制到D:\wamp\www\ 命名为player.new.swf ;
  1. 运行wamp, 在Firefox 里打开`http://localhost/player.new.swf?VideoIDS=XMjA0Mjg4Nzk2` ,打开Firebug 的net tab和 Adblock Plus 的Blockable items , 方便我们观察播放器的网络行为;
  1. 用yogda 打开player.new.swf 查找需要修改的函数名, 记录下需要修改的语句对应的hex 指令;
  1. 用HxD 修改player.new.swf ,把需要修改的指令改掉, 或者直接用02 抹掉(02 对应的行为是 Do nothing, 详见http://learn.adobe.com/wiki/display/AVM2/nop ), 注意修改前后要保持指令等长, 不要影响文件的大小. 改好后 ctrl+s 保存修改;
  1. 有的指令在整个swf 中出现很多次, 为了找准修改点, 可以在同一个函数里选择一些比较罕见的指令作为锚点 (如对某些罕见字符串的调用), 在锚点附近查找目标指令.
  1. 每修改一次都在Firefox 里刷新看有无效果, 是否影响功能, 如果无效就到D:\wamp\www\ 把player.new.swf 删掉, 把player.new.swf.bak 重命名为player.new.swf , 回滚到修改前的状态, 另寻思路进行修改.
  1. 修改语句的过程中, 可能需要拼凑指令, 此时可以用Adobe Flash Pro 写一个小的Hello World, 看编译的结果, 也可以直接在yogda 里修改汇编代码, 记录修改后的对应的指令, 但不要直接使用yogda的保存功能. 我们只用yogda 看汇编, 只用HxD 改文件.
## 压缩swf 文件 ##
修改完成后, 确认功能没有缺失, 程序正常运行. 然后我们可以用swfcombine 把改好的swf 压缩, 节省体积.

`swfcombine -dz player.new.swf -o player.pack.swf`