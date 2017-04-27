---
title: 基本的な URI 構造およびパス
ms.prod: SHAREPOINT
ms.assetid: d73cf6c2-0677-4726-8a3e-2ad130e1a12c
---


# 基本的な URI 構造およびパス

このトピックでは、Excel Services で REST サービスのコマンドの URI 構造とパスを構築する方法を説明します。
  
    
    


> **メモ**
> Excel Services REST API は、SharePoint 2013 および SharePoint 2016 オンプレミスに適用されます。Office 365 Education、Business、および Enterprise の各アカウントには、 [Microsoft Graph](http://graph.microsoft.io/ja-jp/docs/api-reference/v1.0/resources/excel
) エンドポイントの一部である Excel REST API を使用します。
  
    
    


## URL の基本構造およびパス

Excel Services の REST API を使用すると、直接 URL を介してブック内のグラフ、ピボットテーブル、表、名前付き範囲などのリソースにアクセスできます。Excel Services の各 REST URL は 3 つのパーツでできています。ブック内のリソースにアクセスする URL の基本構造を次に示します。
  
    
    

1. **REST aspx ページの URI**.aspx ページのエントリ ポイント
    
  
2. **ブックの場所** ブックへのパス
    
  
3. **リソースの場所** ブック内の要求されたリソースのパス
    
  
ブック内の特定の要素に対する REST URL の構造を次に示します。
  
    
    



```

http://<ServerName>/_vti_bin/ExcelRest.aspx/<DocumentLibrary>/<FileName>/<ResourceLocation>
```

次は、3 つのパーツすべてを組み合わせると Excel Services の REST URL がどのように見えるかの例です。この例では、"SampleChart" というグラフを含む "sampleWorkbook.xlsx" というブックにアクセスします。
  
    
    



```
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Charts('SampleChart')
```

ブックはドキュメント ライブラリに格納されます。ブックへの完全パスは  `http://` _<ServerName>_ `/Docs/Documents/sampleWorkbook.xlsx` です。
  
    
    
REST URL の 3 つのパーツは次のとおりです。
  
    
    

1. **REST aspx ページの URI**: `http://` _<ServerName>_ `/_vti_bin/ExcelRest.aspx`
    
  
2. **ブックの場所**: `/Docs/Documents/sampleWorkbook.xlsx`
    
  
3. **リソースの場所**: `/model/Ranges('nameOfTheNamedRange')`
    
  

### 探索ユーザー インターフェイスを使用したアクセス

グラフには、探索ユーザー インターフェイスを使用してアクセスすることもできます。次のスクリーン ショットに示すように、探索メカニズムを使用してグラフ、表、ピボットテーブル、範囲などのリソースにアクセスする方法について知るには、「 [Excel Services REST API での検出](discovery-in-excel-services-rest-api.md)」を参照してください。
  
    
    

  
    
    
![Excel Services REST モデル URL](images/SharePointServer14Con_XLSvcs_RESTModel.gif)
  
    
    

  
    
    

  
    
    

  
    
    

### マーカーのパス

Excel Services の REST サービスの aspx ページは次のとおりです。
  
    
    

```
http://<ServerName>/_vti_bin/ExcelRest.aspx
```

Excel Services の REST サービスにアクセスするには、URL の前に  `http://` _<ServerName>_ `/_vti_bin/ExcelRest.aspx` を追加します。
  
    
    

### ブックの場所

ブックの場所は、アクセスしようと考えているリソースがあるブックへの相対パスです。たとえば、信頼できる SharePoint ドキュメント ライブラリに保存された、sampleWorkbook.xlsx という名前のブックがあるとします。この場合、sampleWorkbook.xlsx の場所へのパスは次のとおりです。
  
    
    

```
http://<ServerName>/Docs/Documents/sampleWorkbook.xlsx
```

ブック ( `Docs/Documents/sampleWorkbook.xlsx`) の相対パスを、マーカー パスの後に追加します。マーカー パスとブックの場所が後に追加された URL は次のとおりです。
  
    
    



```
http://<ServerName>/_vti_bin/ExcelRest.aspx
```


### リソースの場所

リソースの場所は、ブック内の要求する要素へのパスです。たとえば、グラフを取得する場合、リソースの場所は  `/model/Charts('Chart 1')` のようになります。
  
    
    
完全な URL では、これをブックへのマーカー パスおよび相対パスの後に追加します。完全な URL の例は次のとおりです。
  
    
    



```
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Charts('Chart 1')

```


## 関連項目


#### 概念


  
    
    
 [Excel Services REST API のリソース URI](resources-uri-for-excel-services-rest-api.md)
  
    
    
 [Excel Services REST API での検出](discovery-in-excel-services-rest-api.md)
