---
title: 如何：使用 VSS 请求程序备份和还原 SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: cab5ba90-bd23-4cec-82d7-529e3f86ba88
---


# 如何：使用 VSS 请求程序备份和还原 SharePoint 2013
 **摘要：** 了解如何使用卷影复制服务 (VSS) 请求程序为 Microsoft SharePoint 2013进行备份和还原。
## 使用请求程序备份和还原

使用您的 VSS 请求程序，通过以下步骤备份和还原 Microsoft SharePoint Foundation。
  
    
    

### 使用请求程序备份和还原数据


1. 手动启动 SharePoint Foundation VSS 编写器服务。打开"管理工具"，导航到"服务"并将其打开，然后启用名为"卷影副本"和"SharePoint 2010 VSS 编写器"的服务。
    
  
2. 从系统控制台运行  `STSADM -o registerwsswriter` 命令，在 Windows 注册表中注册编写器。可执行文件位于 %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\BIN 目录中。
    
  
3. 在所有 SharePoint Foundation 服务器上重复步骤 1 和步骤 2。
    
  
4. 使用请求程序备份和还原数据。您可以使用请求程序（如 [卷影复制服务概述](http://msdn.microsoft.com/zh-cn/library/aa384649%28VS.85%29.aspx)所述）或 BETest 测试实用程序（在  [VSS SDK](http://www.microsoft.com/downloads/details.aspx?FamilyID=0B4F56E4-0CCC-4626-826A-ED2C4C95C871&amp;displaylang=en) 中提供）来备份或还原 SharePoint Foundation。
    
  

## 运行 VSS 的安全性

对于在所有目标服务器实例上运行编写器的备份和还原帐户，VSS 有一些特殊要求。
  
    
    

- 运行的帐户必须有权调用 VSS。默认情况下，VSS 需要 VSS 编写器成为目标服务器实例上管理员或 Backup Operators 组的成员。您可以将一个注册表项配置为允许其他帐户访问 VSS。
    
  
- 帐户必须有权对数据库服务器发出 **BACKUP DATABASE** 和 **RESTORE DATABASE** 命令。
    
  
- 帐户必须有权对 SQL 服务器打开 VDI，这需要客户端成为 SQL Server sysadmin 组的成员。
    
  
- 帐户必须能够针对 SQL 服务器上主数据库中的 sys.master_files 目录视图执行查询。
    
  
此外，为了被 SharePoint Foundation 计时器服务 (owstimer.exe) 承载，编写器服务必须在管理应用程序池帐户下运行，即 SharePoint Foundation 基本安装中的"网络服务"帐户。 
  
    
    
 **注意** 此帐户不可能是一个本地机器管理员帐户，这与 VSS 的要求不同，后者的处理帐户必须作为本地系统运行。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 和卷影复制服务概述](overview-of-sharepoint-2013-and-the-volume-shadow-copy-service.md)
    
  

