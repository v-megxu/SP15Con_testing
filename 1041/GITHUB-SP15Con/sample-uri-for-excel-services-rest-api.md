---
title: Excel Services REST API のサンプル URI
ms.prod: SHAREPOINT
ms.assetid: 4ebe1da2-9861-416f-bef1-4a62599efe2e
---


# Excel Services REST API のサンプル URI

このトピックでは、Excel Services における REST (representational state transfer) サービス コマンドの一連のサンプル URI を紹介します。
  
    
    


> **メモ**
> Excel Services REST API は、SharePoint 2013 および SharePoint 2016 オンプレミスに適用されます。Office 365 Education、Business、および Enterprise の各アカウントには、  [Microsoft Graph](http://graph.microsoft.io/ja-jp/docs/api-reference/v1.0/resources/excel
) エンドポイントの一部である Excel REST API を使用します。
  
    
    


## Excel Services における REST コマンドのサンプル URI

以下の例では、各 URI は  *sampleWorkbook.xlsx*  という名前のブックを参照しています。
  
    
    

- sampleWorkbook.xlsx ファイルには、名前付き範囲とグラフが含まれています。
    
  
- sampleWorkbook.xlsx ファイルは、信頼できる SharePoint ドキュメント ライブラリに保存されています。この例では、sampleWorkbook.xlsx の場所へのパスは次のとおりです。
    
  ```
  
http://<ServerName>/Docs/Documents/sampleWorkbook.xlsx
  ```


### サンプル URI

Excel Services の REST サービスに対する .aspx ページは、次のとおりです。
  
    
    

```
http://<ServerName>/_vti_bin/ExcelRest.aspx

```

以下に示すのは、Excel Services の REST サービスを使用して sampleWorkbook.xlsx ブックにアクセスするためのサンプル URI です。
  
    
    

- ブックの最上位モデル (現行のビルドでは範囲とグラフのみ) を取得します。
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model

  ```

- ブック全体を取得します。
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model?$format=workbook

  ```

- 範囲を返します (既定は html)。以下の 2 つの URI サンプルは同等です。
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('Sheet1!A1|G5')

  ```


  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('Sheet1!A1|G5')?$format=html
  ```

- 名前付き範囲を取得します。
    
  ```
  http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('nameOfTheNamedRange')

  ```

- Atom XML フィードを返します。
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model?$format=atom

  ```

- セルを設定し、それを返します。
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Ranges('Sheet1!A1|G5')?Ranges('Sheet1!C3')=demo

  ```

- グラフを取得します。
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Charts('Chart 1')

  ```

- 値を設定し、グラフを取得します。
    
  ```
  
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx/model/Charts('Chart%201')?Ranges('Sheet1!A1')=5.5

  ```


