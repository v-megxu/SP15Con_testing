---
title: SharePoint 2013 BCS REST API リファレンス
ms.prod: SHAREPOINT
ms.assetid: 364fb8d7-87d9-4be7-affd-90caba3cd0c0
---



# SharePoint 2013 BCS REST API リファレンス

  
    
    
![クラス ライブラリおよびリファレンス](images/mod_icon_badge_reference.png)
  
    
    

  
    
    

  
    
    
Representation State Transfer (REST) URL を構築して、SharePoint 2013の Business Connectivity Services (BCS) を使用して外部データ ソースに対するアクセスと操作を行うための参照情報を示します。
## SharePoint 2013 で外部データへアクセスするための REST 対応 API の使用
<a name="bkmk_Overview"> </a>

SharePoint 2013 によって提供される REST インターフェイスを使用すれば、特別に構築された URL を介して大部分の SharePoint 2013 リソースにアクセスできます。Business Connectivity Services (BCS) では、このアーキテクチャを使用して外部データにアクセスします。
  
    
    
外部データには、標準的なリスト アイテムにアクセスする場合と同様に URL を作成することでアクセスできます。
  
    
    

> **メモ**
> BDC を使用してエンティティに直接アクセスすることはできません。外部データを操作するには、外部リストを作成してから、REST URL を使用してその外部リストに含まれるリスト アイテムにアクセスします。 
  
    
    

外部リストを操作するためにサポートされている HTTP 動詞は、 **GET**、 **PUT**、 **POST**、および **DELETE** です。
  
    
    
通常のリストとは異なり、外部リストは REST を使用して作成することはできません。それを行うには、Visual Studio 2012 を使用して BDC モデルと外部リストを作成します。
  
    
    
表 1 は REST 対応の URL と、それに対応する外部データ ソースからデータへのアクセスや操作をするために呼び出すクライアント オブジェクト モデルの作成方法を示します。
  
    
    

**表 1. 外部データ アクセスのための REST 対応 URL の形式**


|**URL**|**説明**|**HTTP メソッド**|
|:-----|:-----|:-----|
| `http://[sharepointsite]/_api` <br/> |すべての REST リクエストの基礎です。_api 仮想ディレクトリは、クライアント オブジェクト モデルが使用される client.svc への呼び出しにマッピングされます。  <br/> |GET  <br/> |
| `http://[sharepointsite]/_api/web/title` <br/> |現在の Web のタイトルを取得します。  <br/> |GET  <br/> |
| `http://[sharepointsite]/_api/lists` <br/> |サイトのすべてのリストを取得します。  <br/> |GET  <br/> |
| `http://[sharepointsite]/_api/lists/getbytitle('listname')` <br/> |指定したリストのメタデータを取得します。  <br/> |GET  <br/> |
| `http://[sharepointsite]/_api/lists/getbytitle('listname')/items` <br/> |指定したリスト内のリスト項目を取得します。  <br/> |GET  <br/> |
| `http://[sharepointsite]/_api/lists/getbytitle('listname')?select=Title` <br/> |指定したリストのタイトルを取得します。  <br/> |GET  <br/> |
   

## データをフィルタリングするためのクエリ文字列の作成
<a name="bkmk_constructquery"> </a>

返されるデータ量を制限する場合、またはそのデータ量をユーザーにより深く関連させる場合には、表 2 に示したフィルター演算子を使用できます。
  
    
    

**表 2. データをフィルタリングするための演算子**


|**演算子**||
|:-----|:-----|
|EQ  <br/> |等しい  <br/> *メモ* <br/> **EQ** を使用してフィルタリングを実行すると、フィルター条件は、サーバー上でフィルタリングが実行される外部システムに渡されます。          |
|GT  <br/> |より大きい  <br/> *メモ* <br/> **GT** 演算子を使用すると、クライアント側のフィルタリングのみが実行されます。 <br/> 例:  `web/lists/getByTitle('ListName')/Items?$select=Title&amp;$filter=AverageRating gt 3` は、平均レートが 3 を超えるすべてのタイトルを返します。          |
   

> **メモ**
> 関連付けの一部である列を取得するには、クエリ文字列に **$select** を使用して、URL にその列を明示的に含める必要があります。
  
    
    


## その他の技術情報
<a name="bkmk_AdditionalResources"> </a>


-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 REST エンドポイントを使用して基本的な操作を完了する](http://msdn.microsoft.com/library/e3000415-50a0-426e-b304-b7de18f2f7d9%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 REST サービスを使用したプログラミング](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  
-  [SharePoint 2013: アプリで REST を使用して、基本的なデータアクセス操作を実行する](http://code.msdn.microsoft.com/SharePoint-2013-Perform-335d925b)
    
  
-  [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の JavaScript ライブラリ コードを使用して基本的な操作を完了する](http://msdn.microsoft.com/library/29089af8-dbc0-49b7-a1a0-9e311f49c826%28Office.15%29.aspx)
    
  
