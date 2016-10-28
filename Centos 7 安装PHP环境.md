一、安装Apache
yum install httpd  
systemctl start httpd.service #启动apache  
systemctl stop httpd.service #停止apache  
systemctl restart httpd.service #重启apache  
systemctl enable httpd.service #设置apache开机启动  

二、安装PHP  
yum install php  

三、安装MariaDB  
yum install mariadb mariadb-server  
systemctl restart mariadb.service #重启MariaDB  
systemctl enable mariadb.service #设置MariaDB开机启动  

MariaDB中文乱码问题
登录数据库后输入:  
SHOW VARIABLES LIKE 'character%';  
查看character_set_database和character_set_server的默认字符集,如果还是latin1。需修改为utf8,如下:  
vi /etc/my.cnf  
在[mysqld]下面添加  
character-set-server=utf8  
保存后重启MariaDB  





