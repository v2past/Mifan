❤️ 项目简介:❤️

    📌 项目环境: 搬瓦工、openVZ、CentOS 6 X86.
    📌 项目作用: 通过VPS搭建SS服务器 方便自己以及他人登高远望; 还能学习各种技术. 





❤️ 文件简介:❤️



00-ssh.txt       免密码SSH连接vps

VPS-Speed.txt   减少VPS延迟,极大改善体验.  Kcptun / 




30-LNMP.txt      搭建LNMP环境
31-Naginx.txt    








4. 进行快照设置!! 以后重装系统 直接恢复到这步.


2. 搭建 Nginx 网页()

1. 搭建 ss

3. 搭建 ngrok
4. 搭建 数据库.
5. 搭建认证系统








❤️ VPS 基本信息.
看内存:  free -m

📌 磁盘IO测试: 
    [root@localhost ~]🔅 dd if=/dev/zero of=test bs=64k count=4k oflag=dsync
    记录了4096+0 的读入
    记录了4096+0 的写出
    268435456字节(268 MB)已复制，0.612572 秒，438 MB/秒

    [root@localhost ~]🔅 dd if=/dev/zero of=test bs=8k count=256k conv=fdatasync
    记录了262144+0 的读入
    记录了262144+0 的写出
    2147483648字节(2.1 GB)已复制，8.78009 秒，245 MB/秒


📌 网速: 上传/下载/ping

服务器下载速度: 
    或者用一键测试脚本来测试下载等速度,直接运行就可以了:
    🔅 wget freevps.us/downloads/bench.sh -O - -o /dev/null | bash

    下载个文件到服务器试试就能知道下载速度是多少.
        [root@localhost ~]🔅 wget https://cachefly.cachefly.net/100mb.test
        --2017-04-01 08:51:36--  https://cachefly.cachefly.net/100mb.test
        正在解析主机 cachefly.cachefly.net... 205.234.175.175
        正在连接 cachefly.cachefly.net|205.234.175.175|:443... 已连接。
        已发出 HTTP 请求，正在等待回应... 200 OK
        长度：104857600 (100M) [application/octet-stream]
        正在保存至: “100mb.test”

        100%[====================================>] 104,857,600 79.9M/s   in 1.3s

        2017-04-01 08:51:37 (79.9 MB/s) - 已保存 “100mb.test” [104857600/104857600])


📌 服务器出口速度: 也就是我们从服务器上下载文件的速度.








📌 Ping 值














❤️  搭建 & 配置 SS

帮瓦工的控制台里就可以快捷的安装ss. 这步就不说了
安装ss 看这个教程 http://www.jianshu.com/p/36e55c289d65
我们从 安装好后开始说.也就是进行ss配置.


📌 配置
  vi /etc/shadowsocks.json
  会自动建立一个空白文件.
  这个就是 ss 的主要配置文件.
  帐号、密码、端口、加密方式 都是这里修改的.

  复制下面的模板 稍微修改下就可以了.
  {
  "server":"0.0.0.0",
  "local_address": "127.0.0.1",
  "local_port":1080,
  "port_password":{
    "443":"mima12345",
    "6666":"mima12345"
  },
  "timeout":600,
  "method":"aes-256-cfb"
  }

  Server:         自己服务器的公网IP地址
  Port_password:  端口(1-65535) 推荐443;  后面是密码.
  method          加密方式. 


📌 启动/暂停服务

    前台启动:  可以看到详细的日志.
        ssserver -c /etc/shadowsocks.json

    后台启动:  
        开始：ssserver -c /etc/shadowsocks.json -d start
        结束：ssserver -c /etc/shadowsocks.json -d stop
        有问题 就先stop 在start. 


📌 设置开机启动
    vi /etc/rc.local，
    将里面的最后带有ssserver的删除（双击字母d），
    加入ssserver -c /etc/shadowsocks.json -d start,
    再wq保存退出。

查看当前版本: sslocal --version






ss 免费服务网站. 流量用不掉. 那就分享出去.
管理帐号 你需要一个 用户管理面板: ss panerl




ss 编辑PAC 网址规则.
有时候访问某个网站. 用pac 发现打不开. 
有懒得去开全局.
这时候就可以 用pac了.



















❤️ 本地 SS 客户端
可选值:
Surge 神器. 收费几百块.但是确实是最好的.最稳定最快的.
SpechtLite: Surge阉割版本.免费,配置稍麻烦 比其他客户端快很多!!!!
Shadowsocks  最常见了. 不怎么好, 但是配置简单.



📌 Spechtlite 教程: (Mac OS)

    1. open profile folder 
      .yaml后缀的文件就是配置文件.
      你可以给一个配置文件 设置一个帐号.
      也可以给一个配置文件下设置多个帐号.
      我们选一对一的.

    apdpter 建议一个文件一个帐号.没用的adapter删除. 
    - id: adapter1
        type: ss
        host: hk02-14.ssv7.net
        port: 23192
        method: AES-256-CFB
        password: subWfpPAbchP

    2. Speed adapter 
      指定的延迟时间可以指定用那个帐号
    在设置的 delay （单位毫秒）后发送请求，
    哪个节点率先响应，那网络请求就走哪个节点，

    3. 重启软件  选择一个配置文件就可以了.也简单的.




    软件使用:
    Set as system proxy ：设置为系统代理，正常使用必须打开；
    Allow Clients From Lan ：局域网内分享代理，别人也能用你电脑翻墙
    Use dev channel ：接受测试版本推送；
























