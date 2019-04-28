# easyXssPayload

XssPayload

Payload都在easyXssPayload.txt咯 详细用法待续。


### 0x01 前言

xss的定义：

> 即Cross Site Scripting. 为了与"CSS"不混淆，故简称XSS.


xss的作用：

* 窃取cookie
* 伪造请求
* 钓鱼/蠕虫

xss的挖掘：

> 见缝就插

透过人工/机器挖掘到xss的方法不计其数，本文也仅研究其中一种。

力求**简单**，**暴力**，**有效**。

![15563615439939.jpg](https://xzfile.aliyuncs.com/media/upload/picture/20190427195711-97687cb0-68e3-1.jpeg)




### 0x02 分析

反射型的xss各大厂，SRC均不接收，再聊xss也就只针对储存型的。

常见可存入输入字符串的地方：

> 邮件、留言、BBS、在线客服、投稿、新建xxx。

常规fuzz测出过滤了哪些字符后，找出没被过滤的字符来进行拼接，构造有效Payload于代码功底弱的人而言是件痛苦且消耗时间的事，那么能不能暴力的解决这个问题？

如果能提前把各种标签触发的xss，各种编码绕过的xss集中在一起来批量测试，那么，能！


![15563630975318.png](https://xzfile.aliyuncs.com/media/upload/picture/20190427195732-a3d4e416-68e3-1.png)



基本思路：提前备好大量Payload，批量插入，观察反应，定位有效Payload。

以某邮箱为例：

![15558573734520.jpg](https://xzfile.aliyuncs.com/media/upload/picture/20190427195857-d61a0708-68e3-1.jpeg)


先换编辑模式未切为Html。（避免被原有标签干扰）

![15563644402702.jpg](https://xzfile.aliyuncs.com/media/upload/picture/20190427195917-e21ee258-68e3-1.jpeg)


![15563641896879.jpg](https://xzfile.aliyuncs.com/media/upload/picture/20190427195936-ed7b60c2-68e3-1.jpeg)


根据弹窗提示，快捷定位到有效的Payload：

![15563643415822.jpg](https://xzfile.aliyuncs.com/media/upload/picture/20190427195948-f500c15c-68e3-1.jpeg)




### 0x03 总结

这种方式挖掘存储型xss的速度应该胜过使用工具扫，人工绕过，缺陷也很明显，难以尝试真正新颖的绕过手法，Payload的也需经常更新，保证时效性。

项目地址：

```
https://github.com/TheKingOfDuck/easyXssPayload
```

### 0x04 彩蛋

B：

![15563658770778.jpg](https://xzfile.aliyuncs.com/media/upload/picture/20190427200002-fd60e07a-68e3-1.jpeg)



A：

![15563656945595.jpg](https://xzfile.aliyuncs.com/media/upload/picture/20190427200021-08943726-68e4-1.jpeg)



T：

![15563660153777.jpg](https://xzfile.aliyuncs.com/media/upload/picture/20190427200032-0f1416ca-68e4-1.jpeg)


都是存储型


![15563661154148.jpg](https://xzfile.aliyuncs.com/media/upload/picture/20190427200046-1761bd8c-68e4-1.jpeg)






