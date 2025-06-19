# Brew

- 启动数据库：`sudo mysql.server start`
* 关闭数据库：`sudo mysql.server stop`
* 重启数据库：`mysql.server restart`
* 登录根用户：`mysql -u root -p`，密码是 123456
* 进入数据库：`use db_name`

# 导入数据
mysql -u root -p db_name < /path/to/file.sql

# terminate all running instances of the MySQL server

```
sudo killall mysqld
```