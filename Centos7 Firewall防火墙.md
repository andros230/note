systemtctl start firewalld.service  //启动防火墙  
systemtctl stop firewalld.service   //停止防火墙  
systemtctl restart firewalld.service //重启防火墙 
firewall-cmd --list-ports   //查看防火墙开放端口    
firewall-cmd --add-port=80/tcp    //在防火墙开放端口,如开放80端口  
ffirewall-cmd --remove-port=80/tcp    //在防火墙关闭端口,如关闭80端口  

