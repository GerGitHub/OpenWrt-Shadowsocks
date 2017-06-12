## Openwrt路由器安装Python-Mini或者Python-Light

路由器空间都比较小，直接执行opkg install python 会在openwrt安装一个完整的Python,非常占内存，所以可以安装Python-Mini或者Python-Light，实现轻量化py运行环境。

         opkg update
         opkg install python-mini

如果是安装了OpenWrt Chaos Calmer(15.05)及之后版本需要安装另一个包（Python-Light）

         opkg update
         opkg install python-light

如果你还需要其他的模块你可以直接opkg安装，例如你要openssl模块你就可以在终端执行

         opkg install ptyhon-openssl
         
以上ipk文件包也可在相应openwrt版本package中下载后SSH复制到openwrt /tmp文件夹中, 执行 opkg install ...

