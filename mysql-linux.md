### Linux

#### MySQL说明

##### 基本配置说明
* host:192.168.80.128
* 用户名密码：root/root
* 安装位置：/usr/local/mysql
* 配置文件位置：/etc/my.cnf
* 重启mysql:service mysqld restart
* mysql客户端连接：./usr/local/mysql/bin/mysql -uroot -p
##### 开启启动配置
1. cp /usr/local/mysql/support-files/mysql.server /etc/init.d/mysql   将服务文件拷贝到init.d下，并重命名为mysql
2. chmod +x /etc/init.d/mysql    赋予可执行权限
3. chkconfig --add mysql        添加服务
4. chkconfig --list             显示服务列表
如果看到mysql的服务，并且3,4,5都是on的话则成功，如果是off，则键入
chkconfig --level 345 mysql on
5. reboot重启电脑
6. netstat -na | grep 3306，如果看到有监听说明服务启动了

#### 连接操作说明
1. 关闭防火墙：

>``` shell
>	service iptables stop
>	systemctl stop firewalld.service
>```

2. 允许其他IP使用root连接：

> ``` mysql
> 	GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root' WITH GRANT OPTION;
> 	flush privileges;
> ```

#### Nginx说明
##### 基本配置说明
* 安装地址：/usr/local/nginx

#### K8S

```shell
# systemctl start etcd
# systemctl start docker
# systemctl start kube-apiserver
# systemctl start kube-controller-manager
# systemctl start kube-scheduler
# systemctl start kubelet
# systemctl start kube-proxy
```

#### Kafka(/usr/local/kafka)
1. 基本操作

   1. 启动

      ```shell
      -- 启动zookeeper
      bin/zookeeper-server-start.sh -daemon config/zookeeper.properties
      -- 启动kafka
   bin/kafka-server-start.sh -daemon config/server.properties
      ```
   
      
   
   2. topic
   
      ```shell
      // 创建topic
      bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test
      ```
   
      

