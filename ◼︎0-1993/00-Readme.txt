🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸常用黑客工具🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸
                        工与善其事，必先利其器

🔸 Wireshark(抓包利器)


🔸 Nmap（网络探测工具和安全/端口扫描器）


🔸 Arpspoof(ARP欺骗）
    不断的向攻击对象发送ARP数据包，包内容为“我是XXX，请把发给XXX的数据包发给我”


🔸 Ettercap(数据包嗅探和篡改)
    Ettercap，“中间人”攻击利器，ARP欺骗、DNS欺骗、数据包替换等等，十分强大


🔸 Driftnet （网络包图片解析器）
    抓取经过本机的网络数据包中的图片并显示，同时支持抓取和显示音频文件




















🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸🔸






渗透测试执行标准:  Penetration Testing Execution Standard PTES
信息收集nmap ➜ 漏洞分析nessus ➜  渗透攻击metaspolit


🔵 MSF 模块组成：

    🔸Exploit是攻击模块，
        基本上目前所有的操作系统在Metasploit Framework上均有对应的攻击模块；

    🔸Auxiliary是辅助模块，
        用途非常广泛，它可以作为扫描器、拒绝服务攻击工具、Fuzz测试器，以及其他类型的工具；

    🔸Payload是在目标系统被攻陷之后执行的代码，如添加用户账号，获取shell交互权限等；



交互:


作为一个渗透测试者，必须要把通过对目标网络进行各种扫描以获得足够的信息作为自己的职责。
扫描目标计算机上运行的服务、开放的端口，以及验证这些端口上运行着的全部服务，
然后判断这些服务中哪些是可以被攻击的，并且决定如何利用它们作为入侵目标的通道。


这意味着如果他们看到一个Windows操作系统在运行，
将会选择专门针对Windows操作系统的渗透攻击模块（exploit）

在这台服务器上运行的网站中的页面都是.asp或者.aspx类型。
在这种情况下，我们可以选择针对Windows的渗透攻击模块和针对微软互联网信息服务（Internet Information Services，IIS）的测试工具









❤️ 基础:

help 会列出所有可用命令.



渗透攻击模块（Exploit）：
    这是一段程序，运行起来的时候会利用目标的安全漏洞进行攻击。

攻击载荷模块（Payload）：
    这段程序会在成功对目标完成一次渗透攻击之后在目标计算机上开始运行。基本上它能帮助我们在目标系统上获得需要的访问和行动权限。

辅助模块（Auxiliary）：
    这里包含了一系列的辅助支持模块，包括扫描模块、fuzz测试漏洞发掘模块、网络协议欺骗以及其他一些模块。

编码器模块（Encoder）：
    编码器模块通常用来对我们的攻击模块进行代码混淆，来逃过目标安全保护机制的检测。目标安全保护机制包括杀毒软件和防火墙等。




❤️ 主要命令:


use [Auxiliary/Exploit/Payload/Encoder]

show [exploits/payloads/encoder/auxiliary/options]

set [options/payload]

setg [options/payload]



run

exploit

back

Info

Search

check
Sessions
















