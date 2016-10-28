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

