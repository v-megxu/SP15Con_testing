---
title: 再利用可能な SharePoint 2013 用コンポーネントの作成
ms.prod: SHAREPOINT
ms.assetid: bb4467e2-57f0-4cf1-91b8-4d3d8d2358cb
---


# 再利用可能な SharePoint 2013 用コンポーネントの作成
Web パーツ、ワークフロー、カスタム リストなど、SharePoint 2013で構築できる重要な再利用可能コンポーネントのいくつかについて説明します。
## SharePoint 2013で再利用可能なコンポーネント
<a name="SP15Reusecomp_Reusable"> </a>

SharePoint 2013を使用すると、さまざまなアプリケーション、サイト、およびソリューションで再利用できる、リスト、Web パーツ、およびコンテンツ タイプなどの各種コンポーネントを構築できます。このセクションでは、SharePoint 2013で構築できる一般的な再利用可能コンポーネントについて概説します。このドキュメントの将来のアップデートでは、構築できるその他のコンポーネントについて説明します。
  
    
    

> **メモ**
> SharePoint アドイン で使用できるコンポーネントには、いくつかの制限事項があります。詳細については、「 [SharePoint 2013 のホスト Web、アドイン Web、および SharePoint コンポーネント](http://msdn.microsoft.com/library/b791cdf5-8aa2-47fa-bc4c-aee437354759%28Office.15%29.aspx)」を参照してください。 
  
    
    


- **Web パーツ**は、SharePoint を拡張する最も一般的な手段です。Web パーツの構築を習得することは、SharePoint の開発を始めるためのすばらしい方法です。詳細については、「 [SharePoint 2010 の開発構成要素: SharePoint アプリケーションを作成するためのテクノロジ](http://msdn.microsoft.com/library/138422cf-c140-466a-bcd8-cacba51ef886%28Office.15%29.aspx#bb2_WebParts)」を参照してください。
    
  
- SharePoint サイトの **カスタム リスト**は、データを格納する場所を提供します。SharePoint リストでのデータ操作は、幅広く使用されている手法です。リストを使用すると、プログラムによってアクセスするデータを格納できます。詳細については、「 [構成要素: リストとドキュメント ライブラリ](http://msdn.microsoft.com/library/16da8f64-f53b-4490-8636-db0e4d7a6912%28Office.15%29.aspx)」を参照してください。
    
  
- **ワークフロー**を使用すると、ビジネス プロセスをコード化および標準化することができます。ワークフローは、特定のシナリオを実装するために不可欠なツールの 1 つです。詳細については、「 [SharePoint 2013 のワークフロー](workflows-in-sharepoint-2013.md)」を参照してください。
    
  
- **外部コンテンツ タイプ**は、SharePoint 展開外からのデータを SharePoint アプリケーションで使用可能にします。詳細については、「 [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md)」を参照してください。
    
  
- リスト項目のプロトタイプである **コンテンツ タイプ**を定義できます。リスト用のコンテンツ タイプを使用する場合は、1 つのコンテンツ タイプの項目だけが含まれるようにリストを定義したり、複数のコンテンツ タイプのいずれかのタイプの項目をリストに含めることができるように指定したりできます。詳細については、「 [コンテンツ タイプについて](http://msdn.microsoft.com/library/a345a6c5-7031-46ab-a2c2-37bedc3012f4%28Office.15%29.aspx)」を参照してください。
    
  
- **列の型**および **フィールド型**を使用すると、SharePoint リストの標準化されたフィールドや列のためにリッチ メタデータを定義できます。サイト全体で使用できる特定のデータ型のサイト列を (サイト列ギャラリー内に) 定義できます。これは、データベース スキーマ設計でのドメインの定義に似ています。こうすることで、複数のリスト内の列で同じ値空間が使用されることを保証できます。詳細については、「 [ユーザー設定フィールド型](http://msdn.microsoft.com/library/1345b345-226d-443a-918f-af123a3c7b13%28Office.15%29.aspx)」を参照してください。
    
  
- **イベント レシーバー**を使用すると、たとえば、ユーザーが SharePoint のドキュメント ライブラリまたはリストで項目の追加、削除、または修正を行なう際に呼び出されるイベント ハンドラーを記述できます。詳細については、「 [構成要素: イベント処理](http://msdn.microsoft.com/library/212cf488-43cb-4250-82d5-3b962b6e56e6%28Office.15%29.aspx)」を参照してください。
    
  
- **リモート イベント レシーバー**は、SharePoint イベントの外部システムに通知する方法を提供します。イベントが発生したときに呼び出すエンドポイントとイベント プロパティを指定できます。詳細については、「 [SharePoint アドインでリモート イベント レシーバーを作成する](http://msdn.microsoft.com/library/628c6103-52f9-4d85-9464-4a6862b36640%28Office.15%29.aspx)」を参照してください。
    
  

## その他の技術情報
<a name="SP15Reusecomp_AddRes"> </a>


-  [SharePoint 2013 でのプログラミング モデル](programming-models-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 開発の概要](sharepoint-2013-development-overview.md)
    
  
-  [SharePoint 2013 のホスト Web、アドイン Web、および SharePoint コンポーネント](http://msdn.microsoft.com/library/b791cdf5-8aa2-47fa-bc4c-aee437354759%28Office.15%29.aspx)
    
  
-  [SharePoint Foundation 2010 の構成要素](http://msdn.microsoft.com/library/0d7f5106-dcbd-442e-9907-d28a323bbe11%28Office.15%29.aspx)
    
  
-  [SharePoint 2010 の開発構成要素: SharePoint アプリケーションを作成するためのテクノロジ (パート 1/2)](http://msdn.microsoft.com/library/7ef04158-d149-4301-ab91-4617677eefc4%28Office.15%29.aspx)
    
  
-  [SharePoint 2010 の開発構成要素: SharePoint アプリケーションを作成するためのテクノロジ (パート 2/2)](http://msdn.microsoft.com/library/138422cf-c140-466a-bcd8-cacba51ef886%28Office.15%29.aspx)
    
  

