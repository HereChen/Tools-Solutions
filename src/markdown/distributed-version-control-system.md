# 版本控制

## git 多账户

应用于多个代码托管站点多账户场景, 比如 github、gitlab、码云等[^gitMultipleAccount][^gitMultipleAccountBadOwner]. 配置完成后方便多个账户同时使用. 以 github 和 gitlab 为例, 按照以下步骤完成配置. 除了以下提供的配置方法, Windows 10 上可以用 Bash On Ubuntu On Windows 额外添加一个 git 账户, 适用于只有两个账户的情况.

### 生成公钥

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

### 添加 ssh 配置文件

```bash
touch ~/.ssh/config
```

创建 config 文件, 并添加以下内容.

```
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

### 为项目设置单独的账户配置

```bash
git clone git@github.com:HereChen/Tools-Solutions.git
cd Tools-Solutions
git config user.name "HereChen"
git config user.email "chenlei.here@qq.com"
```

[^gitMultipleAccount]: [Multiple SSH Keys settings for different github account](https://gist.github.com/jexchan/2351996)
[^gitMultipleAccountBadOwner]: [ssh hostname returns “Bad owner or permissions on ~/.ssh/config”](https://serverfault.com/questions/253313/ssh-hostname-returns-bad-owner-or-permissions-on-ssh-config)
