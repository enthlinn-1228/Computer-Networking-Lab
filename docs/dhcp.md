# DHCP 动态主机配置协议
DHCP 使用客户服务器模式，报文基于 UDP。

## 连接过程
1. 服务器被动打开 UDP 端口 67，等待客户端的请求报文
2. 客户端使用 UDP 端口 68 发送请求报文
3. 需要 IP 地址的主机在启动时广播发送 DHCP 发现报文（255.255.255.255），本地网络上的主机都能收到，但只有 DHCP 服务器才会响应。
4. 收到 DHCP 发现报文的服务器都会发出 DHCP 提供报文，如果有多个 DHCP 服务器，则客户端在其中选择一个，并向所选择的服务器发送 DHCP 请求报文。
5. 被选择的 DHCP 服务器发送确认报文 DHCPACK（DHCP 服务器在数据库查找配置信息，如果找不到，则从地址池分配一个 IP 给该计算机）。从这时起，客户就可以使用分配的 IP 地址了。
6. 服务器分配的 IP 地址是临时的，租用期为多长由服务器决定，客户端也可在发送报文中提出对租金期的要求。
7. 租用期到了一半，客户端发送请求报文，要求更新租用期。如果服务器不响应此报文，则在租用期到了 87.5% 时再次发送请求要求更新租用期。
8. 如果服务器同意，客户端则获得一个新的租用期，否则要立即停用现在的 IP 地址，重新申请 IP。
9. 客户端可随时发送释放报文终止服务器所提供的租用期。

![](https://github.com/woai3c/Computer-Networking-Lab/blob/master/imgs/dhcp.png)

![](https://github.com/woai3c/Computer-Networking-Lab/blob/master/imgs/dhcp2.png)

## DHCP 报文格式
![](https://github.com/woai3c/Computer-Networking-Lab/blob/master/imgs/dhcp3.png)
