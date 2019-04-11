##  基本定义

	vpn，virtual private network， 虚拟专有网络。

	
##  工作原理

	主机A -> vpn设备1 --------- vpn设备2 -> 主机B

	（1）主机A建立分组，将其IP地址作为源地址，将主机B的IP地址作为目标地址，
		将分组发送到VPN设备1，通常是网关。
	
	（2）分组到达VPN设备1，VPN设备1在分组中添加一个新头。
		将分组的源IP地址改成自己的IP地址，将目标IP地址改成对等vpn设备2的IP地址，然后发送。
		
	（3）分组通过Internet到达vpn设备2，vpn设备2解析出主机A的的原分组，根据原分组的IP地址信息进行转发。


## 关键技术

###  1. 隧道化协议（Tunneling Protocol）

	隧道技术是将分组封装（capsule），包括PPTP/L2TP/IPSec/GRE/GTP。

	隧道技术是一种使用互联网在

###  2. 认证协议

	在远程访问vpn中，使用了用户名及口令，用来判断用户是否有权限访问。

	PPP采用PAP和CHAP等规范进行认证。包括PPTP/L2TP。

### 3.  加密技术

	加密技术由IPSec ESP实现。