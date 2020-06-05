一、网关版本号 8852

二、新增或优化功能
1. 镜像ip统一由11.22.33.44改为192.168.1.1
2. 支持中兴版本的功能。比如数据或日志保存在/opt/var目录下，并且软链接过去
3. 支持异地S3的配置。/cirrusgate/config/cirrus.ini中配置s3_server=https://192.168.20.11:9000
4. 支持邮件messageId相同的去重功能。falco.ini中skip_repeat_messageid=1，默认配置为1
5. 系统加固（系统漏扫加固、root默认密码修改）
	1）Tomcat在升级时会自动升级到最新版本，即apache-tomcat-7.0.100.tar和apache-tomcat-8.5.51.tar	
	2）数据库可以升级到Mariadb10.3.22（仅支持CentOS7.4），注意：数据库升级时不会升级数据库软件本身的版本。除非使用在脚本里选择升级数据库软件本身。
	3）openssh升级到openssh-8.1p1

三、修改的Bug
1、网络DLP，smtp事件有时候相同的样本1次报3条或5条事件

四、后台脚本更新
1. 支持中转服务器上的补丁包升级
2. 支持二级中转服务器的安装，配置。
3. Tomcat升级（说明：执行upgrade.sh后台默认升级，如分布式升级，执行如下命令）
install_all_falco_with_log.sh detail-->1): Upgrade some unit --> 7):Upgrade all tomcat
4. 脚本安装时可以自动执行builtin_conditions_20200221_020349.sql脚本（脚本位置..\platform），导入内置条件
5. 数据库支持正式版与测试版切换
6. 多个mdlp(mds)服务器配合实现共同邮件扫描的功能。一台服务器getmail从邮件服务器下载邮件，分配到各个服务器进行扫描。
