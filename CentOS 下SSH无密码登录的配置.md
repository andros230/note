ssh-keygen -t rsa  
默认在 ~/.ssh目录生成两个文件：  
id_rsa      ：私钥  
id_rsa.pub  ：公钥  
新建文件 authorized_keys  权限600,并把公钥复制到authorized_keys里

vi /etc/ssh/sshd_config  
PasswordAuthentication no  //禁止密码登录
