ssh-keygen -t rsa  
默认在 ~/.ssh目录生成两个文件：  
id_rsa      ：私钥  
id_rsa.pub  ：公钥  
id_rsa.pub更名为: authorized_keys  权限600  

vi /etc/ssh/sshd_config  
RSAAuthentication yes  
PubkeyAuthentication yes  
PasswordAuthentication no  //禁止密码登录
