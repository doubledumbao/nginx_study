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



