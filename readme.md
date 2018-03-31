## Computer Networking Project - C/S and P2P demo
---
A python project of Computer Networking Course

Note that python will use tcp if we use socket packet and use its connection.

Both the C/S project and P2P project require a well designed protocol in application layer. 

### What is Protocol in Application Layer
A protocol should includes：

1. Code Control(decoder and encoder).
2. Procedures Control

### C/S Transfer Protocol Model

TCP principles(the contents that can be found in the textbook is omitted):

TCP disadvantages:

1. 粘包、半包、分包。
    reasons:
    粘包：发送方将较小的数据包进行合并，或者接收方没有将数据包即使取走，一次性取出了多个数据包。

    半包：指接受方没有接受到一个完整的包，只接受了部分，这种情况主要是由于TCP为提高传输效率，将一个包分配的足够大，导致接受方并不能一次接受完。

    分包：可能是IP分片传输导致的，也可能是传输过程中丢失部分包导致出现的半包，还有可能就是一个包可能被分成了两次传输，在取数据的时候，先取到了一部分（还可能与接收的缓冲区大小有关系），总之就是一个数据包被分成了多次接收。
    
    什么时候需要考虑粘包的情况?  

    如果发送数据无结构，如文件传输，这样发送方只管发送，接收方只管接收存储就ok，也不用考虑粘包。
    注意粘包情况有两种，一种是粘在一起的包都是完整的数据包，另一种情况是粘在一起的包有不完整的包。

    solutions:

    + adding delimiters to the packets.
    + adding length information in the packets.
    + RingBuf
    
    What is RingBuf?

    感觉没什么用。
    
    Hand in hand to design a application  protocol

    协议分类：

    + 按编码分类：
        * 二进制
        * 明文
        * 混合
    + 按协议边界
        * 固定边界，即能够明确得知一个协议报文的长度。
        * 模糊边界，即无法明确知道协议报文的长度，通常需要通过某些特定的字节来界定报文是否结束。

    协议评判：

    + 高效，包括打包解包，数据压缩率
    + 简单
    + 易于扩展
    + 容易兼容

    知识储备

    + 大小端
    + 网络字节序，一般是大端的。
    + 序列化与反序列化

    协议设计

    协议头和协议体，注意协议魔数


### P2P Transfer Protocol Model



### Programming Details
+ how to use socket in python?

    [A brief tutorial](https://gist.github.com/kevinkindom/108ffd675cb9253f8f71)

+ how to design a protocol?

    [A hand in hand tutorial](https://segmentfault.com/a/1190000008740863) 
    (learning its codes carefully!)