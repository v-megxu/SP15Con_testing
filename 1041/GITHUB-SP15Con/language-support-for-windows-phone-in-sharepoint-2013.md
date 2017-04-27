---
title: SharePoint 2013 の Windows Phone 向け言語サポート
ms.prod: SHAREPOINT
ms.assetid: 2c396a91-0fc1-4e25-942b-fffad49bd2c6
---


# SharePoint 2013 の Windows Phone 向け言語サポート
モバイル アプリ開発用の SharePoint Software Development Kit (SDK) for Windows Phone によってインストールされる Visual Studio テンプレートの言語サポートについて説明します。
複数の言語を対象としてモバイル アプリケーションを開発するには、アプリケーションのグローバライズとローカライズが必要です。実装する必要のあるグローバリゼーションとローカリゼーションの機能のほとんどは, .NET Framework にすでに組み込まれています。この機能を使用して、他の多くの国や地域の顧客を得ることができます。
  
    
    

Windows Phone SDK には、Visual Studio 2010 Express for Windows Phone、Windows Phone エミュレーター、XNA Game Studio、および Expression Blend が含まれます。作業を始めるには、Windows Phone 開発用の  [Windows Phone SDK 7.1](http://www.microsoft.com/ja-jp/download/details.aspx?id=27570) をインストールします。その後、 [Microsoft SharePoint SDK for Windows Phone 7.1](http://www.microsoft.com/ja-jp/download/details.aspx?id=30476) をインストールして、Windows Phone 用の SharePoint テンプレートをインストールします。
開発環境をセットアップし、SharePoint SDK for Windows Phone をインストールした後、「 [[方法]: SharePoint 用モバイル アプリの開発環境をセットアップする](how-to-set-up-an-environment-for-developing-mobile-apps-for-sharepoint.md)」を参照してください。
  
    
    

Windows Phone 用の SharePoint テンプレートの詳細については、「 [Visual Studio の Windows Phone SharePoint 2013 アプリケーション テンプレートの概要](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md)」を参照してください。
## SharePoint SDK for Windows Phone によってインストールされるテンプレートとライブラリ
<a name="LanguageSupportForWindowsPhoneForSharePoint2013_TemplatesInstalledBySharePointSDKForWindowsPhone"> </a>

SharePoint SDK for Windows Phone 7.1 は、Windows Phone 用のクライアント オブジェクト モデル (CSOM) ライブラリ、Windows Phone 用の SharePoint 認証ライブラリ、および Windows Phone プロジェクト テンプレートをインストールします。これらを使用して、SharePoint 2013 または SharePoint 2010 に対する Windows Phone 7.1 のアプリケーションを構築できます。
  
    
    
SharePoint SDK for Windows Phone をインストールすると、次の 2 つの Silverlight for Windows Phone テンプレートが追加でプロジェクトに利用できます。
  
    
    

- Windows Phone 対応の空の SharePoint アプリケーション
    
  
- Windows Phone の SharePoint List アプリケーション
    
  

## SharePoint SDK for Windows Phone のローカライズ版
<a name="LanguageSupportForWindowsPhoneForSharePoint2013_LocalizedVersionsOfSharePointSDKForWindowsPhone"> </a>

SharePoint SDK for Windows Phone Developer Toolkit 7.1 では 9 つの言語をサポートします。アプリケーションを作成する作業は、プロジェクトの作成、フォームの設計、コントロールの開発、およびコードの追加を含め、ほとんどが設計時に行われます。SharePoint SDK for Windows Phone の次のローカライズ版のうち、いずれを使用しても、Windows Phone アプリケーションを記述できます。
  
    
    

- 英語 (en-US)
    
  
- フランス語 (fr-FR)
    
  
- ドイツ語 (de-DE)
    
  
- イタリア語 (it-IT)
    
  
- 日本語 (ja-JP)
    
  
- 韓国語 (Ko-KR)
    
  
- ロシア語 (ru-RU)
    
  
- スペイン語 (es-ES)
    
  
- 繁体字中国語 (zh-TW)
    
  

## SharePoint Windows Phone アプリケーションでサポートされるローカライズされた言語
<a name="bk_supplocallangs"> </a>

アプリケーションによる制御状態になったら、ユーザーと同じようにアプリケーションを操作します。コードの参照、およびアプリケーションの実行とデバッグができますが、コードの変更はできません。
  
    
    
プログラムでアクセスできるのは 9 つの言語ですが、表 1 に示した 20 の言語で SharePoint モバイル アプリケーションを実行できます。
  
    
    

**表 1. SharePoint SDK for Windows Phone でサポートされる表示/実行時の言語**


|**カルチャ名**|**カルチャ コード**|
|:-----|:-----|
|簡体字中国語 (PRC)  <br/> |zh-CN  <br/> |
|繁体字中国語 (台湾)  <br/> |zh-TW  <br/> |
|チェコ語 (チェコ共和国)  <br/> |cs  <br/> |
|デンマーク語 (デンマーク)  <br/> |da  <br/> |
|オランダ語 (オランダ)  <br/> |nl  <br/> |
|フィンランド語 (フィンランド)  <br/> |fi  <br/> |
|フランス語 (フランス)  <br/> |fr  <br/> |
|ドイツ語 (ドイツ)  <br/> |de  <br/> |
|ギリシャ語 (ギリシャ)  <br/> |el  <br/> |
|ハンガリー語 (ハンガリー)  <br/> |hu  <br/> |
|イタリア語 (イタリア)  <br/> |it  <br/> |
|日本語 (日本)  <br/> |ja  <br/> |
|韓国語 (韓国)  <br/> |ko  <br/> |
|ノルウェー語 (ノルウェー)  <br/> |nb  <br/> |
|ポーランド語 (ポーランド)  <br/> |pl  <br/> |
|ポルトガル語 (ブラジル)  <br/> |pt-BR  <br/> |
|ポルトガル語 (ポルトガル)  <br/> |pt-PT  <br/> |
|ロシア語 (ロシア)  <br/> |ru  <br/> |
|スペイン語 (スペイン)  <br/> |es  <br/> |
|スウェーデン語 (スウェーデン)  <br/> |sv  <br/> |
   

## その他の技術情報
<a name="bk_addresources"> </a>


-  [Visual Studio の Windows Phone SharePoint 2013 アプリケーション テンプレートの概要](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md)
    
  
-  [SharePoint 2013 にアクセスする Windows Phone アプリの作成](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [Windows Phone SDK 8.0](http://www.microsoft.com/ja-jp/download/details.aspx?id=35471)
    
  
-  [Microsoft SharePoint SDK for Windows Phone 8](http://www.microsoft.com/ja-jp/download/details.aspx?id=36818)
    
  

  
    
    

