## Openwrt使用shadowsocks(影梭) DNS-forwarder(DNS转发) ChinaDNS

### 下载shadowsocks-libev luci-app-shadowsocks SSH复制到/tmp 然后putty命令 opkg install /tmp/...ipk 安装

+  https://bintray.com/aa65535/opkg/shadowsocks-libev/#files/
+  https://github.com/shadowsocks/luci-app-shadowsocks/releases/tag/v1.6.3

其它安装包
+  ChinaDNS (openwrt-chinadns)
+  luci-app-ChinaDNS
+  DNS-forwarder (openwrt-dns-forwarder)
+  luci-app-dns-forwarder

安装依赖包
+  opkg update
+  opkg install ip ipset iptables-mod-tproxy libev libpthread libpcre


## Shadowsocks 设置
### 1. 服务器管理
+  添加相应的SS服务器, IP地址 port端口 加密方式 密码...
### 2. 访问控制
+  被忽略IP列表 一般选择chinadns让国内网址不用走代理服务器
+  强制走代理IP 可以添加8.8.8.8 或8.8.4.4 这2个是国外IP地址DNS解析用
+  内网区域  代理类型:直接连接  |   代理自身:正常代理


