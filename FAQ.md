# Introduction #

本项目常见问题



# Details #

## 我是否必须阅读Q&A? ##

不用，以下只是对脚本的一点说明，你不必阅读也可放心使用此脚本，技术细节让我来操心就可以了。


## 这个脚本做了些什么? ##

自动把视频网站站内和外链的播放器替换成无广告版播放器，同时把视频网站自带的“分享到”功能中的地址也替换成无广告版的。

## 用ABP 不就够了吗? ##

无论是否使用本项目, 我推荐所有的用户都安装ABP.

在大部分情况下, 确实ABP够用了, 但ABP也有不足:
  1. ABP 只支持Firefox 和Chrome ;
  1. 优酷和土豆播放器在播放视频前默认会有约4 秒的延时等待, ABP 无法解决 .
  1. ABP 目前对优酷视频的过滤依赖于一个&yad 参数, 这个参数随时会被优酷去掉而失效.

如果你能忍受ABP 的以上缺陷, 可以不使用本项目提供的播放器.

## 本项目相对ABP 有何优点? ##
直接修改播放器, 不损失功能, 没有延时等待, 能支持更多浏览器, 默认使用宽屏模式.

## 项目的播放器是怎么改出来的? ##
原理见[这篇文章](http://opengg.me/751/crack-youku-tudou-player/).

## 项目的播放器放在哪里, 值得信任吗? ##

项目播放器放在Google Code 和player.opengg.me , 如果信得过我就放心用吧.

## 载入速度和服务期限有保障吗? ##
Google Code 和player.opengg.me 都支持ipv6 和ipv4, 中国大陆用户的访问速度中下. 但浏览器一般都有缓存, 加上loader.swf 机制, 除首次载入较慢外( 播放器300KB, 下载速度为20KB/s 的话, 约要载入15 秒), 用户并不会感觉到很慢. 为了加快土豆外链视频的载入, 我使用sina app engine 做中转代理, 把响应时间控制在2 秒以下.

Google Code 没有说能用多久. player.opengg.me 放在朋友的vps 上, 如果这个vps 过期我会转向我的博客服务器, 博客播放器续期3年. sina app engine经我优化后总使用次数可达到 500万到800万人次, 按照目前的资源使用情况, 能保证十年用不完.

如果你仍然对载入速度和服务期限有顾虑, 可以把下面这两个文件下下来, 自己做镜像.

http://player.opengg.me/player.swf

http://player.opengg.me/TudouVideoPlayer_Homer_237.swf
## 这个脚本支持哪些视频网站 ##
见[目前支持的视频网站](Supported_Video_Sites.md), 如有需求添加其他视频网站, 请到[项目Issues](http://code.google.com/p/opengg-clean-player/issues/list)提交功能需求
## 这个脚本支持哪些浏览器 ##
见[测试兼容的浏览器](Supported_Browsers.md), 欢迎到[项目Issues](http://code.google.com/p/opengg-clean-player/issues/list)提交测试报告.
## 我在使用的过程中遇到了问题(bug) ##
欢迎到[项目Issues](http://code.google.com/p/opengg-clean-player/issues/list)提交bug 报告.

土豆网播放器第一次载入时没有载入图标, 会让用户产生无效的错觉( 原版播放器也有这个问题, 但他们服务器比较快, 所以不明显), 请耐心等待20 秒, 若还不能载入, 请提交bug 报告.
## 我作为普通用户, 能为项目做些什么 ##
  1. 提交功能需求
  1. 反馈bug
  1. 提交浏览器测试报告
  1. 帮忙宣传项目
  1. 为项目提供文件和服务托管
  1. 如果sina app engine 流量告急, 可以考虑捐款 ( 是的, 我接受捐款, 但仅用于本项目, 且公平公正公开不以营利为目的 )
## 我作为开发者, 能为项目做些什么 ##
  1. 提供功能建议
  1. 提交patch
  1. 加入项目