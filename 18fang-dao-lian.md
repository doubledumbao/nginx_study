##基于http_refer防盗链配置模块
Syntax:valid_refer none|blocked|server_names
Default:-
Context:server,location

---
192.168.234.132配置
```
server {
    listen       80;
    server_name  localhost;
    gzip on;
    #charset koi8-r;
    #access_log  /var/log/nginx/host.access.log  main;
    #location / {
      # expires 24h;
    #   root /opt/app/code;
    #}
    location ~ .*\.(jpg|png|jpeg)$ {
       valid_referers none blocked 192.168.234.132;
       if ($invalid_referer) {
          return 403;
       }
       root /opt/app/code/images;
    }
    location ~ .*\.(html|htm)$ {
       #add_header Access-Control-Allow-Origin *;
       #add_header Access-Control-Allow-Methods GET,POST,PUT,OPTIONS;
       root /opt/app/code/html;
       index jsonweb.html 1.html;
    }
    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

    # proxy the PHP scripts to Apache listening on 127.0.0.1:80
    #
    #location ~ \.php$ {
    #    proxy_pass   http://127.0.0.1;
    #}

    # pass the PHP scripts to FastCGI server listening on 127.0.0.1:9000
    #
    #location ~ \.php$ {
    #    root           html;
    #    fastcgi_pass   127.0.0.1:9000;
    #    fastcgi_index  index.php;
    #    fastcgi_param  SCRIPT_FILENAME  /scripts$fastcgi_script_name;
    #    include        fastcgi_params;
    #}

    # deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    #    deny  all;
    #}
}
```
192.168.234.132的页面
---
```
<!DOCTYPE html>
<html>
        <head>
                <meta charset="UTF-8">
                <title>测试防盗链</title>
        </head>
        <body>
                <img src="li.jpg"/>
        </body>
</html>
```
192.168.234.131的页面
```
<!DOCTYPE html>
<html>
        <head>
                <meta charset="UTF-8">
                <title>测试防盗链</title>
        </head>
        <body>
                <img src="http://192.168.234.132/li.jpg"/>
        </body>
</html>
```

