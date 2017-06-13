# 版本控制

## git 多账户

应用于多个代码托管站点多账户场景, 比如 github、gitlab、码云等[^gitMultipleAccount][^gitMultipleAccountBadOwner]. 配置完成后方便多个账户同时使用. 以 github 和 gitlab 为例, 按照以下步骤完成配置. 除了以下提供的配置方法, Windows 10 上可以用 Bash On Ubuntu On Windows 额外添加一个 git 账户, 适用于只有两个账户的情况.

### git 多账户配置

1. 生成公钥

生成公钥并添加到代码托管站点. 生成的时候, 输入不同的文件名保存.

```bash
ssh-keygen -t rsa -C "chenlei.here@qq.com"
```

```
chmod 600 ~/.ssh/config
ssh-agent bash
ssh-add ~/.ssh/id_rsa_gitlab
ssh-add ~/.ssh/id_rsa_github
```

2. 添加 ssh 配置文件

创建 config 文件(`touch ~/.ssh/config`), 并添加以下内容.

```conf
# gitlab
Host gitlab
    HostName gitlab.com
    User HereChen
    IdentityFile ~/.ssh/id_rsa_gitlab

# github
Host github
    HostName github.com
    User HereChen
    IdentityFile ~/.ssh/id_rsa_github
```

3. 为项目设置单独的账户配置

```bash
git clone git@github.com:HereChen/Tools-Solutions.git
cd Tools-Solutions
git config user.name "HereChen"
git config user.email "chenlei.here@qq.com"
```

### 启动时添加 SSH

每次重新启动系统或者打开 Git 客户端, ssh-add 添加的信息失效, 可配置在启动时添加. Linux 可在 barshrc 文件(`sudo vim ~/.bashrc`)中添加以下内容.

```bash
# https://unix.stackexchange.com/questions/90853/how-can-i-run-ssh-add-automatically-without-password-prompt
if [ -z "$SSH_AUTH_SOCK" ] ; then
  eval `ssh-agent -s`
  ssh-add -D
  ssh-add ~/.ssh/id_rsa_oschina
  ssh-add ~/.ssh/id_rsa_github
  ssh-add -l
fi
```

[^gitMultipleAccount]: [Multiple SSH Keys settings for different github account](https://gist.github.com/jexchan/2351996)
[^gitMultipleAccountBadOwner]: [ssh hostname returns “Bad owner or permissions on ~/.ssh/config”](https://serverfault.com/questions/253313/ssh-hostname-returns-bad-owner-or-permissions-on-ssh-config)

### git 一个库向两个托管服务器提交

## git 提交信息格式化

1. 工具安装

```bash
npm install -g commitizen
npm install -g cz-conventional-changelog
```

2. 初始化

```bash
commitizen init cz-conventional-changelog --save --save-exact
```

3. 提交

```bash
git cz -a
```

提交时需要填写以下信息: 选择提交的类型(新功能, bug 修复等等), 描述修改的范围, 简要描述修改的内容, 具体描述修改的内容.


