## Openwrt资源 (https://downloads.openwrt.org) 网下载相应Haproxy
由于只是用来对SS进行负载均衡，所以SSL没有必要，我们下载nossl版本的包就可以了

   opkg install /tmp/haproxy*   --force-depends   (--force-depends强制安装)

## Haproxy依赖包在openwrt上更新安装
* 注意安装包部分依赖如以下：

  libltdl* zlib* libncursesw* libreadline*
  
## 配置Haproxy
  haproxy的配置非常简单，编辑/etc/haproxy.cfg

    global
        log         127.0.0.1 local2
        chroot      /root
        pidfile     /tmp/haproxy.pid
        maxconn     4000
        user        root
        daemon
    defaults
        mode                    tcp    #TCP模式
        log                     global
        option                  httplog
        option                  dontlognull
        option http-server-close
        option forwardfor       except 127.0.0.0/8
        option                  redispatch
        retries                 2
        timeout http-request    10s
        timeout queue           1m
        timeout connect         2s     #上游TCP服务器连接等待时间 
        timeout client          1m
        timeout server          1m
        timeout http-keep-alive 10s
        timeout check           10s
        maxconn                 3000
    listen test1
        bind 0.0.0.0:8388       #haproxy监听端口
        mode tcp
        server ser0 45.xx.xx.xx:1231
        server ser1 45.xx.xx.xx:1232
        server ser2 45.xx.xx.xx:1233
        server ser3 45.xx.xx.xx:1234

 * 其中，X.X.X.X为ss服务器，8388~8391这四个端口都为ss服务器上运行ssserver的端口（如果觉得不够你可以再加几个）。haproxy监听的端口为8388。
 
 * 然后使其生效：
	+ /etc/init.d/haproxy enable  #开机启动haproxy
	+ /etc/init.d/haproxy start   #启动haproxy

## 配置SS
SS配置只需要将Server Address改成127.0.0.1，Server Port改成Haproxy的监听端口(8388)即可
然后重启Haproxy以及SS服务

     /etc/init.d/shadowsocks restart
     /etc/init.d/haproxy restart

