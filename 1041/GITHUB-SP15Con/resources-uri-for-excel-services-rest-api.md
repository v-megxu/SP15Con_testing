---
title: Excel Services REST API のリソース URI
ms.prod: SHAREPOINT
ms.assetid: 79f95305-ec9e-4842-b937-85f66ced98e4
---


# Excel Services REST API のリソース URI

Excel Services の REST API を使用して直接エンティティにリンクできます。
  
    
    


> **メモ**
> Excel Services REST API は、SharePoint 2013 および SharePoint 2016 オンプレミスに適用されます。Office 365 Education、Business、および Enterprise の各アカウントには、 [Microsoft Graph](http://graph.microsoft.io/ja-jp/docs/api-reference/v1.0/resources/excel
) エンドポイントの一部である Excel REST API を使用します。
  
    
    


## ベース REST URL

ブック内の特定の要素に対する REST URL の例を以下に示します。
  
    
    

```

http://<ServerName>/_vti_bin/ExcelRest.aspx/<DocumentLibrary>/<FileName>/<ResourceLocation>
```

相対 REST URL はベース REST URL に基づきます。特定のブックに対するベース REST URL の例を以下に示します。
  
    
    



```
http://<ServerName>/_vti_bin/ExcelRest.aspx/<DocumentLibrary>/<FileName>
```

たとえば、次のドキュメント ライブラリに「sampleWorkbook.xlsx」という名前のブックがある場合、
  
    
    



```
http://<ServerName>/Docs/Documents/sampleWorkbook.xlsx
```

ブックに対するベース REST URL は次のとおりです。
  
    
    



```
http://<ServerName>/_vti_bin/ExcelRest.aspx/Docs/Documents/sampleWorkbook.xlsx
```


## リソース URI

表 1 は、Excel Services の REST API にあるすべてのアクセス可能なリソースを示しています。特定のリソースにアクセスするには、ブックに対するベース REST URL の末尾にリソースの場所を付加します。
  
    
    

**表 1. Excel Services の REST API でアクセス可能なリソース**


|****リソースの場所****|****形式****|****例****|****メモ****|
|:-----|:-----|:-----|:-----|
|/model  <br/> |Atom (既定)  <br/> |/model  <br/> |Excel Services の REST API がサポートするリソースが付いた Atom フィードを返します。サポートされているリソースは、範囲、グラフ、表、ピボット テーブルです。  <br/> |
|/model  <br/> |workbook  <br/> |/model?$format=workbook  <br/> |これはブックです。サポートするブックの形式は xlsx、xlsb、xlsm です。  <br/> |
|/model/Ranges  <br/> |Atom (既定)  <br/> |/model/Ranges?$format=atom  <br/> |ブック内の名前付き範囲をすべて一覧表示する Atom フィードです。  <br/> |
|/model/Ranges('[Name]')  <br/> |HTML (既定)  <br/> |/model/Ranges('MyRange')?$format=html  <br/> |要求された範囲の HTML フラグメントです。  <br/> |
|/model/Ranges('[Name]')  <br/> |Atom  <br/> |/model/Ranges('MyRange')?$format=atom  <br/> |範囲内のデータの XML 表現を含む Atom エントリです。  <br/> |
|/model/Charts  <br/> |Atom (既定)  <br/> |/model/Charts?$format=atom  <br/> |ブック内のグラフをすべて一覧表示する Atom フィードです。  <br/> |
|/model/Charts('[Name]')  <br/> |Image (既定)  <br/> |/model/Charts('MyChart')?$format=image  <br/> |グラフのイメージです。イメージはポータブル ネットワーク グラフィックス (PNG) 形式です。  <br/> |
|/model/Tables  <br/> |Atom (既定)  <br/> |/model/Tables?$format=atom  <br/> |ブックのすべての利用可能なテーブルを一覧表示する Atom フィードです。  <br/> |
|/model/Tables('[Name]')  <br/> |HTML (既定)  <br/> |/model/Tables('MyTable')?$format=html  <br/> |要求されたテーブルの HTML フラグメントです。  <br/> |
|/model/Tables('[Name]')  <br/> |Atom  <br/> |/model/Tables('MyTable')?$format=atom  <br/> |テーブル内のデータの XML 表現が含まれる Atom エントリです。  <br/> |
|/model/PivotTables  <br/> |Atom (既定)  <br/> |/model/PivotTables?$format=atom  <br/> |ブック内に使用可能なピボットテーブルをすべて一覧表示する Atom フィードです。  <br/> |
|/model/PivotTables('[Name]')  <br/> |HTML (既定)  <br/> |/model/PivotTables('MyPivotTable)?$format=html  <br/> |要求されたピボットテーブルの HTML フラグメントです。  <br/> |
|/model/PivotTables('[Name]')  <br/> |Atom  <br/> |/model/PivotTables('MyPivotTable')?$format=atom  <br/> |ピボットテーブル内のデータの XML 表記が含まれる Atom エントリです。  <br/> |
   

> **メモ**
> Excel Services は、URL に含めることのできる範囲の最大数を 10 としています。10 より多くの範囲を URL に含めると、サービスが使用できないことを示すエラーが表示されます。 
  
    
    


## 関連項目


#### 概念


  
    
    
 [基本的な URI 構造およびパス](basic-uri-structure-and-path.md)
