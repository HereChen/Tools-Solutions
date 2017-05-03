[![Build Status](https://travis-ci.org/HereChen/Tools-Solutions.svg?branch=master)](https://travis-ci.org/HereChen/Tools-Solutions)

# Tools Solutions

工具使用 tips 及解决方案

## travis-ci 持续集成

- github 授权 travis
- travis 启用要构建的库
- 添加 travis 配置文件
- 生成 travis token 上传 pdf

- travis-ci 使用流程: <https://harshjv.github.io/blog/setup-latex-pdf-build-using-travis-ci/>
- latex 中文: <http://www.cnblogs.com/SivilTaram/p/travis-ci_latex_auto-build_github.html?hmsr=toutiao.io&utm_medium=toutiao.io&utm_source=toutiao.io>
- token 生成: <https://xuanwo.org/2015/08/12/OpenSourceBook/>
- 添加 github 编译状态: <http://stackoverflow.com/questions/19810386/showing-travis-build-status-in-github-repo>

- travis-ci github token: github-> settings -> Personal access tokens 选择权限(只选了前两项)
- travis-ci Permission Denied 错误: <https://nofluffjuststuff.com/blog/brian_kotek/2013/06/grails_travis_ci_and_permission_denied>
- 错误: Skipping a deployment with the releases provider because this is not a tagged commit

## 更新

### 2017-05-03

- 代码质量部分内容(findbugs, checkstyle, sonar).
- LaTeX documentclass 换用 ctexart.
- LaTeX 代码字体, 代码复制
