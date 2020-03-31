# network-analysis
其实我主要用这个脚本来查看端口占用情况 , 以及哪个 IP 在拼命跑流量 – –

此脚本包含的功能有：

1 、实时监控任意网卡的流量

2 、统计 10 秒内平均流量

3 、统计每个端口在 10 秒内的平均流量，基于客户端和服务端端口统计。可以看出哪些端口占流量比较大，对于 web 服务器，一般是 80 端口。其它端口受到攻击时，也有可能其它端口流量比较大。所以此功能可以帮助我们端口流量是否正常。

4 、统计在 10s 内占用带宽最大的前 10 个 ip 。此项功能可以帮助我们来查出是否有恶意占用带宽的 ip 。

5 、统计连接状态。此项功能可以让我们看出哪些连接状态比较大。如果 SYN-RECV 状态比较多的话，有可以受到半连接攻击。如果 ESTABLISED 非常大，但通过日志发现没有那么多请求，或者通过 tcpdump 发现大量 ip 只建立连接不请求数据的话，可能是受到了全连接攻击，这时候如果你使用的是 nginx 服务器，可以在配置文件增加 listen 80 deferred 来防止。

6 、统计各端口连接状态。当可能受到攻击时，此项功能可以帮助我们发现是哪个端口受到攻击。

7 、统计端口为 80 且状态为 ESTAB 连接数最多的前 10 个 IP 。此项功能可以帮助我们来找出创建连接过多的 Ip ，进而屏蔽。

8 、统计端口为 80 且状态为 SYN-RECV 连接数最多的前 10 个 IP 。当受到半连接攻击时，此项功能可以帮助我们找到恶意 ip 。

代码下载 : https://github.com/91yun/91yuncode/blob/master/network-analysis.sh

一键执行 :

wget https://raw.githubusercontent.com/91yun/91yuncode/master/network-analysis.sh && bash network-analysis.sh
 

91yun
