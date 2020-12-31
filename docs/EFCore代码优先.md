# EFCore 代码优先

这里只记录常用的命令。推荐使用方式一

## 方式一

?> 在 VSCode 环境下，需要先安装`dotnet-ef`工具。(也适用于普通命令行)  
安装命令：`dotnet tool install -g dotnet-ef`  
`dotnet tool` 分为`全局工具`和`本地工具`,它们的使用方式有所不同,详细差异查考官网[.NET 工具](https://docs.microsoft.com/zh-cn/dotnet/core/tools/global-tools#install-a-local-tool)

```tex
//查看帮助
dotnet ef

//生成迁移文件命令
dotnet ef migrations add CreateDatabase --context backdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model --output-dir Migrations/BackDb

//执行修改数据库命令
dotnet ef database update --context backdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model

//执行移除迁移文件命令
dotnet ef migrations remove --context backdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model

//执行删除数据库命令
dotnet ef database drop --context backdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model
```

## 方式二

?> Visual Studio 环境下，就直接打开包管理控制台运行命令

```tex
//获取帮助文档
PM> get-help entityframework

//生成迁移文件
PM> add-migration Upd -context zxscdbcontext //其中 Upd 为描述,并且首字母尽量大写

//修改数据库
PM> update-database -context zxscdbcontext //其中 -context 作用是指定要运行的DbContext

//移除迁移文件
PM> remove-migration -context zxscdbcontext

//移除上一次迁移操作 //删除数据库
PM> drop-database -context zxscdbcontext //发生无法解决的错误时使用
```

## 方式一完整的使用示例

### 如果 dotnet-ef 安装为全局工具

```tex
/*后台管理库*/
//生成迁移文件
dotnet ef migrations add CreateBackDatabase --context backdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model --output-dir Migrations/BackDb
//创建或修改数据库
dotnet ef database update --context backdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model

//移除迁移文件
dotnet ef migrations remove --context backdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model
//删除数据库
dotnet ef database drop --context backdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model

/*业务库*/
//生成迁移文件
dotnet ef migrations add CreateWorkDatabase --context workdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model --output-dir Migrations/WorkDb
//创建或修改数据库
dotnet ef database update --context workdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model

//移除迁移文件
dotnet ef migrations remove --context workdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model
//删除数据库
dotnet ef database drop --context workdbcontext --startup-project QuickFrame.Web --project QuickFrame.Model
```

### 如果 dotnet-ef 安装为本地工具

```tex
dotnet ef database drop --context backdbcontext --project ../QuickFrame.Model
dotnet ef migrations add CreateBackDatabase --context backdbcontext --project ../QuickFrame.Model --output-dir Migrations/BackDb
dotnet ef database update --context backdbcontext --project ../QuickFrame.Model

dotnet ef database drop --context workdbcontext --project ../QuickFrame.Model
dotnet ef migrations add CreateWorkDatabase --context workdbcontext --project ../QuickFrame.Model --output-dir Migrations/WorkDb
dotnet ef database update --context workdbcontext --project ../QuickFrame.Model
```
