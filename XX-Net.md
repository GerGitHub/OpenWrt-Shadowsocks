# WR710N V2 硬改16M Flash 64M内存     

硬改回来Bootloader是U-boot ar9331     
1. 刷入openwrt V2.0     
2. 通过openwrt 把Flash重新刷入 U-boot ar9330.bin    
3. 再通过新U-boot 刷入boot选择Breed    
4. putty 安装中文包 opkg install luci-i18n-base-zh-cn   

```
Breed Boot
http://breed.hackpascal.net/
https://github.com/openwrt/luci/wiki
U-Boot   
http://pan.baidu.com/s/1qW9ipis#list/vmode=grid&path=%2FWIFI%2Fuboot%2FU-Boot-2015-04-27&parentPath=%2FWIFI%2Fuboot

openwrt安装中文
https://drive.google.com/drive/folders/0ByqeeKN198fcV1dVWVo4V1hUS1U
http://right.com.cn/forum/thread-147222-2-1.html
http://wiki.openwrt.org/toh/tp-link/tl-wr710n
http://jingyan.baidu.com/article/870c6fc300e8fab03ee4be66.html
```

##  OpenWRT python

    opkg update
    opkg install pyopenssl_0.10-1_ar71xx.ipk

添加自启动

      python /XXNet-WRT/proxy.py >/dev/null 2>&1 &

##  OpenWRT Shadowsocks
opkg install libpolarssl
opkg install resolveip

# 启动 Shadowsocks   PUTTY命令:   

    /etc/init.d/shadowsocks start
    
# 启动 ChinaDNS  PUTTY命令:    

      /etc/init.d/chinadns start

# 自启动 shadowsocks 及 ChinaDNS   

    /etc/init.d/shadowsocks enable    
    /etc/init.d/chinadns enable   

/etc/chinadns_chnroute.txt 替换为 服务->ChinaDNS中的 国内路由表地址    
安装libcurl curl   

    opkg install libcurl curl
    
PUTTY命令:   

    curl 'http://ftp.apnic.net/apnic/stats/apnic/delegated-apnic-latest' | grep ipv4 | grep CN | awk -F\| '{ printf("%s/%d\n", $4, 32-log($5)/log(2)) }' > /etc/chinadns_chnroute.txt

添加自定义防火墙规则   
openwrt后台——网络——防火墙——自定义规则，下面粘贴如下代码：   

      ipset -N redir iphash
      iptables -t nat -A PREROUTING -p tcp -m set --match-set redir dst -j REDIRECT --to-port 1080





```
http://openwrt-dist.sourceforge.net/releases/
https://sourceforge.net/projects/openwrt-dist/files/shadowsocks-libev/2.4.8-a56ac84/ar71xx/
https://github.com/bettermanbao/openwrt-shadowsocks-libev-full
http://ju.outofmemory.cn/entry/271917
https://my.oschina.net/ffs/blog/610615
http://www.aipsd.cc/newifi-y1/
https://zzz.buzz/zh/gfw/2016/02/16/deploy-shadowsocks-on-routers/
https://cokebar.info/archives/664
https://www.logcg.com/archives/860.html
https://blog.chionlab.moe/2016/01/23/openwrt-bypass-gfw-solution/
https://softwaredownload.gitbooks.io/openwrt-fanqiang/content/ebook/03.3.html
```



