# Nginx的访问控制
基于IP的访问控制 - http_access_module
基于用户的信任登录 - http_auth_basic_module

http_access_module
Syntax:allow address | CIDR | unix: | all;
Default:-
Context:http,server,location,limit_except
---
Syntax:deny address | CIDR | unix: | all;
Default:-
Context:http,server,location,limit_except


http_x_forwarded_for
http_x_forwarded_for = Client IP,Proxy(1)IP,Proxy(2)IP,...

---
http_access_module局限性
方法一：采用别的HTTP头信息控制访问，如：HTTP_X_FORWARDED_FRO
方法二：结合geo模块作
方法三：通过HTTP自定义变量传递