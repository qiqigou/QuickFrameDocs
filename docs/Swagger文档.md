# Swagger 文档

Swagger 能够根据 api 注释、路由等信息生成 API 文档，并且提供访问功能

## 授权

提供了两种授权方式，OAuth2.0 授权方式现阶段仅适用于在开发环境下使用

### Token 授权方式

1.在配置文件`appconfig.Development.json`中将`IdentityServer:Enable`修改为`false`  
2.启动项目，并调用`/api/system/Token/GetToken`端点，取得 Token  
3.在 Swagger 文档页点击`Authorize`按钮  
![Authorize按钮](../../img/swagger-authorize.png ":size=35%")  
4.将 Token 组合为`Bearer {Token}`格式，并填入 Value 中，点击授权按钮即可  
![token](../../img/token-auth.png ":size=35%")

### OAuth2.0 授权方式

?> 先决条件：需要启动`ZxSSO`项目

1.在配置文件`appconfig.Development.json`中将`IdentityServer:Enable`修改为`true`  
2.启动项目，在 Swagger 文档页点击`Authorize`按钮  
3.client_id 中填入`test`,并且勾选要访问的资源`zxsofterp_core`，然后点击`Authorize`进行认证授权  
![登录](../../img/swagger-login.png ":size=35%")  
4.这时会跳转到`ZxSSO`项目中，点击登录，确认授权即可。

#### OAuth2.0 授权偶尔出现的问题

!> 偶尔刷新页面后重新授权出现授权失败的问题。这个问题是由 swagger 引起的，与 IdentityServer4 无关

![问题](../../img/swagger-login-error.png ":size=35%")

解决：去掉 url 后面的参数后重试

![解决](../../img/Snipaste_2020-11-19_13-10-45.png ":size=35%")
