ambari-kylin-service
===

## To download the Kylin service folder, run below    

```
VERSION=`hdp-select status hadoop-client | sed 's/hadoop-client - \([0-9]\.[0-9]\).*/\1/'`
sudo git clone https://github.com/iamlinix/ambari-kylin-service.git /var/lib/ambari-server/resources/stacks/HDP/$VERSION/services/KYLIN
```

## What Do I Modify
```
1. Set PATH env to use HDP HBase binary as default instead of the Cloudera one; coz I installed Impala before trying to install Kylin, and Impala required Cloudera version of HBase hence we have 2 different versions of HBase. 
2. During configuration, one can choose nginx user.
3. Create nginx user if it does not exist.
4. Check my first commit for details.
```

## Required Manual Edit
edit package/templates/env.rc.j2 file to set your own JAVA_HOME

## Restart Ambari
\#sandbox  
service ambari restart

\#non sandbox  
sudo service ambari-server restart

## 下载服务配置目录    

```
VERSION=`hdp-select status hadoop-client | sed 's/hadoop-client - \([0-9]\.[0-9]\).*/\1/'`
sudo git clone https://github.com/iamlinix/ambari-kylin-service.git /var/lib/ambari-server/resources/stacks/HDP/$VERSION/services/KYLIN
```

## 我修改的内容
```
1. 设置 PATH 环境变量，以默认使用 HDP 版本的 HBase 程序。由于之前我通过 ambari 安装了 Impala，这个过程中自动安装了 Cloudera 版本的 HBase，因此系统中有两个版本的 HBase。 
2. 配置服务的时候，可以选择运行 nginx 服务的系统用户。
3. 如果所选择的系统用户不存在，则创建用户。
4. 具体修改细节可查看我的第一个 commit。
```

## 手动编辑
需要手动修改 package/templates/env.rc.j2 文件，设置自己环境中的 JAVA_HOME

## 重启 Ambari
\#sandbox  
service ambari restart

\#non sandbox  
sudo service ambari-server restart

## SUMMARY | 总结
![Image](../master/screenshots/kylin.png?raw=true)