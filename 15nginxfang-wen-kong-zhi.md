# Nginx的访问控制

基于IP的访问控制 - http\_access\_module  
基于用户的信任登录 - http\_auth\_basic\_module

##http\_access\_module  
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

---
---
##http_auth_basic_module
Syntax:auth_basic string | off;
Default:auth_basic off;
Context:http,server,location,limit_except
---
Synax:auth_basic_user_file file;
Default:-
Context:http,sever,location,limit_except


