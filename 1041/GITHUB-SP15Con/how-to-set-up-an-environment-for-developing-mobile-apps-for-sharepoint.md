---
title: [方法] SharePoint 用モバイル アプリの開発環境をセットアップする
ms.prod: SHAREPOINT
ms.assetid: acaf556d-e20d-478d-8c59-2efd8efb9dcb
---


# [方法]: SharePoint 用モバイル アプリの開発環境をセットアップする
SharePoint モビリティ プロジェクトのシステム要件および開発環境の構成について説明します。
SharePoint モビリティ プロジェクトを操作するための最小限の構成には、SharePoint 2013を実行しているサーバー (または SharePoint Online アカウント)、および別のクライアント オペレーティング システムの開発環境が必要です。クライアント オペレーティング システム (Windows 7 など) での SharePoint 2013のインストールはサポートされていません。また、Windows Phone 開発に必要なツールのインストールは、サーバー オペレーティング システム (Windows Server 2008 など) ではサポートされていません。
  
    
    


## Windows Phone 開発プロジェクトおよび SharePoint サーバー
<a name="SP15Setupmobile_winphone"> </a>

SharePoint と相互作用する Windows Phone アプリケーションを作成しテストするには、SharePoint 2013を実行しているサーバーまたは SharePoint Online アカウントへのアクセスが必要です。また、ソリューションで使用するサイトおよびリストの十分な権限が必要です。プロジェクトの開発中、対象サーバーとしてテストおよび開発に専念する SharePoint Server のインストールを使用することをお勧めします。開発済みのソリューションが十分なテストを受けた後にのみ、対象サーバーとして運用環境で SharePoint Server を使用します。
  
    
    
SharePoint 2013のインストールおよび構成の情報については, Microsoft TechNet ライブラリの「 [SharePoint 製品](http://technet.microsoft.com/ja-jp/library/ee428287.aspx)」 セクションにあるドキュメントを参照してください。開発ソリューションでの SharePoint Onlineの使用に関する情報については、「  [SharePoint Online 開発リソース センター](http://msdn.microsoft.com/ja-jp/sharepoint/gg153540.aspx)」にアクセスしてください。
  
    
    
このドキュメント内のコード サンプルについては、データの追加、編集、消去が可能な SharePoint サイトおよびリストの十分な権限を持つ、または入手できるサンプルを操作する開発者を前提としています。
  
    
    

## SharePoint モビリティ プロジェクトのクライアント開発環境の構成
<a name="SP15Setupmobile_configure"> </a>

Windows Phone デバイスで使用する SharePoint アドインを開発するには、サーバー オペレーティング システムではなく、クライアント オペレーティング システムを実行しているコンピューターに開発ツールをセットアップする必要があります。
  
    
    

### Windows Phone SDK 8.0 の設定

Windows Phone 8 で使用する SharePoint アドインを開発するには、Windows 8 64 ビット (x64) クライアント バージョンまたは Windows 8 Pro を実行しているコンピューターに開発ツールをセットアップする必要があります。 Windows Phone 8 エミュレーターには、Windows 8 Pro が必要であり、Second Level Address Translation (SLAT) をサポートするプロセッサが必要です。
  
    
    

1. サポートされるクライアント オペレーティング システムを使用したコンピューターで、 [Windows Phone SDK 8.0](http://www.microsoft.com/ja-jp/download/details.aspx?id=35471) をインストールします。Windows Phone Software Development Kit (SDK) 8.0 は、Windows Phone 8 および Windows Phone 7.5 用のアプリやゲームを開発する必要があるユーザーにツールを提供します。
    
    Windows Phone SDK 8.0 は、Windows Phone 8.0 および Windows Phone 7.5 用のアプリとゲームを作成するために使用するすべての機能を備えた開発環境です。 Windows Phone SDK は、スタンドアロンの Windows Phone 用 Visual Studio Express 2012 エディションを提供するか、または Visual Studio 2012 Professional、Premium、または Ultimate エディションへのアドインとして機能します。SDK により、既存のプログラミング スキルとコードを使用して、マネージド コードやネイティブ コードのアプリを作成できます。さらに、SDK には、実際の状況で、Windows Phone アプリをプロファイルし、テストするための複数のエミュレーターと追加のツールも含まれています。
    
    > **メモ**
      > コンピューターがハードウェアおよびオペレーティング システム要件を満たしているが、Windows Phone 8 エミュレーターの要件を満たしていない場合、Windows Phone SDK 8.0 がインストールされ実行されます。ただし、Windows Phone 8 エミュレーターは機能せず、Windows Phone 8 エミュレーターでアプリを展開したり、テストしたりすることはできません。Windows Phone エミュレーターを実行するためのシステム要件については、「 [Windows 電話エミュレーターのシステム要件](http://msdn.microsoft.com/ja-jp/library/ff626524)」を参照してください。 
2.  [Microsoft SharePoint SDK for Windows Phone 8](http://www.microsoft.com/ja-jp/download/details.aspx?id=36818) をインストールします。
    
    SharePoint SDK for Windows Phone により、Windows Phone テンプレート用の 2 つの Silverlight がインストールされます (Windows Phone SDK によりインストールされる Silverlight に加えて)。それは、Windows Phone の空の SharePoint アプリケーション テンプレート、および Windows Phone SharePoint リスト アプリケーション テンプレートです。 さらに、SDK により、SharePoint CSOM ライブラリ、認証ライブラリ、Windows Phone プロジェクト テンプレートもインストールされ、NTLM 認証もサポートされるようになりました。バンドルされた API とテンプレートを使用して、SharePoint 2013 に対して、Windows Phone 8 アプリケーションを作成できます。
    
    また、SharePoint SDK for Windows Phone により、いくつかのサポート ランタイム アセンブリがインストールされます (標準インストールの場合:  `%ProgramFiles(x86)%\\Microsoft SDKs\\SharePoint\\v15.0\\Phone\\v8.0\\Libraries`)。
    
  - Microsoft.SharePoint.Client.Phone.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Runtime.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Auth.UI
    
  
  - Microsoft.SharePoint.Phone.Application.dll
    
  

    > **メモ**
      > SharePoint SDK for Windows Phone のテンプレートは、現在 C# プロジェクトでのみ使用できます。 
SharePoint SDK for Windows Phone のテンプレートの詳細については、「 [Visual Studio の Windows Phone SharePoint 2013 アプリケーション テンプレートの概要](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md)」を参照してください。
  
    
    

### Windows Phone SDK 7.1 の設定

Windows Phone 7 で使用するための SharePoint アドインを開発するには、Windows 7 (32 ビットまたは 64 ビット) または Windows Vista Service Pack 2 (32 ビットまたは 64 ビット) を実行しているコンピューターで開発ツールをセットアップする必要があります。Windows Phone ソフトウェア開発キット (SDK) 7.1 は、Windows Server 2008 または Windows XP ではサポートされていません。
  
    
    

1. サポートされるクライアント オペレーティング システムを備えたコンピューターに、 [Windows Phone SDK 7.1](http://www.microsoft.com/ja-jp/download/details.aspx?id=27570) をインストールします。
    
    > **メモ**
      > Windows Phone SDK の以前のバージョンは、Windows Phone 開発者ツールと名付けられていました。 

    Windows Phone SDK により、Microsoft Visual Studio 2010 Express for Windows Phone、Windows Phone エミュレーター、XNA Game Studio、および Microsoft Expression Blend for Windows Phone がインストールされます。Visual Studio 2010 Express for Windows Phone は、ほとんどの Windows Phone ソリューションに適した開発環境です。優先開発環境として Visual Studio 2010 Professional を使用することもできますが、それでも Windows Phone SDK のインストールが必要であり、それは Visual Studio に必要なアドインをインストールします (Visual Studio 2012 での Windows Phone SDK の使用は現在サポートされていません)。
    
    Windows Phone SDK のインストールに関する追加のシステム要件および指示については、「 [Windows Phone SDK のインストール](http://msdn.microsoft.com/ja-jp/library/ff402530%28VS.92%29.aspx)」を参照してください。Windows Phone エミュレーターの実行に関するシステム要件の情報については、「 [Windows Phone エミュレーターのセットアップとシステム要件](http://msdn.microsoft.com/ja-jp/library/ff626524%28VS.92%29.aspx)」を参照してください。
    
  
2.  [Microsoft SharePoint SDK for Windows Phone 7.1](http://www.microsoft.com/ja-jp/download/details.aspx?id=30476) をインストールします。
    
    SharePoint SDK for Windows Phone により、Windows Phone テンプレート用の 2 つの Silverlight がインストールされます (Windows Phone SDK によりインストールされる Silverlight に加えて)。それは、Windows Phone の空の SharePoint アプリケーション テンプレート、および Windows Phone SharePoint リスト アプリケーション テンプレートです。
    
    また、SharePoint SDK for Windows Phone により、いくつかのサポートしているランタイム アセンブリがインストールされます (標準インストール用の  `%ProgramFiles(x86)%\\Microsoft SDKs\\SharePoint\\v15.0\\Phone\\v7.1\\Libraries` で)。
    
  - Microsoft.SharePoint.Client.Phone.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Runtime.dll
    
  
  - Microsoft.SharePoint.Client.Phone.Auth.UI
    
  
  - Microsoft.SharePoint.Phone.Application.dll
    
  

    > **メモ**
      > SharePoint SDK for Windows Phone のテンプレートは、現在 C# プロジェクトでのみ使用できます。 
SharePoint SDK for Windows Phone のテンプレートの詳細については、「 [Visual Studio の Windows Phone SharePoint 2013 アプリケーション テンプレートの概要](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md)」を参照してください。
  
    
    

## その他の技術情報
<a name="SP15Setupmobile_addlresources"> </a>


-  [SharePoint 2013 にアクセスする Windows Phone アプリの作成](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [Windows Phone SDK 8.0](http://www.microsoft.com/ja-jp/download/details.aspx?id=35471)
    
  
-  [Microsoft SharePoint SDK for Windows Phone 8](http://www.microsoft.com/ja-jp/download/details.aspx?id=36818)
    
  
-  [Windows Phone SDK 7.1](http://www.microsoft.com/ja-jp/download/details.aspx?id=27570)
    
  
-  [Microsoft SharePoint SDK for Windows Phone 7.1](http://www.microsoft.com/ja-jp/download/details.aspx?id=30476)
    
  

