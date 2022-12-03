---
title: Pipenv工作流
date: 2019-02-06 12:08:59
author: chen
categories: tools
tags:
- pipenv
- pip
---

*Pipenv 是基于pip的Python包管理器，可以看做是pip的加强版．具体来说是pip，pipfile和 virtualenv 的结合体*

## 安装pip和Pipenv

### 安装pip

最简单的办法就是下载get-pip.py，然后使用Python执行安装

###### git-pip.py 下载地址

https://bootstrap.pypa.io/get-pip.py

###### 下载成功之后找到文件位置，然后运行

```bash
python get-pip.py
```

*用哪个版本的 Python 运行安装脚本，pip 就被关联到哪个版本*

###### 检查pip版本

```bash
pip --version
```

### 安装Pipenv

```bash
pip install pipenv
```

###### 检查Pipenv是否安装成功

```bash
pipenv --version
pipenv, version 11.10.4
```

## 创建虚拟环境

*虚拟环境（virtual enviroment）就是隔离的Python解释器环境．通过创建虚拟环境，可以为项目制作一个独立的虚拟器环境．*

#### 创造虚拟环境的好处

不同的项目常常会依赖不同版本的库或者Python版本，使用虚拟环境可以保持全局Python解释器环境的干净，避免包和版本的混乱，并且方便记录和区分环境依赖，以便在新环境下复现依赖环境．

#### 创建虚拟环境

```powershell
pipenv install
```

###### 示例

```powershell
➜  ~ cd helloworld  
➜  helloworld ls
➜  helloworld pipenv install              
Creating a virtualenv for this project…
Pipfile: /home/chen/helloworld/Pipfile
Using /usr/bin/python3 (3.7.3) to create virtualenv…
⠙ Creating virtual environment...Already using interpreter /usr/bin/python3
Using base prefix '/usr'
New python executable in /home/chen/.local/share/virtualenvs/helloworld-4EaoGzxK/bin/python3
Also creating executable in /home/chen/.local/share/virtualenvs/helloworld-4EaoGzxK/bin/python
Installing setuptools, pip, wheel...
done.

✔ Successfully created virtual environment! 
Virtualenv location: /home/chen/.local/share/virtualenvs/helloworld-4EaoGzxK
Creating a Pipfile for this project…
Pipfile.lock not found, creating…
Locking [dev-packages] dependencies…
Locking [packages] dependencies…
Updated Pipfile.lock (a65489)!
Installing dependencies from Pipfile.lock (a65489)…
  🐍   ▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉▉ 0/0 — 00:00:00
To activate this project's virtualenv, run pipenv shell.
Alternatively, run a command inside the virtualenv with pipenv run.
```

这会为当前项目独立创建一个包含着基本包的Python环境

```powershell
➜  helloworld cd /home/chen/.local/share/virtualenvs/helloworld-4EaoGzxK
➜  helloworld-4EaoGzxK ls   
bin  include  lib
➜  helloworld-4EaoGzxK cd lib    
➜  lib ls
python3.7
➜  lib cd .. 
➜  helloworld-4EaoGzxK cd bin  
➜  bin ls
activate       activate.ps1      easy_install      pip3    python3        wheel
activate.csh   activate_this.py  easy_install-3.7  pip3.7  python3.7
activate.fish  activate.xsh      pip               python  python-config
➜  bin cd .. 
➜  helloworld-4EaoGzxK ls
bin  include  lib
➜  helloworld-4EaoGzxK cd include    
➜  include ls
python3.7m
```

#### 显式的激活虚拟环境

```powershell
pipenv shell
```

#### 不显式激活环境下执行命令

```powershell
pipenv run python hello.py
```

#### 管理依赖

pipenv install 会在文件下创建　Pipfile 和　Pipfile.lock 文件，前者用来记录项目依赖列表，后者则记录了固定版本的详细依赖包列表．

在使用Pipenv安装或者删除依赖包的时候，两者会自动更新

#### 查看依赖

```powershell
pipenv graph
```

#### 安装Django

```powershell
pipenv install django
```

#### 更新版本

```powershell
pipenv update flask
```

