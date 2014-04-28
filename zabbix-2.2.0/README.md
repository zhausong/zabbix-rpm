zabbix-rpm是一个轻松构建zabbix监控系统的的rpm二次定制项目,基于官方rpm，但做了一些改动
```
如果你想偷懒，想安装好之后即可访问，并且几分钟搞定所有事情，且服务器环境满足以下：
     一台全的服务器，系统为RHEL6.X 或者CentOS6.X，注意，只支持64位系统。
     配置好网络，yum源，如果是本地yum源，会用到其他rpm包，因此，建议你使用下epel源
     rpm -ivh http://dl.fedoraproject.org/pub/epel/6/x86_64/epel-release-6-8.noarch.rpm  
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
    安装过程会自动解决依赖关系，安装好之后呢，通过浏览器即可访问 http://x.x.x.x/zabbix，注意防火墙设置
    默认的zabbix web登录用户为admin，密码为zabbix，
    默认的mysql密码为MysqlPassword

    本次只做了安装，模板等后面继续添加。    
如有任何问题，可以联系我解决，QQ群216490997(zabbix交流2群)


本项目的意义所在：
    1.快速安装，标准配置，几分钟之内即可构建zabbix系统，解决新手安装问题，获得很好的体验，能快速的学习上手。
    2.大规模批量安装，rpm包定制的规范，可以作为参考案例。
    3.提供了SRPM包，大家可以基于此二次定制，欢迎参与本项目。
    4.后续会集成更多模板，方便大家使用。
    
如何重新打包rpm呢？
yum  install rpm-build
useradd admin
su - admin  
mkdir -pv rpmbuild/{BUILD,RPMS,SOURCES,SPECS,SRPMS}  
echo "% _topdir  /home/admin/rpmbuild" >~/.rpmmacros  

rpm2cpio  zabbix-2.2.0-0.el6.zbx.src.rpm |cpio -div  #解压源码rpm包
解压出来的文件如下
cmdline-jmxclient-0.10.3.jar
zabbix-2.2.0-web-php.tar.gz
zabbix-2.2.0.tar.gz
zabbix-java-gateway.init
zabbix-proxy-mysql.sql
zabbix-server-mysql.sql
zabbix-web.conf
zabbix2.2.0.spec
zabbix_custom.tar.gz
zabbix_java_gateway_cmd

mv zabbix2.2.0.spec /home/admin/rpmbuild/SPECS
mv * /home/admin/rpmbuild/SOURCES

重新打包rpm，
cd  /home/admin/rpmbuild/SPECS
rpmbuild -ba zabbix2.2.0.spec #此处会提示你需要依赖包，依次安装
```
