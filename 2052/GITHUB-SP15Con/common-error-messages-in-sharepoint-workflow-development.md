---
title: SharePoint 工作流开发中的常见错误消息
ms.prod: SHAREPOINT
ms.assetid: e9bf6878-c722-4b1f-b5b5-b302ae0ea4da
---


# SharePoint 工作流开发中的常见错误消息
在制定 SharePoint 工作流和指南以解决潜在问题时，您可能会遇到一系列常见错误消息。
## 常见 SharePoint 工作流错误

尽管此列表不会包含您在制定 SharePoint 工作流时可能遇到的所有问题，但是它确实包含您最可能遇见的问题。
  
    
    

-  [等待沙盒代码执行请求在工作进程中完成时出现超时](#bkmk_error01)
    
  
-  [在等待沙盒应用域完成请求时超时](#bkmk_error02)
    
  
-  [处理此请求的工作进程已终止，因为它超出资源 {0}](#bkmk_error03)
    
  
-  [此工作流无法运行，因为沙盒解决方案出错](#bkmk_error04)
    
  
-  [此工作流无法运行，因为沙盒失败：无法从进程池获取进程](#bkmk_error05)
    
  
-  [此工作流无法运行，因为沙盒失败：沙盒代码工作进程突然退出](#bkmk_error06)
    
  
-  [无法发送电子邮件。请确保正确配置了服务器的传出电子邮件设置](#bkmk_error07)
    
  
-  [工作流无法更新此项目，可能是因为此项目的一个或多个列需要其他类型的信息](#bkmk_error08)
    
  
-  [工作流操作失败，因为工作流查找找不到匹配项](#bkmk_error09)
    
  
-  [工作流无法创建列表项，因为文件名缺失或无效](#bkmk_error10)
    
  
-  [强制失败：无法将输入查阅数据转换为请求的类型](#bkmk_error11)
    
  
-  [工作流操作失败，因为该操作需要签出文档](#bkmk_error12)
    
  
-  [编译工作流时发现错误。工作流文件已被保存，但不能运行。与工作流关联的服务器发生意外错误](#bkmk_error13)
    
  

### 等待沙盒代码执行请求在工作进程中完成时出现超时
<a name="bkmk_error01"> </a>

与以下项目相同的问题和解决方案，"等待请求在沙盒 appdomain 中完成时超时"。
  
    
    

### 在等待沙盒应用域完成请求时超时
<a name="bkmk_error02"> </a>

所有这些错误源于相同的问题，即超出工作流执行操作的默认时间。默认的超时期限为 30 秒。
  
    
    
您可以在本地安装中更改超时值，但您不能在 SharePoint Online 安装设置中更改这一项。为避免在 SharePoint Online 安装中出现这一错误，您必须修改代码以限制工作进程或 appdomain 中的操作时间，使其少于 30 秒。
  
    
    
若要修改本地安装的超时期限，请执行以下 Windows PowerShell 命令。请注意，示例代码将超时期限重置为 60 秒，但是您可以使用另一个值。
  
    
    



```

Add-pssnapin microsoft.sharepoint.powershell
   $userCodeSvc = [Microsoft.SharePoint.Administration.SPUserCodeService]::Local
   #change to 60 second timeout
   $userCodeSvc.WorkerProcessExecutionTimeout = 60 
   $userCodeSvc.Update()
```


### 处理此请求的工作进程已终止，因为它超出资源 {0}
<a name="bkmk_error03"> </a>

在错误字符串中， `{0}` 的值是已超出其阈值的特定资源的占位符。为解决这一问题，您应当修改代码，使其不会超过资源阈值。这些资源值存储在文档 [SharePoint 2010 中沙盒解决方案的资源使用率限制](http://msdn.microsoft.com/zh-cn/library/gg615462%28v=office.14%29.aspx)中。
  
    
    

### 此工作流无法运行，因为沙盒解决方案出错
<a name="bkmk_error04"> </a>

工作流代码丢弃了一个未处理的异常情况。解决此错误需要您调试和修改您的沙盒代码。
  
    
    

### 此工作流无法运行，因为沙盒失败：无法从进程池获取进程
<a name="bkmk_error05"> </a>

您的沙盒配置中存在错误。有关配置沙盒解决方案的信息，请参阅 [沙盒解决方案](http://msdn.microsoft.com/zh-cn/library/ee536577%28v=office.14%29.aspx)。
  
    
    

### 此工作流无法运行，因为沙盒失败：沙盒代码工作进程突然退出
<a name="bkmk_error06"> </a>

您的沙盒配置中存在错误。有关配置沙盒解决方案的信息，请参阅 [沙盒解决方案](http://msdn.microsoft.com/zh-cn/library/ee536577%28v=office.14%29.aspx)。
  
    
    

### 无法发送电子邮件。请确保正确配置了服务器的传出电子邮件设置
<a name="bkmk_error07"> </a>

在解决电子邮件问题的故障时，有两个问题需要注意。无论是本地安装还是 SharePoint Online 安装，请确保在"To:"和"Cc:"行上的所有地址都是有效的电子邮件地址。在本地安装中，请确保服务器上的邮件设置已正确配置。
  
    
    
请查看下列内容，确保您已正确配置传入和传出的邮件。
  
    
    

-  [Microsoft SharePoint 2013 部署指南](http://download.microsoft.com/download/1/F/6/1F6D3BE4-1174-4320-A1D1-C0E2681CCCF3/Deployment-guide-for-SharePoint-2013.pdf)
    
  
-  [如何在 SharePoint 服务器上配置传入和传出邮件](http://blogs.msdn.com/b/pareshg/archive/2010/04/23/how-to-configure-incoming-and-outgoing-emails-in-sharepoint-server-2010.aspx)
    
  

### 工作流无法更新此项目，可能是因为此项目的一个或多个列需要其他类型的信息
<a name="bkmk_error08"> </a>

该错误通常源于以下两种情形中的一种：
  
    
    

- 删除或更改了一个列表字段，但是工作流未能更新以对此更改做出解释，因此它仍旧尝试为旧的字段设置值。您应当检查工作流中所有的"更新列表项"操作，确保其为字段设置恰当的值，并且那些字段确实存在于列表上。
    
  
- 当工作流正试图使用错误的数据类型来设置列表项中的字段值时，遇到一个数据类型错误。您应当确认他们查找中的"返回域为" 操作为正确的数据类型。
    
  

### 工作流操作失败，因为工作流查找找不到匹配项
<a name="bkmk_error09"> </a>

这意味着工作流逻辑中存在一个错误。请检查以确保您在查找中选择了正确的列表和字段。
  
    
    

### 工作流无法创建列表项，因为文件名缺失或无效
<a name="bkmk_error10"> </a>

这意味着工作流逻辑中存在一个错误。请确保"路径和名称"字段中输入的文件名是有效的。文件名称无效的常见原因包括丢失文件扩展名或文件扩展名错误，或者文件/路径字符串太长，以至于超出字符数的允许范围。
  
    
    

### 强制失败：无法将输入查阅数据转换为请求的类型
<a name="bkmk_error11"> </a>

操作未能在不兼容的数据类型间强制转换值（例如，将一个随机字符串转换为一个日期/时间值）。您应当检查查阅中的"返回域为"设置，以确保其是预期数据的有效数据类型。
  
    
    

### 工作流操作失败，因为该操作需要签出文档
<a name="bkmk_error12"> </a>

您必须在使用"更新项目"操作之前，先使用"签出项目"操作签出该条目。
  
    
    

### 编译工作流时发现错误。工作流文件已被保存，但不能运行。与工作流关联的服务器发生意外错误
<a name="bkmk_error13"> </a>

有关详细信息，请参阅  [Microsoft 支持知识库文章 ID 2557533](http://support.microsoft.com/kb/2557533) ( `http://support.microsoft.com/kb/2557533`)。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 工作流开发最佳实践](sharepoint-workflow-development-best-practices.md)
    
  
-  [使用 Visual Studio 开发 SharePoint 2013 工作流](develop-sharepoint-2013-workflows-using-visual-studio.md)
    
  

  
    
    

