---
layout: default
title: solr学习(1)：solr与tomacat整合
comments: true
---



###准备工作
1. `solr-4.7.2.zip`[下载](http://mirror.bit.edu.cn/apache/lucene/solr/4.7.2/)
2. `apache-tomcat-7.0.59.zip`[下载](http://mirror.bit.edu.cn/apache/tomcat/tomcat-7/v7.0.59/bin/)

###主要步骤
1. 解压`solr-4.7.2.zip`到`E:\solr\software`，解压后文件目录如下：
![solr与tomcat整合-1](http://h.picphotos.baidu.com/album/s%3D1100%3Bq%3D90/sign=0f7ffb97229759ee4e5064ca82cb7867/a9d3fd1f4134970a37cb8fb591cad1c8a6865deb.jpg)
2. 解压`apache-tomcat-7.0.59.zip`到`E:\solr\software`，解压后文件目录如下：
![solr与tomcat整合-2](http://h.picphotos.baidu.com/album/s%3D1100%3Bq%3D90/sign=7b178650e2cd7b89ed6c3e823f1479d6/faf2b2119313b07e6590d69208d7912397dd8c7f.jpg)
3. 将solr目录中的`example/webapps`中的`solr.war`复制到tomcat的`webapps`目录中，解压`solr.war`包（或启动tomcat解压），并删除`solr.war`包；
4. 新建一个文件夹tomcat-solr（名称可以自己定义），我的创建目录为`E:\solr\tomcat-solr`；
5. 将solr目录`example/solr`中的所有文件和目录拷贝到`E:\solr\tomcat-solr`目录下：
![solr与tomcat整合-3](http://f.picphotos.baidu.com/album/s%3D1100%3Bq%3D90/sign=54bb18fe524e9258a23482efacb2ea29/7af40ad162d9f2d30ab4d475adec8a136227cc87.jpg)
6. 将solr目录`example/lib/ext`所有jar包复制到tomcat`webapps/solr/WEB-INF/lib`目录中，一共5个，是solr的独立日志处理模块：
![solr与tomcat整合-4](http://f.picphotos.baidu.com/album/s%3D1100%3Bq%3D90/sign=d774aa73f6d3572c62e298ddba235856/b2de9c82d158ccbfb12448a01dd8bc3eb0354194.jpg)
7. 在tomcat的`webapps/solr/WEB-INF`下新建一个classes目录，并将solr目录`example/resources`下的`log4j.properties`文件复制到该classes目录中，否则日志模块无法正常工作；
8. 在tomcat的`webapps/solr/WEB-INF`下找到`web.xml`文件，用于配置环境变量的标签去掉注释，并修改环境变量，将新建的`tomcat-solr`目录添加到<env-entry-value>：
```
<env-entry>
    <env-entry-name>solr/home</env-entry-name>
    <env-entry-value>E:\solr\tomcat-solr</env-entry-value>
    <env-entry-type>java.lang.String</env-entry-type>
</env-entry>
```
9. 启动tomcat,输入http://localhost:8080/solr 进入到solr的管理界面：
![solr与tomcat整合-5](http://b.picphotos.baidu.com/album/s%3D1100%3Bq%3D90/sign=a06cac946309c93d03f20af6af0dc3ad/91529822720e0cf3beb1a8610e46f21fbf09aae2.jpg)
