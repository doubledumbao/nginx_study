#跨域访问

Syntax:add_header name value [always];
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

```
