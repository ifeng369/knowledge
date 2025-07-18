# 知识库

## git
### git 设置代理

#### http代理
```
git config --global http.proxy http://127.0.0.1:10808
git config --global https.proxy http://127.0.0.1:10808
```
#### socks5代理
```
git config --global http.proxy socks5 127.0.0.1:10808
git config --global https.proxy socks5 127.0.0.1:10808
```
#### 仅针对github
```
git config --global http.https://github.com.proxy http://127.0.0.1:10808
```
#### 取消代理
```
git config --global --unset http.proxy
git config --global --unset https.proxy
git config --global --unset http.https://github.com.proxy
```

## anaconda
### anaconda 安装
> Miniconda (仅包含python、Conda)
```
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh | bash
```
> Anaconda (包含python、Conda、内置库及可视化界面)
```
wget https://repo.anaconda.com/archive/Anaconda3-2025.06-0-Linux-x86_64.sh | bash
```
> 创建环境
```
conda create --name py313 python=3.13
```
> 激活环境
```
conda activate py313
```
> 设置虚拟环境环境变量
```
conda env config vars set LD_LIBRARY_PATH=/usr/lib/wsl/lib:$LD_LIBRARY_PATH -n py313
```
> 退出环境
```
conda deactivate
```
> 激活默认环境
```
conda activate
```
> 克隆环境
```
conda create --name py313-1 --clone py3.13
```
> 查看已安装环境
```
conda env list
```
> 查看环境包
```
conda list [-n py313]
```
> 搜索包
```
conda search packname
```
> 安装包
```
conda install packname
conda install -n py313 packname
```
> 使用国内源
```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/cloud/bioconda/
```

## pip
### pip 使用国内源
> 临时设置
```
pip3 install numpy -i https://pypi.tuna.tsinghua.edu.cn/simple
```
> 永久设置
```
pip config set global.extra-index-url https://pypi.tuna.tsinghua.edu.cn/simple/
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple/
pip config set install.trusted-host pypi.tuna.tsinghua.edu.cn
```

```
pip config set global.extra-index-url https://mirrors.bfsu.edu.cn/pypi/web/simple
pip config set global.index-url https://mirrors.bfsu.edu.cn/pypi/web/simple
pip config set install.trusted-host mirrors.bfsu.edu.cn/pypi/web/simple
```

> 部分国内镜像

```
清华大学
https://pypi.tuna.tsinghua.edu.cn/simple
中国科学技术大学
https://mirrors.ustc.edu.cn/pypi/simple
北京外国语大学
https://mirrors.bfsu.edu.cn/pypi/web/simple
上海交通大学
https://mirror.sjtu.edu.cn/pypi/web/simple
南方科技大学
https://mirrors.sustech.edu.cn/pypi/web/simple
北京大学
https://mirrors.pku.edu.cn/pypi/web/simple
南阳理工学院
https://mirror.nyist.edu.cn/pypi/web/simple
南京工业大学
https://mirrors.njtech.edu.cn/pypi/web/simple
吉林大学
https://mirrors.jlu.edu.cn/pypi/simple
大连东软信息学院
https://mirrors.neusoft.edu.cn/pypi/web/simple
```


### pip 报错PEP668
#### 使用venv虚拟环境
> Linux
```
python3 -m venv myenv
source myenv/bin/activate
pip install 包名
```

> Windows
```
python -m venv myenv
./myenv/Scripts/activate
pip install 包名
```

## npm，pnpm，yarn
### npm，pnpm，yarn 国内源
```
 npm config set registry https://registry.npmmirror.com/
```
### 安装 PNPM
> 方式1：npm 安装
```
npm install pnpm -g  --registry=http://registry.npmmirror.com
```
> 方式2：cmd安装。进入cmd环境：右键`在终端中打开`,会进入powershell环境，然后输入`cmd`进入cmd环境 (在ps环境下， curl 实际调用 Invoke-WebRequest 无法接受 -x -o 参数，所以需要进入cmd环境操作)
```
curl -L -x http://127.0.0.1:10809 https://github.com/pnpm/pnpm/releases/latest/download/pnpm-win-x64.exe -o pnpm.exe
./pnpm.exe setup
```

## Docker
### 非root用户不使用sudo执行命令
```
#添加到`groupadd`用户组（已经有docker用户组，所以可以不用再新增docker用户组）
#更新docker用户组
#添加当前用户到docker组

sudo groupadd docker
sudo gpasswd -a $USER docker
newgrp docker
```

### 升级
```
export DOWNLOAD_URL="https://mirrors.tuna.tsinghua.edu.cn/docker-ce"
curl -x 192.168.16.17:10808 -fsSL https://get.docker.com/ | sudo -E sh
```

## Linux
### linux(Ubuntu 22.04) 环境下 net8调用httpclient报错： The SSL connection could not be established, see inner exception
```
sudo nano /etc/ssl/openssl.cnf
```
```
[openssl_init]
providers = provider_sect
ssl_conf = ssl_sect
```
```
[ssl_sect]
system_default = system_default_sect

[system_default_sect]
CipherString = DEFAULT:@SECLEVEL=2
Options = UnsafeLegacyRenegotiation
```
> 重新服务
```
sudo systemctl restart NetworkManager
```

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

### debian 设置国内源
```
sed -i "s/deb.debian.org/mirrors.ustc.edu.cn/g" /etc/apt/sources.list.d/debian.sources
```

### ubuntu 完全使用磁盘空间
```
df -hl #查看分区情况
sudo fdisk -l  #查看磁盘容量
sudo lvextend -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv  #剩余空间分配到/dev/mapper/ubuntu--vg-ubuntu--lv
sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv   #重新计算 /dev/mapper/ubuntu--vg-ubuntu--lv 大小
```

### alpine 设置国内源
```
sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories
```

## Windows
### 解除 PowerShell 默认禁止运行 ps脚本
```
set-executionpolicy remotesigned
```

### 设置 VSCode 中 Markdown 粘贴图片的位置
> 1. 在VS Code中，按下`Ctrl + ,`，打开设置界面。
> 2. 在搜索框中输入`markdown.copy`, 找到`Markdown> Copy Files:Destination`
> 3. 新增配置项 key 为 `**/*.md` , value 为 你的目标路径。比如我想将图片放在 assets 目录下 markdown文件同名的目录下，那么我就可以设置为 `assets/${documentBaseName}/${fileName}`， 其中 `${documentBaseName}` 代表markdown文件的文件名，`${fileName}` 代表图片的文件名。
> 4. 保存设置即可。

![alt text](assets/README/image.png)

### C#读写 注册表 HKEY_LOCAL_MACHINE\SOFTWARE 位置，与实际位置不对应问题
> 原因是 vs2022 项目默认优先生成32位程序集，在64位系统下32位程序中读写 `HKEY_LOCAL_MACHINE\SOFTWARE` 实际上是读写 `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node` 
> 解决办法：修改项目属性，在生成中将 `目标平台` 设置为 `64位` 重新生成即可

### vs2019下载地址

https://aka.ms/vs/16/release/vs_community.exe