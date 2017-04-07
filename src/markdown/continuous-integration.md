# 持续集成

## travis-ci

### travis-ci 使用流程

travis-ci 结合 github 使用, 每次提交自动执行编译或测试任务.

1. <travis-ci.org> 用 github 账户授权登录
2. travis-ci 上添加需要持续集成的 github repo
3. github repo 中添加 `.travis.yml` 配置, 用以配置 travis 所要执行的任务和环境
4. repo 更改完成, 提交, 可在 travis-ci 上实时查看任务执行过程

备注:

### 添加编译状态图标

```
[![Build Status](https://travis-ci.org/HereChen/Tools-Solutions.svg?branch=master)](https://travis-ci.org/HereChen/Tools-Solutions)
```

### travis 配置文件样本

此库的 `.travis.yml` 样本

```
sudo: required
dist: trusty     # ubuntu 14.04

# install
before_install:
    - sudo apt-get update
    - sudo apt-get -y install texlive-full
    - sudo apt-get -y install pandoc

before_script:
    - chmod +x build.sh

script:
    - ./build.sh
```
