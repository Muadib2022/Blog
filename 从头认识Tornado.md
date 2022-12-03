---
title: 从头认识Tornado
date: 2019-02-06 12:08:59
author: chen
categories: web
tags:
- tornado
---

# Tornado 框架简介

## Tornado特性与适用场景

- 使用Python编写的网络框架和高性能的异步网络库
- 适用于大量连接， 长轮询、WebSockets应用

优势

- 微框架，高性能
- 异步支持

劣势

- 轮子较少，不像Django和Flask等框架有大量的插件支持
- 缺少最佳实践，使用公司较少，学习资料少。

构建微服务

- 不适合复杂的CMS（内容管理系统）应用
- 适合构建网站或者APP后端微服务

## Tornado学习资料

- 官方文档
- https://github.com/tornadoiweb/tornado
- 《Introduction to Tornado》

## Tornado的安装

- pip install tornado
- pip install tornado

## Tornado的启动

```python
import tornado.ioloop
import tornado.web


class MainHandler(tornado.web.RequestHandler):
    def get(self):
        self.write("Hello, world")


def make_app():
    return tornado.web.Application([
        (r"/", MainHandler),
    ])


if __name__ == "__main__":
    app = make_app()
    app.listen(8888)
    tornado.ioloop.IOLoop.current().start()
```

## Tornado异步请求与同步请求的时间对比

### server

```python
import time
import datetime as dt
import tornado.gen
import tornado.httpserver
import tornado.ioloop
import tornado.web


class SleepHandler(tornado.web.RequestHandler):
    @tornado.gen.coroutine
    def get(self):
        yield tornado.gen.sleep(3)
        self.write(str(dt.datetime.now()))


if __name__ == "__main__":
    app = tornado.web.Application(
        [
            (r"/sleep", SleepHandler)
        ],
        debug=True
    )
    http_server = tornado.httpserver.HTTPServer(app)
    http_server.listen(8888)
    print("server start at 8888")
    tornado.ioloop.IOLoop.instance().start()
```

### client

```python
import time
import requests
import tornado.gen
import tornado.httpclient
import tornado.ioloop
from tornado import gen


N = 3
URL = "http://localhost:8888/sleep"


@gen.coroutine
def main():
    http_client =tornado.httpclient.AsyncHTTPClient()
    response = yield [
        http_client.fetch(URL) for i in range(N)
    ]


beg1 = time.time()
tornado.ioloop.IOLoop.current().run_sync(main)
print("asunc", time.time()-beg1)

beg = time.time()
for i in range(N):
    requests.get(URL)
print("req", time.time()-beg)
```

## Tornado Web主要模块

- tornado.web.Application 和 RequestHandler 类处理http请求
- tornado.template模板渲染
- tornado.routing处理路由

## 异步网络模块

### 异步 networking

- tornado.ioloop 事件循环
- tornado.iostream 非阻塞socket 封装
- tornado.tcpserver 和 tornado.tcpclient

