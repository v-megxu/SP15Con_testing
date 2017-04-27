---
title: 如何：为 SharePoint 2013 中的 PerformancePoint Services 创建表格数据源提供程序
ms.prod: SHAREPOINT
ms.assetid: 8d734ed6-7636-40c5-a99b-bc038362cffe
---


# 如何：为 SharePoint 2013 中的 PerformancePoint Services 创建表格数据源提供程序
了解如何在自定义表格式数据源扩展名中为 PerformancePoint Services 创建数据源提供程序组件。
## 什么是 PerformancePoint Services 的自定义数据源提供程序？
<a name="bk_intro"> </a>

数据源提供程序连接到数据源、访问其数据，然后返回查询结果。PerformancePoint Services 使用表格式数据源提供程序访问来自 Excel 和 Excel Services 工作表、SharePoint 列表和 Microsoft SQL Server 表的数据。您可以创建自定义数据源提供程序以使用不受 PerformancePoint Services 支持的表格式数据源中的数据。
  
    
    
表格式数据源提供程序的主要功能是创建模拟运算表，并用来自数据源的数据填充该表。它还创建列映射以定义每个列所包含的数据的类型（事实、维度或时间维度）。这会将基本的多维结构应用到表格式数据中。
  
    
    
本主题中的程序和代码示例基于 [自定义对象示例](http://msdn.microsoft.com/library/af021d52-7562-4e7a-9de4-e1fc5784a59d%28Office.15%29.aspx)中的 **WSTabularDataSourceProvider** 类。提供程序从指定股票代号的外部 Web 服务检索股票报价。它会将历史股票报价数据储存在缓存文件中，这样就可以按时间对数据进行分割。有关类的完整代码，请参阅 [代码示例：为 SharePoint Server 2013 中的自定义 PerformancePoint Services 表格式数据源创建数据源提供程序](#bk_example)。
  
    
    
我们建议您使用示例数据源提供程序作为模板。示例中显示了如何调用 PerformancePoint Services API 中的对象，并演示了 PerformancePoint Services 开发的最佳实践。
  
    
    

## 为自定义 PerformancePoint Services 表格式数据源创建数据源提供程序
<a name="BKMK_CreateClass"> </a>


1. 安装 PerformancePoint Services，或者将您的扩展使用的 DLL（步骤 3 中列出）复制到您的计算机上。有关说明，请参阅  [开发方案中使用的 PerformancePoint Services DLL](http://msdn.microsoft.com/library/41e92619-8253-481d-82f9-35b6a6abc477%28Office.15%29.aspx)。
    
  
2. 在 Visual Studio 中，创建一个 C# 类库。如果您已为扩展创建了一个类库，请添加新 C# 类。
    
    您必须用强名称对 DLL 进行签名，此外，确保 DLL 所引用的所有程序集都具有强名称。有关如何用强名称对程序集进行签名和如何创建公钥/私钥对的信息，请参阅 [How to: Create a Public/Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114.aspx)。
    
  
3. 将以下 PerformancePoint Services DLL 作为程序集引用添加到项目中：
    
  - Microsoft.PerformancePoint.Scorecards.Client.dll
    
  
  - Microsoft.PerformancePoint.Scorecards.DataSourceProviders.Standard.dll
    
  

    示例数据源提供程序还包含对 System.Core.dll、System.ServiceModel.dll、System.Web.dll、System.Web.Services.dll 和 System.Xml.Linq.dll 的程序集引用。可能需要其他项目引用，具体取决于您的扩展名功能。
    
  
4. 添加将引用位于地址  `http://www.webservicex.net/stockquote.asmx` 的 Web 服务的名为 **StockQuotes** 的服务引用。这是为示例数据源提供股票报价的 Web 服务。
    
  
5. 将示例中的 **BasicTabularDataSourceProvider** 和 **SampleDSCacheHandler** 类添加到您的项目中。 **BasicTabularDataSourceProvider** 从 [TabularDataSourceProvider](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.aspx) 类（其为表格式数据源提供程序的基类）继承而来。
    
    示例数据源还将该类用作  [TabularDataSourceProvider](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.aspx) 不实现（ [GetDatabaseNames()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetDatabaseNames.aspx) 、 [GetCubeNames()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetCubeNames.aspx) 、 [GetCubeNameInfos()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetCubeNameInfos.aspx) 、 [GetCubeMetaData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetCubeMetaData.aspx) 和 [Validate()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.Validate.aspx) ）的已重写抽象方法的容器。
    
  
6. 在您的提供程序类中，请为以下 PerformancePoint Services 命名空间添加 **using** 指令：
    
  -  [Microsoft.PerformancePoint.Scorecards](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.aspx)
    
  
  -  [Microsoft.PerformancePoint.Scorecards.ServerCommon](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.ServerCommon.aspx)
    
  
  - **Microsoft.PerformancePoint.SDK.Samples.StockQuotes**（表示步骤 4 中创建的 StockQuotes 服务引用）
    
  

    根据您的扩展的功能，可能需要其他 **using** 指令。
    
  
7. 从 **BasicTabularDataSourceProvider** 类继承而来。
    
  
8. 声明变量，并定义用于解析、存储和检索股票代码的属性、缓存文件位置和代理服务器的 URI。
    
  
9. 重写  [IsConnectionStringSecure](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.IsConnectionStringSecure.aspx) 属性。PerformancePoint Services 不使用此属性，但是旨在自定义应用程序以可选的方式使用，以便确定连接字符串是否会公开可能带来安全性风险的信息。
    
    如果您的扩展名将敏感信息（如，用户名或密码）储存在数据源的连接字符串中，则返回 **true**。如果它不储存敏感信息或数据源不使用连接字符串，则返回 **false**。
    
  
10. 重写  [GetId()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetId.aspx) 方法以为您的提供程序返回唯一标识符。 [GetId()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetId.aspx) 必须返回与在自定义数据源提供程序的 PerformancePoint Services web.config 文件中注册的 **key** 属性相同的字符串。
    
  
11. 重写  [SetDataSource](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.SetDataSource.aspx) 方法以定义列映射。 [SetDataSource](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.SetDataSource.aspx) 调用 **CreateDataColumnMappings** 方法以将数据源列定义为 [Fact](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.MappedColumnTypes.Fact.aspx) 、 [Dimension](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.MappedColumnTypes.Dimension.aspx) 和 [TimeDimension](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.MappedColumnTypes.TimeDimension.aspx) 类型。
    
     [SetDataSource](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.SetDataSource.aspx) 还从自定义数据源对象的 [CustomData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.CustomData.aspx) 属性检索股票代码、缓存文件位置和代理服务器地址。这些值由仪表板创作者在示例数据源编辑器中定义。
    
  
12. 重写  [GetDataSet()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.GetDataSet.aspx) 方法以创建存储数据源中的数据的 [DataSet](https://msdn.microsoft.com/library/System.Data.DataSet.aspx) 对象。示例数据源提供程序使用 **FillResultsTable** 和 **GetLiveQuote** 方法，从而用 Web 服务中的数据填充模拟运算表。
    
  

## 代码示例：为 SharePoint Server 2013 中的自定义 PerformancePoint Services 表格式数据源创建数据源提供程序
<a name="bk_example"> </a>

以下代码示例中的类将创建从外部 Web 服务检索股票报价的表格式数据源提供程序，然后将数据转换成表格式格式。
  
    
    
您必须首先配置如 [为自定义 PerformancePoint Services 表格式数据源创建数据源提供程序](#BKMK_CreateClass)中所述的开发环境，然后才能编写此代码示例。
  
    
    



```cs

using System;
using System.Data;
using System.IO;
using System.Linq;
using System.Xml.Linq;
using Microsoft.PerformancePoint.Scorecards;
using Microsoft.PerformancePoint.Scorecards.ServerCommon;
using Microsoft.PerformancePoint.SDK.Samples.StockQuotes;
using System.ServiceModel;

namespace Microsoft.PerformancePoint.SDK.Samples.SampleDataSource
{

    // Represents the class that defines the sample data source provider.
    // It inherits from the BasicTabularDataSourceProvider class, which
    // contains overridden abstract methods that are not implemented.
    public class WSTabularDataSourceProvider : BasicTabularDataSourceProvider
    {
        #region Constants
        private const int StockSymbolsIndex = 0;
        private const int CacheFileLocationIndex = 1;
        private const int ProxyAddressIndex = 2;
        #endregion

        #region Properties

        // This property stores the stock symbols that are used
        // to query the Web service.
        // Its value is obtained by parsing the CustomData property
        // of the data source object. 
        private string[] StockSymbols
        {
            get;
            set;
        }

        // The address of the proxy server.
        private Uri ProxyAddress
        {
            get;
            set;
        }

        // This property is not used by PerformancePoint Services.
        // Its intended use is for custom applications to indicate
        // whether a provider stores sensitive information in the
        // connection string, such as user name and password.
        // This sample does not, so it returns false. 
        public override bool IsConnectionStringSecure
        {
            get { return false; }
        }
        #endregion

        #region Overridden methods

        // The source name for your data source. This value must match the key
        // attribute that is registered in the web.config file.
        public override string GetId()
        {
            return "WSTabularDataSource";
        }

        // Add column mappings for the sample columns if they do not exist.
        // Column mappings may be missing if the custom data source has never
        // been edited or if the workspace was not refreshed, which saves
        // changes to the server.
        public override void SetDataSource(DataSource dataSource)
        {

            base.SetDataSource(dataSource);

            // Check for symbols stored in the CustomData
            // property of the data source.
            if (null == dataSource ||
                 string.IsNullOrEmpty(dataSource.CustomData))
            {

                // Create a symbol for testing purposes.
                StockSymbols = new[] { "MSFT" };
            }
            else
            {
                string[] splitCustomData = dataSource.CustomData.Split('&amp;');
                if (splitCustomData.Length > 2)
                {
                    StockSymbols = splitCustomData[StockSymbolsIndex].ToUpper().Split(',');
                    for (int iLoop = 0; iLoop < StockSymbols.Length; iLoop++)
                    {
                        StockSymbols[iLoop] = StockSymbols[iLoop].Trim();
                    }

                    SampleDSCacheHandler.CacheFileLocation = splitCustomData[CacheFileLocationIndex];
                    ProxyAddress = new Uri(splitCustomData[ProxyAddressIndex]);
                }
            }

            // Check whether column mappings exist. Do not overwrite them.
            if (dataSource.DataTableMapping.ColumnMappings.Count == 0)
            {
                dataSource.DataTableMapping = CreateDataColumnMappings();
            }
        }

        // Get the data from the data source.
        // GetDataSet contains the core logic for the provider.
        public override DataSet GetDataSet()
        {

            // Create a dataset and a data table to store the data.
            DataSet resultSet = new DataSet();
            DataTable resultTable = resultSet.Tables.Add();

            // Define column names and the type of data that they contain. 
            resultTable.Columns.Add("Symbol", typeof(string));
            resultTable.Columns.Add("Value", typeof(float));
            resultTable.Columns.Add("P-E Ratio", typeof(float));
            resultTable.Columns.Add("Percentage Change", typeof(float));
            resultTable.Columns.Add("Date", typeof(DateTime));

            FillResultTable(ref resultTable);

            return resultSet;
        }
        #endregion

        #region Internal methods

        // Fill the data table with the stock quote values from
        // the Web service and local cache file.
        protected void FillResultTable(ref DataTable resultsTable)
        {

            // Check the sematic validity of symbols (out of scope for this sample).
            if (null != StockSymbols &amp;&amp;
                StockSymbols.Length > 0 &amp;&amp;
                !string.IsNullOrEmpty(SampleDSCacheHandler.CacheFileLocation))
            {
                try
                {
                    if (!File.Exists(SampleDSCacheHandler.CacheFileLocation))
                    {

                        // Create the cache file.
                        XDocument doc = SampleDSCacheHandler.DefaultCacheFileContent;
                        doc.Save(@SampleDSCacheHandler.CacheFileLocation);
                    }

                    // Get real-time quotes and update cache file.
                    string wsResult = GetLiveQuote();

                    SampleDSCacheHandler.UpdateXMLCacheFile(wsResult);

                    // Check if a valid cache file location exists.
                    if (SampleDSCacheHandler.CacheFileContent != null)
                    {
                        var query = from c in SampleDSCacheHandler.CacheFileContent.Elements("StockQuotes").Elements("StockQuote")
                                    where StockSymbols.Contains(c.Attribute("Symbol").Value)
                                    select c;

                        foreach (var stockQuote in query)
                        {
                            DataRow row = resultsTable.NewRow();
                            row["Symbol"] = stockQuote.Attribute("Symbol").Value;
                            row["Value"] = stockQuote.Element("Value").Value;
                            row["Percentage Change"] = stockQuote.Element("PercentageChange").Value;
                            row["Date"] = stockQuote.Element("Date").Value;

                            decimal peRatio;

                            // Handle symbols that return 'N/A' for this field.
                            if (decimal.TryParse(stockQuote.Element("PERatio").Value, out peRatio))
                            {
                                row["P-E Ratio"] = peRatio;
                            }

                            resultsTable.Rows.Add(row);
                        }
                    }
                }
                catch (Exception ex)
                {
                    ServerUtils.HandleException(ex);
                }
            }
        }

        // Get real-time quotes from the Web service.
        protected string GetLiveQuote()
        {
            EndpointAddress endpoint = new EndpointAddress("http://www.webservicex.net/stockquote.asmx");
            BasicHttpBinding binding = new BasicHttpBinding();
            binding.ReceiveTimeout = new TimeSpan(0, 0, 120);
            binding.ProxyAddress = ProxyAddress;
            binding.UseDefaultWebProxy = false;

            StockQuotes.StockQuoteSoapClient wsStockQuoteService = new StockQuoteSoapClient(binding, endpoint);

            // Check the sematic validity of symbols (out of scope for this sample).
            if (null != StockSymbols &amp;&amp;
                StockSymbols.Length > 0)
            {
                try
                {
                    string quoteRequest = StockSymbols[0];
                    for (int iLoop = 1; iLoop < StockSymbols.Length; iLoop++)
                    {
                        quoteRequest = string.Format("{0}, {1}", quoteRequest, StockSymbols[iLoop]);
                    }

                    string wsResult = wsStockQuoteService.GetQuote(quoteRequest);
                    return wsResult;
                }
                catch (Exception ex)
                {
                    ServerUtils.HandleException(ex);
                }
            }
            return string.Empty;
        }

        // Create the column mappings.
        internal static DataTableMapping CreateDataColumnMappings()
        {
            DataTableMapping dtTableMapping = new DataTableMapping();

            // Define the data in the Symbol column as dimension data.
            dtTableMapping.ColumnMappings.Add(new DataColumnMapping
            {
                SourceColumnName = "Symbol",
                FriendlyColumnName = "Symbol",
                UniqueName = "Symbol",
                ColumnType = MappedColumnTypes.Dimension,
                FactAggregation = FactAggregations.None,
                ColumnDataType = MappedColumnDataTypes.String
            });

            // Define the data in the Value column as fact data.
            dtTableMapping.ColumnMappings.Add(new DataColumnMapping
            {
                SourceColumnName = "Value",
                FriendlyColumnName = "Value",
                UniqueName = "Value",
                ColumnType = MappedColumnTypes.Fact,
                FactAggregation = FactAggregations.Average,
                ColumnDataType = MappedColumnDataTypes.Number
            });

            // Define the data in the P-E Ratio column as fact data.
            dtTableMapping.ColumnMappings.Add(new DataColumnMapping
            {
                SourceColumnName = "P-E Ratio",
                FriendlyColumnName = "P-E Ratio",
                UniqueName = "P-E Ratio",
                ColumnType = MappedColumnTypes.Fact,
                FactAggregation = FactAggregations.Average,
                ColumnDataType = MappedColumnDataTypes.Number
            });

            // Define the data in the Percentage Change column as fact data.
            dtTableMapping.ColumnMappings.Add(new DataColumnMapping
            {
                SourceColumnName = "Percentage Change",
                FriendlyColumnName = "Percentage Change",
                UniqueName = "Percentage Change",
                ColumnType = MappedColumnTypes.Fact,
                FactAggregation = FactAggregations.Average,
                ColumnDataType = MappedColumnDataTypes.Number
            });

            // Define the Date column as a time dimension.
            dtTableMapping.ColumnMappings.Add(new DataColumnMapping
            {
                SourceColumnName = "Date",
                FriendlyColumnName = "Date",
                UniqueName = "Date",
                ColumnType = MappedColumnTypes.TimeDimension,
                FactAggregation = FactAggregations.None,
                ColumnDataType = MappedColumnDataTypes.DateTime
            });

            // Increase the granularity of the time dimension.
            dtTableMapping.DateAggregationType |= DateAggregationTypes.Quarter;
            dtTableMapping.DateAggregationType |= DateAggregationTypes.Month;
            dtTableMapping.DateAggregationType |= DateAggregationTypes.Week;
            dtTableMapping.DateAggregationType |= DateAggregationTypes.Day;

            return dtTableMapping;
        }
        #endregion
    }
}

```


## 后续步骤
<a name="bk_next"> </a>

创建了数据源提供程序和数据源编辑器（包括其用户界面，如果需要）后，请部署如 [如何：手动注册 PerformancePoint Services 扩展](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)中所描述的扩展名。 
  
    
    

## 其他资源
<a name="bk_addResources"> </a>


-  [如何：为 SharePoint 2013 中的 PerformancePoint Services 创建表格数据源编辑器](how-to-create-tabular-data-source-editors-for-performancepoint-services-in-share.md)
    
  
-  [SharePoint 2013 中的 PerformancePoint Services](performancepoint-services-in-sharepoint-2013.md)
    
  

