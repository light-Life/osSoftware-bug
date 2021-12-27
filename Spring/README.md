# 利用 Spring Data REST PATCH 请求远程代码执行 CVE-2017-8046
## 影响版本
2.6.9 (Ingalls SR9)、3.0.1 (Kay SR1) 之前的 Spring Data REST 版本  
# 利用 Spring Security 标头注入 CVE-2011-2732
## 漏洞详情
Spring Security 允许使用参数（默认名为“spring-security-redirect”）来确定用户登录后将重定向到的位置 URL。这通常会作为登录请求的一部分提交，所以是被认为是可接受的远程提供数据的使用。但是，该功能位于注销代码共享的基类中，因此可能会恶意构建注销 URL 以包含此参数的版本，该版本包含 CRLF 字符，以便注入额外的标头或拆分响应。  
## 影响版本
2.0.0 到 2.0.6  
3.0.0 到 3.0.5  
## 修复方案
任何使用 Spring Security 的默认注销处理支持的人都可能容易受到攻击，除非他们使用不支持此参数的自定义 LogoutSuccessHandler。  
所有用户都可以通过升级到 3.0.6 来缓解这个问题  
2.0.x 的用户可以升级到 2.0.7  
# 利用 Spring Security 安全约束绕过 CVE-2010-3700
## 漏洞详情
Spring Security 在处理安全约束时不考虑 URL 路径参数。通过向请求添加 URL 路径参数，攻击者可能能够绕过安全约束。此问题的根本原因是 Servlet 规范中路径参数的处理不够明确（见下文）。有些 Servlet 容器在为 getPathInfo() 返回的值中包含路径参数，有些则没有。Spring Security 使用 getPathInfo() 返回的值作为将请求映射到安全约束的过程的一部分。路径参数的意外存在可能会导致绕过约束。  
## 影响版本
Spring Security 3.0.0 到 3.0.3  
Spring Security 2.0.0 t0 2.0.5  
Acegi Security 1.0 .0 到 1.0.7  
## 修复方案
 使用已知在 getServletPath() 和 getPathInfo() 的返回值中不包含路径参数的 Servlet 容器  
 升级到 Spring Security 2.0.6 或 Spring Security 3.0.4  
# 利用 Spring Framework 任意代码执行 CVE-2010-1622
## 漏洞详情
Spring Framework 提供了一种机制，可以使用客户端提供的数据来更新对象的属性。这种 
机制允许攻击者修改用于加载对象的类加载器的属性（通过 
'class.classloader'）。这可能导致任意命令执行，因为例如，攻击者可以修改
类加载器使用的 URL 以指向攻击者控制的位置。
## 影响版本
3.0.0 到 3.0.2
2.5.0至 2.5.6.SEC01（社区版本）
2.5.0 至 2.5.7（订阅客户）
## 修复方案
2.5.x 及更早版本的社区用户也可以通过升级 2.5.6.SEC02
2.5.x 及更早版本的订阅用户也可以通过升级 2.5 来缓解这个问题.6.SEC02 或 2.5.7.SR01
# 利用多个 SpringSource 产品多个 HTML 注入漏洞 CVE-2009-2907
## 影响版本
Hyperic HQ 4.0 4.0.3.2 之前的
Hyperic HQ 4.1 4.1.2.1 之前的
Hyper HQ 开源
Hyperic HQ 4.2 预发布
tc Server 6.0.20.B 和 2.0.0.SR4 之前的
AMS 2.0 
# 利用 Spring Security OAuth – 打开重定向器 CVE-2019-3778 CVE-2019-11269
## 漏洞详情
Spring Security OAuth 版本 2.3.6 之前的 2.3、2.2.5 之前的 2.2、2.1.5 之前的 2.1 和 2.0.18 之前的 2.0，以及旧的不受支持的版本可能容易受到开放重定向器攻击，从而泄漏授权码。恶意用户或攻击者可以使用授权代码授权类型向授权端点发出请求，并通过 redirect_uri 参数指定操纵的重定向 URI。这可能导致授权服务器将资源所有者用户代理重定向到攻击者控制下的 URI，并使用泄露的授权代码。
## 影响版本
Spring Security OAuth 2.3 2.3.6 之前的版本 -org.springframework.security.oauth:spring-security-oauth2 :2.3.3.RELEASE
# 利用 Spring Cloud Config 2.1.x – 路径遍历 (Metasploit) CVE-2019-3799
## 影响版本
它存在于 2.1.2 之前的 Spring Cloud Config 2.1.x
        版、2.0.4 之前的 2.0.x 版和 1.4.6 之前的 1.4.x 版中
