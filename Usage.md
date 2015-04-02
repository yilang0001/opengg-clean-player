

# 注意 #

  * OpenGG.Clean.Player 的安装地址为http://userscripts.org/scripts/show/120679
  * Xunlei.Any.Player 的安装地址为http://userscripts.org/scripts/show/138814
  * 其他脚本可能有所不同, 请注意鉴别.
  * 本文不囊括所有的浏览器, 如果你希望补充本文, 请在文末留言.

# 安装 #

## Firefox ##
  * [安装Greasemonkey](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/) , 然后重启Firefox 使之生效.
  * 打开安装地址 , 点击 install 安装.
## Chrome 20- ##
  * 打开安装地址 , 点击 install 安装.

注意: 无论是否使用Xunlei.Any.Player, Chrome 用户都有可能会遇到迅雷播放器提示302 错误. 请打开浏览器设置, 依次点击"显示高级设置" -> "内容设置", 去掉"阻止第三方 Cookie 和网站数据" 前面的勾, 然后确定.
## Chrome 21+ ##
Chrome 21 系列增加了对扩展安装的限制, 用户只能安装Chrome Store 内的扩展. 要绕过这个限制有三种解决方法, 任选一种即可.
  * 右键 install 将脚本保存到本地硬盘上, 拖动.user.js 文件到Chrome 的扩展管理页面内执行安装. 注意文件名一定要是xxx.user.js, xxx.user .js 和 xxx.user(1).js都不可以.
  * 在 Chrome 的桌面快捷方式上右键编辑属性, 在"目标" 后增加参数 --enable-easy-off-store-extension-install , 然后再点击install 安装.
  * 先安装[Tampermonkey](https://chrome.google.com/webstore/detail/dhdgffkkebhmkfjojejmpbldmpobfkfo), [NinjaKit](https://chrome.google.com/webstore/detail/gpbepnljaakggeobkclonlkhbdgccfek)之类的Chrome扩展, 再点击安装页面的 install 安装脚本. (Tampermonkey 上某些脚本有BUG )

注意: 无论是否使用Xunlei.Any.Player, Chrome 用户都有可能会遇到迅雷播放器提示302 错误. 请打开浏览器设置, 依次点击"显示高级设置" -> "内容设置", 去掉"阻止第三方 Cookie 和网站数据" 前面的勾, 然后确定.
## Opera ##
  * 在浏览器的 "设置-首选项-高级-内容-JavaScript选项" 中设置"JavaScript 文件夹";
  * 右键install "目标另存为" 将脚本保存到"JavaScript 文件夹", 重启浏览器.
## safari ##
  * 先安装[NinjaKit](https://github.com/os0x/NinjaKit)
  * 打开安装地址 , 点击 install 安装.
## 搜狗浏览器 3.2 ##
  * 先按下键盘上的win+r , 在运行框里输入 %appdata%/Sogouexplorer/Webkit/UserScripts , 回车, 打开一个文件夹.
  * 打开安装地址 , 右键 install 将目标另存到桌面上 .
  * 将桌面上的120679.user.js 复制到之前打开的文件夹里, 重启浏览器.
## 其他基于Chrome 或Chromium 的浏览器(猎豹, 360极速浏览器等) ##
  * 打开安装地址 , 点击 install 安装.
  * 多核浏览器的兼容模式(IE) 上脚本不能工作, 请手动切换到极速模式.
## 遨游3(由热心网友维护, 版本可能稍有滞后) ##
  * [OpenGG.Clean.Player](http://extension.maxthon.cn/detail/index.php?view_id=1286)
  * [Xunlei.Any.Player](http://extension.maxthon.cn/detail/index.php?view_id=1296)
# 升级 #
除Firefox+Greasemonkey 可以检测升级之外, 其他浏览器均须手动更新, 更新步骤与安装一致.
# 检查是否安装成功 #
打开一个优酷或土豆, 点击一个视频网页, 待播放器载入完毕后, 在播放器上右键点击, 看菜单中是否有opengg 字样.

# 参考文章 #
[Cross-browser userscripting](http://wiki.greasespot.net/Cross-browser_userscripting)