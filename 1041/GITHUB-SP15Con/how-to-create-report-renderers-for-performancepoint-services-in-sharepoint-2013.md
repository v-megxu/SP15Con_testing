---
title: [方法] SharePoint 2013 の PerformancePoint Services 用のレポート レンダラーを作成する
ms.prod: SHAREPOINT
ms.assetid: 642175cb-8fcb-4210-8d1e-626ad1f58bb0
---


# [方法] SharePoint 2013 の PerformancePoint Services 用のレポート レンダラーを作成する
PerformancePoint サービス のカスタム レポート拡張でレンダラー コンポーネントを作成する方法を説明します。
## PerformancePoint サービス のカスタム レポート レンダラーとは
<a name="bk_intro"> </a>

PerformancePoint サービス のカスタム レポート レンダラーは、Web パーツでカスタム レポートをレンダリングする Web サーバーのコントロールです。レンダラーは、レポート可視化 (テーブルやグラフなど) の HTML を記述し、レポートのパラメーターを処理するロジックを提供し、リポジトリーからレポート オブジェクトを取得します。
  
    
    
以下の手順とコード サンプルは、 [カスタム オブジェクト サンプル](http://msdn.microsoft.com/library/af021d52-7562-4e7a-9de4-e1fc5784a59d%28Office.15%29.aspx)からの **SampleReportRenderer** クラスに基づいています。レンダラーは、テーブルをレンダリングして、リンクされたフィルターから受信した値をそのテーブルに取り込みます。クラスの完全なコードについては、「 [コード サンプル: SharePoint Server 2013 でのカスタム PerformancePoint サービス レポートのレンダラーの作成](#bk_example)」を参照してください。
  
    
    
テンプレートとして、サンプル レポート レンダラーを使用するようお勧めします。サンプルは、PerformancePoint サービス API のオブジェクトを呼び出す方法と、PerformancePoint サービス 開発のベスト プラクティスを示しています。
  
    
    

## カスタム PerformancePoint サービス レポートのレンダラーの作成
<a name="BKMK_ConfigRenderer"> </a>


  
    
    

1. PerformancePoint サービス をインストールするか、拡張機能が使用する (手順 3 で示した) DLL をコンピューターにコピーします。詳細については、「 [開発シナリオで使用される PerformancePoint Services DLL](http://msdn.microsoft.com/library/41e92619-8253-481d-82f9-35b6a6abc477%28Office.15%29.aspx)」を参照してください。 
    
  
2. Visual Studio で、C# クラス ライブラリを作成します。拡張機能用クラス ライブラリを既に作成している場合は、新規 C# クラスを追加します。
    
    DLL には厳密な名前で署名する必要があります。 さらに、DLL によって参照されたすべてのアセンブリが厳密な名前を持つことを確認してください。厳密な名前を使用してアセンブリに署名する方法の詳細、および公開/秘密キーのペアを作成する方法の詳細については、「 [How to: Create a Public/Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114.aspx)」を参照してください。
    
  
3. 以下の PerformancePoint サービス DLL をアセンブリ参照としてプロジェクトに追加します。
    
  - Microsoft.PerformancePoint.Scorecards.Client.dll
    
  
  - Microsoft.PerformancePoint.Scorecards.Server.dll
    
  
  - Microsoft.PerformancePoint.Scorecards.Store.dll
    
  

    拡張機能の機能によっては、その他のプロジェクト参照が必要になることがあります。
    
  
4. レンダラー クラスで、次の PerformancePoint サービス 名前空間の **using** ディレクティブを追加します。
    
  -  [Microsoft.PerformancePoint.Scorecards](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.aspx)
    
  
  -  [Microsoft.PerformancePoint.Scorecards.Server.Extensions](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.aspx)
    
  
  -  [Microsoft.PerformancePoint.Scorecards.Store](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Store.aspx)
    
  

    拡張機能に応じ、その他の **using** ディレクディブが必要になることがあります。
    
  
5.  [ParameterizableControl](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.ParameterizableControl.aspx) 基本クラスから継承します。
    
  
6. リポジトリからレポート オブジェクトを取得するように、 [GetElement](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.ParameterizableControl.GetElement.aspx) メソッドを上書きします。
    
  
7. レポートのデータ セットをセットアップし、受信するパラメーター値を取得するように、 [SetData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Server.Extensions.ParameterizableControl.SetData.aspx) メソッドを上書きします。
    
  
8. レポートの視覚エフェクト用の HTML をレンダリングするように、 [Render](https://msdn.microsoft.com/library/System.Web.UI.WebControls.WebControl.Render.aspx) メソッドを上書きします。
    
  

## コード サンプル: SharePoint Server 2013 でのカスタム PerformancePoint サービス レポートのレンダラーの作成
<a name="bk_example"> </a>

以下のコードサンプルのクラスは、サンプル フィルターから渡される株価情報を表示するレポート レンダラーを作成します。
  
    
    
このコード例をコンパイルする前に、「 [レンダラー クラスを作成して構成するには](#BKMK_ConfigRR)」で説明されているとおりに開発環境を設定する必要があります。
  
    
    



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


## 次の手順
<a name="bk_next"> </a>

次の手順: レポート レンダラーとレポート エディター (必要な場合は、そのユーザー インターフェイスも含む) を作成した後、「 [[方法] PerformancePoint Services の拡張機能を手動で登録する](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)」に説明されているとおりに拡張機能を展開します。
  
    
    

## その他の技術情報
<a name="bk_addResources"> </a>


-  [[方法] SharePoint 2013 の PerformancePoint Services 用のレポート レンダラーを作成する](how-to-create-report-renderers-for-performancepoint-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の PerformancePoint Services](performancepoint-services-in-sharepoint-2013.md)
    
  

