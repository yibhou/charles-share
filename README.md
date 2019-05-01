#### 1 Charles 简介 

![charles_hdr.f03a5646](images/charles_hdr.f03a5646.png)

Charles 是一个支持多平台的 HTTP 代理器、HTTP 监控、反向代理器。它能够让开发者查看本地机器与互联网之间的所有 HTTP 以及 SSL/HTTPS 传输数据。包括请求数据、响应数据 以及 HTTP 头部信息（包括 Cookie 和缓存信息）。

官网： https://www.charlesproxy.com/

##### 1.1 Charles 主要功能

- 支持SSL代理。可以截取分析SSL的请求。
- 支持流量空盒子。可以模拟慢速网络，以及等待时间（latency）较长的请求。
- 支持重发网络请求，方便后端调试。
- 支持修改网络请求参数。
- 支持网络请求的截获和动态修改。
- 支持端口映射。
- 支持反向代理。
- 支持SOCKS。

##### 1.2 界面介绍

![G8V1N51AOL6%M3MB7_R{X](images/1.2.1.jpg)



![794HAFRD`O$GNWBF1ZVO552](images/1.2.2.jpg)

 ![1PX89(S4)NRM$N2%A39%}V](./images/1.2.3.jpg)

#### 2 下载与安装

1. 下载最新版v4.0.2 （2017.03.15）

   到网盘下载 Charles404.dmg 安装包，下载链接: https://pan.baidu.com/s/1hr332ao 密码: 8ddk

2. 安装Charles

   打开 Charles402.dmg 包，后将 Charles 拖到 Application 目录下即完成安装。

3. 安装完毕后，进行“upgrade”，方法很简单: 

   Mac 将 `charles.jar` 覆盖到 `Contents/Java` 下；

   Windows 将 `charles.jar` 覆盖到 `安装目录/lib` 下。

#### 3 功能介绍

##### 3.1 使用 Charles 首先打开代理功能

在Charles菜单栏上选择Proxy - Mac OS X Proxy，或者点击右上方Charles小图标直接选择 Mac OS X Proxy，使得请求转给Charles代理。 

代理的相关设置可以在菜单栏Proxy-Proxy Setting.. 中找到。如果抓取不到浏览器的请求，请检查下浏览器代理设置是否使用本地代理，或者直接将代理服务器设置成 127.0.0.1:8888 也是可以的。

![1](images/3.1.1.png)

##### 3.2 视图模式

Charles支持两种模式，`Structure`和`Sequence`，其优点分别如下：

- Structure：可以很清晰的看到请求的数据结构，而且是以域名划分请求信息的，可以很清晰的去分析和处理数据。![a](images/3.2.1.jpg)
- Sequence：可以很清晰的看到全部请求，不用一层一层的去点开，这里是以数据请求的顺序去执行的，也就是说那个请求快就在前面显示。![b](images/3.2.2.jpg)

##### 3.3 重复请求功能

![@QH3~$`ID5MPDN(1L5QNY](images/3.3.1.jpg)

使用Repeat Advanced 还可以指定请求次数，这个功能非常有用，比如用来测试短信轰炸漏洞很方便。

![333](images/3.3.2.jpg)

![888](images/3.3.3.jpg)

##### 3.4 查找功能

点击工具栏的放大镜或者使用快捷键command+F 即可打开查找面板：

![find](images/3.4.1.jpg)

双击查找结果会跳到想要的结果：

![find2](images/3.4.2.jpg)

##### 3.5 过滤网络请求

对网络请求进行过滤，只监控向指定服务器发送的请求。

在菜单栏选择 Proxy - Recording Setting。然后选择Include，选择添加一个行，然后填入需要监控的协议、主机地址、端口号，即可监控指定服务器的请求。

![4](images/3.5.1.png)

##### 3.6 Focus 功能

使用 Focus 功能指定想要查看的域名，可以避免这个域名相关的请求淹没在茫茫请求当中。当然使用“Structure”视图也可以避免这个问题。

对想要Focus的域名，右键菜单-选择Focus，这个域名就会添加到Focused列表，可以在这里找到：

![f1](images/3.6.1.jpg)

 ![f2](images/3.6.2.jpg)

##### ![f3](images/3.6.3.jpg)

##### 3.7 控制网速

在Charles的菜单上，选择Proxy-Throttle Setting，在弹出的对话框中，可以选择勾选上Enable Throttling，并且可以设置Throttle Preset的类型。

如果只想模拟指定网站的慢速网络，可以再勾选图中Only for selected hosts选项。然后在对话框的下半部分设置中增加指定的Hosts项即可。

![5](images/3.7.1.jpg)

##### 3.8 构造请求

![45](images/3.8.1.jpg)

点击compose按钮进入下图，就可以随便 添加Headers 或者query参数，HTTP版本支持HTTP1.0/1.1/2.0。

![46](images/3.8.2.jpg)

 点击执行就得到想要的报文了：

![47](images/3.8.3.jpg)

##### 3.9 修改请求

为了调试服务器接口，需要反复尝试不同参数的网络请求。Charles可以方便的提供网络请求的修改和重发功能。

在网络请求上单击右键，选择Edit。即可创建一个可编辑的网络请求。可以修改该请求的任何信息，包括URL、端口，参数等。修改完后，单击Execute按钮，即可发送修改后的网络请求。这对于调试s与服务器端的接口非常方便。

![6](./images/3.9.1.jpg)

![7](./images/3.9.2.jpg)

##### 3.10 设置断点拦截请求响应

 首先开启断点功能，然后再到想要设置断点的请求上，右键设置一个断点，如图所示：

![d1](images/3.10.1.jpg)

 然后我们看看这个断点是否加入到断点设置面板：

![d2](images/3.10.2.jpg)

果然加到这里，而且默认是拦截请求和响应，如果只需两者之一，那就双击另行设置，我这里就不改了：

![d3](images/3.10.3.jpg)

 然后，我们再次发起请求，试下是否生效了：

![d4](images/3.10.4.jpg)

OK，没问题，在请求发送到服务器之前就被我们拦截了，这时，我们可以根据需要修改请求报文，这里我们就默认执行：

![d5](images/3.10.5.jpg)

 断点再一次生效，不过这次是拦截了响应，同样，我们可以在响应返回到客户端之前根据需要修改响应报文：

![d6](images/3.10.6.jpg)

##### 3.11 使用Charles抓取 iOS/Android 设备的网络包

打开 iPhone 设置 - 无线局域网，将手机网络连接到与电脑相同WiFi，点击WiFi详情按钮设置HTTP代理，将其改为手动，然后填写Charles所在电脑的代理IP地址，端口号默认为8888。

![2](images/3.11.1.jpg)

点击返回，设置成功。

此时Charles弹出请求连接的确认菜单，点击 allow 按钮即可完成设置。

![3](images/3.11.2.jpg)

##### 3.12 对HTTPS请求抓包

原理：Charles实现对HTTPS进行抓包，使用的原理就是中间人技术（man-in-the-middle）。Charles会动态生成一个使用自己根证书签名的证书，Charles接收web服务器的证书，而客户端/浏览器接收Charles生成的证书，以此客户端和Charles之间建立HTTPS连接，Charles和Web服务器之间建立HTTPS连接，实现对HTTPS传输信息的抓包。如果Charles根证书不被信任则无法建立HTTPS连接，所以需要添加Charles根证书为信任证书。

 ![1121998-f4aac7356d979e5e](images/3.12.1.png)



首先在电脑上安装Charles证书：菜单栏找到 Help - SSL Proxying - Install Charles Root Certificate 安装证书。![8](images/3.12.2.jpg)

给Mac安装证书：

 ![9](images/3.12.3.jpg)

设置为信任证书：

![1121998-2115212d231e8c90](images/3.12.4.png)

然后回到Charles，因为Charles默认不监听HTTPS请求，所以还需要开启SSL代理功能：在Proxy - SSL Proxying Setting中激活，即勾选 Enable SSL Proxying 选项。并添加域名端口，匹配想要监听的域名端口，这里可以添加`*:443`或`*:*`匹配全部：

 ![10](images/3.12.5.jpg)

如果是需要抓取手机的HTTPS请求，还需要多操作一步，就是在手机上安装相应证书：

同样找到Help - SSL Proxying - Install Charles Root Certificate on a Mobile Device or Remote Browser.. ，按照弹出的提示会让你将手机切换为手动代理到电脑的Charles，然后用浏览器打开提示上面的地址下载安装证书。 

![12](images/3.12.6.jpg)

![11](images/3.12.7.png)

然后就可以随意抓HTTPS包了： ![11](images/3.12.8.jpg)

##### 3.13 Rewrite重写功能

Rewrite 可以通过正则表达式匹配并添加、修改、删除请求或响应中的头部header参数、主体内容、请求参数、响应状态、Host/Path/URL。功能非常强大、配置也非常简单。

首先在菜单栏找到Tools-Rewrite..打开设置面板：

![r1](images/3.13.1.jpg)

![r2](images/3.13.2.jpg)

##### 3.14 Map Local/Remote 

用过Fiddler 的同学，看名字应该可以想象得到这大概是什么功能。其实就类似AutoResponder功能，将请求映射到给定的文件。

可以通过菜单Tools-找到这些功能的设置，这里以Map Local举栗：

![555](images/3.14.1.jpg)

##### 3.15 Firefox 调试

制作个人证书

```bash
brew install openssl
```

```bash
openssl req -new -x509 -days 3650 -extensions v3_ca \
-keyout charles_ca_key.pem -out charles_ca_cert.pem \
-config /System/Library/OpenSSL/openssl.cnf
```

生成 Charles 支持的 PKCS12 格式的证书

```bash
openssl pkcs12 -export -out charles_ca_cert.p12 -inkey \
charles_ca_key.pem -in charles_ca_cert.pem
```

以上步骤生成了三个文件：

- charles_ca_cert.pem - 添加到客户端的CA证书
- charles_ca_key.pem - CA证书的密钥
- charles_ca_cert.p12 - Charles使用的CA证书

然后将 `charles_ca_cert.p12` 导入到 Charles 中，当使用证书前 Charles 会要求输入 passphrase，我上面设置为 `charles`：

![cert1](images/cert.png)

![cert2](images/cert2.png)

将 `charles_ca_cert.pem` 添加到 Firefox：

![cert3](images/cert3.png)

![cert4](images/cert4.png)

![cert5](images/cert5.png)

![cert6](images/cert6.png)

![cert7](images/cert7.png)


#### 4 实践

##### 4.1 HTTP Script 注入

在 Charles 里脚本注入非常简单，只需使用 Rewrite 功能简单的配置一下即可实现：

![re](images/4.1.1.jpg)

这段脚本就是弹出一段文字：

![rr1](images/4.1.2.jpg)

##### 4.2 HTTP Mock

在开发环境，接口经常会挂掉，而且有时这些接口临时找不到人修复的，为了保证开发进度，无奈之下只能利用一些手段Mock数据，刚好，Charles提供了这方面的支持，那么就可以使用 Map Local 映射到本地的json文件，当Charles捕获到这个请求，不管是40X、还是50X，都会本地指向的json文件。

那么看看如何操作：

这里拿兑换密码来举栗，因为要测试修改设置兑换密码接口，但是请求这个接口之前会先请求一个叫/isHasPass的接口，来判断用户是否设置过兑换密码，为了能使用一个账号来反复测试修改兑换密码接口，就必须写一个Mock数据，模拟账号始终未设置过兑换密码，这个json文件内容，将data=1改为0：

```json
{"servertime":1489407444,"callback":[],"data":0,"status":1,"errorcode":"","errorno":0}
```

然后：

![555](images/3.14.1.jpg)

![yyy](images/4.2.1.jpg)



可是，问题来了。Fiddler的AutoResponder提供了许多默认的返回响应码，比如40X，50X等等。貌似 Map Local并没有提供，确实是没有提供，那怎么办呢？还记得前面提到的Rewrite功能吗，它提供了修改响应状态的方式，过程如下：

![777](images/4.2.2.jpg)

##### 4.3 AppStore 抓包

这里拿修改AppStore请求为例，有时候手贱更新了应用，却发现App有bug或更新之后不好用，为了回退到低版本的App，那么可以使用 Charles解决了，这里拿酷狗直播App来试验，尝试下载3.2.0版本：

**启动Charles，开启Charles代理，即Mac OS X Proxy。并且设置允许SSL代理。然后顺手将视图模式改为Structure。这一步不清楚回到上文看看。**

**首先进入AppStore把酷狗直播App所在页面恢复Download按钮：**

![01](images/4.3.0.jpg)



![022](images/4.3.1.jpg)



**然后点击Download下载App，然后到下载框里面选中App按Delete键两次（一次停止下载一次删除下载），这一步是为了获取App的下载信息以及为断点设置作准备：**

![02](images/4.3.2.jpg)

**看到Charles Structure视图的好处了吧，直接看域名找到接口。右侧响应数据包含了最新版本号和历史版本号：**

![03](images/4.3.3.jpg)

**由于这么多id，不知道哪个是3.2.0，所以就需要上文说到的修改请求：**

![z6](images/4.3.4.jpg)

**最终找到3.2.0版本对应的id是819441670：**

![0333](images/4.3.5.jpg)

**OK，接下来就为这个接口设置下断点，并启动断点捕获，然后清空所有请求数据：**

 ![04](images/4.3.6.jpg)

****

**再次回到AppStore酷狗直播页面，点击Command+R刷新页面，使其恢复下载按钮，然后点击Download按钮。**

**回到Charles看看，可看到请求被拦截了，我们可以编辑请求：**

![z1](images/4.3.7.jpg)

![z2](images/4.3.8.jpg)

**点击Execute执行，响应也被拦截了，因为设置断点默认包括请求和响应：**

![z3](images/4.3.9.jpg)

**这里不需要修改响应，直接Execute执行。**

**回到AppStore，已经看到在下载了：**

 ![z4](images/4.3.10.jpg)

**下载完成后，可以看到，酷狗直播是3.2.0了：**

 ![z5](images/4.3.11.jpg)

#### 5 参考文献

- [Charles Documentation](https://www.charlesproxy.com/documentation)
- [如何使用charles对Android Https进行抓包](http://www.jianshu.com/p/3bbf596c9ca6)
- [猫哥网络编程系列：HTTP PEM 万能调试法](https://github.com/kaiye/kaiye.github.com/issues/4)
- [iOS如何下载旧版本应用APP](http://www.xuanfengge.com/ios-how-to-download-old-app.html)
- [Proxying connections from FFOS with Charles](https://muffinresearch.co.uk/proxying-connections-from-ffos/)
