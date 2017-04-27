---
title: Excel Services 最佳实践
keywords: guidelines
f1_keywords:
- guidelines
ms.prod: OFFICE365
ms.assetid: 56fa3913-c156-49da-bed0-a6a106fc129f
---


# Excel Services 最佳实践

本主题列出了使用 Excel Services 的最佳做法建议。
  
    
    


## 减轻威胁


### 匿名访问和信息泄露

以下设置组合使匿名用户可以访问过程帐户有权访问的共享中的任何文件。因此，建议不要使用以下设置组合，因为它可能导致信息泄漏：
  
    
    

- 对 Microsoft SharePoint Foundation 的匿名访问已启用。
    
  
- 您具有 UNC 信任的位置，且"过程帐户"已启用。
    
  

> **注释**
> "过程帐户"是影响所有受信任位置的全局 Excel Services 设置。 
  
    
    


### 查看过程帐户选项


1. 在"开始"菜单中，单击"所有程序"。
    
  
2. 指向"Microsoft SharePoint 2010 产品"，然后单击"SharePoint 管理中心"。
    
  
3. 在"应用程序管理"下，单击"管理服务应用程序"。
    
  
4. 在"管理服务应用程序"页面上，单击"Excel Services 应用程序"。
    
  
5. 在"Excel Services 应用程序"页面上，单击"全局设置"。
    
  
6. 在"安全"部分中，在"文件访问方法"下查找"过程帐户"选项。
    
  

### 拒绝服务攻击

在对 Web 服务的拒绝服务攻击中，攻击者将生成针对 Web 服务的单个超大请求。其目的是试图利用一个或多个 Web 服务输入值的限制。
  
    
    
建议您使用 Microsoft Internet Information Services (IIS) 设置来设置 Web 服务的最大请求大小。
  
    
    
使用 **system.web** 元素中 **httpRuntime** 元素的 **maxRequestLength** 属性防御拒绝服务攻击，这可能是由于用户在服务器上发布大型文件所致。默认大小为 4096 KB (4 MB)。
  
    
    
有关详细信息，请参阅 [<httpRuntime> Element](http://msdn.microsoft.com/library/e9b81350-8aaf-47cc-9843-5f7d0c59f369.aspx)和 [<maxRequestLength> Element](http://msdn.microsoft.com/library/fd52b2c5-5014-4e6f-b869-4ea666dc83d6.aspx)。
  
    
    

### 在调用应用程序和 Web 服务计算机之间监听

如果调用应用程序和 Excel Web Services 部署到不同的计算机，攻击者可以侦听调用应用程序和 Web 服务之间数据传输的网络流量。此威胁也称为"监听"或"窃听"。
  
    
    
为帮助减轻此威胁，我们建议您：
  
    
    

- 使用安全套接字层 (SSL) 设置一个安全通道来保护客户端和服务器之间的数据传输。SSL 协议可保护数据不被任何具有网络物理访问权限的用户监听。
    
  
- 如果使用 Excel Web Services 的自定义应用程序在封闭网络中运行，请采取物理措施保护相关网络例如，如果 Excel Web Services 部署在企业内的 Web 前端计算机上。
    
  
有关详细信息，请参阅 [Securing Your Network](http://msdn.microsoft.com/library/af62ece0-0dd7-4b8e-ad12-4d13f2d60816.aspx)和  [SOAP 安全](http://msdn.microsoft.com/zh-cn/library/aa912494.aspx)。
  
    
    
有关 Excel Services 拓扑、可扩展性、性能和安全性的信息，请参阅 Microsoft SharePoint Server 2010 技术中心。
  
    
    

### 网络钓鱼

我们建议您使用 SSL 以帮助减轻 Web 服务 Internet 协议 (IP) 地址和端口被黑客攻击的威胁，并帮助防御攻击者代表 Web 服务接收和回复请求。
  
    
    
SSL 证书根据多个属性进行匹配，其中一个是消息从其传递的 IP 地址。如果 IP 地址没有 Web 服务 SSl 证书，攻击者则无法仿冒该 IP 地址。
  
    
    
有关详细信息，请参阅 [Securing Your Network](http://msdn.microsoft.com/library/af62ece0-0dd7-4b8e-ad12-4d13f2d60816.aspx)。
  
    
    

## Excel Services 用户定义函数 (UDF)


### 强名称相关性

在某些情况下，用户定义函数 (UDF) 程序集依赖于与它一起部署的其他程序集。如果这些相关 DLL 位于全局程序集缓存中，或者位于与 UDF 程序集相同的文件夹中，将加载成功。
  
    
    
但是，在后一种情况，如果 Excel Calculation Services 已加载使用相同名称的其他程序集，加载可能会失败。（失败可能是由于程序集命名不严格，或者由于已部署和加载使用相同名称的另一个版本。）
  
    
    
考虑使用以下目录结构的方案：
  
    
    

1. C:\\Udfs\\Udf01
    
    Udf01 文件夹包含:
    
  - Udf01.dll 
    
  
  - dependent.dll（未严格命名）
    
  

    Udf01.dll 文件对 dependent.dll 文件具有依赖性。
    
  
2. C:\\Udfs\\Udf02
    
    Udf02 文件夹包含:
    
  - Udf02.dll（依赖于 Interop.dll）
    
  
  - dependent.dll（未严格命名）
    
  

    Udf02.dll 文件对 dependent.dll 文件具有依赖性。Udf01.dll 的依赖性和 Udf02.dll 的 UI 依赖性共享同一个名称。但 Udf02.dll 的 dependent.dll 文件与 Udf01.dll 的 dependent.dll 文件并不相同。
    
  
假定以下流：
  
    
    

1. Udf01.dll 是要第一个加载的 DLL。Excel Calculation Services 查找 dependent.dll 并加载 Udf01.dll 的相关性，在本示例中为 dependent.dll。 
    
  
2. Udf02.dll 在 Udf01.dll 之后加载。Excel Calculation Services 看到 Udf02.dll 依赖于 dependent.dll。但是，名为"dependent.dll"的 DLL 已加载。因此，Udf02.dll 的 dependent.dll 文件未加载，当前加载的 dependent.dll 文件用作相关性。
    
  
因此，对象不会加载到内存中，在本示例中为 Udf02.dll 需要的 dependent.dll 文件。
  
    
    
为避免名称冲突，我们建议您对依赖性进行强命名，并将它们唯一命名。
  
    
    

## 常规


### 命名托管代码 DLL

为确保您的程序集名称唯一，请使用完全限定的类名，遵循 [Namespace Naming Guidelines](http://msdn.microsoft.com/library/c08bc0d8-9b3a-4564-9af6-71699f62e00d.aspx)。
  
    
    
例如，使用 CompanyName.Hierarchichal.Namespace.ClassName，而非 Namespace.ClassName。 
  
    
    

## 另请参阅


#### 任务


  
    
    
 [如何：信任位置](how-to-trust-a-location.md)
#### 概念


  
    
    
 [Excel Services 体系结构](excel-services-architecture.md)
  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
  
    
    
 [Excel Services 警告](excel-services-alerts.md)
  
    
    
 [Excel Services 已知问题和提示](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services 博客、论坛和资源](excel-services-blogs-forums-and-resources.md)
