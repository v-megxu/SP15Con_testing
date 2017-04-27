---
title: SharePoint 2013 開発の概要
ms.prod: SHAREPOINT
ms.assetid: f86e2695-4d7a-4fc5-bc23-689de96c4b06
---


# SharePoint 2013 開発の概要
SharePoint 2013は、SharePoint アドインおよび ファーム ソリューションのための開発プラットフォームです。SharePoint 2013の各種機能について詳しく学び、開発を開始しましょう。
## SharePoint 2013開発プラットフォームの概要
<a name="bk_introduction"> </a>

SharePoint 2013は、多様なニーズに対応するさまざまなスコープを持つアドインとソリューションを構築するための用途の広い開発プラットフォームです。SharePoint 2013 開発者ドキュメントでは、開発プラットフォームとしての SharePoint 2013を特徴づける、開発用の機能、テクノロジ、モデルについて説明します。マイクロソフトの開発ドキュメントでは、初めてのアドイン開発の基本、プラットフォームの使用の基本、自分のコードでの SharePoint 2013 リソースの作成、使用とやり取りについて説明します。SharePoint アドインおよび SharePoint ソリューションの構築をすばやくかつ手軽に開始できるように、SharePoint の概念に関する詳しい記事、タスクの操作手順のガイド、コード サンプルを提供します。
  
    
    

## SharePoint 2013で可能な開発の種類
<a name="bk_whatkinds"> </a>

SharePoint に詳しい開発者は、SharePoint のコア機能を拡張するサーバー側ファーム ソリューションを構築できることを理解しています。SharePoint 2013は、新しい柔軟な開発モデルを提供します。SharePoint 2013では、JavaScript や OAuth、OData などの標準の Web テクノロジの利点を活用する SharePoint アドインを作成できます。さらに、SharePoint 2013は、SharePoint リソースとやり取りできる機能と、多様なホスティング オプションを提供します。この新しい SharePoint アドイン開発モデルにより、SharePoint ファーム上ではなくクラウドで実行される、SharePoint の機能を活かしたアドインを開発できます。この柔軟な開発モデルと、統合された標準の Web テクノロジにより、SharePoint での開発作業を、既に経験のある他の種類の Web 開発作業と同じように行えるようになります。
  
    
    
 **SharePoint アドインの開発について**
  
    
    
次の記事は、SharePoint アドインに関する理解を深め、自分の開発に適しているかどうかを判断するのに役立ちます。
  
    
    

-  [SharePoint アドインと SharePoint ソリューションの比較](sharepoint-add-ins-compared-with-sharepoint-solutions.md)
    
  
 **モバイル機能向けの SharePoint ソリューションとアドインの開発**
  
    
    
ファーム ソリューションを開発する場合、ソーシャル アプリケーション向けの機能や、リモート データ ストアとの統合 (Business Connectivity Services)、モバイル開発などの数々の新機能のメリットを活用できます。まずは「 [SharePoint 2013 の開発者のための新機能](what’s-new-for-developers-in-sharepoint-2013.md)」のガイダンスをお読みください。
  
    
    
次のセクションでは、SharePoint 2013向けのモバイル ソリューションの作成方法について説明します。
  
    
    

-  [SharePoint 2013 にアクセスする Windows Phone アプリの作成](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [[方法] ナビゲーションとイベント記録の REST インターフェイスを備えた検索利用モバイル アプリを作成する](how-to-build-search-driven-mobile-apps-with-the-navigation-and-event-logging-res.md)
    
  
次のセクションでは、ファーム ソリューションに使用できる SharePoint 2013の機能について説明します。
  
    
    

-  [SharePoint サイトの構築](build-sites-for-sharepoint.md)
    
  
-  [SharePoint 2013 機能の追加](add-sharepoint-2013-capabilities.md)
    
  

## 開発環境のセットアップと開発の開始
<a name="bk_getstarted"> </a>

 **モバイル機能向けの SharePoint ソリューションとアドインの開発**
  
    
    
表 1 に、SharePoint 2013を使用して ファーム ソリューションを開発するにあたって、開発環境のセットアップおよび新機能のメリットの活用に役立つリソースを示します。
  
    
    

  
    
    

**表 1. SharePoint ファーム ソリューション開発に役立つリソース**


|**トピック**|**説明**|
|:-----|:-----|
| [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md) <br/> |SharePoint 2013開発環境のコンポーネントをインストールする方法について、手順を追って説明します。  <br/> |
| [SharePoint 2013 での適切な API セットの選択](choose-the-right-api-set-in-sharepoint-2013.md) <br/> |サーバー オブジェクト モデル、各種クライアント側オブジェクト モデル、REST/OData Web サービスなど、SharePoint 2013に搭載されている各種 API セットについて説明します。  <br/> |
| [SharePoint 2013 の開発者のための新機能](what’s-new-for-developers-in-sharepoint-2013.md) <br/> |SharePoint 2013の各種新機能の詳細を紹介します。  <br/> |
| [SharePoint 2013 でのプログラミング モデル](programming-models-in-sharepoint-2013.md) <br/> |SharePoint 2013を使用して作成できる各種 SharePoint 開発プロジェクトの概要を簡潔に紹介します。  <br/> |
| [SharePoint 2013 機能の追加](add-sharepoint-2013-capabilities.md) <br/> |開発するソリューション内での SharePoint 2013の機能の使用に関する詳細情報を提供します。  <br/> |
   
 **SharePoint アドインの開発について**
  
    
    
SharePoint アドインの開発を始める場合には、まず、開発するアドインの種類、含めるテクノロジ、使用するホスティング オプションについて検討する必要があります。
  
    
    
作成したい SharePoint アドインの種類がわかったら、ガイダンスに従って、そのアドインに適した開発環境を探します。表 2 に、SharePoint 開発環境のセットアップとアドインの作成の開始に役立つリソースを示します。
  
    
    

**表 2. SharePoint アドインの開発の開始に役立つリソース**


|**トピック**|**説明**|
|:-----|:-----|
|||
| [Office 365 開発者向けサイトにサインアップする](http://msdn.microsoft.com/library/b22ce52a-ae9e-4831-9b68-c9210af6dc54%28Office.15%29.aspx) <br/> |SharePoint アドインを開発するためにOffice 365の開発者サイトにサインアップして使用する方法について説明します。  <br/> |
| [SharePoint アドインのオンプレミスの開発環境をセットアップする](http://msdn.microsoft.com/library/b0878c12-27c9-4eea-ae3b-7e79e5a8838d%28Office.15%29.aspx) <br/> |社内設置型の SharePoint 2013のローカル インストールをセットアップし、SharePoint アドインの開発用に設定する方法について説明します。  <br/> |
| [プロバイダー ホスト型 SharePoint アドインの作成を始める](http://msdn.microsoft.com/library/3038dd73-41ee-436f-8c78-ef8e6869bf7b%28Office.15%29.aspx) <br/> |SharePoint 2013 サイトとは別にホストされる基本の SharePoint アドインを作成する方法について、手順を追って説明します。  <br/> |
| [SharePoint ホスト型の SharePoint アドインの作成を始める](http://msdn.microsoft.com/library/1b992485-6efe-4ea4-a18c-221689b0b66f%28Office.15%29.aspx) <br/> |SharePoint 2013 サイト上にホストされる基本の SharePoint アドインを作成する方法について、手順を追って説明します。  <br/> |
   

## その他の技術情報
<a name="bk_additionalresources"> </a>


-  [SharePoint 2013 におけるアクセシビリティ](accessibility-in-sharepoint-2013.md)
    
  
-  [Protocol handler error due to deprecated interface in SharePoint 2016](protocol-handler-error-due-to-deprecated-interface-in-sharepoint-2016.md)
    
  
-  [SharePoint 2013 .NET サーバー API リファレンス](http://msdn.microsoft.com/library/fb8a82f1-9239-49ae-89f3-ce1385fb28b5%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 .NET クライアント API リファレンス](http://msdn.microsoft.com/library/88e5e1b9-eab2-4f3b-a3f2-75c96b86f1f4%28Office.15%29.aspx)
    
  

  
    
    

