---
title: Selenium安装配置及基础入门
date: 2019-07-28 03:37:25
categories:
- python
tags:
- 自动化测试
- 爬虫
- selenium
---

*最近面试一家公司，说需要爬取aliexpress.com这个网站．我一看这不是阿里速卖通嘛，分析了很久很久放弃了，最后想想还是用selenium最简单．这里记录一些selenium基本的用法．*

### selenium简单介绍

Selenium是一个用于Web应用程序自动化测试工具。Selenium测试直接运行在浏览器中，就像真正的用户在操作一样。支持的浏览器包括IE（7, 8, 9, 10, 11），Mozilla Firefox，Safari，Google Chrome，Opera等。

Selenium也是一款同样使用Apache License 2.0协议发布的开源框架。

### selenium支持与模式

#### 1、支持平台

WebDriver支持Android和BlackBerry两个移动平台的浏览器测试。Android目前为市场占有率第一的移动平台，对于在其上面进行自动化测试，推荐Appium，Appium扩展了WebDriver的协议，支持ios平台和Android平台上的原生应用、Web应用和混合应用等。

#### 2、支持浏览器

WebDriver 目前所支持的浏览器包括：Firefox、Chrome、IE、Edge、Opera、Safari. 为什么会选择上面几款浏览器进行支持呢？主要与浏览器的内核有关。

#### 3、支持模式

HtmlUnit和PhantomJS是两个比较特殊的模式，我们可以把它们看作是伪浏览器，在这种模式下支持html**、**Java Saript等的解析，但不会真正地渲染出页面。由于不进行CSS及GUI渲染，所以运行效率上要比真实的浏览器快很多，主要用在功能性测试上面。

### selenium网络爬虫

Selenium直接驱动浏览器来加载网页，便可以直接拿到JavaScript渲染的结果，不需要再去分析网页所用的加密系统是什么，直接自动化操作渲染网页就可以了．

常用于JavaScript动态加载的网页

### selenium安装与配置

#### pip安装selenium

```shell
pip install selenium
```

通常在Linux环境下会有两个版本的Python存在，在安装时注意要使用你需要selenium存在Python环境的pip包管理器．

###### 验证安装

```python
➜  ~ python            
Python 3.7.3 (default, Jun 24 2019, 04:54:02) 
[GCC 9.1.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import selenium
>>> 
```

如果不报错就是安装成功了

#### 安装浏览器驱动(Chorme版本)

###### ChormeDriver驱动下载

官方网站：https://sites.google.com/a/chromium.org/chromedriver

下载地址：https://chromedriver.storage.googleapis.com/index.html

###### 查看Chorme浏览器版本

下载并安装google chorme浏览器，然后查看Chorme浏览器版本

**"菜单"→＂帮助＂→＂关于Google Chorme＂**可以看到版本号

进入ChormeDriver官网查看可以与本地浏览器版本适配的ChormeDriver版本

记住ChormeDriver版本号之后去下载地址找到相应的镜像之后将其下载下来

###### Windows环境

直接将ChormeDriver.exe文件移动至Python的Scripts目录下，或者也可以单独将其所在路径配置到环境变量

###### Linux或Mac环境

移动到环境变量的目录中

```shell
sudo mv chormedriver /usr/bin
```

将ChromeDriver配置到$PATH，例如将可执行文件放置在/usr/local/chromedriver目录下

接下来修改~/.profile文件并保存

```shell
export PATH="$PATH:/usr/local/chromedriver	"
```

使文件生效

```shell
source ~/.profile
```

###### 验证安装

直接在命令行中输入chromedriver不报错便是安装成功了

```shell
➜  ~ chromedriver
Starting ChromeDriver 75.0.3770.140 (2d9f97485c7b07dc18a74666574f19176731995c-refs/branch-heads/3770@{#1155}) on port 9515
Only local connections are allowed.
Please protect ports used by ChromeDriver and related test frameworks to prevent access by malicious code.
```

### selenium基本使用方法

#### 声明浏览器对象

```python
from selenium import webdriver
broswer = webbriver.Chorme()
broswer = webbriver.Firefox()
broswer = webbriver.Edge()
broswer = webbriver.PhantomJS()
broswer = webbriver.Safari()
```

#### 访问页面

```python
from selenium import webdriver

browser = webdriver.Chorme()
browser.get('https://www.taobao.com')
print(browser.page_source)
browser.close()
```

#### 查找节点

往往在对节点进行操作之前需要先找到节点．selenium提供了一系列的查找节点的方法．通常我们获取节点有多种不同的方法．此处先给出常用的获取节点的方法．

- find_element_by_id
- find_element_by_name
- find_element_by_xpath
- find_element_by_link_text
- find_element_by_partial_link_text
- find_element_by_tag_name
- find_element_by_class_name
- find_element_by_css_selector

###### 单个节点



###### 多个节点

#### 节点交互

#### 动作链

#### 执行Javascript

#### 获取节点信息

###### 获取属性

###### 获取文本值

###### 获取id，位置，标签名和大小

#### 切换Frame

#### 演示等待

###### 隐式等待

###### 显示等待

#### 前进与后退

#### Cookies

#### 选项卡管理

#### 异常处理