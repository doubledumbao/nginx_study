### 四个确认：

#### 1.确认网络可用。

#### 2.确认yum可用。

#### 3.关闭iptables。

命令：

查看iptables规则： iptables -L  

关闭iptables规则：iptables -F

查看iptables nat 规则：iptables -t nat -L

关闭iptables nat 规则：iptables -t nat -F

#### 4.关闭selinux。

查看selinux是否开启：getenforce

关闭selinux:setenforce 0

