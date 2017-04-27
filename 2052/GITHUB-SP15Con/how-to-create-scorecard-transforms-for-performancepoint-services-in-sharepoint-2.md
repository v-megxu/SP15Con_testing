---
title: 如何：为 SharePoint 2013 中的 PerformancePoint Services 创建记分卡转换
ms.prod: SHAREPOINT
ms.assetid: 16117716-6ce5-4890-a829-5312f76164d0
---


# 如何：为 SharePoint 2013 中的 PerformancePoint Services 创建记分卡转换
了解如何为 SharePoint Server 2013 中的 PerformancePoint Services 创建自定义记分卡转换。
## 什么是 PerformancePoint Services 中的记分卡转换？
<a name="bk_intro"> </a>

在 PerformancePoint Services 中，记分卡转换会在记分卡视图呈现在仪表板中之前，更改这些视图的外观、内容或功能。有关详细信息，请参阅 [PerformancePoint Services 记分卡转换概述](http://msdn.microsoft.com/library/d69d171b-827a-48a8-a3e1-7aaf0bfbc7f8%28Office.15%29.aspx)。
  
    
    

## 创建 PerformancePoint Services 记分卡转换
<a name="BKMK_CreateClass"> </a>


1. 安装 PerformancePoint Services，或者将随 PerformancePoint Services一起安装的 DLL 复制到您的计算机。有关详细信息，请参阅  [开发方案中使用的 PerformancePoint Services DLL](http://msdn.microsoft.com/library/41e92619-8253-481d-82f9-35b6a6abc477%28Office.15%29.aspx)。
    
  
2. 在 Visual Studio 中，创建一个 C# 类库。如果您已为扩展创建了一个类库，请添加新 C# 类。
    
    您必须用强名称对您的 DLL 进行签名，并您的 DLL 所引用的所有程序集都具有强名称。若要了解如何使用强名称对程序集进行签名以及如何创建公钥/私钥对的信息，请参阅 [How to: Create a Public/Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114.aspx)。
    
  
3. 将 Microsoft.PerformancePoint.Scorecards.Client.dll 作为程序集引用添加到项目中。
    
  
4. 为以下命名空间添加 **using** 指令：
    
  - **Microsoft.PerformancePoint.Scorecards**
    
  
  - **Microsoft.PerformancePoint.Scorecards.Extensions**
    
  
  - **System.Collections.Generic**
    
  
5. 实现  [IGridViewTransform](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.IGridViewTransform.aspx) 接口。
    
  
6. 重写  [GetId](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.IGridViewTransform.GetId.aspx) 方法以返回您的转换的字符串标识符。 [GetId](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.IGridViewTransform.GetId.aspx) 必须返回与在 PerformancePoint Services web.config 文件中为转换注册的 **key** 属性相同的字符串。有关注册记分卡转换的详细信息，请参阅 [如何：手动注册 PerformancePoint Services 扩展](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)。
    
  
7. 重写  [GetTransformType](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.IGridViewTransform.GetTransformType.aspx) 方法以指定何时运行转换。转换的运行时间点取决于由 [GridViewTransformType](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.GridViewTransformType.aspx) 枚举定义的类型： **PreQuery**、 **PostQuery** 或 **PreRender**。有关详细信息，请参阅 [PerformancePoint Services 记分卡转换概述](http://msdn.microsoft.com/library/d69d171b-827a-48a8-a3e1-7aaf0bfbc7f8%28Office.15%29.aspx)。
    
  
8. 重写  [Execute](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.IGridViewTransform.Execute.aspx) 方法以定义如何转换记分卡。下面的代码示例演示如何向记分卡视图添加列以及如何更改空白记分卡单元格的格式。
    
  
对 DLL 进行签名和生成之后，按 [如何：手动注册 PerformancePoint Services 扩展](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)中所述安装扩展。
## 代码示例 1：向 PerformancePoint Services 记分卡添加列
<a name="bk_example1"> </a>

下面的代码示例创建一个 **PreQuery** 转换，该转换向在列的叶级别处包含 KPI 的已呈现记分卡视图中添加一列。（如果记分卡视图在 KPI 下包含成员，则不会添加该列。）
  
    
    
您必须先按 [创建 PerformancePoint Services 记分卡转换](#BKMK_CreateClass)中所述配置开发环境，然后才能编译此代码示例。
  
    
    



```cs

using System;
using System.Collections.Generic;
using Microsoft.PerformancePoint.Scorecards;
using Microsoft.PerformancePoint.Scorecards.Extensions;

namespace Microsoft.PerformancePoint.SDK.Samples.ScorecardTransforms.PreQuery
{

    // Represents the class that adds columns of data to a scorecard view. 
    public class AddColumnTransform : IGridViewTransform
    {

        // Set transform type to PreQuery.
        public GridViewTransformType GetTransformType()
        {
            return GridViewTransformType.PreQuery;
        }

        // Return the string identifier of your transform. This value must
        // match the key attribute registered in the web.config file.
        public string GetId()
        {
            return "AddColumn";
        }

        // Run the transform to add a column. 
        public void Execute(GridViewData viewData, PropertyBag parameters, IGlobalCache cache)
        {
            // Verify the scorecard definition.
            if (viewData == null)
            {
                throw new ArgumentException("Parameter cannot be null", "viewData");
            }
                     
            List<GridHeaderItem> leafRowHeaders = viewData.RootRowHeader.GetAllLeafHeadersInTree();

            foreach (GridHeaderItem rowHeader in leafRowHeaders)
            {
                if (rowHeader.HeaderType == ScorecardNodeTypes.Kpi)
                {
                    Kpi kpi = cache.GetKpi(rowHeader.LinkedKpiLocation);
                    if (kpi != null &amp;&amp; viewData.RootColumnHeader != null)
                    {

                        // Create the column header and add it to the root.
                        GridHeaderItem theNewColumn = GridHeaderItem.CreateDetailsHeader(kpi.Owner.DisplayName);

                        // Set the GUIDs for the data headers.
                        // Setting the DefinitionGuid property to the
                        // same value as the root column header enables
                        // Dashboard Designer to display the scorecard. 
                        // Note: Do not try to modify or delete the new
                        // column from within Dashboard Designer.
                        theNewColumn.DefinitionGuid = viewData.RootColumnHeader.DefinitionGuid;
                        theNewColumn.Parent = viewData.RootColumnHeader;
                        theNewColumn.Guid = new Guid();

                        // Insert the column at the end of the collection
                        // of child elements.
                        if (viewData.RootColumnHeader.Children.Count != 0)
                        {
                            viewData.RootColumnHeader.Children.Insert(viewData.RootColumnHeader.Children.Count, theNewColumn);
                        }
                                                                         
                        break;
                    }
                }
            }
            viewData.RootColumnHeader.LinkAndIndexTreeFromRoot();
        }
    }
}
```


## 代码示例 2：更改 PerformancePoint Services 记分卡中的空白单元格的格式
<a name="bk_example2"> </a>

下面的代码示例创建一个 **PreQuery** 转换，该转换向空白记分卡单元格应用灰色背景色。
  
    
    

> **注释**
> 您必须先按 [创建 PerformancePoint Services 记分卡转换](#BKMK_CreateClass)中所述配置开发环境，然后才能编译此代码示例。此外，还必须向项目中添加对 **System.Drawing** 程序集的引用。
  
    
    


```cs

using System;
using System.Collections.Generic;
using Microsoft.PerformancePoint.Scorecards;
using Microsoft.PerformancePoint.Scorecards.Extensions;

namespace Microsoft.PerformancePoint.SDK.Samples
{

    // Represents a transform that applies a grey background color to empty scorecard cells.
    public class GreyEmptiesTransform : IGridViewTransform
    {

        // Set the transform type to "PreRender".
        public GridViewTransformType GetTransformType()
        {
            return GridViewTransformType.PreRender;
        }

        // Return the string identifier of the transform.
        public string GetId()
        {
            return "GreyEmptyCells";
        }

        // Run the transform.
        public void Execute(GridViewData viewData, PropertyBag parameters, IGlobalCache cache)
        {
            // Validate parameters. 
            if (viewData == null)
            {
                throw new ArgumentException("Parameter cannot be null", "viewData");
            }

            // Get the headers under the root row header.
            List<GridHeaderItem> nonLeafRowHeaders = viewData.RootRowHeader.GetAllHeadersInTree();

            // Get the leaf headers under the root column header.
            List<GridHeaderItem> leafColumnHeaders = viewData.RootColumnHeader.GetAllLeafHeadersInTree();

            foreach (GridHeaderItem rowHeader in nonLeafRowHeaders)
            {
                foreach (GridHeaderItem columnHeader in leafColumnHeaders)
                {
                    // Get scorecard cells.
                    GridCell cell = viewData.Cells[rowHeader, columnHeader];

                    if (cell.IsCellEmpty || string.IsNullOrEmpty(cell.ActualValue.ToString()))
                    {
                        GridFormatInfo emptyFormat = new GridFormatInfo(viewData.DefaultCellFormatInfo);
                        emptyFormat.BackColor = new GridColor(System.Drawing.Color.Gray);
                        cell.FormatInfo = emptyFormat;
                    }
                    viewData.Cells[rowHeader, columnHeader] = cell;
                }
            }
        }
    }
}


```


## 其他资源
<a name="bk_addResources"> </a>


-  [SharePoint 2013 中的 PerformancePoint Services](performancepoint-services-in-sharepoint-2013.md)
    
  
-  [PerformancePoint Services 记分卡](http://msdn.microsoft.com/library/e77eccdb-82b3-483a-bb91-dfdc716400dd%28Office.15%29.aspx)
    
  

