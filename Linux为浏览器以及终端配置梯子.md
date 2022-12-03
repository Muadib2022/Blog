---
title: Lniux为浏览器以及终端配置梯子
date: 2018-11-1５ 12:42:08
summary: Lniux为浏览器以及终端配置梯子
tags: 
- Linux
- shadowsocks
categories: Linux

---

# Lniux为浏览器以及终端配置梯子



准备：一台能正常上网的电脑、Linux Ubuntu系统、Google Chorme浏览器、shadowsocks-QT5
##GUI版本

### 安装Shadowsocks-QT5

shadowsocks-QT5下载地址：

[]: https://github.com/shadowsocks/shadowsocks-qt5/releases

![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Linux%E6%B5%8F%E8%A7%88%E5%99%A8%E4%BB%A5%E5%8F%8A%E7%BB%88%E7%AB%AF%E7%BF%BB%E5%A2%99/1.png)

下载第一个**Shadowsocks-Qt5-3.0.1-x86_64.AppImage**直接双击就可以运行

如果你是第一下安装.AppImage后缀的文件，那么你还需要安装一个管理工具**appimagelauncher**

下载地址：

[]: https://github.com/TheAssassin/AppImageLauncher/releases

![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Linux%E6%B5%8F%E8%A7%88%E5%99%A8%E4%BB%A5%E5%8F%8A%E7%BB%88%E7%AB%AF%E7%BF%BB%E5%A2%99/2.png)

*AppImageLauncher 支持 Ubuntu、 Debian、Netrunner 和 openSUSE。如果你使用 Ubuntu 18.04，请确保你下载的 deb 包的名字中有“bionic”，而其它的 deb 是用于旧一些的 Ubuntu 版本的。*

下载好之后开始安装

- 给它执行的权限，使它可执行

  ```
  chmod a + x Subsurface * .AppImage
  ```

- 执行

  ```
  $ ./Subsurface*.AppImage
  ```

**AppImageLauncher**：该程序可让你轻松运行 AppImage 文件，而无需使其可执行。但它最有趣的特点是可以轻松地将 AppImage 与你的系统进行整合：AppImageLauncher 可以自动将 AppImage 程序快捷方式添加到桌面环境的程序启动器/菜单（包括程序图标和合适的说明）中。

```
我第一次双击它时（安装好了 AppImageLauncher），AppImageLauncher 提供了两个选项：

“Run once**”或者“Integrate and run”。

点击 “Integrate and run”，这个 AppImage 就被复制到 `~/.bin/` （家目录中的隐藏文件夹）并添加到菜单中，然后启动该程序。

要删除它也很简单，只要您使用的桌面环境支持桌面动作就行。例如，在 Gnome Shell 中，只需右键单击“活动概览”中的应用程序图标，然后选择“Remove from system”：

摘录自：https://linux.cn/article-9655-1.html
```

安装好shadowsocks-QT5之后，就可以进入GUI界面进行配置了。但是配置好之后还是不能上网，因为没有设置代理，可以使用Google Chorme的插件Proxy SwitchyOmega，也可以选择Ubuntu设置中的网络设置，我用的第二种。

### 2.配置pac代理文件，让代理的时候根据pac的内容自动走代理。

具体如何生成的时间太久忘记了，当时那篇博客也没找到，所以先放在这里，之后再动。

### 3.设置自动代理，代理文件路径填上面的pac文件的路径file:///xxx/xxx/xxx.pac

![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Linux%E6%B5%8F%E8%A7%88%E5%99%A8%E4%BB%A5%E5%8F%8A%E7%BB%88%E7%AB%AF%E7%BF%BB%E5%A2%99/3.png)

### 4.我打开shadowsocksqt5，输入服务器，端口之类的代理信息，连接之后就能继续上了。

更新：建议谷歌浏览器使用谷歌浏览器上的SwichyOmega代理插件，其他浏览器可以去网上百度，也有对应的插件。


## 终端版本

Linux会自带Python，这里会用到Python的pip工具

### 1.安装pip

#### 1.1首先检查你的系统是否安装了pip

```
pip --version
```

如果未安装，执行1.2，否则直接执行1.3

#### 1.2 安装pip

```
sudo apt-get install python-pip
```

如果你的linux版本为Centos可能用不了这个命令，可以使用以下方法安装

```
$ curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py   # 下载安装脚本
$ sudo python get-pip.py    # 运行安装脚本
```

Python3的话

```
$ sudo python3 get-pip.py    # 运行安装脚本。
```

执行完毕，重新执行1.1检验是否安装成功

### 2 安装shadowsocks

```
pip install shadowsocks
```

安装成功之后，在/etc中创建shadowsocks.json

```
vim /etc/shadowsocks.json
```

文件配置内容如下

```
{
    "server":"xxx.xxx.xxx.xxx",   //你的服务器地址
    "server_port":10844,          //你的服务器端口
    "local_address": "127.0.0.1",
    "local_port":1080,            //你的本地端口
    "password":"xxxxxx",   		  //你的密码
    "timeout":300,
    "method":"xxxxxx",     		  //你的加密方式
    "fast_open": false
}
```

配置好保存退出之后

启动shadowsocks与停止shadowsocks

```
启动：sslocal -c /etc/shadowsocks.json -d start
```

```
停止：sslocal -c /etc/shadowsocks.json -d stop
```

到了这里你会发现还是不正常，我们还需要一个代理

### 3 永久全局代理版本

在～/.bashrc中（最后面）加入以下代码

```
export http_proxy="http://127.0.0.1:你的本地端口"
export https_proxy="https://127.0.0.1:你的本地端口"
```
###我使用的灵活代理配置
alias setproxy="export ALL_PROXY=socks5://127.0.0.1:1080"
alias unsetproxy="unset ALL_PROXY"
alias ip="curl -i http://ip.cn"


检测是否成功

![](https://personal-blog-1253377966.cos.ap-beijing.myqcloud.com/Linux%E6%B5%8F%E8%A7%88%E5%99%A8%E4%BB%A5%E5%8F%8A%E7%BB%88%E7%AB%AF%E7%BF%BB%E5%A2%99/4.png)

## 参考博客地址

https://blog.csdn.net/hejunqing14/article/details/52670341 

https://blog.csdn.net/liuqinglong_along/article/details/52463200 

[^如有错误望指正]: 1456438724@qq.com
