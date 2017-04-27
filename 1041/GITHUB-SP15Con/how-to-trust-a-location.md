---
title: 方法 場所を信頼する
keywords: how to,howdoi,howto,trusted location
f1_keywords:
- how to,howdoi,howto,trusted location
ms.prod: OFFICE365
ms.assetid: 0f396c0b-f578-4d1a-9e6b-a75f352265ab
---


# 方法: 場所を信頼する

アクセスする必要のあるブックは、信頼できる場所に置かなければなりません。そうしないと、そのブックを開く呼び出しが失敗します。この例では、[SharePoint サーバーの全体管理] ページを使用して、場所を信頼する方法について説明します。 
  
    
    

別の方法として、Windows PowerShell を使用して場所を信頼することもできます。詳細については、「 [TechNet](http://technet.microsoft.com/ja-jp/library/ee428287%28office.14%29.aspx)」にある Microsoft SharePoint Server 2010 IT Pro および管理に関する資料を参照してください。 
> **ヒント**
> 管理操作の改善点と、[信頼できるファイル保存場所] ページのスクリーン ショットの詳細については、「 [SharePoint 2010 管理における Excel Services の改善点](http://blogs.msdn.com/excel/archive/2009/11/16/excel-services-in-sharepoint-2010-administration-improvements.aspx)」というブログ投稿を参照してください。 
  
    
    


### 場所を信頼するには


1. [ **スタート**] メニューで、[ **すべてのプログラム**] をクリックします。 
    
  
2. [ **Microsoft SharePoint 2010 製品**] をポイントし、[ **SharePoint 2010 サーバーの全体管理**] をクリックします。 
    
  
3. [SharePoint 2010 サーバーの全体管理] ページで、[ **アプリケーション構成の管理**] の下の [ **サービス アプリケーションの管理**] をクリックします。
    
  
4. [サービス アプリケーションの管理] ページで、[ **Excel Services Application**] をクリックします。
    
  
5. [Excel Services Application] ページで、[ **信頼できるファイル保存場所**] をクリックします。 
    
  
6. [Excel Services Application: 信頼できるファイル保存場所] ページで、[ **信頼できるファイル保存場所の追加**] をクリックします。 
    
  
7. [Excel Services Application: 信頼できるファイル保存場所の追加] ページで、[ **アドレス**] ボックスに、ブックを保存する場所を入力します。例: http:// _MyServer002_/Shared%20Documents。 
    
  
8. [ **場所の種類**] の下で、該当する場所の種類をクリックします。この例では、[ **SharePoint Foundation**] を選択してください。
    
  
9. 子のライブラリまたはディレクトリを信頼するには、[ **子の信頼**] の下で [ **子の信頼**] を選択します。
    
  
10. [ **OK**] をクリックします。
    
  

## 関連項目


#### タスク


  
    
    
 [ステップ 3: UDF を展開して有効にする](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [方法: Excel クライアントからサーバーへの保存](how-to-save-from-excel-client-to-the-server.md)
#### 概念


  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
#### その他の技術情報


  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
