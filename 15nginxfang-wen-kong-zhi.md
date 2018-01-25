# Nginx的访问控制

基于IP的访问控制 - http\_access\_module  
基于用户的信任登录 - http\_auth\_basic\_module

## http\_access\_module

Syntax:allow address \| CIDR \| unix: \| all;  
Default:-

Context:http,server,location,limit\_except

---

Syntax:deny address \| CIDR \| unix: \| all;  
Default:-  
Context:http,server,location,limit\_except

http\_x\_forwarded\_for  
http\_x\_forwarded\_for = Client IP,Proxy\(1\)IP,Proxy\(2\)IP,...

---

http\_access\_module局限性  
方法一：采用别的HTTP头信息控制访问，如：HTTP\_X\_FORWARDED\_FRO  
方法二：结合geo模块作  
方法三：通过HTTP自定义变量传递

## http\_auth\_basic\_module

Syntax:auth\_basic string \| off;  
Default:auth\_basic off;

Context:http,server,location,limit\_except

Synax:auth\_basic\_user\_file file;  
Default:-  
Context:http,sever,location,limit\_except

---

查看本机是否安装htpasswd软件  
rpm -qf /usr/bin/htpasswd

```
[root@doubledumbao conf.d]# rpm -qf /usr/bin/htpasswd
httpd-tools-2.4.6-45.el7.centos.4.x86_64
```

如果没有安装执行  
yum info httpd-tools  
yum install -y httpd-tools

---

http\_auth\_basic\_module局限性  
一、用户信息依赖文件方式  
二、操作管理机械，低效  
解决方案  
一、Nginx结合LUA实现高效验证  
二、Nginx和LDAP打通，利用nginx-auth-ldap模块

