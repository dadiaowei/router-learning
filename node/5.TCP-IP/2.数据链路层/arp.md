
## 1. 基本定义
	
		ARP（Address Resolution Protocol，地址解析协议）

        ARP协议是局域网中用来进行地址解析的协议，将IP地址映射到MAC地址。

        （1）当PC1要给PC2发送报文时，它首先检查本地的ARP缓存。

        （2）如果没有PC2的MAC地址，则向网络发送一个广播的ARP Request报文，表示请求解析PC2（172.16.1.2）的MAC地址。

        此报文的目的MAC地址为广播地址FF:FF:FF:FF:FF:FF。

        （3）此时网络中的所有设备都会接受到该ARP广播，但是只有IP地址与ARP请求中的IP地址相关的设备（PC2）才会回复。

        PC2回复给PC1一个单播的ARP Reply报文，包含PC2的MAC地址。

        （4）当PC1收到ARP单播后，将此条目加入到ARP缓存中，用于后续发送。