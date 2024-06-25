这也是我第一次写博客，先不说废话，直接上源码

```python
from socket import *
from threading import Thread

def recvmsg(seedmsg):
    while True:
        data = seedmsg.recvfrom(1024)
        print('来源:',data[1])
        print('接收文件:',data[0].decode('gbk'))

def sendmsg(seedmsg):
    ip = input('请输入对方通讯ip地址')
    port = int(input('请输入对方端口号'))
    while True:
        text = input('请输入发送内容\n')
        seedmsg.sendto(text.encode('gbk'),(ip,port))


app = socket(AF_INET,SOCK_DGRAM)

app.bind(('IP地址',端口号))

Thread(target=recvmsg,args=(app,)).start()
Thread(target=sendmsg,args=(app,)).start()
```

这个程序依赖的库都是Python自带库

复制两份一样的代码端口号不一样就行

IP地址查询方法：
Windows：Windows键+r 输入cmd
输入指令：ipconfig 回车
端口号：如：8100
1-1023不要填，其他自然数都行，最好是简单的、不被其他软件占用的，如果使用重复的端口，会报错，如果报错可以换一个端口再次尝试

想要测试可以自己给自己发信息。

喜欢的话点个赞
————————————————

版权声明：本文转载于本人在 2020-08-05 发布于CSDN社区的文章，内容有修改，遵循 CC 4.0 BY-SA 版权协议，转载请附上原文出处链接和本声明。
                        
原文链接：https://blog.csdn.net/masud_2020/article/details/107814964