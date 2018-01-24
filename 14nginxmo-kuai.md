# nginx模块

| 编译选项 | 作用 |
| :--- | :--- |
| --with-http\_stub\_status\_module | Nginx的客户端状态 |

http\_stub\_status\_module配置

Syntax: stub\_status;

Default:-

Context:server,location

| 编译选项 | 作用 |
| :--- | :--- |
| --with-http\_random\_index\_module | 目录中选择一个随机主页 |

random\_index\_module  
Syntax:random\_index on \| off;  
Default:random\_index off;  
Context:location

| 编译选项 | 作用 |
| :--- | :--- |
| --with-http\_sub\_module | HTTP内容替换 |

http\_sub\_module

Syntax: sub\_filter  string（修改前的字符串） replacement（修改后的字符串）;

Default:-

Context:http,server,location

