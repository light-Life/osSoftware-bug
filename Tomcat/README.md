# 提权 CVE-2016-1240
## 影响版本
Tomcat 8 <= 8.0.36-2   
Tomcat 7 <= 7.0.70-2   
Tomcat 6 <= 6.0.45+dfsg-1~deb8u1  
# 文件包含漏洞 CVE-2020-1938
## 影响版本
Apache Tomcat 6
Apache Tomcat 7 \< 7.0.100
Apache Tomcat 8 \< 8.5.51
Apache Tomcat 9 \< 9.0.31
# 漏洞详情
对于处在漏洞影响版本范围内的 Tomcat 而言，若其开启 AJP Connector 且攻击者能够访问 AJP Connector 服务端口的情况下，即存在被 Ghostcat 漏洞利用的风险。
 注意 Tomcat AJP Connector 默认配置下即为开启状态，且监听在 0.0.0.0:8009
## 修复方案
禁用AJP端口
#  Tomcat 本地提权漏洞 CVE-2016-1240
## 漏洞详情
Debian系统的Linux上管理员通常利用apt-get进行包管理，CVE-2016-1240这一漏洞其问题出在Tomcat的deb包中,使 deb包安装的Tomcat程序会自动为管理员安装一个启动脚本：/etc/init.d/tocat利用该脚本，可导致攻击者通过低权限的Tomcat用户获得系统root权限！
## 影响版本
Tomcat 8 \<= 8.0.36-2 Tomcat 7 \<= 7.0.70-2 Tomcat 6 \<= 6.0.45+dfsg-1\~deb8u1
## 修复方案
1.及时更新tomcat版本
2.加入-h参数防止其他文件所有者被更改
chown -h $TOMCAT6_USER “$CATALINA_PID” “$CATALINA_BASE”/logs/catalina.out
# 通过 JSP 上传绕过的 Tomcat RCE CVE-2017-12617
## 漏洞详情
Apache Tomcat 版本9.0.0.M1至9.0.0、8.5.0至8.5.22、8.0.0.RC1至8.0.46和7.0.0至7.0.81且允许HTTP PUT时（例如，通过设置只读如果将默认 servlet 的初始化参数设置为 false，则可以通过特制请求将 JSP 文件上传到服务器。然后可以请求此 JSP，并且服务器将可以包含其中的所有代码。
## 影响版本
Apache Tomcat版本9.0.0.M1至9.0.0Apache Tomcat版本8.5.0至8.5.22Apache Tomcat版本8.0.0.RC1至8.0.46Apache Tomcat版本7.0.0至7.0.81
## 修复方案
将Tomcat更新到该漏洞被修复的版本（例如，Tomcat 8.5.23）只能防止攻击者上传JSP。

但是readonlyinit-param不应该将false首先设置。如果此参数保留到默认（true），则攻击者无法上传文件
# Tomcat 信息泄露 CVE-2017-12616
## 漏洞详情
 CVE-2017-12616(信息泄露):允许未经身份验证的远程攻击者查看敏感信息。如果tomcat开启VirtualDirContext有可能绕过安全限制访问服务器上的JSP文件源码。漏洞触发的先决条件是需要在conf/server.xml配置VirtualDirContex参数，默认情况下tomcat7并不会对该参数进行配置。

那么为什么要配置一个这样的虚拟目录呢？

通过VirtualDirContext,允许在单独的一个webapp应用下对外暴露出多个文件系统的目录。在实际开发中，为了避免拷贝静态资源文件如(images等)至webapp目录下，tomcat推荐的做法是在server.xml配置文件中建立虚拟子目录。

在开启了这个配置之后，可以通过windows目录下的文件的解析问题，从而暴露在在目录中的源码。
## 影响版本
Apache Tomcat 7.0.0 - 7.0.80
# session 反序列化漏洞 CVE-2020-9484
## 漏洞详情
对 于一个企业级应用而言，Session对象的管理十分重要。Sessio对象的信息一般情况下置于服务器的内存中，当服务器由于故障重启，或应用重新加载 时候，此时的Session信息将全部丢失。为了避免这样的情况，在某些场合可以将服务器的Session数据存放在文件系统或数据库中，这样的操作称为 Session对象的持久化。Session对象在持久化时，存放在其中的对象以序列化的形式存放，这就是为什么一般存放在Session中的数据需要实 现可序列化接口（java.io.Serializable）的原因了。当一个Session开始时，Servlet容器会为Session创建一个HttpSession对象。Servlet容器在某些情况下把这些 HttpSession对象从内存中转移到文件系统或数据库中，在需要访问 HttpSession信息时再把它们加载到内存中
## 影响版本
Tomca \<= 9.0.34Tomca \<= 8.5.54Tomca \<= 7.0.103
## 修复方案
升级版本
禁止使用Session持久化功能FileStore。（或单独配置sessionAttributeValueClassNameFilte的值确保只有特定属性的对象可以被序列化与反序列化）
# XSS 漏洞 CVE-2011-0013
## 影响版本
Tomcat 7.0.0 到 7.0。 5  
Tomcat 6.0.0 到 6.0.29  
Tomcat 5.5.0 到 5.5.31  
早期不受支持的版本也可能受到影响  
# Tomcat UTF-8 目录遍历 CVE-2008-2938
## 影响版本
Tomcat < 6.0.18
# Tomcat 信息泄露 CVE-2008-5515
## 受影响的版本
Tomcat 4.1.0 到 4.1.39  
Tomcat 5.5.0 到 5.5.27  
Tomcat 6.0.0 到 6.0.18  
不支持的 Tomcat 3.x、4.0.x 和 5.0.x 版本也可能受到影响  
# Tomcat 跨站脚本 CVE-2009-0781
## 漏洞详情
示例中的日历应用程序包含无效的 HTML，这  
使得对时间参数的 XSS 保护无效。一个  
因此攻击者就可以使用的时间属性的XSS攻击。  
## 影响版本
Tomcat 6.0.0 到 6.0 .18  
Tomcat 5.5.0 到 5.5.27  
Tomcat 4.1.0 到 4.1.39  
## 修复方案
6.0.x 用户应执行以下操作之一：  
 删除示例 Web 应用程序  
 应用此补丁 http://svn.apache.org/viewvc?rev=750924&view=rev  
 发布 5.5.x 时升级到 6.0.19  
用户应执行以下操作之一：  
 删除示例 Web 应用程序  
 应用此补丁http://svn.apache.org/viewvc?rev=750928&view=rev  
 发布
4.1.x时升级到 5.5.28  用户应该执行以下操作之一：  
 删除示例 Web 应用程序  
 应用此补丁 http:// svn.apache.org/viewvc?rev=750927&view=rev  
 发布时升级到 4.1.40 
