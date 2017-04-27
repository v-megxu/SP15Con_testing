---
title: VSS リクエスターと SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 0b2e5a4e-40f0-4ccf-a21a-7274921f2169
---


# VSS リクエスターと SharePoint 2013
 **概要:** ボリューム シャドウ コピー サービス (VSS) システムのリクエスター システムがどのように Microsoft SharePoint 2013 と連携するかについて説明します。
Windows Server の VSS は、Microsoft SharePoint Foundation をバックアップおよび復元するアプリケーションの作成に使用できます。VSS は、サードパーティ ストレージ管理プログラム、ビジネス プログラム、およびハードウェア プロバイダーを連携させてシャドウ コピーを作成および管理することを可能にするインフラストラクチャを提供します。このインフラストラクチャに基づくソリューションはシャドウ コピー (ミラー コピー) を使用して、1 つ以上の SharePoint Foundation データベースをバックアップおよび復元することができます。
  
    
    


## VSS リクエスター システム

VSS は、リクエスター (バックアップ アプリケーション)、ライター (SharePoint Foundation や Microsoft SQL Server などの Windows アプリケーション)、およびプロバイダー (シャドウ コピーを作成するシステム、ソフトウェア、またはハードウェア コンポーネント) の間の通信を調整します。VSS 機能を使用して SharePoint Foundation をバックアップするには、バックアップ プログラムに、SharePoint Foundation を認識している VSS リクエスターが含まれる必要があります。Windows Server で提供されているバックアップ プログラムにはこうしたリクエスターが存在しないため、組織はサードパーティ バックアップ アプリケーションを使用する必要があります。
  
    
    
SharePoint Foundation に準拠するには、VSS に基づくバックアップ アプリケーションは、シャドウ コピー バックアップの整合性と回復可能性を確保するための 2 つの基本要件に従う必要があります。顧客は、このトピックに一覧表示された SharePoint Foundation の準拠要件をバックアップ アプリケーションが満たしていることを、バックアップ ベンダーに確認する必要があります。
  
    
    
SharePoint Foundation データベースの整合性と回復可能性を確保するためにシャドウ コピー バックアップ アプリケーションが従う必要がある SharePoint Foundation 要件は、以下のとおりです。 
  
    
    

- SharePoint Foundation データベースおよび検索インデックス ファイルは、SPF-VSS ライターによって排他的にバックアップする必要があります。 
    
  
- バックアップ アプリケーションは、シャドウ コピー バックアップ セットの整合性を検証する必要があります。元の場所への復元操作は、SPF-VSS ライターによって排他的に行う必要があります。
    
  

## 復元

復元を実行する前に、以下の条件を満たす必要があります。
  
    
    

- 以下のサービスを *開始*  する必要があります。
    
  - SharePoint VSS ライター
    
  
  - ボリューム シャドウ コピー
    
  
  - SharePoint トレース
    
  
- 以下のサービスを *停止*  する必要があります。
    
  - SharePoint 管理
    
  
  - SharePoint 検索
    
  
  - SharePoint タイマー
    
  
  - SharePoint Server Search (SharePoint Server がインストールされている場合)
    
  
- ファーム全体を復元する場合は、SharePoint Foundation *および Internet Information Server (IIS)*  をシャットダウンする必要があります。
    
  
- 選択された Web アプリケーションまたはその他のコンポーネントのみを復元する場合は、Web アプリケーションをシャットダウンする必要があり、復元中にコンポーネントを使用することはできません。
    
  

## 次の手順
<a name="Next"> </a>

SharePoint 2013 の VSS リクエスターを作成および使用する方法について説明します。
  
    
    

-  [SharePoint 2013 で使用する VSS リクエスターを作成する方法](how-to-create-a-vss-requestor-for-use-with-sharepoint-2013.md)
    
  
-  [VSS リクエスターを使用して SharePoint 2013 のバックアップと復元を行う方法](how-to-back-up-and-restore-sharepoint-2013-using-a-vss-requestor.md)
    
  
-  [VSS を使用して SharePoint 2013 で検索サービス アプリケーションをバックアップおよび復元する方法](how-to-back-up-and-restore-a-search-service-application-in-sharepoint-2013-using.md)
    
  

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 およびボリューム シャドウ コピー サービスの概要](overview-of-sharepoint-2013-and-the-volume-shadow-copy-service.md)
    
  
-  [SharePoint 2013 で使用する VSS リクエスターを作成する方法](how-to-create-a-vss-requestor-for-use-with-sharepoint-2013.md)
    
  
-  [VSS リクエスターを使用して SharePoint 2013 のバックアップと復元を行う方法](how-to-back-up-and-restore-sharepoint-2013-using-a-vss-requestor.md)
    
  
-  [VSS を使用して SharePoint 2013 で検索サービス アプリケーションをバックアップおよび復元する方法](how-to-back-up-and-restore-a-search-service-application-in-sharepoint-2013-using.md)
    
  

