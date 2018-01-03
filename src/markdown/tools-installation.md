# 工具安装

## nodejs

安装的方式包括: 从源码编译安装, 直接下载二进制, 依靠工具直接从库下载安装.

**从源码安装**

```
curl -o node-v6.10.0.tar.gz https://nodejs.org/dist/v6.10.0/node-v6.10.0.tar.gz
tar -xvzf node-v6.10.0.tar.gz
cd node-v6.10.0
./configure
make
make install
```

**CentOS 下载二进制安装**

```
# 64bit node install
curl -o node-v6.10.0-linux-x64.tar.xz https://nodejs.org/dist/v6.10.0/node-v6.10.0-linux-x64.tar.xz
tar -xvJf node-v6.10.0-linux-x64.tar.xz
mv node-v6.10.0-linux-x64 node

vi ~/.bash_profile
# 添加以下内容到 .bash_profile
# export NODE_HOME=/opt/node
# export PATH=$NODE_HOME/bin:$PATH
source ~/.bash_profile

node -v
```

**Ubuntu 从库中下载安装**

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
```

## git

### Ubuntu

安装最新版的 git[^ubuntuInstallLastVersionGit].

```
sudo add-apt-repository ppa:git-core/ppa
sudo apt-get update
sudo apt-get install git
```

如果上面执行报错 `Errors were encountered while processing: runit git-daemon-run`, 尝试执行下面命令.

```
sudo apt-get purge runit
sudo apt-get purge git-all
sudo apt-get purge git
sudo apt-get autoremove
sudo apt update
sudo apt install git
```

[^ubuntuInstallLastVersionGit]: [Installing Latest version of git in ubuntu](http://stackoverflow.com/questions/19109542/installing-latest-version-of-git-in-ubuntu/19109661#19109661), [How to fix processing with runit and git-daemon-run [duplicate]](http://askubuntu.com/questions/765565/how-to-fix-processing-with-runit-and-git-daemon-run/772095#772095)

### CentOS 从源码安装 git

执行 `yum install git` 安装的版本比较老, 安装最新版可从源码安装[^centOSInstallLastVersionGit].

```
# 依赖工具安装
yum install curl-devel expat-devel gettext-devel openssl-devel zlib-devel
yum install gcc perl-ExtUtils-MakeMaker

# git 源码下载
# https://www.kernel.org/pub/software/scm/git/
curl -o git-2.9.3.tar.xz https://www.kernel.org/pub/software/scm/git/git-2.9.3.tar.xz
tar -xvJf git-2.9.3.tar.xz

# 编译安装 git
cd git-2.9.3
make prefix=/usr/local all
sudo make prefix=/usr/local install
```

[^centOSInstallLastVersionGit]: [How to install latest version of git on CentOS 6.x/7.x](http://stackoverflow.com/questions/21820715/how-to-install-latest-version-of-git-on-centos-6-x-7-x)
, [起步 - 安装 Git](https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-%E5%AE%89%E8%A3%85-Git)
