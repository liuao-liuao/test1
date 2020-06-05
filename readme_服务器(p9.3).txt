一、服务器版本 40753

二、优化功能或修复bug
1. 系统加固（双向传输强认证，系统漏扫加固、root默认密码修改）
	1）Tomcat在升级时会自动升级到最新版本，即apache-tomcat-7.0.100.tar和apache-tomcat-8.5.51.tar	
	2）数据库可以升级到Mariadb10.3.22（仅支持CentOS7.4），注意：数据库升级时不会升级数据库软件本身的版本。除非使用在脚本里选择升级数据库软件本身。
	3）openssh升级到openssh-8.1p1
2. 补上数据库中用户表缺的索引
3. 支持全新安装和从P9.2直接升级的升级脚本
4. Fastjson升级至最新1.2.67版本
5 之前版本内置条件需要手动导入，升级至p9.3或者全新安装p9.3完成后，内置条件显示285条（内置条件增加姓名）

三、新增功能
1. 支持异地S3（可通过配置文件开关）添加主管理,二级异地S3配置信息:
	一级: /var/lib/tomcat7/webapps/DLP/WEB-INF/classes/application.properties
	二级: /var/lib/tomcat7/webapps/operationService/WEB-INF/classes/application.properties
	enable.off.site.data=false,是否启用异地S3 (true为启用,false为禁用,默认为false)                 
	data.store.bucket=version,异地S3桶名
说明：配置详见《思睿嘉得数据泄露防护系统（DLP4.0）产品配置手册V3.9.docx》2.1.14章节或安装部署手册

2. 支持中转服务器
说明：安装和检查事项详见
《思睿嘉得数据泄露防护系统（DLP4.0）二级中转服务器安装部署手册V1.2.docx》
《二级中转服务器布署后检查注意事项_v1.1.docx》

3. 支持手动域用户域密码认证（可通过配置文件开关）
所有二级配置文件：/var/lib/tomcat7/webapps/operationService/WEB-INF/classes/application.properties
添加配置项：enable.AD.authentication=true, (true为启用,false为禁用,默认为true)

4. 产品登录页面的终端下载链接默认隐藏，如需开启下载链接则在服务器修改后台配置文件
一级配置文件：/var/lib/tomcat7/webapps/DLP/WEB-INF/classes/appliaction.properties
添加配置项：enable.client.pkg.download=false。false为不显示，true为显示，默认为false

5. 增加终端禁用启用日志

四、修改的Bug
1、扫描结果管理-全部导出功能，数据发现模块，扫描完成后，导出全部数据功能导出的表格为空
2、管理平台—安全事件—姓名查询框输入异常
3、系统设置-邮件服务器设置-服务器地址只能填写smtp开头的域名
4、系统设置-域服务器设置，域服务器地址中无法填写带两个点的域名
5、管理平台---->组织机构管理---->导入用户模板文件时报错，原因是：导入的文件内容用户名和邮箱中含点（.），如用户名是：sam.zhang，邮箱是：sam.zhang@xxxx.com
6、升级到p9版本：事件管理--点开一个事件详情页面--点击用户姓名(用户姓名后面带括号)--跳转到事件查询页面，发现筛选项里面的用户姓名是乱码；如果事件详情里面的用户姓名没有带括号，点击用户姓名跳转到事件查询页面后，筛选项里面的用户姓名正常显示，正常查询
7、事件管理--用户姓名搜索页面--支持输入符号查询，比如带有括号（） _ 等，和用户账号是一样的

五、升级说明
详见升级手册《思睿嘉得数据泄露防护系统（DLP4.0）服务器及网关升级说明(20200103-20200323).docx》
