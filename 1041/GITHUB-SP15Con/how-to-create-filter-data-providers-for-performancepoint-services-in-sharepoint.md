---
title: [方法] SharePoint 2013 の PerformancePoint Services 用にフィルター データ プロバイダーを作成する
ms.prod: SHAREPOINT
ms.assetid: 25508ec6-86bf-4eea-acf0-00f88e4faa55
---


# [方法] SharePoint 2013 の PerformancePoint Services 用にフィルター データ プロバイダーを作成する
PerformancePoint サービス のユーザー設定フィルター拡張機能においてデータ プロバイダー コンポーネントを作成する方法を説明します。
## PerformancePoint サービス のカスタム データ プロバイダーとは
<a name="bk_introduction"> </a>

PerformancePoint サービス では、カスタム データ プロバイダーがフィルターの基となるデータ ソースからデータを取得し、このデータの使用方法を定義します。最も重要なことは、フィルターの開始ポイントとして使用できるフィルター コントロールおよびデータに公開するためのデータ値をデータ プロバイダーが指定することです。また、データ プロバイダーには、ユーザーがフィルター コントロールから選択する値が格納されます。ユーザーが選択した値は、その後、フィルター コンシューマーに送信されます。データ プロバイダーは 2 つの  [DataTable](https://msdn.microsoft.com/library/System.Data.DataTable.aspx) オブジェクトを使用して、データの整理と格納を行います。詳細については、「 [PerformancePoint Services フィルター](http://msdn.microsoft.com/library/915382d0-3997-495c-a65a-7db3fe0b8f85%28Office.15%29.aspx)」を参照してください。
  
    
    
フィルター データ プロバイダーを作成、構成、定義する方法を示す次の手順および例は、 [カスタム オブジェクト サンプル](http://msdn.microsoft.com/library/af021d52-7562-4e7a-9de4-e1fc5784a59d%28Office.15%29.aspx)の **SampleFilterDataProvider** クラスに基づいています。エディターは、ユーザーがレポートの名前と詳細を変更できるシン Web アプリケーションです。クラスのための完全なコードについては、「 [コード例: SharePoint Server 2013 でのユーザー設定の PerformancePoint サービス フィルター用のデータ プロバイダーの作成](#bk_example)」を参照してください。
  
    
    
サンプルのデータ プロバイダーをテンプレートとして使用することをお勧めします。このサンプルは PerformancePoint サービス API 内のオブジェクトを呼び出す方法を示し、PerformancePoint サービス の開発のベスト プラクティスを紹介しています。 
  
    
    

## ユーザー設定の PerformancePoint サービス フィルター用のデータ プロバイダーの作成
<a name="bk_createconfig"> </a>


1. PerformancePoint サービス をインストールするか、拡張機能が使用する (手順 3. で示した) DLL をコンピューターにコピーします。 詳細については、「 [開発シナリオで使用される PerformancePoint Services DLL](http://msdn.microsoft.com/library/41e92619-8253-481d-82f9-35b6a6abc477%28Office.15%29.aspx)」を参照してください。
    
  
2. Visual Studio で、C# クラス ライブラリを作成します。拡張機能のためのクラス ライブラリを既に作成している場合、新しい C# クラスを追加します。
    
    DLL には厳密な名前で署名する必要があります。さらに、DLL によって参照されたすべてのアセンブリが厳密な名前を持つことを確認してください。厳密な名前でアセンブリに署名する方法の詳細、および公開/秘密キーのペアを作成する方法の詳細については、「 [How to: Create a Public/Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114.aspx)」を参照してください。
    
  
3. プロジェクトに、アセンブリ参照として以下の PerformancePoint サービス DLL を追加します。
    
  - Microsoft.PerformancePoint.Scorecards.Client.dll
    
  
  - Microsoft.PerformancePoint.Scorecards.Server.dll
    
  

    拡張機能によっては、その他のプロジェクト参照が必要になることがあります。
    
  
4. プロバイダー クラスで、以下の PerformancePoint サービス 名前空間のために **using** ディレクティブを追加します。
    
  -  [Microsoft.PerformancePoint.Scorecards](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.aspx)
    
  
  -  [Microsoft.PerformancePoint.Scorecards.Server.Extensions](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.aspx)
    
  

    拡張機能によっては、その他の **using** ディレクティブが必要になることがあります。
    
  
5.  [CustomParameterDataProvider](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.CustomParameterDataProvider.aspx) 基本クラスから継承します。
    
  
6. データ プロバイダー名の文字列識別子を設定します。これは、拡張機能を登録するときに web.config ファイルの **CustomParameterDataProviders** セクションに追加するキーと一致する必要があります。詳細については、「 [[方法] PerformancePoint Services の拡張機能を手動で登録する](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)」を参照してください。
    
  
7.  [GetId()](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.CustomParameterDataProvider.GetId.aspx) メソッドを上書きして、使用するデータ プロバイダーの識別子を返すようにします。
    
  
8.  [GetDisplayDataInternal](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.CustomParameterDataProvider.GetDisplayDataInternal.aspx) メソッドを上書きし、基盤となるデータ ソースからデータ値を格納するように [DataTable](https://msdn.microsoft.com/library/System.Data.DataTable.aspx) オブジェクトを定義します。フィルターはこのメソッドを使用して、フィルター選択コントロールのデータを設定します。表示データ テーブルには、以下の列名を含める必要があります。
    
  - **Key** レコードの一意な識別子。この値を null に指定できません。パフォーマンスとセキュリティ上の目的で、コントロールではキーのみが作成されます。他の列からの値は作成されません。
    
  
  - **Display** フィルター コントロールに表示する値。
    
  
  - **ParentKey** この値は、ツリー コントロール内の階層データの配置に使用されます。
    
  
  - **IsDefault** この値は、フィルター永続化のために使用されます。
    
    > **ヒント**
      > 列をさらに追加して、フィルターの機能を拡張できます。 

     [GetDisplayDataInternal](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.CustomParameterDataProvider.GetDisplayDataInternal.aspx) は、 [DataSourceRegistry.GetDataSource(DataSource)](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceRegistry.GetDataSource.aspx) メソッドを呼び出して、次のように、名前によってデータ ソースの種類を確認します。
    
  - データ ソース拡張機能の PerformancePoint サービス web.config ファイルに登録された **subType** 属性と同じ値のデータ ソースの [SubTypeId](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.SubTypeId.aspx) プロパティを使用して、カスタム データ ソースの種類を参照します。
    
  
  -  [DataSourceNames](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSourceNames.aspx) クラスからフィールドを返す [SourceName](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.SourceName.aspx) プロパティを使用して、ネイティブ データ ソースを参照します。
    
  
9.  [GetMessageData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.CustomParameterDataProvider.GetMessageData.aspx) メソッドを上書きして、フィルター コントロールからユーザーの選択を格納するようにします。フィルターは、ユーザーの選択をコンシューマーに送信するときに、このメソッドを使用します。
    
  

## コード例: SharePoint Server 2013 でのユーザー設定の PerformancePoint サービス フィルター用のデータ プロバイダーの作成
<a name="bk_example"> </a>

次のコード例は、データ プロバイダーが Web サービスまたは Excel ワークシートから値を取得し、フィルターの表示データおよびメッセージ データ用の  [DataTable](https://msdn.microsoft.com/library/System.Data.DataTable.aspx) オブジェクトを返す方法を示しています。
  
    
    
このコード例をコンパイルする前に、「 [プロバイダー クラスを作成して設定するには](#BKMK_ConfigClass)」で説明しているように、開発環境を設定する必要があります。
  
    
    



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


## 次の手順
<a name="bk_next"> </a>

フィルター エディター (必要な場合は、そのユーザー インターフェイスも含む) とデータ プロバイダーを作成した後、「 [[方法] PerformancePoint Services の拡張機能を手動で登録する](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)」に説明されているとおりに拡張機能を展開します。
  
    
    

## その他の技術情報
<a name="bk_next"> </a>


-  [[方法] SharePoint 2013 の PerformancePoint Services 用のフィルター エディタを作成する](how-to-create-filter-editors-for-performancepoint-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の PerformancePoint Services](performancepoint-services-in-sharepoint-2013.md)
    
  

