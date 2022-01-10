# nginx 文件名逻辑漏洞 CVE-2013-4547

## 影响版本

`Nginx 0.8.41 ~ 1.4.3 / 1.5.0 ~ 1.5.7`

 # NGINX 越界读取缓存漏洞 - nginx 整数溢出漏洞 CVE-2017-7529

## 影响版本

`Nginx 0.5.6 - 1.13.2`

# 拒绝服务 CVE-2013-2028

## 影响版本

`nginx v1.3.9`

# DoS 漏洞 CVE-2010-2263 CVE-2010-2266

## 影响版本

`Nginx 0.8.36 `

# “logrotate” 本地权限提升 CVE-2016-1247

## 影响版本

`Debian: Nginx1.6.2-5+deb8u3
Ubuntu 16.04: Nginx1.10.0-0ubuntu0.16.04.3
Ubuntu 14.04: Nginx1.4.6-1ubuntu3.6
Ubuntu 16.10: Nginx1.10.1-0ubuntu1.1`

# 下载漏洞 CVE-2010-2263

## 影响版本

`Nginx <= 0.7.65 / 0.8.39 `

# 远程代码执行 CVE-2019-11043

## 影响版本

`未知`

`nginx.conf配置以下参数即可触发

    location ~ [^/]\.php(/|$) {
     ...
     fastcgi_split_path_info ^(.+?\.php)(/.*)$;
     fastcgi_param PATH_INFO $fastcgi_path_info;
     fastcgi_pass   php:9000;
     ...
    }
`

# 目录遍历序列输入验证漏洞 CVE-2010-2266

## 影响版本

`nginx 0.8.36 `

# HTTP 请求访问漏洞_CVE-2009-2622

## 影响版本

`nginx-0.6.38.tar.gz # 版本：<= 0.6.38, <= 0.7.61`

# 远程利用

## 影响版本

`nginx 1.3.9/1.4.0`
