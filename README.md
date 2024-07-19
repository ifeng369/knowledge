<style type="text/css">
    h1 { counter-reset: h2counter; }
    h2 { counter-reset: h3counter; }
    h3 { counter-reset: h4counter; }
    h4 { counter-reset: h5counter; }
    h5 { counter-reset: h6counter; }
    h6 { }
    h2:before {
      counter-increment: h2counter;
      content: counter(h2counter) ".\0000a0\0000a0";
    }
    h3:before {
      counter-increment: h3counter;
      content: counter(h2counter) "."
                counter(h3counter) ".\0000a0\0000a0";
    }
    h4:before {
      counter-increment: h4counter;
      content: counter(h2counter) "."
                counter(h3counter) "."
                counter(h4counter) ".\0000a0\0000a0";
    }
    h5:before {
      counter-increment: h5counter;
      content: counter(h2counter) "."
                counter(h3counter) "."
                counter(h4counter) "."
                counter(h5counter) ".\0000a0\0000a0";
    }
    h6:before {
      counter-increment: h6counter;
      content: counter(h2counter) "."
                counter(h3counter) "."
                counter(h4counter) "."
                counter(h5counter) "."
                counter(h6counter) ".\0000a0\0000a0";
    }
</style>

# 知识库

## 开发相关

### git 设置代理

#### 针对所有域名的 Git 仓库

```
git config ––global http.proxy http://127.0.0.1:10809
```
#### 针对github的 Git 仓库

```
git config ––global http.https://github.com.proxy http://127.0.0.1:10809
```
### pip 使用国内源

#### 临时设置

```
pip3 install numpy -i https://pypi.tuna.tsinghua.edu.cn/simple
```

#### 永久设置

```
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple/
pip config set install.trusted-host pypi.tuna.tsinghua.edu.cn
```

## Windows

## Linux

## Docker


### 非root用户直接使用docker命令，而不是使用sudo


`sudo groupadd docker` ：添加到`groupadd`用户组（已经有docker用户组，所以可以不用再新增docker用户组）

`sudo gpasswd -a $USER docker`：添加当前用户到docker组

`newgrp docker`：更新docker用户组
