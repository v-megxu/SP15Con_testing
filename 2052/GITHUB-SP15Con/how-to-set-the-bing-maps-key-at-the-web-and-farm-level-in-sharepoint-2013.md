---
title: 如何：在 SharePoint 2013 中设置 Web 和服务器场级别的必应 Bing 地图密钥
ms.prod: SHAREPOINT
ms.assetid: 507ed9de-c349-44b5-b182-e838795dd862
---


# 如何：在 SharePoint 2013 中设置 Web 和服务器场级别的必应 Bing 地图密钥

  
    
    
![操作方法主题](images/mod_icon_howto.png)
  
    
    

  
    
    

  
    
    
了解如何在 Web 和场级别通过使用 SharePoint 2013 客户端对象模型和 Windows PowerShell 以编程方式设置 Bing 地图密钥，以便在 SharePoint 列表和基于位置的 Web 和移动应用中启用 Bing 地图功能。

  
    
    


## 设置 Bing 地图密钥的先决条件
<a name="SP15Bing_prereq"> </a>

若要遵循此示例中的这些步骤，您应具备以下组件：
  
    
    

- SharePoint 2013，具有管理权限。
    
  
- 有效 Bing 地图密钥，其中您可从  [Bing 地图帐户中心](https://www.bingmapsportal.com/) 中获取。
    
    > **重要信息**
      > 请注意您负责遵守适用于 Bing 地图密钥使用的条款以及向您的应用程序的用户对有关传递到 Bing 地图服务的数据进行任何必要公开。 

## 代码示例：设置场或 Web 级别的 Bing 地图密钥
<a name="SP15Setbing_farm"> </a>

可以设置场或 Web 级别的 Bing 地图密钥。若要设置场级别的 Bing 地图密钥，您需要对该服务器具备管理员权限；然后，您可以通过使用 SharePoint 2013 命令行管理程序添加密钥。若要设置 Web 级别的 Bing 地图密钥，则编写使用 SharePoint 客户端对象模型的控制台应用程序。
  
    
    

> **提示**
> 与在场级别设置的 Bing 地图密钥相比，在 Web 级别设置的此密钥具有更高的优先级顺序。 
  
    
    


### 使用 Windows PowerShell 设置场级别的 Bing 地图密钥


1. 以管理员身份登录到 SharePoint 服务器，然后打开 SharePoint 2013 命令行管理程序。
    
  
2. 请执行以下命令： 
    
     `Set-SPBingMapsKey -BingKey "<Enter a valid Bing Maps key>"`
    
    立即在 SharePoint Server 2013 中设置场级别的 Bing 地图密钥。 
    
    > **注释**
      > 在使用 Windows PowerShell 时，仅在场级别设置 Bing 地图密钥。如果想要在 Web 级别设置 Bing 地图密钥，则可以以编程的方式设置该密钥，如下一小节所示。 

### 使用客户端对象模型设置场或 Web 级别的 Bing 地图密钥


1. 启动 Visual Studio。
    
  
2. 在菜单栏上，选择"文件"、"新建项目"。将打开"新建项目" 对话框。
    
  
3. 在"新建项目"对话框中，选择"C#"（"已安装模板" 框，然后选择"控制台应用程序"模板。
    
  
4. 向该项目提供一个名称，然后选择"确定"按钮。
    
  
5. Visual Studio 创建此项目。向以下程序集添加引用，并选择"确定"。
    
  - Microsoft.SharePoint.Client.dll
    
  
  - Microsoft.SharePoint.Client.Runtime.dll
    
  
6. 在默认 .cs 文件中，添加以下 **using** 指令。
    
     `using Microsoft.SharePoint.Client;`
    
  
7. 在 .cs 文件中向主方法添加以下代码。
    
  ```cs
  
class Program
    {
        static void Main(string[] args)
        {
            SetBingMapsKey();
            Console.WriteLine("Bing Maps set successfully");
        }
     static private void SetBingMapsKey()
        {

            ClientContext context = new ClientContext("<Site Url>");
            Web web = context.Web;
            web.AllProperties["BING_MAPS_KEY"] = "<Valid Bing Maps Key>"
            web.Update();
            context.ExecuteQuery();
        }    
    }

  ```

8. 替换 <Site Url> 和具有有效值的  _<Valid Bing Maps Key>_。
    
  
9. 在"项目属性"中将目标框架设置为 .NET Framework 4.0，并运行该示例。
    
  
10. 应立即在 Web 级别设置该密钥。 
    
  

## 后续步骤
<a name="SP15Bing_nextsteps"> </a>

若要了解使用 SharePoint 2013 中的位置和映射功能的详细信息，请参阅以下信息：
  
    
    

-  [如何：在 SharePoint 2013 中以编程方式向列表添加 Geolocation 列](how-to-add-a-geolocation-column-to-a-list-programmatically-in-sharepoint-2013.md)
    
  
-  [如何：使用客户端呈现扩展地理位置字段类型](how-to-extend-the-geolocation-field-type-using-client-side-rendering.md)
    
  

