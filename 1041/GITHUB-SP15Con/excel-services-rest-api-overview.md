---
title: Excel Services REST API の概要
ms.prod: OFFICE365
ms.assetid: 5872f311-e180-4578-ac80-2519c1081951
---


# Excel Services REST API の概要

Excel Services の REST API は、Microsoft SharePoint Server 2010 の新機能です。REST API を使用すると、URL を介してブックのパーツや要素に直接アクセスできます。
  
    
    


> **メモ**
> Excel Services REST API は、SharePoint 2013 および SharePoint 2016 オンプレミスに適用されます。Office 365 Education、Business、および Enterprise の各アカウントには、 [Microsoft Graph](http://graph.microsoft.io/ja-jp/docs/api-reference/v1.0/resources/excel) エンドポイントの一部である Excel REST API を使用します。
  
    
    


REST サービスは、次の 2 つの要件に基づいています。
  
    
    


- ネットワーク リソースを検索するために使用するアドレス指定方式
    
  
- これらのリソースを表現したものを返すための手法
    
  
REST サービスは、リソースを中心にしています。REST では、データはリソースに分割され、各リソースには URL が与えられ、リソースに対する標準的な操作が実装されます。これらを利用すると、作成、取得、更新、削除などの操作を実現できます。
> **メモ**
> REST サービスとカスタム Web サービスの違いに関する詳細は、「 [カスタム サービスまたは RESTful サービス](http://msdn.microsoft.com/ja-jp/magazine/dd882522.aspx)」を参照してください。 
  
    
    

Excel Services の REST API を使用すると、HTTP 標準で指定された操作を使用して Excel ブックに対する操作を実行できます。これは、Excel Services の内容にアクセスして操作するための、柔軟で、セキュリティで保護され、シンプルなメカニズムとなります。さらに、Excel Services の REST API に組み込まれた検出メカニズムを使用すると、特定のブックに存在する要素に関する情報を指定した  [Atom](http://tools.ietf.org/html/rfc4287) フィードを提供することにより、開発者やユーザーは、ブックの内容を手動で、またはプログラムを使用して探索することができます。REST API を通じてアクセスできるリソースの例としては、グラフ、ピボット テーブル、テーブルなどがあります。REST API によって提供される Atom フィードを使用すると、関心のあるデータを取得するのが容易になります。フィードに含まれる要素を詳細に調べれば、少しのコードにより、ブック内に存在する要素を検索できます。Excel Services における REST サービスへのアクセスや REST サービスのサンプル URI の取得については、「 [基本的な URI 構造およびパス](basic-uri-structure-and-path.md)」および「 [Excel Services REST API のサンプル URI](sample-uri-for-excel-services-rest-api.md)」を参照してください。
