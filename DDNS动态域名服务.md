# DDNS动态域名服务

+ 由于没有固定公网IP, 只能通达DDNS域名服务来固定访问的动态的IP地址, 动态DNS允许为拥有动态IP的主机配置一个固定的可访问域名;

## Openwrt安装DDNS

    opkg update
    opkg install ddns-scripts
    opkg install luci-i18n-ddns-zh-cn

## DDNS使用设置

+ DDNS设置
![DDNS界面1](https://github.com/GerGitHub/Openwrt-Set/blob/master/OpenwrtImg/DDNS%20P1.png)

+ 添加DDNS动态域名
![添加DDNS动态域名](https://github.com/GerGitHub/Openwrt-Set/blob/master/OpenwrtImg/DDNS%20P2.png)

+ 其它设置
![添加DDNS动态域名](https://github.com/GerGitHub/Openwrt-Set/blob/master/OpenwrtImg/DDNS%20P3.png)
![添加DDNS动态域名](https://github.com/GerGitHub/Openwrt-Set/blob/master/OpenwrtImg/DDNS%20P4.png)

## 其它设置
+ 添加自定义动态域名

+ SCP登录SSH添加DDNS动态域名服务商
  SCP登录Openwrt 文本工具打开编辑 /usr/lib/ddns/services 
![DDNS add services](https://github.com/GerGitHub/Openwrt-Set/blob/master/OpenwrtImg/DDNS%20add%20Services.png)

