---
title: SharePoint 2013 の BCS 開発環境のセットアップ
ms.prod: SHAREPOINT
ms.assetid: d83c8a43-49dd-47eb-94d4-23aa2cf71a9a
---


# SharePoint 2013 の BCS 開発環境のセットアップ
Business Connectivity Services (BCS) を使用してSharePoint 2013ソリューションや SharePoint アドインを開発するための開発環境のセットアップについて説明します。
構築するソリューションのタイプによって、クライアント コンピューターまたはサーバー コンピューター上で、BCS を使用して SharePoint 2013 ソリューションや SharePoint アドインを作成できます。
  
    
    


## サーバーベースのソリューションと SharePoint アドインを構築する
<a name="SP15SettingupdevenvBCS_server"> </a>

通常、BCS ソリューションとアプリの多くは、サーバー環境でホストされます。これらのサーバー ソリューションおよびアプリは、SharePoint 2013の BCS のすべての機能によって大きな柔軟性が得られます。
  
    
    
サーバーベースのソリューションでは、ソリューションの開発は、通常、SharePoint 2013がインストールされたローカル コンピューターで行うほうが有利です。そうすれば、ソリューションの作成とテストを行う際に、本番環境のサーバーに展開することができます。開発環境は、ホスト ワークステーション上または、Windows Server 2008 Service Pack 2 を実行する 1 つ以上の仮想コンピューター上に構築できます。
  
    
    

### SharePoint アドインを構築するための環境をセットアップする

BCSでアプリを開発するために使用する環境は、あらゆる SharePoint アドインを開発するための環境と同じです。 
  
    
    
オペレーティング システム、SharePoint 2013、Visual Studio 2012、Office Developer Tools for Visual Studio 2012 など、開発環境のコンポーネントをインストールする方法を習得するには、「 [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md)」の手順に従ってください。
  
    
    

## クライアントベースのソリューションを構築する
<a name="SP15SettingupdevenvBCS_client"> </a>

クライアントベースのソリューションでは、Office 2013 クライアント アプリケーションを使用して、SharePoint 2013 ソリューションまたは SharePoint アドインからアクセスできる同じ外部データにアクセスすることができます。これを行うには、BCS クライアント キャッシュを使用してコードを実行します。クライアント コンポーネントは、クライアントサイドのコードとクライアント キャッシュを使用して BCSとデータをやり取りします。これにより、Office クライアント アプリケーションに、外部コンテンツ タイプを介して SharePoint が使用できるリッチ データを提供します。
  
    
    
これらのソリューションはコードを必要としないため、SharePoint Designer 2013や Office 2013 を使用できます。
  
    
    

## その他の技術情報
<a name="SP15SettingupdevenvBCS_addresources"> </a>


-  [SharePoint アドインのオンプレミスの開発環境をセットアップする](http://msdn.microsoft.com/library/b0878c12-27c9-4eea-ae3b-7e79e5a8838d%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 の Business Connectivity Services の概要](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 開発の概要](sharepoint-2013-development-overview.md)
    
  

