# 知识库

## 开发相关


### git 设置代理

> 针对所有域名的 Git 仓库

```
git config ––global http.proxy http://127.0.0.1:10809
```

> 针对github的 Git 仓库

```
git config ––global http.https://github.com.proxy http://127.0.0.1:10809
```

### pip 使用国内源

> 临时设置

```
pip3 install numpy -i https://pypi.tuna.tsinghua.edu.cn/simple
```

> 永久设置

```
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple/
pip config set install.trusted-host pypi.tuna.tsinghua.edu.cn
```


## Windows

> 解除 PowerShell 默认禁止运行 ps1 脚本

```
set-executionpolicy remotesigned
```

## Linux

### ubuntu 设置国内源

> Ubuntu 24.04 之前版本

```
sed -i "s/archive.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g" /etc/apt/sources.list
sed -i "s/security.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g" /etc/apt/sources.list
```

> Ubuntu 24.04 之后版本

```
sed -i "s/archive.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g" /etc/apt/sources.list.d/ubuntu.sources
sed -i "s/security.ubuntu.com/mirrors.tuna.tsinghua.edu.cn/g" /etc/apt/sources.list.d/ubuntu.sources
```

### alpine 设置国内源

```
sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories
```

## Docker

### 非root用户不使用sudo执行命令

`sudo groupadd docker` ：添加到`groupadd`用户组（已经有docker用户组，所以可以不用再新增docker用户组）

`sudo gpasswd -a $USER docker`：添加当前用户到docker组

`newgrp docker`：更新docker用户组