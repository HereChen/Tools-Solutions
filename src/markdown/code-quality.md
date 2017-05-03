# 代码质量

## checkstyle

### maven

```xml
<reporting>
    <plugins>
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-checkstyle-plugin</artifactId>
            <version>2.17</version>
            <configuration>
                <!--自定义 checkstyle 配置路径-->
                <configLocation>${project.basedir}/checkstyle.xml</configLocation>
            </configuration>
        </plugin>

        <!--使 checkstyle 结果可以直接跳转到代码行位置-->
        <plugin>
            <groupId>org.apache.maven.plugins</groupId>
            <artifactId>maven-jxr-plugin</artifactId>
            <version>2.3</version>
        </plugin>
    </plugins>
</reporting>
```

`mvn site` 执行后, 打开 `target/site/index.html`, 在 Project Reports -> Checkstyle 查看报告. 点击对应行数, 可查看具体代码位置.

**checkstyle 常见问题包括**:

1. 代码缩进不对.
2. 控制语句没加大括号.
3. `equals` 字符串应放在前面.
4. if-else 条件语句包含 return 的未简化(可去除 if-else 直接 return).
5. 无用的包引入.
6. 命名问题: 包名、变量名、类名、函数名.
7. 字符串太长(超出限制).
8. 缺注释.

**checkstyle 修改快捷方法(eclipse 或者 IDEA)**:

1. 变量名修改可用 Refactor 的快捷键. eclipse、IDEA 可用.
2. 缩进或控制语句缺大括号, 可配置格式化属性(或导入模板), 快捷键针对工程中所有文件格式化, 比如 IDEA 的 Ctrl+Alt+L. eclipse, IDEA 可用.
3. eclipse 可安装 javadoc (不是这个名字), 对整个包快捷键添加注释.

## findbugs

### IDEA 插件

idea 编辑器可安装 FindBugs-IDEA 插件 (File->Settings->Plugins->Browse repo...).  安装重启后编辑器后, 底部会显示. 选择 src 文件夹, 点击 `Analyze Module Files` 可分析全部源文件.

### maven

```xml
<reporting>
    <plugins>
        <!-- https://mvnrepository.com/artifact/org.codehaus.mojo/findbugs-maven-plugin -->
        <plugin>
            <groupId>org.codehaus.mojo</groupId>
            <artifactId>findbugs-maven-plugin</artifactId>
            <version>3.0.4</version>
        </plugin>
    </plugins>
</reporting>
```

`mvn site` 执行后在 Project Reports -> FindBugs 查看报告. `mvn site` 执行下载 FindBugs 相关依赖错误时, 可尝试用 VPN 解决.

## sonar

### IDEA 插件

idea 编辑器可安装 SonarLint 插件 (File->Settings->Plugins->Browse repo...). 安装重启后, 点击底部显示的 SonarLint, 并点击此 tab 里面的 Project Files, Scope 项选择 All projects files, 点击绿色运行图标进行分析. 在编写代码过程中, 可切换到 Current file 实时查看当前编写代码的问题.

### maven

需配置数据库.
