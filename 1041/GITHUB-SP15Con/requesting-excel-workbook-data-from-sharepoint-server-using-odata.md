---
title: OData を使用して SharePoint Server から Excel ブックのデータを要求する
ms.prod: SHAREPOINT
ms.assetid: 2f846e96-6c9e-4ed2-9602-4081ad0ab135
---



# OData を使用して SharePoint Server から Excel ブックのデータを要求する

> **メモ**
> Excel Services REST API は、SharePoint 2013 および SharePoint 2016 オンプレミスに適用されます。Office 365 Education、Business、および Enterprise の各アカウントには、  [Microsoft Graph](http://graph.microsoft.io/ja-jp/docs/api-reference/v1.0/resources/excel
) エンドポイントの一部である Excel REST API を使用します。
  
    
    

OData は、URL を使用してリソースからの情報を要求します。要求している情報を返すには、クエリ オプションを使用して特定の方法で URL を作成します。次の URL は、典型的な OData 要求を示しています。
http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$top=20
  
    
    

このサンプルの OData 要求は、contoso1 サーバーの Documents フォルダーに保存されたブック ProductSales.xlsx の Table1 という名前のテーブルから最初の 20 行を取得するような構造になっています。この URL は、返す行数を指定するために、システム クエリ オプション **$top** を使用しています。URL をよく見ると、サービス ルート URI、リソースのパス、およびクエリ オプションの 3 つの部分で構成されていることがわかります。
## サービス ルート URI

URL の最初の部分はサービス ルートと呼ばれ、サーバー名以外は SharePoint 2013 サーバーに対する各 OData 要求で同じになります。これは、次の例のように、ブックが保存される SharePoint サーバーの名前とパス _vti_bin/ExcelRest.aspx を含みます。
  
    
    
http://contoso1/_vti_bin/ExcelRest.aspx
  
    
    

## リソース パス

URL の 2 番目の部分には、Excel ブックへのパスがあり、またこれが OData 要求であることを指定しています。
  
    
    
/Documents/ProductSales.xlsx/OData
  
    
    

## システム クエリ オプション

URL の 3 番目の部分は、要求のシステム クエリ オプションです。クエリ オプションは常にドル記号 ($) で始まり、URI の最後にクエリ パラメーターとして付加されます。この例では、要求は Table1 という名前のテーブルの最初の 20 行に対するものです。
  
    
    
/Table1?$top=20
  
    
    
システム クエリ オプションには、リソースから特定のデータを取得する方法が用意されています。Excel Services OData の実装では、次のセクションに示されているとおり、多くのクエリ オプションがサポートされます。
  
    
    

## システム クエリ オプション
<a name="xlsSystemQueryOptions"> </a>

OData の Excel Services の実装では、数多くの標準の OData システム クエリ オプションをサポートしています。これらのクエリ オプションは、リソースから取得する必要があるデータを指定するためにこのオプションを使用するので、OData 要求の核となります。次の表に、OData の Excel Services 実装で現在サポートしているシステム クエリ オプションを示します。
  
    
    

**表 1. Excel Services OData のシステム クエリ オプション**


|****システム クエリ オプション****|****説明****|
|:-----|:-----|
|/<tableName>  <br/> |<tableName> で指定されたテーブルのすべての行を返します。<tableName> は取得する行を含む Excel ブックのテーブルの名前です。  <br/> > **重要**> このフォームの OData 要求は同時に 500 行までを返します。500 行の各セットが 1 ページになります。500 行を超えるテーブルのさらなるページの行を取得するには、 **$skiptoken** クエリ オプションを使用します (以下を参照)。          次の例では、ProductSales.xlsx ブックの Table1 の 500 行目までのすべての行を返します。  <br/> |
|**$metadata** <br/> |指定されたブックの使用可能なすべてのテーブルと各テーブルのすべての行のタイプ情報を返します。  <br/> 次の例では、ProductSales.xlsx ブックのテーブルとテーブルのタイプ情報を返します。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/$metadata  <br/> |
|**$orderby** <br/> |**$orderby** で指定された値によって並べ替えられた指定のテーブルの行を返します。 <br/> 次の例では、ProductSales.xlsx ブックの Name 列で並べ替えられた Table 1 のすべての行を返します。  <br/> > **メモ**> **$orderby** の既定値は昇順です。          http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$orderby=Name  <br/> |
|**$top** <br/> |テーブルから N 行を返します。N は、 **$top** の値で指定された数字です。 <br/> 次の例では、ProductSales.xlsx ブックの Name 列で並べ替えられた、Table1 から最初の 5 行を返します。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$orderby=Name&amp;$top=5  <br/> |
|**$skip** <br/> |N 行をスキップします。N は **$skip** の値で指定された数字です。その後、テーブルの残りの行を返します。 <br/> 次の例では、ProductSales.xlsx ブックの Table1 から 5 行目の後の残りの行をすべて返します。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$skip=5  <br/> |
|**$skiptoken** <br/> |N 番目の行を探します。N は **$skiptoken** の値によって示される行の順序の位置です。その後、行 N + 1 で開始する残りの行をすべて返します。このコレクションはゼロベースのため、たとえば 2 行目は $skiptoken=1 で示されます。 <br/> 次の例では、ProductSales.xlsx ブックの Table1 の 2 行目の後のすべての行を返します。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$skiptoken=1  <br/> **$skiptoken** クエリ オプションを使用して、500 行を超える行を含むテーブルから最初のページより後のページの行を取得することもできます。次の例では、500 行を超えるテーブルから 500 行目以降を取得する方法を示しています。 <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$skiptoken=499  <br/> |
|**$filter** <br/> |**$filter** の値で指定された条件を満たす行のサブセットを返します。 **$filter** で使用できる演算子および関数のセットについて詳しくは、OData の [ドキュメント](http://www.odata.org/documentation/odata-version-2-0/uri-conventions/) をご覧ください。 <br/> 次の例では、Price 列の値が 100 を超えている行のみを返します。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$filter=Price gt 100  <br/> |
|**$format** <br/> |Atom XML 形式が唯一サポートされている値で、 **$format** クエリ オプションの既定となります。 <br/> |
|**$select** <br/> |**$select** で指定されたエンティティを返します。 <br/> 次の例では、ProductSales.xlsx ブックの Table1 から Name 列を選択します。  <br/> http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$select=Name  <br/> |
|**$inlinecount** <br/> | 指定されたテーブルの行数を返します。 <br/>  $ **inlinecount** は次の 2 つの値のうちの 1 つのみを使用できます。 <br/> **allpages**: テーブルのすべての行のカウントを返します。  <br/> **none**: テーブルの行のカウントを含めません。  <br/>  次の例では、ProductSales.xlsx ブックの Table1 の行の総数のカウントを返します。 <br/>  http://contoso1/_vti_bin/ExcelRest.aspx/Documents/ProductSales.xlsx/OData/Table1?$inlinecount=allpages <br/> |
   

## その他の技術情報
<a name="xlsAdditionalResources"> </a>


-  [SharePoint 2013 の Excel Services REST で OData を使用する](using-odata-with-excel-services-rest-in-sharepoint-2013.md)
    
  
-  [Excel Services の開発者のための新機能](09e96c8b-cb55-4fd1-a797-b50fbf0f9296.md)
    
  
-  [OData specification documentation](http://www.odata.org)
    
  
