# linux安装MySQL并初始化root密码

- 安装MySQL`sudo apt install mysql-server`

- 因为过程中不提示设置密码，才会有后面的步骤

- 进入到`etc/mysql` 目录下，查看`debian.cnf`文件

- 找到其中的`user`和`password`，用`mysql -uuser -ppassword`登入MySQL

- 修改root用户的密码：

```sql
  show databases；
  
  use mysql;
  
  update user set authentication_string=PASSWORD("自定义密码") where user='root';
  
  update user set plugin="mysql_native_password";
  
  flush privileges;
  
  quit;
```

  重启MySQL`sudo service mysql restart`，然后就可以登入了

