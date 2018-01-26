# 跨域访问

Syntax:add\_header name value \[always\];  
Default:-  
Context:http,server,location,if in location

实验步骤：  
搭建两台nginx服务器,ip地址分别是192.168.234.131和192.168.234.132。浏览器访问192.168.234.132机器上的页面，该页面有用ajax调用192.168.234.131的页面。  
配置如下：

192.168.234.132的页面如下：

```
<!DOCTYPE html>
<html>
        <head>
                <meta charset="UTF-8">
                <title>跨域请求测试页面</title>
                <script src="./js/jquery.min.js"></script>
        </head>

        <body>
                <h1>跨域请求测试</h1>
                <button id="hello">跨域请求</button>
                <script>
                        $("#hello").click(function(){
                                $.ajax({
                                        type:"get",
                                        url:"http://192.168.234.131:9000/",
                                        async:true,
                                        success:function(){
                                                alert("success");
                                        },
                                        error:function(){
                                                alert("error");
                                        }
                                });
                        });

                </script>
        </body>
</html>
```

192.168.234.132的配置文件如下：

```
server {
    listen       80;
    server_name  localhost;
    gzip on;
    #charset koi8-r;
    #access_log  /var/log/nginx/host.access.log  main;
    #location ~ .*\.(html|htm)$ {
    #   expires 24h;
    #   root /opt/app/code/html;
    #}

    location / {
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


}
```

192.168.234.131的配置文件如下：

```
server {
    listen       9000;
    server_name  localhost;

    #charset koi8-r;
    #access_log  /var/log/nginx/host.access.log  main;

    location / {
        add_header Access-Control-Allow-Origin http://192.168.234.132;
        add_header Access-Control-Allow-Methods GET,POST,PUT,DELETE,OPTIONS;
        root   /usr/share/nginx/html;
        index  index.html index.htm;
    }

    #error_page  404              /404.html;

    # redirect server error pages to the static page /50x.html
    #
    error_page   500 502 503 504  /50x.html;
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

}
```

浏览器请求页面

![](/assets/browser.png)

