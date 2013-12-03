zabbix-rpm是一个轻松构建zabbix监控系统的的rpm二次定制项目。
```
如果你想偷懒，想安装好之后即可访问，并且几分钟搞定所有事情，且服务器环境满足以下：
     一台全的服务器，系统为RHEL6.X 或者CentOS6.X，注意，只支持64位系统。
     配置好网络，yum源，如果是本地yum源，会用到其他rpm包，因此，建议你使用下epel源
     rpm -ivh http://yum.puppetlabs.com/el/6/products/x86_64/puppetlabs-release-6-6.noarch.rpm 
     这些准备工作做好，那就开始吧，
克隆rpm包到本地
1. git clone https://github.com/itnihao/zabbix-rpm.git
2. cd zabbix-rpm
服务端安装
3. yum localinstall  zabbix-server-2.2.0-0.el6.zbx.x86_64.rpm   \
                     zabbix-server-mysql-2.2.0-0.el6.zbx.x86_64.rpm  \
                     zabbix-web-apache-2.2.0-0.el6.zbx.noarch.rpm
代理端安装
4. yum localinstall  zabbix-proxy-2.2.0-0.el6.zbx.x86_64.rpm   \
                     zabbix-proxy-mysql-2.2.0-0.el6.zbx.x86_64.rpm
客户端安装
5. yum localinstall  zabbix-agentd-2.2.0-0.el6.zbx.x86_64.rpm

zabbix-java-gateway安装
6.yum localinstall   zabbix-java-gateway-2.2.0-0.el6.zbx.x86_64.rpm



说明：
    如果你只作为测试环境，只需要安装server和agent即可
    安装过程会自动解决依赖关系，安装好之后呢，通过浏览器即可访问 http://x.x.x.x/zabbix
    默认的zabbix web登录用户为admin，密码为zabbix，
    默认的mysql密码为MysqlPassword

    本次只做了安装，模板等后面继续添加。    
如有任何问题，可以联系我解决，QQ群216490997(zabbix交流2群)


本项目的意义所在：
    1.快速安装，标准配置，几分钟之内即可构建zabbix系统，解决新手安装问题，获得很好的体验，能快速的学习上手。
    2.大规模批量安装，rpm包定制的规范，可以作为参考案例。
    3.提供了SRPM包，大家可以基于此二次定制，欢迎参与本项目。
    4.后续会集成更多模板，方便大家使用。
```
