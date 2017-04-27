---
title: 如何：在 SharePoint 2013 中使用 VSS 备份和还原搜索服务应用程序
ms.prod: SHAREPOINT
ms.assetid: 87ee28e6-8170-4dba-8c9d-f04ab9e632dc
---


# 如何：在 SharePoint 2013 中使用 VSS 备份和还原搜索服务应用程序
 **摘要：** 了解如何使用卷影复制服务 (VSS) 备份和还原 SharePoint 2013 中的搜索服务应用程序。
## 使用卷影复制服务备份和还原 SharePoint 的先决条件

若要为 SharePoint 2013 的备份和还原解决方案进行编程，您需要了解 VSS 的工作原理以及含有 VSS 的 SharePoint 界面。
  
    
    

**表 1. 使用卷影复制服务备份和还原 SharePoint 的核心概念**


|**文章**|**说明**|
|:-----|:-----|
| [卷影复制服务](http://msdn.microsoft.com/zh-cn/library/windows/desktop/bb968832%28v=vs.85%29.aspx)及其子文章。  <br/> |了解 VSS 以及如何为其编程。  <br/> |
| [Windows SharePoint Services 和卷影复制服务](http://msdn.microsoft.com/library/adae101a-078e-40b9-9cfa-db2cfb10270a%28Office.15%29.aspx)及其子文章。  <br/> |使用 VSS 和含有 VSS 的 SharePoint 界面来备份和还原 SharePoint 2013 数据的信息概述以及分步操作程序。  <br/> |
   

## 使用卷影复制服务来备份和还原搜索服务应用程序
<a name="Use"> </a>

以下程序旨在帮助开发人员创建一个使用 VSS 的备份/还原应用程序。如果您是一个正在寻找有关如何备份或还原 SharePoint 2013 搜索服务应用程序的说明的 IT 专业人士，请参阅 [备份和还原 SharePoint 2013](http://technet.microsoft.com/zh-cn/library/ee662536.aspx)。 
  
    
    
 **先决条件：**下载 [适用于 Windows 7 的 Microsoft Windows SDK 和 .NET Framework 4](http://www.microsoft.com/en-us/download/details.aspx?id=8279)，并将其安装到装有搜索服务应用程序 (SSA) 的服务器，以及所有装有搜索索引组件的服务器上。此外，这样做会将 vshadow.exe 和 betest.exe 安装到  `C:\\Program Files\\Microsoft SDKs\\Windows\\v7.1\\Bin\\x64\\vsstools`。
  
    
    

> **提示**
> 有关本文中提到的 Windows PowerShell cmdlet 的详细信息，请参阅 [用于 SharePoint 2013 的 Windows PowerShell 参考](http://technet.microsoft.com/zh-cn/library/ee890108.aspx)。 
  
    
    


### 若要注册 SharePoint VSS 编写器并为备份和还原准备好服务器


- 使用以下任意一种方法注册 SharePoint VSS 编写器：
    
  - 打开"管理工具"中的"服务"，并启动"SharePoint VSS 编写器"服务。
    
  
  - 打开命令控制台，并执行  `stsadm.exe -o registerwsswriter`。在 %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\BIN 中可以找到 stsadm 实用程序。验证服务是否正在"管理工具"的"服务"中运行。
    
  

### 使用 VSS 备份 SharePoint 搜索服务应用程序


1. 在每台含有索引组件的服务器和每台运行 SQL Server（搜索数据库所在的位置）的计算机上的命令行中执行  `vshadow.exe -wm > writers.txt`，以获取 VSS 元数据。创建的 writers.txt 文件中列出了所有与服务器相关联的 VSS 编写器。在接下来的步骤中使用此文件生成用于搜索服务应用程序 (SSA) 和搜索索引的清单文件。
    
  
2. 按照这些步骤在运行 SQL Server（搜索数据库所在的位置）的计算机上创建一个用于 SSA 的清单。
    
1. 创建一个 XML 文件，并将以下内容复制到文件中： 
    
  ```XML
  
<BETest>
  <Writer writerid="SharePoint Services Writer ID">
    <Component logicalPath="PathSSA" componentName="SearchAppOffice" />
    <Component logicalPath="PathC" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="PathA" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="PathL" componentName="SearchAppOffice_LinksStore" />
  </Writer>
  <Writer writerid="SQL Server Writer ID">
    <Component logicalPath="PathDbSSA" componentName="SearchAppOffice" />
    <Component logicalPath="PathDbC" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="PathDbA" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="PathDbL" componentName="SearchAppOffice_LinksStore" />
  </Writer>
</BETest>

  ```

2. 使用在第一步中生成的 writer.txt 文件中的相应值替换此文件中的 10 个占位符。请使用下表作为指导。 
    
    > **注释**
      > 在右栏中， _SSA_ 本身是一个占位符，表示搜索服务应用程序的名称。

   **表 2. SSA 清单文件占位符和来自 writers.txt 的值**


|**占位符**|**信息在 writers.txt. 中的位置。**|
|:-----|:-----|
| _SharePoint Services 编写器 ID_ <br/> |"SharePoint Services 编写器"条目下列出的 WriterId GUID  <br/> |
| _PathSSA_ <br/> |使用"SharePoint Services 编写器"条目中搜索服务应用程序的名称列出的逻辑路径条目  <br/> |
| _PathC_ <br/> |为"SharePoint Services 编写器"条目中名为" _SSA__CrawlStore"的组件列出的逻辑路径条目  <br/> |
| _PathA_ <br/> |为"SharePoint Services 编写器"条目中名为" _SSA__AnalyticsReportingStore"的组件列出的逻辑路径条目  <br/> |
| _PathL_ <br/> |为"SharePoint Services 编写器"条目中名为" _SSA__LinksStore"的组件列出的逻辑路径条目  <br/> |
| _SQL Server Writer ID_ <br/> |列于"SqlServerWriter"条目下方的 WriterId GUID  <br/> |
| _PathDbSSA_ <br/> |为"SqlServerWriter"条目中含有"搜索服务应用程序"名称的组件列出逻辑路径条目  <br/> |
| _PathDbC_ <br/> |为"SqlServerWriter"条目中名为" _SSA__CrawlStore"的组件列出的逻辑路径条目  <br/> |
| _PathDbA_ <br/> |为"SqlServerWriter"条目中名为" _SSA__AnalyticsReportingStore"的组件列出的逻辑路径条目  <br/> |
| _PathDbL_ <br/> |为"SqlServerWriter"条目中名为" _SSA__LinksStore"的组件列出的逻辑路径条目  <br/> |
   

    这是 SSA 清单文件。有关完整 SSA 清单文件的示例，请参阅 [示例清单文件](#Examples)。
    
  
3. 按照这些步骤为搜索索引文件创建一个清单。在每台含有索引组件的服务器上重复这些步骤。
    
1. 创建一个 XML 文件，并将以下内容复制到文件中：
    
  ```XML
  
<BETest>
   <Writer writerid="SharePoint Services Writer ID">
      <Component logicalPath="PathIndex" componentName="NameIndex" />
   </Writer>
   <Writer writerid="OSearch15 Writer ID">
      <Component logicalPath="PathOSearch15" componentName="IndexComponentGroup" />
   </Writer>    
</BETest>
  ```

2. 使用在第一步中生成的 writer.txt 文件中的相应值替换此文件中的 6 个占位符。请使用下表作为指导。
    
   **表 3. 搜索索引清单文件占位符和来自 writer.txt 的值**


|**占位符**|**信息在 writers.txt. 中的位置。**|
|:-----|:-----|
| _SharePoint Services 编写器 ID_ <br/> |"SharePoint Services 编写器"条目下列出的 WriterId GUID  <br/> |
| _PathIndex_ <br/> |为"SharePoint Services 编写器"条目中以"IndexComponentGroup"开始命名的组件列出的逻辑路径条目  <br/> |
| _NameIndex_ <br/> |为"SharePoint Services 编写器"条目中以"IndexComponentGroup"开始命名的组件列出的名称条目  <br/> |
| _OSearch15 Writer ID_ <br/> |"OSearch15 VSS 编写器"条目下方列出的 WriterId GUID  <br/> |
| _PathOSearch15_ <br/> |为"OSearch15 VSS 编写器"条目中以"IndexComponentGroup"开始命名的组件列出的逻辑路径条目。它通常为空。  <br/> |
| _IndexComponentGroup_ <br/> |为"OSearch15 VSS 编写器"条目中以"IndexComponentGroup"开始命名的组件列出的名称条目  <br/> |
   

    这是搜索索引清单文件。有关完整搜索索引清单文件的示例，请参阅 [示例清单文件](#Examples)。
    
  
4. （可选）记录每台含有索引组件的服务器上的"IndexComponent"文件夹大小。之后，您可以使用此信息来验证备份。
    
  
5. 在场中的任一服务器上，打开 SharePoint Management Shell 并执行以下命令行，其中， _name of search service application_ 是您要备份的 SSA。之后，保持 SharePoint Management Shell 窗口为打开状态。
    
  ```
  
$ssa = Get-SpenterpriseSearchServiceApplication -Identity "name of search service application"
Suspend-SPEnterpriseSearchServiceApplication -Identity $ssa
  ```

6. 按照以下步骤执行 SSA 数据库的备份和索引：
    
1. 在装有 SSA 数据库的服务器上，在命令行中执行以下命令，其中， _destination backup folder_ 是备份文件的文件夹的完整路径， _backup log file_ 是备份日志文件的完整路径和名称， _SSA manifest file_ 是 SSA 清单文件的路径和文件名称。
    
  ```
  
betest.exe /v /b /d "destination backup folder" /s "backup log file" /x "SSA manifest file"
  ```

2. 在带有打开的 SharePoint Management Shell 窗口的服务器上，执行以下命令行，其中， _topology file name_ 是包含拓扑信息的导出文件的完整路径和名称。您将在 SSA 的还原过程中使用此文件。
    
  ```
  Export-SPEnterpriseSearchTopology -SearchApplication $ssa -Filename "topology file name"
  ```

3. 验证文件是否已创建。
    
  
4. 在每台含有索引组件的服务器上，执行以下命令行，其中， _destination backup folder_ 是备份文件的文件夹的完整路径， _backup log file_ 是备份日志文件的完整路径和名称， _index manifest file_ 是索引清单的路径和文件名称。
    
  ```
  betest.exe /v /b /d "destination backup folder" /s "backup log file" /x "index manifest file"
  ```

5. （可选）检查已备份的索引文件夹。验证文件夹的名称和大小是否与之前步骤中所记录的相匹配。
    
  

### 使用 VSS 还原 SharePoint 搜索服务应用程序


1. 在场中的任意服务器上，打开 SharePoint Management Shell 并执行以下命令行，以删除现有的搜索服务应用程序及其代理，其中， _name of search service application_ 是您要还原的 SSA， _name of proxy_ 是其应用程序代理。请注意， _name of SSA proxy_ 通常与结尾处添加了"Proxy"一词的 SSA 的名称相同。 `RemoveData` 开关确保搜索数据库已删除。
    
  ```
  $ssa = Get-SPEnterpriseSearchServiceApplication -Identity "name of search service application"
Remove-SPEnterpriseSearchServiceApplication -Identity $ssa -RemoveData
Remove-SPEnterpriseSearchServiceApplicationProxy -Identity "name of SSA proxy"
  ```

2. 在同一服务器上，在命令行中执行以下命令，以还原 SSA 数据库，其中， _destination backup folder_ 是备份文件的文件夹的完整路径， _backup log file_ 是备份日志文件的完整路径和名称， _SSA manifest file_ 是 SSA 清单文件的路径和文件名称。
    
  ```
  
betest.exe /v /r /d "destination backup folder" /s "backup log file" /x SSA_manifest_file
  ```

3. 在同一服务器上，打开一个 SharePoint Management Shell，并执行以下命令行来还原 SSA，其中， _application pool name_ 是新池的名称， _domain\\user_ 是应用程序池登录所用的用户的域名， _name of the search service application_ 是 SSA 的名称， _topology_file_name_ 是备份 SSA 时您所创建的类型文件的路径和名称。
    
    > **提示**
      > 此代码可创建一个新的应用程序池标识，以运行还原的 SSA，但您也可以使用将现有帐户与 **Get-SPServiceApplicationPool** cmdlet 结合使用。

  ```
  $applicationPool = New-SPServiceApplicationPool -name "application pool name" -account "domain\\user"
Restore-SPEnterpriseSearchServiceApplication -Name "name of the search service application" -ApplicationPool $applicationPool -TopologyFile "topology_file_name" -KeepId
  ```

4. 使用以下 cmdlet 创建一个 SSA 代理。我们建议您对  _name of the search service application_ 和 _name of SSA proxy_ 使用与步骤 1 相同的值。
    
  ```
  
$ssa = Get-SpenterpriseSearchServiceApplication -Identity "name of search service application"
New-SPEnterpriseSearchServiceApplicationProxy -Name "name of SSA proxy" -SearchApplication $ssa
  ```

5. （可选）通过打开"管理中心"来验证现有 SSA 及其代理是否存在。选择"管理服务应用程序，并验证列出的 SSA 及其代理是否列出。
    
  
6. （可选）单击服务列表上的 SSA，然后，在打开的页面上验证"搜索应用程序拓扑"表格是否与您在备份过程中导出的类型匹配。（您也可以使用 cmdlet **Get-SPEnterpriseSearchStatus** 来验证拓扑。）
    
  
7. **在所有含有索引组件的服务器上** 使用以下程序还原索引文件。
    
1. 在"管理工具">"服务"中停止主机控制器服务，或在 SharePoint Management Shell 中执行以下 cmdlet：
    
  ```
  
stop-service SPSearchHostController
  ```

2. 在相同的服务器上，执行以下命令行，其中， _index manifest file_ 是您在备份过程中创建的索引清单的路径和文件名称。
    
  ```
  betest.exe /v /r /d "destination backup folder" /s "backup log file" /x "index manifest file"
  ```

3. （可选）验证文件夹的名称和大小是否与您在备份过程中所记录的相匹配。
    
  
4. 对于每个索引组件，按照以下步骤对数据文件夹下的数据重命名：
    
1. 在 SharePoint Management Shell 中，执行以下 cmdlet。
    
  ```
  Get-SPEnterpriseSearchVssDataPath
  ```

2. 从 cmdlet 的输出中，记录每个 GUID 的最后一部分。例如，如果一个输出行是  `IndexComponentGroup_e255918b-6ab0-4d7c-8049-720b2744c62f`，则记录 720b2744c62f。
    
  
3. 在"文件资源管理器"中（或在 Windows Server 2008 的"Windows 资源管理器"中），导航到  `C:\\Program Files\\Microsoft Office Servers\\15.0\\Data\\Office Server\\Applications\\Search\\Nodes\\24488A\\IndexComponentN\\storage\\data`，其中， *N*  是索引组件号。
    
  
4. 其中的每个文件夹都有一个以"SP"开头且后面跟有 12 个十六进制数字以及版本号的子文件夹。如果子文件夹 12 个十六进制数字与您在之前步骤中记录的 GUID 结尾部分匹配的，则将子文件夹重命名到 importindex 中。在接下来的示例中，您可以将子文件夹 `SP720b2744c62f.1.I.1.0` 重命名到importindex 中。
    
  
5. 在"管理工具">"服务"中重启主机控制器服务，或在 SharePoint Management Shell 中执行以下 cmdlet：
    
  ```
  start-service SPSearchHostController
  ```

6. 验证索引数据文件夹名称是否已还原为之前的名称。（在接下来的示例中，它应当是"SP720b2744c62f.1.I.1.0"。）
    
  
8. （可选）验证"IndexComponent"文件夹大小是否与您在备份过程中所记录的大小相匹配。
    
  
9. 重启 SSA。
    
  
10. 在所有受影响的服务器上，在 SharePoint Management Shell 中运行以下 cmdlet，以验证搜索应用程序服务是否在正常运行：
    
  ```
  Get-SPEnterpriseSearchStatus
  ```

11. 验证新文档的提供和搜索是否正常。例如，使用查询"size>=0"来检查索引大小。还可以添加新文档并验证它是否可以搜索到。
    
  

## 示例清单文件
<a name="Examples"> </a>

 **SSA 清单文件**
  
    
    

```XML
<BETest>
  <Writer writerid="da452614-4858-5e53-a512-38aab25c61ad">
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\2e1f9435-d714-4bcb-be8d-ae1214e2ea22" componentName="SearchAppOffice" />
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\b8bb09b8-a823-43b0-a131-7bd5464f91fb" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\20c0c0b5-2086-4b16-8ce8-2cecb5186ebe" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\15004c47-21ca-441e-80fe-9e068ef4ad14" componentName="SearchAppOffice_LinksStore" />
  </Writer>
  <Writer writerid="a65faa63-5ea8-4ebc-9dbd-a0c4db26912a">
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice" />
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice_LinksStore" />
  </Writer>
</BETest>

```

 **索引清单文件**
  
    
    



```XML

<BETest>
  <Writer writerid="da452614-4858-5e53-a512-38aab25c61ad">
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\cfbddb07-2409-4b3d-997b-ee1b936c3dbd" componentName="IndexComponentGroup_3bca1050-c15a-4987-93dc-8f911d35a0ba" />
  </Writer>
  <Writer writerid="0ff1ce15-0201-0000-0000-000000000000">
    <Component logicalPath="" componentName="IndexComponentGroup_3bca1050-c15a-4987-93dc-8f911d35a0ba" />
  </Writer>
</BETest>
```


## 其他资源
<a name="bk_addresources"> </a>


-  [Windows SharePoint Services 和卷影复制服务](http://msdn.microsoft.com/library/adae101a-078e-40b9-9cfa-db2cfb10270a%28Office.15%29.aspx)
    
  

