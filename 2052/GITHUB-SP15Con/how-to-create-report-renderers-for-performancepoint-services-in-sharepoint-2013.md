---
title: 如何：为 SharePoint 2013 中的 PerformancePoint Services 创建报告呈现器
ms.prod: SHAREPOINT
ms.assetid: 642175cb-8fcb-4210-8d1e-626ad1f58bb0
---


# 如何：为 SharePoint 2013 中的 PerformancePoint Services 创建报告呈现器
了解如何在自定义报告扩展中为 PerformancePoint Services 创建呈现器组件。
## 什么是 PerformancePoint Services 的自定义报告呈现器？
<a name="bk_intro"> </a>

在 PerformancePoint Services 中，自定义报告呈现器是用于 Web 部件中呈现自定义报告的 Web 服务器控件。呈现器可为报告可视化（如表和图）编写 HTML，提供用于处理报告参数的逻辑以及从存储库中检索报告对象。
  
    
    
下面的过程和代码示例基于 [自定义对象示例](http://msdn.microsoft.com/library/af021d52-7562-4e7a-9de4-e1fc5784a59d%28Office.15%29.aspx)中的 **SampleReportRenderer** 类。该呈现器会呈现一个表并用从链接的筛选器接收的值填充该表。有关该类的完整代码，请参阅 [代码示例：为 SharePoint Server 2013 中的自定义 PerformancePoint Services 报告创建呈现器](#bk_example)。
  
    
    
建议您将示例报告呈现器用作模板。该示例说明如何调用 PerformancePoint Services API 中的对象，并演示针对 PerformancePoint Services 开发的最佳实践。
  
    
    

## 为自定义 PerformancePoint Services 报告创建呈现器
<a name="BKMK_ConfigRenderer"> </a>


  
    
    

1. 安装 PerformancePoint Services，或者将您的扩展使用的 DLL（步骤 3 中列出）复制到您的计算机上。有关详细信息，请参阅  [开发方案中使用的 PerformancePoint Services DLL](http://msdn.microsoft.com/library/41e92619-8253-481d-82f9-35b6a6abc477%28Office.15%29.aspx)。 
    
  
2. 在 Visual Studio 中，创建一个 C# 类库。如果您已为扩展创建了一个类库，请添加新 C# 类。
    
    您必须用强名称对您的 DLL 进行签名。此外，请确保您的 DLL 所引用的所有程序集都具有强名称。有关如何使用强名称对程序集进行签名以及如何创建公钥/私钥对的信息，请参阅  [How to: Create a Public/Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114.aspx)。
    
  
3. 将以下 PerformancePoint Services DLL 作为程序集引用添加到项目：
    
  - Microsoft.PerformancePoint.Scorecards.Client.dll
    
  
  - Microsoft.PerformancePoint.Scorecards.Server.dll
    
  
  - Microsoft.PerformancePoint.Scorecards.Store.dll
    
  

    根据扩展的功能不同，可能需要其他项目引用。
    
  
4. 在呈现器类中，为以下 PerformancePoint Services 命名空间添加 **using** 指令：
    
  -  [Microsoft.PerformancePoint.Scorecards](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.aspx)
    
  
  -  [Microsoft.PerformancePoint.Scorecards.Server.Extensions](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.aspx)
    
  
  -  [Microsoft.PerformancePoint.Scorecards.Store](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Store.aspx)
    
  

    根据您的扩展的功能，可能需要其他 **using** 指令。
    
  
5. 从  [ParameterizableControl](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.ParameterizableControl.aspx) 基类继承。
    
  
6. 重写  [GetElement](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.ParameterizableControl.GetElement.aspx) 方法，以从存储库中检索报告对象。
    
  
7. 重写  [SetData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.ParameterizableControl.SetData.aspx) 方法，以设置报告数据集并检索传入的参数值。
    
  
8. 重写  [Render](https://msdn.microsoft.com/library/System.Web.UI.WebControls.WebControl.Render.aspx) 方法，以呈现报告可视化的 HTML。
    
  

## 代码示例：为 SharePoint Server 2013 中的自定义 PerformancePoint Services 报告创建呈现器
<a name="bk_example"> </a>

以下代码示例中的类将创建一个报告呈现器，该呈现器显示从示例筛选器传入的库存信息。
  
    
    
您必须先按 [创建和配置呈现器类](#BKMK_ConfigRR)中所述配置开发环境，然后才能编译此代码示例。
  
    
    



```cs

using System;
using System.Collections.Generic;
using System.Data;
using System.Web.UI;
using Microsoft.PerformancePoint.Scorecards;
using Microsoft.PerformancePoint.Scorecards.Server.Extensions;
using Microsoft.PerformancePoint.Scorecards.Store;

namespace Microsoft.PerformancePoint.SDK.Samples.SampleReport
{

    // The class that define the sample report's renderer.
    public class SampleReportRenderer : ParameterizableControl 
    {
        private ReportView reportView;

        private ReportView ReportView
        {
            get
            {

                // The GetElement method is used internally by this property, which is used
                // in turn by the SetData method.
                reportView = GetElement(ElementLocation) as ReportView;
                return reportView;
            }
        }

        // Initializes the current instance according to a standard interface. This method
        // sets up the dataset.
        public override void SetData(RepositoryLocation elementLocation, string resourcePath, string targetControlId, BIDataContainer dataContainer, bool accessibilityMode)
        {

            // The renderer must call the base implementation of the SetData method
            // to set report properties.
            base.SetData(elementLocation, resourcePath, targetControlId, dataContainer, accessibilityMode);
        
            if (null != ReportView)
            {

                // If the report view's custom data represents a serialized object, deserialize
                // it, and then use it to access a data source or other object.
                string customData = ReportView.CustomData;
                if (!string.IsNullOrEmpty(customData))
                {
                    System.Diagnostics.Debug.WriteLine(string.Format("Report view '{0}' has the following custom data: {1}", ReportView.Name.Text, customData));
                }
                
                // Iterate through the user's selections sent by the filter. 
                // The MultiSelectTreeControl filter control can send multiple
                // rows of data but other native controls send one message only.
                foreach (ParameterMessage message in BIDataContainer.ParameterMessages)
                {
                    // This line demonstrates how to do something with each incoming parameter message.
                    System.Diagnostics.Debug.WriteLine(string.Format("Parameter message: {0}", message.DisplayName));
                }
            }
        }
        
        // Render page content using the specified writer.
        protected override void Render(HtmlTextWriter output)
        {
            try
            {
                if (null != ReportView &amp;&amp; !string.IsNullOrEmpty(ReportView.CustomData))
                {
                    output.RenderBeginTag(HtmlTextWriterTag.P);
                    output.RenderBeginTag(HtmlTextWriterTag.B);

                    // This line shows how to retrieve the content of the
                    // report's optional CustomData property. CustomData can store
                    // information that the report does not store elsewhere.
                    output.Write(string.Format("The ReportView &amp;quot;{0}&amp;quot; has CustomData information. The CustomData is &amp;quot;{1}&amp;quot;", 
                        ReportView.Name.Text, ReportView.CustomData));
                    output.RenderEndTag(); // B
                    output.RenderEndTag(); // P
                }

                Dictionary<Guid, ParameterMessage> parametersIndex =
                    IndexParameterMessages(BIDataContainer.ParameterMessages.ToArray());

                // Each connection gets a unique identifier.
                foreach (Guid parameterMappingId in parametersIndex.Keys)
                {
                    ParameterMessage message = parametersIndex[parameterMappingId];

                    output.RenderBeginTag(HtmlTextWriterTag.Table);
                    
                    output.AddAttribute(HtmlTextWriterAttribute.Style, "ms-partline");
                    output.RenderBeginTag(HtmlTextWriterTag.Tr);

                    output.AddAttribute(HtmlTextWriterAttribute.Colspan, "5");
                    output.RenderBeginTag(HtmlTextWriterTag.Td);
                    
                    output.RenderBeginTag(HtmlTextWriterTag.B);
                    output.Write(string.Format("EndPoint name is: {0}", message.Values.TableName));

                    output.RenderEndTag();  // B
                    output.RenderEndTag();  // Td
                    output.RenderEndTag();  // Tr

                    output.AddAttribute(HtmlTextWriterAttribute.Style, "\\"border-bottom:solid 10px #ffdd00; background:PapayaWhip\\"");
                    output.RenderBeginTag(HtmlTextWriterTag.Tr);

                    // Read the message.Values data table and print the column names.
                    foreach (DataColumn col in message.Values.Columns)
                    {
                        output.RenderBeginTag(HtmlTextWriterTag.Td);
                        output.Write(string.IsNullOrEmpty(col.Caption) ? "&amp;nbsp;" : col.Caption);
                        output.RenderEndTag();
                    }
                    output.RenderEndTag();  // Tr

                    // Print the data from the Values property, which is a data table.
                    foreach (DataRow row in message.Values.Rows)
                    {
                        output.RenderBeginTag(HtmlTextWriterTag.Tr);
                        for (int i = 0; i < message.Values.Columns.Count; i++)
                        {
                            output.RenderBeginTag(HtmlTextWriterTag.Td);
                            output.Write(string.IsNullOrEmpty(row[i].ToString()) ? "&amp;nbsp;" : row[i].ToString());
                            output.RenderEndTag();
                        }
                        output.RenderEndTag();  // Tr
                    }
                    output.RenderEndTag(); // table
                }
            }
            catch (Exception e)
            {
                output.RenderBeginTag(HtmlTextWriterTag.H1);
                output.Write("Error! An exception has occurred!");
                output.RenderEndTag();
                
                output.RenderBeginTag(HtmlTextWriterTag.P);
                output.Write(e.Message);
                output.RenderEndTag();

                output.RenderBeginTag(HtmlTextWriterTag.P); 
                output.Write(e.StackTrace);
                output.RenderEndTag();
            }
        }

        // Get the report object.
        protected override Element GetElement(RepositoryLocation elementLocation)
        {
            ReportView rv = null;
            if (!RepositoryLocation.IsNullOrEmpty(elementLocation))
            {
                rv = SPDataStore.GlobalDataStore.GetReportViewForExecution(elementLocation);
            }
            return (rv);
        }
    }
}
```


## 后续步骤
<a name="bk_next"> </a>

在创建报告呈现器和报告编辑器（如果需要，包括其用户界面）后，部署扩展，如 [如何：手动注册 PerformancePoint Services 扩展](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)中所述。
  
    
    

## 其他资源
<a name="bk_addResources"> </a>


-  [如何：为 SharePoint 2013 中的 PerformancePoint Services 创建报告呈现器](how-to-create-report-renderers-for-performancepoint-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 PerformancePoint Services](performancepoint-services-in-sharepoint-2013.md)
    
  

