# 1. 概述

        PPP（Point-to-Point Protocol）协议是一种在点到点链路上传输、封装网络层数据包的数据链路层协议。

        PPPoE（PPP over Ethernet）属于链路层协议，主要功能是在以太网提供点到点的连接，采用C/S架构，建立PPP会话，以及封装PPP数据包。

        PPPoE包含发现（Discover）和会话（Session）两个阶段，并通过以太网的类型域（Ether_Type）进行区分。

        PPPoE报文包含固定格式的报文头和可变长度的payload（版本、类型、代码、会话ID、长度、payload负载）。

# 2. PPPoE发现的四个阶段

## （1）PADI：PPPoE Active Discovery Initial

        因为笔记本一开始不知道拨号服务器的MAC地址， 所以广播了一个PADI报文。

        该报文包含了两个标记：主机唯一标识；服务名称。

        如果服务名称为空，则说明笔记本可以接受任何服务器的服务。

##（2）PADO：PPPoE Active Discovery Offer

        所有服务器接受到广播报文后，如果它可以提供相应的服务，则单播回复一个PADO报文。

        该报文包含服务器的名称。

##（3） PADR：PPPoE Active Discovery Request

        笔记本选择最先收到的Offer报文对应的服务器，并单播一个PADR报文。

##（4）PADS：PPPoE Active Discovery Session-confirmation

		服务器并给笔记本发送一个PADS报文，该报文包含会话ID。

        Discovery阶段完成之后，笔记本和服务器都知道了对方的MAC地址，并通过会话ID维护唯一的会话。

# 3. PPPoE会话的两个阶段

        会话阶段分成两个部分：PPP认证协商；PPP报文传输。

##（1）LCP协商

        协商双方互相发送一个Config-Request报文。

        如果双方都回应了Config-ACK，则标志LCP链路建立成功。

        LCP协商包括认证方式（PAP或者CHAP）、最大接收单元MRU（Maximum Receive Unit）。

        一般而言，MRU和MTU取值相同，PPPoE的最大MTU不能超过1492。

        计算方法如下：

        	以太网帧大小限制：[64, 1518]

        	去掉以太网帧头18字节，去掉PPPoE头8字节，得到1492Byte。

##（2）认证（PAP或者CHAP）

        PAP明文传输用户名和密码；

		CHAP为三次握手验证协议，安全性较高。

##（3）NCP协商

        NCP的主要功能是协商PPP报文的网络层参数，如：IP地址、DNS服务地址。

# 参考教程
		
		[PPPoE报文格式及交互详解](https://blog.csdn.net/xinyuan510214/article/details/79635015)