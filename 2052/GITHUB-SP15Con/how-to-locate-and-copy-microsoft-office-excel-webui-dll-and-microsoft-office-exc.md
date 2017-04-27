---
title: 如何：查找和复制 Microsoft.Office.Excel.WebUI.dll 与 Microsoft.Office.Excel.WebUI.Internal.dll
keywords: how to,howdoi,howto,WebUI DLL
f1_keywords:
- how to,howdoi,howto,WebUI DLL
ms.prod: SHAREPOINT
ms.assetid: 09ad5d5e-1678-45e4-8159-23ef56f84215
---


# 如何：查找和复制 Microsoft.Office.Excel.WebUI.dll 与 Microsoft.Office.Excel.WebUI.Internal.dll

如果您希望以编程方式将 Excel Web Access Web 部件添加到 SharePoint 页面，并以编程方式更改 Excel Web Access Web 部件，您必须添加对所需 SharePoint DLL 的引用。例如： 
  
    
    


- Microsoft.Office.Excel.WebUI.dll
    
  
- Microsoft.Office.Excel.WebUI.Internal.dll
    
  
- Microsoft.SharePoint.dll
    
  

在运行 Microsoft SharePoint Server 2010 的计算机上，您可以在全局程序集缓存中找到 Microsoft.Office.Excel.WebUI.dll 和 Microsoft.Office.Excel.WebUI.Internal.dll 的副本。在 Microsoft Visual Studio 中，要使用"添加引用"对话框添加对 Microsoft.Office.Excel.WebUI.dll 的引用，您必须先将 Microsoft.Office.Excel.WebUI.dll 和 Microsoft.Office.Excel.WebUI.Internal.dll 从全局程序集缓存复制到一个文件夹中。然后您可以使用"添加引用"对话框中的"浏览"选项卡，浏览到包含 Microsoft.Office.Excel.WebUI.dll 和 Microsoft.Office.Excel.WebUI.Internal.dll 的副本的文件夹。
  
    
    

以下步骤演示如何： 
- 查找 Microsoft.Office.Excel.WebUI.dll。 
    
  
- 将 Microsoft.Office.Excel.WebUI.dll 从全局程序集缓存复制到您选择的文件夹中。
    
  

> **注释**
> 重复将 Microsoft.Office.Excel.WebUI.Internal.dll 从全局程序集缓存复制到一个文件夹中的步骤。 
  
    
    


### 查找 Microsoft.Office.Excel.WebUI.dll


1. 要启动命令提示符控制台，请单击"开始"，然后单击"运行"。 
    
  
2. 在"打开"字段的文本框中，键入 cmd。 
    
    将显示命令提示符控制台。
    
  
3. 使用 **cd** 命令导航到"C:\\Windows\\assembly"目录：
    
    > **注释**
      > 您的计算机上的目录结构可能略有不同。此示例以已安装 Windows Server 2008 的计算机为例。 

  ```
  
cd C:\\Windows\\assembly
  ```

4. 使用 **dir** 命令显示"C:\\Windows\\assembly"目录的内容：
    
  ```
  C:\\Windows\\assembly>dir
  ```


    您将看到如下内容：
    


  ```
  Volume in drive C has no label.
 
 Directory of C:\\Windows\\assembly

02/20/2010  09:22 AM    <DIR>          GAC
02/20/2010  09:39 AM    <DIR>          GAC_32
02/20/2010  09:32 AM    <DIR>          GAC_64
02/22/2010  05:05 PM    <DIR>          GAC_MSIL
02/22/2010  05:35 PM    <DIR>          NativeImages_v2.0.50727_32
02/22/2010  04:33 PM    <DIR>          NativeImages_v2.0.50727_64
02/20/2010  10:34 AM    <DIR>          NativeImages_v4.0.30219_32
02/20/2010  10:35 AM    <DIR>          NativeImages_v4.0.30219_64
02/22/2010  05:04 PM    <DIR>          temp
02/22/2010  05:05 PM    <DIR>          tmp
               0 File(s)              0 bytes
              10 Dir(s)  104,032,665,600 bytes free
  ```

5. 再次使用 **cd** 命令更改目录并导航到 gac_msil 目录：
    
  ```
  
C:\\Windows\\assembly>cd gac_msil
  ```

6. 使用 **dir** 命令显示"C:\\Windows\\assembly\\GAC_MSIL"目录的内容：
    
  ```
  C:\\Windows\\assembly\\GAC_MSIL>dir
  ```


    您将看到如下内容：
    


  ```
  Volume in drive C has no label.
Directory of C:\\Windows\\assembly\\GAC_MSIL
...
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.Server.Udf
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.Server.WebServices

02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.WebUI
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.WebUI.Internal
...
02/20/2010  07:57 AM    <DIR>          Microsoft.SharePoint
...
0 File(s)              0 bytes
             739 Dir(s)  100,594,409,472 bytes free
  ```

7. 现在，您已找到 Microsoft.Office.Excel.WebUI.dll 和 Microsoft.Office.Excel.WebUI.Internal.dll，您可以将它们复制到您选择的文件夹中了。
    
  

### 复制 Microsoft.Office.Excel.WebUI.dll


1. 再次使用 **cd** 命令将目录更改为"Microsoft.Office.Excel.WebUI"：
    
  ```
  
C:\\Windows\\assembly\\GAC_MSIL>cd Microsoft.Office.Excel.WebUI 
  ```

2. 使用 **dir** 命令显示内容：
    
  ```
  C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI>dir
  ```


    您将看到如下内容：
    


  ```
  Volume in drive C has no label.
Directory of C:\\Windows\\assembly\\GAC_MSIL\Microsoft.Office.Excel.WebUI

02/20/2010  07:57 AM    <DIR>          .
02/20/2010  07:57 AM    <DIR>          ..
02/20/2010  07:57 AM    <DIR>          14.0.0.0__71e9bce111e9429c
               0 File(s)              0 bytes
               3 Dir(s)  104,006,115,328 bytes free
  ```

3. 再次使用 **cd** 命令更改目录：
    
  ```
  
C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI>cd 14.0.0.0__71e9bce111e9429c
  ```

4. 使用 **copy** 命令将 Microsoft.Office.Excel.WebUI.dll 复制到您选择的文件夹中。
    
    在下面的示例中，Microsoft.Office.Excel.WebUI.dll 被复制到"C:\\WebUIAssembly"中，其中"C:\\WebUIAssembly"是您之前创建的文件夹：
    


  ```
  C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI\\14.0.0.0__71e9bce111e9429c>copy Microsoft.Office.Excel.WebUI.dll c:\\WebUIAssembly
        1 file(s) copied.
  ```


## 示例

下面举例说明使用命令提示符查找 Microsoft.Office.Excel.WebUI.dll 并复制到文件夹中的结果。
  
    
    

```

C:\\Windows\\assembly>dir
Volume in drive C has no label.
Directory of C:\\Windows\\assembly

02/20/2010  09:22 AM    <DIR>          GAC
02/20/2010  09:39 AM    <DIR>          GAC_32
02/20/2010  09:32 AM    <DIR>          GAC_64
02/22/2010  05:05 PM    <DIR>          GAC_MSIL
02/22/2010  05:35 PM    <DIR>          NativeImages_v2.0.50727_32
02/22/2010  04:33 PM    <DIR>          NativeImages_v2.0.50727_64
02/20/2010  10:34 AM    <DIR>          NativeImages_v4.0.30219_32
02/20/2010  10:35 AM    <DIR>          NativeImages_v4.0.30219_64
02/22/2010  05:04 PM    <DIR>          temp
02/22/2010  05:05 PM    <DIR>          tmp
               0 File(s)              0 bytes
              10 Dir(s)  104,032,665,600 bytes free
C:\\Windows\\assembly>cd gac_msil

C:\\Windows\\assembly\\GAC_MSIL>dir
 Volume in drive C has no label.
 Directory of C:\\Windows\\assembly\GAC_MSIL
...
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.Server.Udf
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.Server.WebServices

02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.WebUI
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.WebUI.Internal
...

C:\\Windows\\assembly\\GAC_MSIL>cd Microsoft.Office.Excel.WebUI

C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI>dir
 Volume in drive C has no label.
Directory of C:\\Windows\\assembly\\GAC_MSIL\Microsoft.Office.Excel.WebUI

02/20/2010  07:57 AM    <DIR>          .
02/20/2010  07:57 AM    <DIR>          ..
02/20/2010  07:57 AM    <DIR>          14.0.0.0__71e9bce111e9429c
               0 File(s)              0 bytes
               3 Dir(s)  104,006,115,328 bytes free

C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI>cd 14.0.0.0__71e9bce111e9429c

C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI\\14.0.0.0__71e9bce111e9429c>copy Microsoft.Office.Excel.WebUI.dll c:\\WebUIAssembly
        1 file(s) copied.

C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI\\14.0.0.0__71e9bce111e9429c>
```


## 另请参阅


#### 任务


  
    
    
 [如何：以编程方式将 Excel Web Access Web 部件添加到页面](how-to-programmatically-add-an-excel-web-access-web-part-to-a-page.md)
  
    
    
 [如何：信任位置](how-to-trust-a-location.md)
#### 概念


  
    
    
 [Excel Services 警告](excel-services-alerts.md)
  
    
    
 [Excel Services 已知问题和提示](excel-services-known-issues-and-tips.md)
