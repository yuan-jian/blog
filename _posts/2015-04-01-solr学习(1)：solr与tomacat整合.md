---
layout: default
title: solr学习(1)：solr与tomacat整合
comments: true
---



###准备工作
1. solr-4.7.2.zip[下载](http://mirror.bit.edu.cn/apache/lucene/solr/4.7.2/)
2. apache-tomcat-7.0.59.zip[下载](http://mirror.bit.edu.cn/apache/tomcat/tomcat-7/v7.0.59/bin/)

###主要步骤
1. 解压solr-4.7.2.zip到E:\solr\software，解压后文件目录如下：
![solr与tomcat整合-1](https://github.com/yuan-jian/blog/blob/gh-pages/images/solr/solr_tomcat-1.png?raw=true)
2. 解压apache-tomcat-7.0.59.zip到E:\solr\software，解压后文件目录如下：
![solr与tomcat整合-2](https://github.com/yuan-jian/blog/blob/gh-pages/images/solr/solr_tomcat-2.png?raw=true)
3. 将solr目录中的example/webapps中的solr.war复制到tomcat的webapps目录中，解压solr.war包（或启动tomcat解压），并删除solr.war包；
4. 新建一个文件夹tomcat-solr（名称可以自己定义），我的创建目录为E:\solr\tomcat-solr；
5. 将solr目录example/solr中的所有文件和目录拷贝到E:\solr\tomcat-solr目录下：
![solr与tomcat整合-3](https://github.com/yuan-jian/blog/blob/gh-pages/images/solr/solr_tomcat-3.png?raw=true)
6. 将solr目录example/lib/ext所有jar包复制到tomcat的webapps/solr/WEB-INF/lib目录中，一共5个，是solr的独立日志处理模块：
![solr与tomcat整合-4](https://github.com/yuan-jian/blog/blob/gh-pages/images/solr/solr_tomcat-4.png?raw=true)
7. 在tomcat的webapps/solr/WEB-INF下新建一个classes目录，并将solr目录example/resources下的log4j.properties文件复制到该classes目录中，否则日志模块无法正常工作；
8. 在tomcat的webapps/solr/WEB-INF下找到web.xml文件，用于配置环境变量的标签去掉注释，并修改环境变量，将新建的tomcat-solr目录添加到\<env-entry-value\>标签中：

        <env-entry>
            <env-entry-name>solr/home</env-entry-name>
            <env-entry-value>E:\solr\tomcat-solr</env-entry-value>
            <env-entry-type>java.lang.String</env-entry-type>
        </env-entry>

9. 启动tomcat,输入http://localhost:8080/solr 进入到solr的管理界面：
![solr与tomcat整合-5](https://github.com/yuan-jian/blog/blob/gh-pages/images/solr/solr_tomcat-5.png?raw=true)
