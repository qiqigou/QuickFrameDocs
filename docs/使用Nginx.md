# Nginx 的简单使用

nginx 是一个静态的 http 服务器。不仅能够部署静态网站，还能转发请求(反向代理)，简单的负载均衡。是.NET Core 开发必备的神奇之一

## 如何安装

官网下载：[Nginx](http://nginx.org/en/download.html)

## 如何配置

?> `listen 80`是指监听`80`端口  
`server_name 0.0.0.0`是指监听所有 IP,如果想要外网访问本网站就可以这样设置  
`location /dev`指定访问子域名。例如：`http://localhost/dev`  
`alias`指定访问的本地文件位置

如图所示:

![nginxconfig](../../img/nginxconfig.png ":size=50%")
