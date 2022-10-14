# Windows下的Maven安装与配置【附Idea设置默认】 - 腾讯云开发者社区-腾讯云
[Windows下的Maven安装与配置【附Idea设置默认】 - 腾讯云开发者社区-腾讯云](https://cloud.tencent.com/developer/article/1538383) 

 Maven是一个[项目管理](https://cloud.tencent.com/product/coding-pm?from=10680)和综合工具。Maven提供了开发人员构建一个完整的生命周期框架。开发团队可以自动完成项目的基础工具建设，Maven使用标准的目录结构和默认构建生命周期。

在多个开发团队环境时，Maven可以设置按标准在非常短的时间里完成配置工作。由于大部分项目的设置都很简单，并且可重复使用，Maven让开发人员的工作更轻松，同时创建[报表](https://cloud.tencent.com/product/bi?from=10680)，检查，构建和测试自动化设置。

> 以上摘自网上

不废话了，进入正题。Maven可以方便的为我们自动管理各种包，或者其它一些工具建设。

### 步骤

#### 下载

官网下载地址：[http://maven.apache.org/download.cgi](http://maven.apache.org/download.cgi)

![](https://ask.qcloudimg.com/http-save/yehe-2626829/lur7ule613.png?imageView2/2/w/1620)

我们下载Binary zip archive （二进制压缩归档文件）

**下载完成：** 

![](https://ask.qcloudimg.com/http-save/yehe-2626829/2g1vtdvr18.png?imageView2/2/w/1620)

#### 解压

我们下载的是压缩归档文件，不用安装，解压即可。

我这里将其解压到了F盘：`F:\Maven3.6.2`

![](https://ask.qcloudimg.com/http-save/yehe-2626829/pmw8z3r60a.png?imageView2/2/w/1620)

#### 环境变量配置

Win10可以直接搜索“环境变量”打开配置界面：

![](https://ask.qcloudimg.com/http-save/yehe-2626829/8rieq5sqid.png?imageView2/2/w/1620)

![](https://ask.qcloudimg.com/http-save/yehe-2626829/kglbcrs90m.png?imageView2/2/w/1620)

> 其他用户请：计算机右键→属性→高级系统设置→环境变量

A. 我们需要在系统变量新建两个变量`M2_HOME`和`MAVEN_HOME`，值为安装路径；

```
M2_HOME=F:\Maven3.6.2
MAVEN_HOME=F:\Maven3.6.2
```

B. 编辑系统变量PATH，添加`%M2_HOME%\bin`

C. 验证

Win+R 运行 输入`cmd`打开命令行，在命令行里面输入`mvn -version`

#### 配置

**配置setting.xml**

路径在：`安装目录\conf`下

A. 配置本地仓库

```
<localRepository>F:\Maven3.6.2\repository</localRepository>
```

> 上面的`F:\Maven3.6.2`改成自己的安装目录

B. maven配置阿里[镜像仓库](https://cloud.tencent.com/product/tcr?from=10680)

```
<mirror>
    <id>nexus-aliyun</id>
    <mirrorOf>central</mirrorOf>
    <name>Nexus aliyun</name>
    <url>http://maven.aliyun.com/nexus/content/groups/public</url>
</mirror>
```

> 不配置阿里云镜像，下载会很慢

![](https://ask.qcloudimg.com/http-save/yehe-2626829/c32bhj8iw4.png?imageView2/2/w/1620)

### 在Idea中配置

由于Idea默认会使用自己的maven，不会使用我们下载的，所以要配置一番。

打开File | Settings | Build, Execution, Deployment | Build Tools | Maven

> 或者打开设置后，搜索mav就行

![](https://ask.qcloudimg.com/http-save/yehe-2626829/lujcb03yac.png?imageView2/2/w/1620)

如上图，要将home directory设置成安装目录，也要覆盖settings file 和 local repository目录。

### 附超全mirros

```
<mirrors>
    <!-- mirror
     | Specifies a repository mirror site to use instead of a given repository. The repository that
     | this mirror serves has an ID that matches the mirrorOf element of this mirror. IDs are used
     | for inheritance and direct lookup purposes, and must be unique across the set of mirrors.
     |
    <mirror>
      <id>mirrorId</id>
      <mirrorOf>repositoryId</mirrorOf>
      <name>Human Readable Name for this Mirror.</name>
      <url>http://my.repository.com/repo/path</url>
    </mirror>
     -->
     <mirror>
        <id>aliyun-public</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun public</name>
        <url>https://maven.aliyun.com/repository/public</url>
    </mirror>

    <mirror>
        <id>aliyun-central</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun central</name>
        <url>https://maven.aliyun.com/repository/central</url>
    </mirror>

    <mirror>
        <id>aliyun-spring</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun spring</name>
        <url>https://maven.aliyun.com/repository/spring</url>
    </mirror>

    <mirror>
        <id>aliyun-spring-plugin</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun spring-plugin</name>
        <url>https://maven.aliyun.com/repository/spring-plugin</url>
    </mirror>

    <mirror>
        <id>aliyun-apache-snapshots</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun apache-snapshots</name>
        <url>https://maven.aliyun.com/repository/apache-snapshots</url>
    </mirror>

    <mirror>
        <id>aliyun-google</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun google</name>
        <url>https://maven.aliyun.com/repository/google</url>
    </mirror>

    <mirror>
        <id>aliyun-gradle-plugin</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun gradle-plugin</name>
        <url>https://maven.aliyun.com/repository/gradle-plugin</url>
    </mirror>

    <mirror>
        <id>aliyun-jcenter</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun jcenter</name>
        <url>https://maven.aliyun.com/repository/jcenter</url>
    </mirror>

    <mirror>
        <id>aliyun-releases</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun releases</name>
        <url>https://maven.aliyun.com/repository/releases</url>
    </mirror>

    <mirror>
        <id>aliyun-snapshots</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun snapshots</name>
        <url>https://maven.aliyun.com/repository/snapshots</url>
    </mirror>

    <mirror>
        <id>aliyun-grails-core</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun grails-core</name>
        <url>https://maven.aliyun.com/repository/grails-core</url>
    </mirror>

    <mirror>
        <id>aliyun-mapr-public</id>
        <mirrorOf>*</mirrorOf>
        <name>aliyun mapr-public</name>
        <url>https://maven.aliyun.com/repository/mapr-public</url>
    </mirror>
  </mirrors>
```

> 以上源复制自：[https://blog.csdn.net/m0\_37566718/article/details/86978890](https://blog.csdn.net/m0_37566718/article/details/86978890)