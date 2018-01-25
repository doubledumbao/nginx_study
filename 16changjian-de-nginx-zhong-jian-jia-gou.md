# 进阶学习-常见的Nginx中间件架构

## 一、静态资源WEB服务

## 二、代理服务

## 三、负载均衡调度器SLB

## 四、动态缓存



### 一、静态资源WEB服务
####语法配置-文件读取
Syntax:sendfile on | off;
Default:sendfile off;
Context:http,server,location,if in location

引读：-with-file-aio 异步文件读取
---
####语法配置-tcp_nopush
Syntax:tcp_nopush on | off;
Default:tcp_nopush off;
Context:http,server,location
作用：sendfile开启的情况下，提高网络包的传输效率
####-tcp_nodelay
Syntax:tcp_nodelay on | off;
Default:tcp_nodelay on;
Context:http,server,location
####配置语法-压缩
Syntax:gzip on | off;
Default:gzip off;
Context:http,server,location,if in location
作用：压缩传输
####配置语法-压缩
Syntax:gzip_comp_level level;
Default:gzip_comp_level 1;
Context:http,server,location


