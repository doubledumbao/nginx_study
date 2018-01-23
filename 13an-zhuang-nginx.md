# 安装nginx

打开nginx网站 [http://nginx.org/en/linux\_packages.html\#stable](http://nginx.org/en/linux_packages.html#stable)

To set up the yum repository for RHEL/CentOS, create the file named`/etc/yum.repos.d/nginx.repo`with the following contents:

> ```
> [nginx]
> name=nginx repo
> baseurl=http://nginx.org/packages/OS/OSRELEASE/$basearch/
> gpgcheck=0
> enabled=1
> ```

Replace “`OS`” with “`rhel`” or “`centos`”, depending on the distribution used, and “`OSRELEASE`” with “`6`” or “`7`”, for 6.x or 7.x versions, respectively.

按照上面的说明，进行配置。

开启nginx

service nginx start

关闭nginx

service nginx stop

重新加载配置文件

nginx -s reload -c /etc/nginx/nginx.conf

查看帮助

nginx version: nginx/1.12.2

Usage: nginx \[-?hvVtTq\] \[-s signal\] \[-c filename\] \[-p prefix\] \[-g directives\]

Options:

-?,-h         : this help

-v            : show version and exit

-V            : show version and configure options then exit

-t            : test configuration and exit

-T            : test configuration, dump it and exit

-q            : suppress non-error messages during configuration testing

-s signal     : send signal to a master process: stop, quit, reopen, reload

-p prefix     : set prefix path \(default: /etc/nginx/\)

-c filename   : set configuration file \(default: /etc/nginx/nginx.conf\)

-g directives : set global directives out of configuration file

检查配置文件是否正确

nginx -t -c /etc/nginx/nginx.conf



