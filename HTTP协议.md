## HTTP协议

HTTP协议优点类似于文本的协议,网络里的接口协议

是Tcp/udp协议里的一种。

HTTP：GET（获取）、POST（更新）、PUT（更新，用的少）、DELETE（删除）

url:     XXX.com/api/v1/login   ?userid=?

- api接口
- v1表示第一版
- login表示这是登录的
- param： ?userid=?这是参数

header：     content-type   \      cos-tolcen   \    session   ...

body： 

（Get请求没有body，POST有的有有的没有body）

[在线HTTP接口测试 程序员工具-程序员开发工具大全 在线小工具网站](https://tool.p2hp.com/tool-online-http)

[在线HTTP接口测试 - HTTP GET/POST模拟请求测试工具,JSON模拟请求](https://www.sojson.com/http/test.html)

例如bilibi网址来看Get请求

![93](.\imageruance\image-93)

![96](./imageruance/image-96)

返回就是html源码

![94](.\imageruance\image-94)

如果变成Post请求呢

![95](.\imageruance\image-95)

![97](./imageruance/image-97)

请看下图为啥可以加参数？因为param可有可无，body不一定有，但是前面一定有。

![98](./imageruance/image-98)

下图请看，假如我想让它返回json，但是它是否能返回我想要的不一定，比如下面返回就不是。

![99](./imageruance/image-99)

练习

![100](./imageruance/image-100)

[在线HTTP POST/GET模拟请求api接口http请求测试工具](http://post.wxai.club/)

![101](./imageruance/image-101)

[【接口开发】支持http请求的api接口测试网站，适合练习建议收藏！_网页请求测试网站-CSDN博客](https://blog.csdn.net/weixin_45532870/article/details/141814678)

![102](./imageruance/image-102)

HTTP版本

1.0    单次链接   （半双工） 

-------》

《-------

eg.两个人发短信：发一条，等回复，再发下一条

2.0    （半双工）

-------》

《-------

《-------

eg.微信聊天：可以同时聊多个话题，但如果网络卡了，所有话题都卡住

3.0    （全双工）

-------》

《-------

-------》

《-------

eg.多个独立电话线路：每个话题一条专线，哪条卡了不影响其他

单工：数据只能单向传输

半双工：双向传输，但不能同时进行（交替）

全双工：双向传输，可以同时进行

## POST、PULL

干饭系统：

GET:www.ganfan.com/api/v1/todaynewhowmuchfoodcanieat?userid=1

返回：米（500g）菜（500g）

GET:www.ganfan.com/api/v1/image/mi1

返回：盘锦大米

![103](./imageruance/image-103)

![104](./imageruance/image-104)

```
【带 CDN 的核心本质】
源站不再直接面向用户，而是“藏”在 CDN 后面。
CDN 是用户的“前台接待”，源站是“后台办公室”。
用户只跟前台说话，前台解决不了才去找后台。
```

```-
用户请求路径：用户 ──> CDN 节点 ──(可能)──> 源站
                    ↑
              大部分请求到这里就结束了
              只有缓存未命中才继续往后走
```

问题：比如现在23:59吃面条主食，正常到第二天刷新吃别的，但是CDN(比如每天早上八点刷新，或者隔20分钟刷新)，这样CDN 就不行不适合。所以CDN适合用于图片、文件、视频等东西，不是老刷新更新。接口情况不能用CDN。

push：服务器主动把数据发给客户端。（实时性好，但要是客户端太多处理不来，会被压垮）

eg.微信发消息、点赞 | （和钱有关的敏感度高）订单、物流

pull(轮询)：客户端主动向服务器要数据。（客户端自己控制，不易崩溃，但可能有延迟）

客户端这里发（Get）去服务器，服务器有三件事要做：

- 会话升级（把HTTP请求一次中断升级成不断连接）HTTP+SSE或streamablehttp

- 保存句柄（“芒果的会话”给它存一下）

- 发送心跳，心跳就是验证句柄是否还好用；不好用就句柄扔掉，拜拜，重新连接。（芒果给服务器发完消息，服务器高斯它，为啥？？？）<eg,我开始用wifi网，卡了，换成流量，请问ip一样吗，不一样>

支付用pull，eg.要是推送交钱时候（push），我手机网断了，服务器说我发了，但是我没收到我的钱！！！ 我会爆炸。

eg.每小时对会话句柄发“你还有多少大米饭要吃”

**这两种方法是都可以使用，要看当下啥情况更适合**

**判断使用哪个，从数据的频率来讲**

客户端ws://.....用websockte(没有会话升级)