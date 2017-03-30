❤️ 项目简介:❤️

充分利用 VPS 实现各种功能:

1. 搭建 ss
2. 搭建 vpn
3. 搭建 ngrok
4. 搭建 数据库.
5. 搭建认证系统


📌帮瓦工密码:
  一个是控制台的密码.
  一个是ssh的密码. 不一样的..


📌 ssh 密码修改

  1. 查看ssh 初始登录密码
    控制台 → root password modification 
  2. 登录ssh
    ssh -p 27401 root@23.105.192.96
	3. 修改密码
	  passwd → 输入两次密码 就改掉了.



📌 ssh 免密码登录 (密钥登录)
    1. 本地生成对密钥先.
    2. 服务器用户目录建立 .ssh 文件夹, 并给700权限
    3. 把本地公钥用scp传到服务器
    4. 服务器上把公钥加到公钥验证列表.
    5. 当你ssh服务器.服务器就可以自动连接了.

    Mac OS 密钥默认生成路径:
        cd /Users/v/.ssh/
        有个 id_rsa.pub 就说明生成成功了.

    上传文件:
        1. 本地终端 cd /Users/v/.ssh/

        ✘✘∙𝒗 .ssh scp -P 27401 -r id_rsa.pub root@23.105.192.96:~/.ssh/
        root@23.105.192.96's password:
        id_rsa.pub                         100%  742     4.2KB/s   00:00 

            P             必须大写.
            27401         服务器的SSh端口
            root          服务器的ssh用户名
            23.105.192.96 服务器IP

    2.  注册公钥文件: 把你的公钥添加到公钥验证列表.
        cat ~/.ssh/id_ecdsa.pub >> ~/.ssh/authorized_keys
        // 就是把上传上去的文件里的内容 全部追加到authorized_keys这个文件 后面.
        
        也可以直接重命名上传的文件.  mv id_rsa.pub authorized_keys
        这样的话 整个验证列表中 只有你的公钥. 这个服务器 只有你能ssh 秘钥免密码登录了.





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




❤️ 优化 SS 速度
详细参考: https://github.com/phuslu/goproxy/issues/186
大概步骤:

1. 调整搬瓦工Shadowsocks的加密方式
    rc4-md5 相对aes-256-cfb来说可能加密方式更弱，
    但加密速度是后者的好几倍，
    看你自己怎么取舍了....

2. 服务器端口一定要使用默认的443端口（很重要）

3. 增加系统文件描述符的最大限数
    vi /etc/security/limits.conf
    增加以下两行
    soft nofile 51200
    hard nofile 51200


📌📌📌📌📌 巨大提速 📌📌📌📌📌
    用了帮瓦工 网速慢. 丢包高.. 
    其实是本地网络服务商坑.不怪帮瓦工. 
    这个坑 可以解决.
    用了下面的神器.ssh进去 延迟少了好几倍!!!!

    Net-Speeder是一个linux软件，主要目的是为了解决丢包问题，
    实现TCP双倍发送，也就是同一份数据包发送两份。
    这样的话在服务器带宽充足情况下，
    丢包率会平方级降低。网络传输速度也会有所提升。
    详情参考:
    http://banwagongvpn.lofter.com/post/1d541acc\_7b4bfc0




❤️ 本地 SS 客户端
可选值:
Surge 神器. 收费几百块.但是确实是最好的.最稳定最快的.
SpechLite: Surge阉割版本.免费,配置稍麻烦 比其他客户端快很多!!!!
Shadowsocks  最常见了. 不怎么好, 但是配置简单.





