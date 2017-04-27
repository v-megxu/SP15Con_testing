---
title: 如何：为 SharePoint 2013 中的 PerformancePoint Services 创建筛选器数据提供程序
ms.prod: SHAREPOINT
ms.assetid: 25508ec6-86bf-4eea-acf0-00f88e4faa55
---


# 如何：为 SharePoint 2013 中的 PerformancePoint Services 创建筛选器数据提供程序
了解如何在 PerformancePoint Services 的自定义筛选器扩展中创建数据提供程序组件。
## 什么是 PerformancePoint Services 的自定义数据提供程序？
<a name="bk_introduction"> </a>

在 PerformancePoint Services 中，自定义数据提供程序从筛选器的基础数据源中检索数据并定义如何使用这些数据。最重要的是，数据提供程序指定要在筛选控件中公开的数据值和可用作筛选器起始点的数据。数据提供程序还会存储用户从筛选控件中选择的值，这些值随后将发送给筛选器使用方。数据提供程序使用两个  [DataTable](https://msdn.microsoft.com/library/System.Data.DataTable.aspx) 对象来组织和存储数据。有关详细信息，请参阅 [PerformancePoint Services 筛选器](http://msdn.microsoft.com/library/915382d0-3997-495c-a65a-7db3fe0b8f85%28Office.15%29.aspx)。
  
    
    
以下过程和示例说明了如何创建、配置和定义筛选器数据提供程序，这些过程和示例基于  [自定义对象示例](http://msdn.microsoft.com/library/af021d52-7562-4e7a-9de4-e1fc5784a59d%28Office.15%29.aspx)中的 **SampleFilterDataProvider** 类。该编辑器是一个瘦 Web 应用程序，使用户能够修改报表的名称和说明。有关此类的完整代码，请参阅 [代码示例：在 SharePoint Server 2013 中为自定义 PerformancePoint Services 筛选器创建数据提供程序](#bk_example)。
  
    
    
建议您将示例数据提供程序用作模板。该示例说明如何调用 PerformancePoint Services API 中的对象，并演示针对 PerformancePoint Services 开发的最佳实践。 
  
    
    

## 为自定义 PerformancePoint Services 筛选器创建数据提供程序
<a name="bk_createconfig"> </a>


1. 安装 PerformancePoint Services，或者将您的扩展使用的 DLL（步骤 3 中列出）复制到您的计算机上。有关详细信息，请参阅  [开发方案中使用的 PerformancePoint Services DLL](http://msdn.microsoft.com/library/41e92619-8253-481d-82f9-35b6a6abc477%28Office.15%29.aspx)。
    
  
2. 在 Visual Studio 中，创建一个 C# 类库。如果您已为扩展创建了一个类库，请添加新 C# 类。
    
    您必须用强名称对您的 DLL 进行签名。此外，请确保您的 DLL 所引用的所有程序集都具有强名称。有关如何使用强名称对程序集进行签名以及如何创建公钥/私钥对的信息，请参阅  [How to: Create a Public/Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114.aspx)。
    
  
3. 将以下 PerformancePoint Services DLL 作为程序集引用添加到项目：
    
  - Microsoft.PerformancePoint.Scorecards.Client.dll
    
  
  - Microsoft.PerformancePoint.Scorecards.Server.dll
    
  

    根据扩展的功能不同，可能需要其他项目引用。
    
  
4. 在您提供程序类中，请为以下 PerformancePoint Services 命名空间添加 **using** 指令：
    
  -  [Microsoft.PerformancePoint.Scorecards](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.aspx)
    
  
  -  [Microsoft.PerformancePoint.Scorecards.Server.Extensions](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.aspx)
    
  

    根据您的扩展的功能，可能需要其他 **using** 指令。
    
  
5. 从  [CustomParameterDataProvider](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.CustomParameterDataProvider.aspx) 基类继承。
    
  
6. 为数据提供程序名称设置字符串标识符。此标识符必须与在注册扩展时添加到 web.config 文件的 **CustomParameterDataProviders** 部分中的项匹配。有关详细信息，请参阅 [如何：手动注册 PerformancePoint Services 扩展](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)。
    
  
7. 替代  [GetId()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.CustomParameterDataProvider.GetId.aspx) 方法，以返回数据提供程序的标识符。
    
  
8. 替代  [GetDisplayDataInternal](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.CustomParameterDataProvider.GetDisplayDataInternal.aspx) 方法，以定义要存储来自基础数据源的数据值的 [DataTable](https://msdn.microsoft.com/library/System.Data.DataTable.aspx) 对象。筛选器可使用此方法填充筛选器选择控件。显示模拟运算表必须包含以下列名：
    
  - **Key** 记录的唯一标识符。该值不能为空。出于性能和安全原因，控件只发出一个项；控件不发出其他列中的值。
    
  
  - **Display** 筛选器控件中显示的值。
    
  
  - **ParentKey** 此值用于排列树控件中的分层数据。
    
  
  - **IsDefault** 此值用于设置筛选器的持久性。
    
    > **提示**
      > 可以添加多个列以扩展筛选器功能。 

     [GetDisplayDataInternal](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.CustomParameterDataProvider.GetDisplayDataInternal.aspx) 可调用 [DataSourceRegistry.GetDataSource(DataSource)](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceRegistry.GetDataSource.aspx) 方法以按名称验证数据源类型，如下所示：
    
  - 它通过使用数据源的  [SubTypeId](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.SubTypeId.aspx) 属性来引用自定义数据源类型，该属性的值与在 PerformancePoint Services web.config 文件中为数据源扩展注册的 **subType** 特性的值相同。
    
  
  - 它通过使用  [SourceName](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.SourceName.aspx) 属性来引用本机数据源，该属性返回 [DataSourceNames](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceNames.aspx) 类中的字段。
    
  
9. 替代  [GetMessageData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.CustomParameterDataProvider.GetMessageData.aspx) 方法，以存储用户在筛选器控件中选择的内容。
    
  

## 代码示例：在 SharePoint Server 2013 中为自定义 PerformancePoint Services 筛选器创建数据提供程序
<a name="bk_example"> </a>

以下代码示例演示数据提供程序如何从 Web 服务或 Excel 工作表检索值，并为筛选器的显示数据和消息数据返回  [DataTable](https://msdn.microsoft.com/library/System.Data.DataTable.aspx) 对象。
  
    
    
在编译此代码示例之前，您必须配置开发环境，如 [创建和配置提供程序类](#BKMK_ConfigClass)中所述。
  
    
    



```cs

using System.Data;
using Microsoft.PerformancePoint.Scorecards;
using Microsoft.PerformancePoint.Scorecards.Server.Extensions;

namespace Microsoft.PerformancePoint.SDK.Samples.SampleFilter
{

    // Represents the sample filter's data provider.
    public class SampleFilterDataProvider : CustomParameterDataProvider
    {

        // This value must match the key that you register for this extension
        // in the CustomParameterDataProviders section in the web.config file.
        private const string dataProviderName = "SampleFilterDataProvider";

        // Returns a table of all possible values (rows) for the
        // filter's beginpoints. The filter's BeginPoint property returns
        // one ParameterDefinition object.
        protected override DataTable GetDisplayDataInternal(ParameterDefinition parameterDefinition, RepositoryLocation parameterSourceLocation, object custom)
        {
            DataTable retrievedData = null;

            // Get the data source.
            DataSource parameterDataSource = SafeGetDataSource(parameterSourceLocation);
            if (null != parameterDataSource)
            {

                // Verify that the data source is the sample data source
                // or an Excel workbook, which are the types that the
                // sample supports.
                // If you modify these types of data source, you must make
                // the corresponding change in the filter's editor.
                if (parameterDataSource.SourceName == "WSTabularDataSource" || parameterDataSource.SourceName == DataSourceNames.ExcelWorkbook)
                {
                    IDataSourceProvider parameterDataSourceProvider =
                        DataSourceRegistry.GetDataSource(parameterDataSource);
                    if (null != parameterDataSourceProvider)
                    {
                        var dataSourceMetadata = parameterDataSourceProvider as IDataSourceMetadata;
                        if (null != dataSourceMetadata)
                        {

                            // Get the data and store it in the retrievedDataSet
                            // variable. The -1 parameter returns all records
                            // from the data source.
                            DataSet retrievedDataSet = dataSourceMetadata.GetPreviewDataSet(-1);

                            // Verify that the dataset contains data.  
                            if (retrievedDataSet != null &amp;&amp;
                                retrievedDataSet.Tables != null &amp;&amp;
                                retrievedDataSet.Tables.Count > 0 &amp;&amp;
                                retrievedDataSet.Tables[0] != null &amp;&amp;
                                retrievedDataSet.Tables[0].Columns != null &amp;&amp;
                                retrievedDataSet.Tables[0].Columns.Count > 0 &amp;&amp;
                                retrievedDataSet.Tables[0].Rows != null &amp;&amp;
                                retrievedDataSet.Tables[0].Rows.Count > 0 &amp;&amp;
                                retrievedDataSet.Tables[0].Columns.Contains(parameterDefinition.KeyColumn))
                            {
                                retrievedData = retrievedDataSet.Tables[0];
                            }
                        }
                    }
                }

                if (null != retrievedData)
                {
                    // Name the display data table.
                    retrievedData.TableName = "ParamData";

                    // Verify that the table has the correct structure. 
                    EnsureDataColumns(retrievedData, parameterDefinition);

                    bool firstRowSeen = false;
                    foreach (DataRow row in retrievedData.Rows)
                    {
                        // Set the ParentKeyColumn to null because the data
                        // does not have a hierarchical structure.
                        row[parameterDefinition.ParentKeyColumn] = null;

                        // Set the IsDefaultColumn column in the first row to true.
                        row[parameterDefinition.IsDefaultColumn] = !firstRowSeen;
                        if (!firstRowSeen)
                        {
                            firstRowSeen = true;
                        }
                    }

                    // Set the column visibility.
                    SetColumnVisibility(retrievedData);
                }
            }
            
            return retrievedData;
        }

        // Adds the ShowColumn extended property to a column in the display data table
        // and sets it to true. This exposes the column in Dashboard Designer as 
        // a source value for the beginpoint. 
        private static void SetColumnVisibility(DataTable displayData)
        {
            for (int i = 0; i < displayData.Columns.Count; i++)
            {
                if (!displayData.Columns[i].ExtendedProperties.Contains("ShowColumn"))
                {
                    displayData.Columns[i].ExtendedProperties.Add("ShowColumn", true);
                }
            }
        }

        // Verify that all required columns are in the data table.
        // The data table returned by this method is expected to contain a
        // Key, ParentKey, IsDefault, Display, and an arbitrary number of
        // Value columns.
        // The specific column names (except for Value columns) are defined
        // in the filter's ParameterDefinition object, which is referenced by
        // the filter's BeginPoint property.
        private static void EnsureDataColumns(DataTable dataTable, ParameterDefinition parameterDefinition)
        {
            if (!string.IsNullOrEmpty(parameterDefinition.KeyColumn) &amp;&amp; !dataTable.Columns.Contains(parameterDefinition.KeyColumn))
            {
                dataTable.Columns.Add(parameterDefinition.KeyColumn);
            }
            if (!string.IsNullOrEmpty(parameterDefinition.DisplayColumn) &amp;&amp; !dataTable.Columns.Contains(parameterDefinition.DisplayColumn))
            {
                dataTable.Columns.Add(parameterDefinition.DisplayColumn);
            }
            if (!string.IsNullOrEmpty(parameterDefinition.ParentKeyColumn) &amp;&amp; !dataTable.Columns.Contains(parameterDefinition.ParentKeyColumn))
            {
                dataTable.Columns.Add(parameterDefinition.ParentKeyColumn);
            }
            if (!string.IsNullOrEmpty(parameterDefinition.IsDefaultColumn) &amp;&amp; !dataTable.Columns.Contains(parameterDefinition.IsDefaultColumn))
            {
                dataTable.Columns.Add(parameterDefinition.IsDefaultColumn, typeof(bool));
            }
        }

        // Returns the unique string identifier of the data provider.
        // This value must match the key that you register for this extension
        // in the CustomParameterDataProviders section in the web.config file.
        public override string GetId()
        {
            return dataProviderName;
        }

        // Returns a table of rows that match the keys in the passed
        // ParameterMessage object.
        // This method is used by controls that accept parameters, such as
        // scorecard and reports. It can also apply a Post Formula.
        public override DataTable GetMessageData(RepositoryLocation providerLocation, ParameterMessage parameterMessage, RepositoryLocation parameterSourceLocation, ParameterMapping parameterMapping, object custom)
        {   
            DataTable msgTable = null;

            // The ParameterMapping object contains information about
            // linked dashboard items.
            // The CustomData object is optionally used to store information
            // that is not stored in other properties.
            DataTable displayTable = GetDisplayDataInternal(parameterMessage, parameterSourceLocation, custom);

            if (null != displayTable)
            {
                msgTable = displayTable.Clone();
                for (int i = 0;i < parameterMessage.Values.Rows.Count; i++)
                {
                    for (int j = 0;j < displayTable.Rows.Count; j++)
                    {
                        if (!parameterMessage.Values.Rows[i][parameterMessage.KeyColumn].Equals(displayTable.Rows[j][parameterMessage.KeyColumn].ToString())) 
                            continue;

                        msgTable.ImportRow(displayTable.Rows[j]);
                        break;
                    }
                }
            }

            return msgTable;
        }
    }
}
```


## 后续步骤
<a name="bk_next"> </a>

在创建数据提供程序和筛选器编辑器（如果需要，包括其用户界面）后，部署扩展，如 [如何：手动注册 PerformancePoint Services 扩展](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)中所述。
  
    
    

## 其他资源
<a name="bk_next"> </a>


-  [如何：为 SharePoint 2013 中的 PerformancePoint Services 创建筛选器编辑器](how-to-create-filter-editors-for-performancepoint-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的 PerformancePoint Services](performancepoint-services-in-sharepoint-2013.md)
    
  

