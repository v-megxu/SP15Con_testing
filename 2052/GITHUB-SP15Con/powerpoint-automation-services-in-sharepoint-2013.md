---
title: SharePoint 2013 中的 PowerPoint Automation Services
ms.prod: SHAREPOINT
ms.assetid: 168c7dc0-fbdc-41a2-84db-65d211d3d673
---


# SharePoint 2013 中的 PowerPoint Automation Services
了解如何使用 Microsoft PowerPoint Automation Services 执行服务器端至各种文件格式的演示文稿转换。 

  
    
    

 * **Applies to:*** *Microsoft SharePoint Server 2013*  | *Microsoft PowerPoint Automation Services* 
## 简介
<a name="PAS_Intro"> </a>

许多大型和小型企业都将其 Microsoft SharePoint Server 库用作 Microsoft PowerPoint 演示文稿的存储库。所有这些企业在存储、分发和更新演示文稿方面都有其特定的需求。Microsoft PowerPoint Automation Services 是 Microsoft SharePoint Server 2013 的一种新功能，可帮助企业管理其演示文稿。它是一项共享服务，可提供无人参与的、服务器端至其他格式的演示文稿转换。其最初便是针对在服务器上运行而设计的，并能够以可靠且可预测的方式处理许多演示文稿文件。
  
    
    
通过使用 PowerPoint Automation Services，可以从 PowerPoint 二进制文件格式 (.ppt) 和 PowerPoint Open XML 文件格式 (.pptx) 转换为其他格式。例如，您可能需要将一批 PowerPoint 97-2003 文件升级到 Open XML 演示文稿文件。您还可以在"编辑"菜单中创建自定义操作，以允许用户按需创建 PDF 版本的演示文稿。
  
    
    

> **注释**
> PowerPoint Automation Services 利用 SharePoint 2013 的工具，且作为其功能而存在。您必须安装 SharePoint Server 2013 才能使用 PowerPoint Automation Services。如果您要在服务器场中使用 SharePoint Server 2013，则必须明确启用 PowerPoint Automation Services。 
  
    
    


## PowerPoint Automation Services 方案
<a name="PAS_Scenarios"> </a>

下列方案描述了可通过 PowerPoint Automation Services 在服务器上自动处理演示文稿的两种方式：
  
    
    

- 大型企业将其所有年收益演示文稿存储在企业 Intranet 网站上的单个文档库中。该库包含多年累积的大量演示文稿。IT 部门需要将 PowerPoint 97-2003 二进制文件格式 (.ppt) 的所有演示文稿文件转换为 Open XML 演示文稿文件格式 (.pptx)。执行此转换的开发人员决定执行以下操作：将解决方案部署到将循环访问库中的所有文件的服务器，检查以确定该文件的格式是否为 .ppt 并将每个 .ppt 文件转换为 .pptx 文件格式。
    
  
- 地区销售部门向其所有客户提供了自定义服务估计值。每个销售人员将在现场会议或在线会议上与其客户审查其报价。在会议结束后，销售人员将向客户提供一份 PDF 格式的报价单副本。该部门聘请了一个供应商在"编辑"菜单中为存储在其 Extranet 中的文档库中的 PowerPoint 文件创建一个自定义动词。单击此动词时，服务器将运行一个程序，此程序会将 PowerPoint 文件转换为位于同一个库中的 PDF。
    
  

### 支持的源演示文稿格式

以下是适用于转换的受支持的源演示文稿格式：
  
    
    

- Open XML 文件格式演示文稿格式 (.pptx)
    
  
- PowerPoint 97-2003 演示文稿 (.ppt)
    
  

### 支持的目标文档格式

支持的目标文档格式包括所有支持的源文档格式，以及以下格式：
  
    
    

- .pptx（Open XML 文件格式演示文稿格式）
    
  
- .pdf
    
  
- .xps（Open XML 纸张规范）
    
  
- .jpg
    
  
- .png（可移植网络图形格式）
    
  

### PowerPoint Automation Services 的限制

PowerPoint Automation Services 不包括打印文档的功能。但是它能够直接将 PowerPoint 演示文稿文件（.ppt 和 .pptx）转换为 PDF 或 XPS，并将它们后台打印至打印机。
  
    
    

## PowerPoint Automation Services API
<a name="PAS_APIs"> </a>

若要使用 PowerPoint Automation Services，您需要使用其编程接口将转换请求发送到 SharePoint Server 2013 服务器。对于每个转换请求，您指定要转换的文件和转换作业的输出格式。对于某些转换请求，还可以指定转换哪些类型的内容，包括注释、隐藏幻灯片或文档属性。
  
    
    
PowerPoint Automation Services 使用用于发送和接收转换请求的异步模式方法。因而，您可以编写在发送转换请求后继续执行的代码。如果您需要在完成转换请求后向用户发送通知，可以指定引用在操作完成时执行的回调方法的委托。 
  
    
    

> **注释**
> 有关如何使用异步设计模式的详细信息，请参阅 [异步编程概述](http://msdn.microsoft.com/zh-cn/library/ms228963.aspx)。 
  
    
    

以下各节包含了一组有限数量的类，这些类是发送和接收转换请求所必需的。所有这些类都包含在 **Microsoft.Office.Server.PowerPoint.Conversion** 命名空间中。
  
    
    

### 请求基类

 **Request** 类是 **Microsoft.Office.Server.PowerPoint.Conversion** 命名空间中的最基本类。所有其他请求 类型（ **PresentationRequest**、 **PictureRequest**、 **PdfRequest** 和 **XpsRequest**）都从该类继承。 
  
    
    

**表 1. 请求基类成员**


|**成员名称**|**说明**|
|:-----|:-----|
|**BeginConvert(Microsoft.SharePoint.SPServiceContext, System.AsyncCallback, System.Object)** 方法 <br/> |开始转换操作。第一个参数为  _serviceContext_，该参数指定要转换的文件所在的 SharePoint 网站的上下文。使用  _callback_ 参数可指定引用在操作完成时执行的方法的委托。如果您需要将任何其他信息从调用代码传递到回调方法，请使用 _state_ 参数。 <br/> 返回一个  [IAsyncResult](https://msdn.microsoft.com/library/System.IAsyncResult.aspx) 对象。 <br/> |
|**EndConvert(IAsyncResult)** 方法 <br/> |结束转换操作。 _result_ 参数需要相应的 **BeginConvert** 转换请求返回的结果 [IAsyncResult](https://msdn.microsoft.com/library/System.IAsyncResult.aspx) 对象。如果该请求在调用 **EndConvert** 时尚未完成，则将阻止调用线程，直到转换操作完成。 <br/> 不返回值。  <br/> |
   

### PresentationRequest 类

 **PresentationRequest** 类（继承自 **Request** 类）将 PowerPoint 97-2003 文件 (.ppt) 或 Open XML 文件格式演示文稿 (.pptx) 转换为其他演示文稿文件格式。在上面提及的第一种方案中，您使用此类将文档库中的旧的演示文稿文件转换为 Open XML 文件格式演示文稿格式。
  
    
    
 **PresentationRequest** 类的构造函数方法具有三个必需参数：
  
    
    

-  _input_ - 采用需要转换为 [Stream](https://msdn.microsoft.com/library/System.IO.Stream.aspx) 对象的文件。
    
  
-  _extension_ - 指定将转换的文件的文件扩展名的字符串。
    
  
-  _output_ - 指定将存储输出的 [SPFileStream](http://msdn.microsoft.com/zh-cn/library/microsoft.sharepoint.spfilestream%28office.12%29.aspx) 对象。
    
  
 **PresentationRequest** 类具有针对其添加 _settings_ 参数的构造函数方法的单个重载。 _settings_ 参数接受 **PresentationSettings** 对象作为参数。
  
    
    

> **提示**
> 在将输出  [Stream](https://msdn.microsoft.com/library/System.IO.Stream.aspx) 对象转换回 [SPFile](http://msdn.microsoft.com/zh-cn/library/microsoft.sharepoint.spfile%28office.12%29.aspx) 对象时，检查为结果文件给定的扩展名是否与所需的文件类型扩展名（.ppt 或 .pptx）匹配。
  
    
    


### PdfRequest 类

 **PdfRequest** 类（也继承自 **Request** 类）将 PowerPoint 97-2003 文件 (.ppt) 或 Open XML 文件格式演示文稿 (.pptx) 转换为 .pdf 文件。在上面提及的第二种方案中，您使用此类将演示文稿转换为 PDF 文件。
  
    
    
 **PdfRequest** 类的构造函数方法也具有三个必需参数（ _input_、 _extension_ 和 _output_），这类似于 **PresentationRequest** 类。
  
    
    
 **PdfRequest** 类也具有针对其添加 _settings_ 参数的构造函数方法的单个重载。 _settings_ 参数接受 **FixedFormatSettings** 对象作为参数。
  
    
    

> **提示**
> 在将输出  [Stream](https://msdn.microsoft.com/library/System.IO.Stream.aspx) 对象转换回 [SPFile](http://msdn.microsoft.com/zh-cn/library/microsoft.sharepoint.spfile%28office.12%29.aspx) 对象时，检查为结果文件给定的扩展名是否与所需的文件类型扩展名 (.pdf) 匹配。
  
    
    


### PictureRequest 类

 **PictureRequest** 类（也继承自 **Request** 类）将 PowerPoint 97-2003 文件 (.ppt) 或 Open XML 文件格式演示文稿 (.pptx) 转换为一组 .jpg 或 .png 格式的图像文件。
  
    
    
此外， **PictureRequest** 类的构造函数方法具有四个必需参数。 _input_、 _extension_ 和 _output_ 参数与 **PresentationRequest** 类构造函数的参数类似。 **PictureRequest** 类的构造函数方法也具有必需的 _format_ 参数，该参数必需是 **PictureFormat** 枚举中的常数。
  
    
    
 **PictureRequest** 类不具有针对其构造函数方法的任何重载。
  
    
    

> **提示**
> **PictureRequest** 类返回包含一个图像文件包的流。在将输出 [Stream](https://msdn.microsoft.com/library/System.IO.Stream.aspx) 对象转换回 [SPFile](http://msdn.microsoft.com/zh-cn/library/microsoft.sharepoint.spfile%28office.12%29.aspx) 对象时，检查为结果文件给定的扩展名是否为 .zip。
  
    
    


## 构建 PowerPoint Automation Services 应用程序
<a name="PAS_Build"> </a>

说明如何编写使用 PowerPoint Automation Services 的代码的最简单方法是构建控制台应用程序。您必须在 SharePoint Server 上构建和运行控制台应用程序，而不是在客户端计算机上。启动转换请求的代码是类似的，无论转换请求代码是集成到 Web 部件、工作流还是事件处理程序中。通过从控制台应用程序使用 PowerPoint Automation Services，以下过程说明了如何在不增加 Web 部件、事件处理程序或工作流的复杂性的情况下使用 API。
  
    
    

> **注释**
> 由于 PowerPoint Automation Services 是 SharePoint Server 2013 的服务，因此您仅能将其用于直接在 SharePoint Server 上运行的应用程序中。您必须将应用程序构建为服务器场解决方案。您无法从沙盒解决方案使用 PowerPoint Automation Services。 
  
    
    


### 构建应用程序


1. 启动 Microsoft Visual Studio 2012。
    
  
2. 在"文件"菜单上，指向"新建"，然后选择"项目"。 
    
  
3. 在"新建项目"对话框中的"已安装"下方，依次展开"模板"和"Visual C#"，然后选择"Windows"。
    
  
4. 在项目模板列表中，单击"控制台应用程序"。
    
  
5. 请确保，Visual Studio 中的项目面向 .NET Framework 4。
    
    > **注释**
      > 早期版本的 SharePoint Server 需要您面向 .NET Framework 3.5。Microsoft.SharePoint 库现在引用 .NET Framework 4 中的程序集。此外，请确保您的项目面向整个 .NET Framework 4 而非 .NET Framework 4 Client Profile。 
6. 在"名称"框中，键入您要用于项目的名称，例如 PAS_Sample。
    
  
7. 在"位置"框中，键入您要放置项目的位置。
    
  
8. 单击"确定"以创建解决方案。
    
  
9. 默认情况下，Visual Studio 2008 创建面向 x86 CPU 的项目，但是若要构建 SharePoint Server 应用程序，您必须面向所有 CPU。
    
    如果您要构建 Microsoft Visual C# 应用程序，请在"解决方案资源管理器"中，右键单击项目，然后单击"属性"。
    
  - 在项目"属性"窗口中，单击"构建"。
    
  
  - 指向"配置"列表，并选择"所有配置"。
    
  
  - 指向"平台目标"列表，并选择"任何 CPU"。
    
  

    
    
    如果您要构建 Microsoft Visual Basic .NET Framework 应用程序，请在"属性"窗口中，单击"编译"。
    
  - 单击"高级编译选项"。
    
  
  - 指向"配置"列表，并选择"所有配置"。
    
  
  - 指向"平台目标"列表，然后选择"任何 CPU"。
    
  

    
    
  
10. 在"项目"菜单上，单击"添加引用"以打开"添加引用"对话框。 
    
  
11. 展开"程序集"，然后执行下列操作： 
    
  - 展开"框架"，然后添加对 System.Web 的引用。
    
  
  - 展开"扩展名"，然后添加对 Microsoft.SharePoint 的引用。
    
  
12. 此外，在"添加引用"对话框中，选择"浏览"，导航到 Microsoft.Office.Server.PowerPoint.dll 的位置（默认位置为 C:\\Windows\\Microsoft.NET\\assembly\\GAC_MSIL\\Microsoft.Office.Server.PowerPoint\\v4.0_15.0.0.0__71e9bce111e9429c），选择程序集，然后选择"添加"。 
    
  
下面的 C# 和 Visual Basic 示例说明了一个简单 PowerPoint Automation Services 应用程序，该应用程序将 SharePoint 网站的共享文档文件夹中的 PowerPoint 97-2003 文件 (.ppt) 转换为同一文件夹中的 PowerPoint Open XML 文件 (.pptx)。
  
    
    



```cs

using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Web;
using Microsoft.SharePoint;
using Microsoft.Office.Server.PowerPoint.Conversion;

namespace PAS_Sample
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                string siteURL = "http://localhost";
                using (SPSite site = new SPSite(siteURL))
                {
                    using (SPWeb web = site.OpenWeb())
                    {
                        Console.WriteLine("Begin conversion");

                        // Get a reference to the "Shared Documents" library 
                        // and the presentation file to be converted.
                        SPFolder docs = web.Folders[siteURL + 
                            "/Shared Documents"];
                        SPFile file = docs.Files[siteURL + 
                            "/Shared Documents/Pres1.ppt"];

                        // Convert the file to a stream and create an
                        // SPFileStream object for the conversion output.
                        Stream fStream = file.OpenBinaryStream();
                        SPFileStream stream = new SPFileStream(web, 0x1000);

                        // Create the presentation conversion request.
                        PresentationRequest request = new PresentationRequest(
                            fStream,
                            ".ppt",
                            stream);

                        // Send the request synchronously, passing
                        // in a 'null' value for the callback parameter, 
                        // and capturing the response in the result object.
                        IAsyncResult result = request.BeginConvert(
                            SPServiceContext.GetContext(site),
                            null,
                            null);

                        // Use the EndConvert method to get the result. 
                        request.EndConvert(result);

                        // Add the converted file to the document library.
                        SPFile newFile = docs.Files.Add(
                            "newPres1.pptx", 
                            stream, 
                            true);
                        Console.WriteLine("Output: {0}", newFile.Url);

                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine("Error: " + ex.Message);
            }
            finally
            {
                Console.WriteLine("Complete");
                Console.ReadKey();
            }
        }
    }
}
```




```VB.net

Imports System
Imports System.Collections.Generic
Imports System.IO
Imports System.Linq
Imports System.Text
Imports System.Web
Imports Microsoft.SharePoint
Imports Microsoft.Office.Server.PowerPoint.Conversion

Namespace PAS_Sample
    Class Program
        Private Shared Sub Main(args As String())
            Try
                Dim siteURL As String = "http://localhost"
                Using site As New SPSite(siteURL)
                    Using web As SPWeb = site.OpenWeb()
                        Console.WriteLine("Begin conversion")

                        ' Get a reference to the "Shared Documents" library 
                        ' and the presentation file to be converted.
                        Dim docs As SPFolder = web.Folders(siteURL + _
                            "/Shared Documents")
                        Dim file As SPFile = docs.Files(siteURL + _
                            "/Shared Documents/Pres1.ppt")

                        ' Convert the file to a stream and create an
                        ' SPFileStream object for the conversion output.
                        Dim fStream As Stream = file.OpenBinaryStream()
                        Dim stream As New SPFileStream(web, &amp;H1000)

                        ' Create the presentation conversion request.
                        Dim request As New PresentationRequest(fStream, _
                            ".ppt", 
                            stream)

                        ' Send the request synchronously, passing
                        ' in a Nothing value for the callback parameter, 
                        ' and capturing the response in the result object.
                        Dim result As IAsyncResult = request.BeginConvert(_
                            SPServiceContext.GetContext(site), _
                            Nothing, _
                            Nothing)

                        ' Use the EndConvert method to get the result. 
                        request.EndConvert(result)

                        ' Add the converted file to the document library.
                        Dim newFile As SPFile = docs.Files.Add(_
                            "newPres1.pptx", _
                            stream, _
                            True)

                        Console.WriteLine("Output: {0}", newFile.Url)
                    End Using
                End Using
            Catch ex As Exception
                Console.WriteLine("Error: " + ex.Message)
            Finally
                Console.WriteLine("Complete")
                Console.ReadKey()
            End Try
        End Sub
    End Class
End Namespace

```


### 构建和运行示例


1. 将 PowerPoint 文档（名为 Pres1.ppt ）添加到 SharePoint 网站中的共享文档文件夹。
    
  
2. 构建和运行示例。
    
  
3. 等待一分钟以便转换进程开始运行，然后导航至 SharePoint 网站中的共享文档文件夹，并刷新页面。文档库中目前包含一个新的 PowerPoint 文档 Pres1.pptx。
    
  
SharePoint Server 2013 上的 PowerPoint Automation Services 为企业提供了用于管理其演示文稿文件的高级功能。此高性能解决方案允许可伸缩的、服务器端演示文稿操作和生成（批量或按需）。 
  
    
    

> **注释**
>  必须先确保已在 SharePoint 管理中心控制台中启用 PowerPoint Automation Services，然后才能运行此示例。>  若要验证是否已启用 PowerPoint Automation Services，请执行以下操作：>  在管理中心控制台中的"系统设置"下方，选择"管理服务器上的服务"，然后确保"PowerPoint Conversion Service"设置为"已启动"。>  此外，在管理中心控制台中的"应用程序管理"下方，选择"管理服务应用程序"，然后确保"PowerPoint Conversion Service 应用程序"和"PowerPoint Conversion Service 应用程序代理"都设置为"已启动"。
  
    
    


## 结论
<a name="PAS_Conclusion"> </a>

SharePoint Server 2013 上的 PowerPoint Automation Services 为企业提供了用于管理其演示文稿文件的高级功能。此高性能解决方案允许可伸缩的、服务器端演示文稿操作和生成（批量或按需）。 
  
    
    

## 其他资源
<a name="PAS_Additional"> </a>


-  [使用 SharePoint 2010 Word Automation Services 进行开发](http://msdn.microsoft.com/zh-cn/library/ff742315.aspx)
    
  
-  [PowerPoint 开发中心](http://msdn.microsoft.com/zh-cn/office/aa905465)
    
  
-  [SharePoint 开发人员中心](http://msdn.microsoft.com/zh-cn/sharepoint/default.aspx)
    
  

