# mysql

安装mysql遇到问题：就是密码得是mysql_native_password才可以被远程访问

select user, host,plugin from mysql.user;