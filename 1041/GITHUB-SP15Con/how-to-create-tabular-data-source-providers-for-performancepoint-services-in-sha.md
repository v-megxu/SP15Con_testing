---
title: [方法] SharePoint 2013 で PerformancePoint Services 用の表形式のデータ ソース プロバイダーを作成する
ms.prod: SHAREPOINT
ms.assetid: 8d734ed6-7636-40c5-a99b-bc038362cffe
---


# [方法] SharePoint 2013 で PerformancePoint Services 用の表形式のデータ ソース プロバイダーを作成する
PerformancePoint サービス のユーザー設定の表形式データ ソース拡張機能のデータ ソース プロバイダー コンポーネントを作成する方法を確認します。
## PerformancePoint サービス のユーザー設定のデータ ソース プロバイダーの概要
<a name="bk_intro"> </a>

データ ソース プロバイダーは、データ ソースに接続し、そのデータにアクセスして、クエリ結果を返します。PerformancePoint サービス は、表形式のデータ ソース プロバイダーを使用して、Excel および Excel Services ワークシート、SharePoint リスト、Microsoft SQL Server テーブルのデータにアクセスします。カスタム データ ソース プロバイダーを使用して、PerformancePoint サービス でサポートされていない表形式のデータ ソースのデータを使用できます。
  
    
    
表形式のデータ ソース プロバイダーの主な機能は、データ テーブルを作成して、それにデータ ソースのデータを入力することです。さらに列のマッピングを作成し、各列に含まれるデータの型 (ファクト、ディメンション、時間ディメンション) を定義します。これにより、基本的な多次元構造が表形式のデータに適用されます。
  
    
    
このトピックの手順とコード例は、 [カスタム オブジェクト サンプル](http://msdn.microsoft.com/library/af021d52-7562-4e7a-9de4-e1fc5784a59d%28Office.15%29.aspx)の **WSTabularDataSourceProvider** クラスに基づいています。プロバイダーは、指定された株式シンボル用の外部 Web サービスから株式を取得します。プロバイダーは株式の履歴データをキャッシュ ファイルに格納します。これによりデータは時間単位で分割できます。クラスの完全なコードは、「 [コード例: SharePoint Server 2013のユーザー設定の PerformancePoint サービス の表形式データ ソースのデータ ソース プロバイダーを作成する](#bk_example)」を参照してください。
  
    
    
テンプレートとして、サンプルのデータ ソース プロバイダーを使用することをお勧めします。サンプルは、PerformancePoint サービス API のオブジェクトを呼び出す方法と、PerformancePoint サービス 開発のベスト プラクティスを示します。
  
    
    

## ユーザー設定の PerformancePoint サービス 表形式のデータ ソースのデータ ソース プロバイダーを作成する
<a name="BKMK_CreateClass"> </a>


1. PerformancePoint サービス をインストールするか、拡張機能が使用する (手順 3. で示した) DLL をコンピューターにコピーします。方法は、「 [開発シナリオで使用される PerformancePoint Services DLL](http://msdn.microsoft.com/library/41e92619-8253-481d-82f9-35b6a6abc477%28Office.15%29.aspx)」を参照してください。
    
  
2. Visual Studio で、C# クラス ライブラリを作成します。拡張機能のためのクラス ライブラリを既に作成している場合、新しい C# クラスを追加します。
    
    DLL には厳密な名前で署名する必要があります。さらに、DLL によって参照されたすべてのアセンブリが厳密な名前を持つことを確認してください。厳密な名前を使用してアセンブリに署名する方法の詳細、および公開/秘密キーのペアを作成する方法の詳細については、「 [How to: Create a Public/Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114.aspx)」を参照してください。
    
  
3. プロジェクトに、アセンブリ参照として以下の PerformancePoint サービス DLL を追加します。
    
  - Microsoft.PerformancePoint.Scorecards.Client.dll
    
  
  - Microsoft.PerformancePoint.Scorecards.DataSourceProviders.Standard.dll
    
  

    サンプル データ ソース プロバイダーには、System.Core.dll、System.ServiceModel.dll、System.Web.dll、System.Web.Services.dll、および System.Xml.Linq.dll へのアセンブリ参照も含まれます。拡張機能の機能によっては、その他のプロジェクト参照が必要になることがあります。
    
  
4. アドレス  `http://www.webservicex.net/stockquote.asmx` にある Web サービスを参照する **StockQuotes** という名前のサービス参照を追加します。これは、サンプル データ ソース用の株価を提供する Web サービスです。
    
  
5. サンプルの **BasicTabularDataSourceProvider** クラスおよび **SampleDSCacheHandler** クラスをプロジェクトに追加します。 **BasicTabularDataSourceProvider** は、表形式のデータ ソース プロバイダーの基本クラスである [TabularDataSourceProvider](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.aspx) クラスから継承します。
    
    サンプル データ ソースは、 [TabularDataSourceProvider](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.aspx) が実装しない無効にされた抽象メソッド ( [GetDatabaseNames()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetDatabaseNames.aspx) 、 [GetCubeNames()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetCubeNames.aspx) 、 [GetCubeNameInfos()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetCubeNameInfos.aspx) 、 [GetCubeMetaData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetCubeMetaData.aspx) 、および [Validate()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.Validate.aspx) ) のコンテナーとしてクラスを使用します。
    
  
6. プロバイダー クラスで、以下の PerformancePoint サービス 名前空間のために **using** ディレクティブを追加します。
    
  -  [Microsoft.PerformancePoint.Scorecards](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.aspx)
    
  
  -  [Microsoft.PerformancePoint.Scorecards.ServerCommon](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.ServerCommon.aspx)
    
  
  - **Microsoft.PerformancePoint.SDK.Samples.StockQuotes** (手順 4. で作成された StockQuotes サービス参照を表します)
    
  

    拡張機能の機能によっては、その他の **using** ディレクティブが必要になることがあります。
    
  
7. **BasicTabularDataSourceProvider** クラスから継承します。
    
  
8. 変数を宣言し、株式シンボルの解析、格納、取得に使用するプロパティ、キャッシュ ファイルの場所、プロキシ サーバーの URI を定義します。
    
  
9.  [IsConnectionStringSecure](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.IsConnectionStringSecure.aspx) プロパティを上書きします。このプロパティは PerformancePoint サービス には使用されません。このプロパティは、セキュリティ リスクをもたらす情報を接続文字列が公開するかどうかを特定するために、カスタム アプリケーションが任意に使用します。
    
    拡張機能によってユーザー名、パスワードなどの機密情報がデータ ソースの接続文字列に格納される場合は、 **true** を返します。機密情報が格納されないか、データ ソースで接続文字列が使用されない場合は、 **false** を返します。
    
  
10.  [GetId()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetId.aspx) メソッドを上書きして、プロバイダー用の一意の識別子を返します。 [GetId()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.CustomDataSourceProvider.GetId.aspx) は、カスタム データ ソース プロバイダー用の PerformancePoint サービス web.config ファイルに登録されている **key** 属性と同じ文字列を返す必要があります。
    
  
11.  [SetDataSource](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.SetDataSource.aspx) メソッドを上書きして、列のマッピングを定義します。 [SetDataSource](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.SetDataSource.aspx) は、 **CreateDataColumnMappings** メソッドを呼び出し、 [Fact](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.MappedColumnTypes.Fact.aspx) 、 [Dimension](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.MappedColumnTypes.Dimension.aspx) 、 [TimeDimension](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.MappedColumnTypes.TimeDimension.aspx) の型としてデータ ソース列を定義します。
    
     [SetDataSource](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.SetDataSource.aspx) はさらに、株式シンボル、キャッシュ ファイルの場所、およびプロキシ alsoサーバー アドレスを、ユーザー設定のデータ ソース オブジェクトの [CustomData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.CustomData.aspx) プロパティから取得します。これらの値は、サンプル データ ソース エディターのダッシュボード作成者によって定義されます。
    
  
12.  [GetDataSet()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceProviders.TabularDataSourceProvider.GetDataSet.aspx) メソッドを上書きして、データ ソースのデータを格納する [DataSet](https://msdn.microsoft.com/library/System.Data.DataSet.aspx) オブジェクトを作成します。サンプル データ ソース プロバイダーは **FillResultsTable** メソッドおよび **GetLiveQuote** メソッドを使用して、データ テーブルに Web サービスからのデータを入力します。
    
  

## コード例: SharePoint Server 2013のユーザー設定の PerformancePoint サービス の表形式データ ソースのデータ ソース プロバイダーを作成する
<a name="bk_example"> </a>

以下のコード例のクラスでは、外部 Web サービスから株価を取得する表形式のデータ ソース プロバイダーを作成し、データを表形式に変換します。
  
    
    
このコード例をコンパイルするには、「 [ユーザー設定の PerformancePoint サービス 表形式のデータ ソースのデータ ソース プロバイダーを作成する](#BKMK_CreateClass)」に示されているとおりに開発環境を構成する必要があります。
  
    
    



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


## 次の手順
<a name="bk_next"> </a>

次の手順: データ ソース プロバイダーとデータ ソース エディター (必要に応じて、ユーザー インターフェイスも) を作成したら、「 [[方法] PerformancePoint Services の拡張機能を手動で登録する](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)」で説明されているように、拡張機能を展開します。 
  
    
    

## その他の技術情報
<a name="bk_addResources"> </a>


-  [[方法] SharePoint 2013 の PerformancePoint Services 用に表形式のデータ ソース エディタを作成する](how-to-create-tabular-data-source-editors-for-performancepoint-services-in-share.md)
    
  
-  [SharePoint 2013 の PerformancePoint Services](performancepoint-services-in-sharepoint-2013.md)
    
  

