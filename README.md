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

## SUMMARY
![Image](../master/screenshots/kylin.png?raw=true)