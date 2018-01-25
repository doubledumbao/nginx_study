# 进阶学习-常见的Nginx中间件架构

## 一、静态资源WEB服务

## 二、代理服务

## 三、负载均衡调度器SLB

## 四、动态缓存

### 一、静态资源WEB服务

#### 语法配置-文件读取

Syntax:sendfile on \| off;  
Default:sendfile off;  
Context:http,server,location,if in location

## 引读：-with-file-aio 异步文件读取

#### 语法配置-tcp\_nopush

Syntax:tcp\_nopush on \| off;  
Default:tcp\_nopush off;  
Context:http,server,location  
作用：sendfile开启的情况下，提高网络包的传输效率

#### -tcp\_nodelay

Syntax:tcp\_nodelay on \| off;  
Default:tcp\_nodelay on;  
Context:http,server,location

#### 配置语法-压缩

Syntax:gzip on \| off;  
Default:gzip off;  
Context:http,server,location,if in location  
作用：压缩传输

#### 配置语法-压缩

Syntax:gzip\_comp\_level level;  
Default:gzip\_comp\_level 1;  
Context:http,server,location

#### 配置语法-压缩

Syntax:gzip\_http\_version 1.0 \| 1.1;  
Default:gzip\_http\_version 1.1;  
Context:http,server,location

---

```
server {
    listen       80;
    server_name  localhost;
    sendfile on;
    #charset koi8-r;
    #access_log  /var/log/nginx/host.access.log  main;
   
    location ~ .*\.(png|jpeg|gif)$ {
        gzip on;
        gzip_http_version 1.1;
        gzip_comp_level 2;
        gzip_types text/plain application/javascript application/x-javascript text/css application/xml text/javascript application/x-httpd-php image/jpeg image/gif image/png;
        root /opt/app/code/image;
    } 
    
    location ~ .*\.(txt|xml)$ {
        gzip on;
        gzip_http_version 1.1;
        gzip_comp_level 3;
        gzip_types text/plain application/javascript application/x-javascript text/css application/xml text/
javascript application/x-httpd-php image/jpeg image/gif image/png;
        root /opt/app/code/doc;
    } 
    location ~ ^/download {
        gzip_static on;
        tcp_nopush on;
        root /opt/app/code;

    }    
#error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page 404 500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

}
```





