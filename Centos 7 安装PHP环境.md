### 一、安装Apache
yum install httpd  
systemctl start httpd.service #启动apache  
systemctl stop httpd.service #停止apache  
systemctl restart httpd.service #重启apache  
systemctl enable httpd.service #设置apache开机启动  

### 二、安装PHP  
yum install php  

### 三、安装MariaDB  
yum install mariadb mariadb-server  
systemctl restart mariadb.service #重启MariaDB  
systemctl enable mariadb.service #设置MariaDB开机启动  


`修改root密码`  
1.以root身份在终端登陆，必须  
2.输入 mysqladmin -u root -p password root  
后面的 `root` 是要设置的密码  
3.回车后出现 Enter password   
输入`旧密码`，如果没有，直接回车  

`MariaDB中文乱码问题`  
登录数据库后输入:  
SHOW VARIABLES LIKE 'character%';  
查看character_set_database和character_set_server的默认字符集,如果还是latin1。需修改为utf8,如下:  
vi /etc/my.cnf  
在[mysqld]下面添加  
character-set-server=utf8  
保存后重启MariaDB  

### 四.安装PHP组件，使PHP支持 MariaDB  
yum install php-mysql php-gd libjpeg* php-ldap php-odbc php-pear php-xml php-xmlrpc php-mbstring php-bcmath php-mhash  

### 五.PHP连接数据库中文乱码问题  
代码中设置添加 $mysqli->query("SET NAMES UTF8")  
$mysqli = new mysqli("localhost","root","andros230","feedback");  
if ($mysqli->connect_error) {  
    die("连接失败: " . $conn->connect_error);  
}    
`$mysqli->query("SET NAMES UTF8");`  
$insert_row = $mysqli->query("INSERT INTO feedback (app,msg) VALUES('app名称','msg信息')");  

### 六.mariadb远程访问
登录数据后输入:  
GRANT ALL PRIVILEGES ON *.* TO 'root'@'%'IDENTIFIED BY '123456' WITH GRANT OPTION;
flush privileges;
root是登陆数据库的用户，123456是登陆数据库的密码，*就是意味着任何来源任何主机,另注意防火墙的3306端口





php站点: /var/www/html
