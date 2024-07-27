# Windows安装nacos服务



## 1. 导入数据

- 新建nacos数据库，并修改你存放nacos\conf目录下的application.properties文件
- **核心**修改部分参考，记得把DB相关的注释去掉，打开使用

```properties
#*************** Spring Boot Related Configurations ***************#
### Default web context path:
server.servlet.contextPath=/nacos
### Include message field
server.error.include-message=ON_PARAM
### Default web server port:
server.port=8848

#*************** Config Module Related Configurations ***************#
### If use MySQL as datasource:
spring.datasource.platform=mysql

### Count of DB:
db.num=1

### Connect URL of DB:
db.url.0=jdbc:mysql://127.0.0.1:3306/nacos?characterEncoding=utf8&connectTimeout=1000&socketTimeout=3000&autoReconnect=true&useUnicode=true&useSSL=false&serverTimezone=UTC
db.user.0=root
db.password.0=root

### Connection pool configuration: hikariCP
db.pool.config.connectionTimeout=30000
db.pool.config.validationTimeout=10000
db.pool.config.maximumPoolSize=20
db.pool.config.minimumIdle=2
```

- 将你存放nacos\conf目录下的nacos-mysql.sql文件导入到数据库中即可

## 2. 安装服务

**以管理员身份**运行cmd，cd到你存放nacos\bin的目录下，在命令提示符中输入以下命令（**一定要用管理员身份打开！**）

```shell
nacos-service.exe install
```

显示成功即可。

## 3. 启动服务

1）命令启动

**以管理员身份**运行cmd，输入以下命令

```shell
net start nacos
```

2）进入任务管理器服务列表，找到nacos服务手动开启，设置等。

## 4. 开始使用

浏览器输入：http://127.0.0.1:8848/nacos

- **nacos启动默认端口为8848**

- **默认用户名和密码都是nacos**

##  5. 关闭服务

如果要停止服务，以管理员身份运行cmd，输入以下命令

```shell
net stop nacos
```

## 6. 卸载服务

如果要卸载服务，**以管理员身份**运行cmd，到nacos的bin目录，执行以下命令

```shell
nacos-service.exe uninstall
```

## 7. 集群配置

参考文章：https://blog.csdn.net/Bianca1/article/details/123866127

按以上步骤则设置为本地127.0.0.1默认开启，无需设置单机配置
