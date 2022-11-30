Network Extension API -> 网络包 捕获和处理 能力

正常数据流动:
| APP --> iOS (Darwin) --Network Extension-|-> Web

沙盒模型:
+--------------------------------------------------------+
|                         iOS
| +-------------------+      +-------------------+
| |      Sandbox      |      | Network Extension |
| |      +-----+      |      +-------------------+
| |      | APP |      |      +-----+
| |      +-----+      |      | XPC |
| +-------------------+      +-----+
+--------------------------------------------------------+

抓包:
myAPP <-IPC-> myXPC <-API-> Network Extension
包名:
com.example.myapp     (myAPP)
com.example.myapp.xpc (myXPC)
组名:
com.example.app (组名相同)

*nix tun 用法:
TUN是一种虚拟网卡
把发送到指定 TUN 的数据转发给指定软件

组合shadowsocket: 软件把数据包通过 ss 的 socks5 代理发送出去
数据 -> TUN -> | APP -> socks5 -> shadowsocket | -> ss服务器
