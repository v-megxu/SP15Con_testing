---
title: SharePoint 2013 の Excel Services REST で OData を使用する
ms.prod: SHAREPOINT
ms.assetid: 8a20225a-323c-4420-bbb4-eef60aed4b42
---


# SharePoint 2013 の Excel Services REST で OData を使用する
SharePoint Server 2010 に、SharePoint ドキュメント ライブラリに格納された Excel ワークブック内で情報を取得および設定するための REST API が導入されました。SharePoint Server 2013 では、Excel Services のリソースに関する情報の取得に使用できる Open Data Protocol (OData) を使用する Excel Services からデータを要求するための新しい方法が追加されています。この新しいサービスは、既存の Excel Services REST API に大きく依存しています。このトピックでは、Excel Services での OData の使用の概要について説明します。
> **メモ**
> Excel Services REST API は、SharePoint 2013 および SharePoint 2016 オンプレミスに適用されます。Office 365 Education、Business、Enterprise の各アカウントには、 [Microsoft Graph](http://graph.microsoft.io/ja-jp/docs/api-reference/v1.0/resources/excel
)エンドポイントの一部である Excel REST API を使用します。 
  
    
    


## OData とは
<a name="xlsWhatIsOdata"> </a>

OData は、データをクエリおよび更新するためのオープンな Web プロトコルです。REST 対応のアプローチを使用して、Web 上のリソースからデータを返します。つまり、ユーザーはクエリ パラメーターを含む URI を使用して、特定のリソースに関する情報を取得します。
  
    
    
OData の詳細については、Web サイトで  [Open Data Protocol 仕様](http://www.odata.org/)を参照してください。
  
    
    

## Excel Services での OData の使用方法
<a name="xlsHowUseOdata"> </a>

Excel Services では、OData を使用して、SharePoint ライブラリに格納されたワークブック内のテーブル (クエリ テーブルを含む) に関する情報を取得します。OData サービスは、要求されたデータを XML Atom 形式で返します。
  
    
    

### Excel Services への OData 要求を作成するための構文
<a name="xlsOdataSyntax"> </a>

SharePoint は、情報の要求元にできる個別リソースとして各ワークブックを公開します。本リリースの SharePoint Server では、ワークブック内のテーブルのデータのみを取得できます。
  
    
    
Excel ワークブックからデータを取得するには、ワークブックを指し、ワークブックから取得するデータとそのデータの配置方法を指定する URL を構築します。たとえば、Documents というフォルダー内の SharePoint ライブラリに格納されている ProductSales.xlsx というワークブック内の Table1 に関する情報を取得するには、次のような URL を使用します。
  
    
    
http://<serverName>/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1
  
    
    
OData を使用して SharePoint Server に格納された Excel ワークブックから情報を要求する方法の詳細については、「 [OData を使用して SharePoint Server から Excel ブックのデータを要求する](requesting-excel-workbook-data-from-sharepoint-server-using-odata.md)」を参照してください。
  
    
    

## OData が返すデータ
<a name="xlsOdataReturnData"> </a>

Excel Services への OData 要求を作成すると、XML が Atom 形式で返されます。Atom 形式は、OData の Excel Services 実装で唯一サポートされている形式です。たとえば、次の URL は、WindowsPhoneComparison.xlsx というワークブック内の先頭のテーブル (Table1) の先頭行に対する OData 要求を示します。
  
    
    
http://<serverName>/_vti_bin/ExcelRest.aspx/Documents/WindowsPhoneComparison.xlsx/odata/Table1
  
    
    
Excel Services は、次のコードに示す Atom XML を返します。
  
    
    



```XML

<?xml version="1.0" encoding="utf-8" standalone="yes"?>
<entry xml:base="http://{serverName}/_vti_bin/ExcelRest.aspx/Documents/WindowsPhoneComparison.xlsx/OData" xmlns:d="http://schemas.microsoft.com/ado/2007/08/dataservices" xmlns:m="http://schemas.microsoft.com/ado/2007/08/dataservices/metadata" m:etag="W/&amp;quot;datetime'0001-01-01T00%3A00%3A00'&amp;quot;" xmlns="http://www.w3.org/2005/Atom">
  <id>http://{serverName}/_vti_bin/ExcelRest.aspx/Documents/WindowsPhoneComparison.xlsx/OData/Table1(0)</id>
  <title type="text"></title>
  <updated>0001-01-01T00:00:00-08:00</updated>
  <author>
    <name />
  </author>
  <link rel="edit" title="Table1Item" href="/Table1(0)" />
  <category term="ExcelServices.Table1Item" scheme="http://schemas.microsoft.com/ado/2007/08/dataservices/scheme" />
  <content type="application/xml">
    <m:properties>
      <d:Phone>Samsung Focus</d:Phone>
      <d:sizeweight m:type="Edm.Double">4</d:sizeweight>
      <d:camera m:type="Edm.Double">2.5</d:camera>
      <d:battery m:type="Edm.Double">3</d:battery>
      <d:memory m:type="Edm.Double">3</d:memory>
      <d:speed m:type="Edm.Double">3</d:speed>
      <d:style m:type="Edm.Double">3</d:style>
      <d:callquality m:type="Edm.Double">3</d:callquality>
      <d:overall m:type="Edm.Double">3</d:overall>
      <d:excelRowID m:type="Edm.Int32">0</d:excelRowID>
    </m:properties>
  </content>
</entry>

```


## まとめ
<a name="xlsOdataReturnData"> </a>

OData を使用すると、SharePoint に格納された Excel ワークブックからデータを簡単に取得できます。OData では、HTTP や REST のような Web 標準に基づいた簡単な構文を使用することにより、すばやく容易に Excel ワークブックからデータを取得できます。
  
    
    

## その他の技術情報
<a name="xlsOdataAddRes"> </a>


-  [Excel Services の開発者のための新機能](09e96c8b-cb55-4fd1-a797-b50fbf0f9296.md)
    
  
-  [OData を使用して SharePoint Server から Excel ブックのデータを要求する](requesting-excel-workbook-data-from-sharepoint-server-using-odata.md)
    
  
-  [OData 仕様のドキュメント](http://www.odata.org/)
    
  

