---
title: SharePoint テンプレートに基づいて Windows Phone 用のローカライズされたアプリケーションを作成する
ms.prod: SHAREPOINT
ms.assetid: c12d7fd4-8c6b-446b-970b-1eb0e5d0a9b2
---


# SharePoint テンプレートに基づいて Windows Phone 用のローカライズされたアプリケーションを作成する
新しい SharePoint テンプレートを使用したローカライズ可能な Windows Phone アプリの作成方法と、他の Windows Phone テンプレートを使用した作成方法との相違について説明します。
Windows Phone 7.1 用の SharePoint SDK では、Windows Phone プロジェクト テンプレートがインストールされます。これらのテンプレートを使用して、SharePoint 2013 または SharePoint 2010 に対する Windows Phone 7.1 アプリケーションを作成できます。詳細については、「 [Visual Studio の Windows Phone SharePoint 2013 アプリケーション テンプレートの概要](overview-of-windows-phone-sharepoint-2013-application-templates-in-visual-studio.md)」を参照してください。 
  
    
    

Visual Studio では、言語固有のリソース ファイルを使用してアセンブリが作成され、これによりモバイル アプリケーションで多言語をサポートできるようになります。このプロセスの詳細については、「 [デスクトップ アプリケーションでのリソースのパッケージ化と配置](http://msdn.microsoft.com/library/b224d7c0-35f8-4e82-a705-dd76795e8d16%28Office.15%29.aspx)」を参照してください。
> **重要**
> 東アジアの言語用にアプリケーションをローカライズする場合は、「 [Windows Phone のフォントのサポート](http://msdn.microsoft.com/library/b0d855ad-3fd2-4872-9a88-7f5d0a270ff9%28Office.15%29.aspx)」の「フォントとアプリケーション」を必ずお読みください。 
  
    
    


## SharePoint テンプレートを使用した Windows Phone 用のローカライズされたアプリケーション作成時の相違点

新しい SharePoint テンプレートを使用したローカライズ可能な Windows Phone アプリの作成方法は、他の Windows Phone テンプレートを使用した作成方法と若干異なります。SharePoint テンプレートを使用する場合、 **SupportedCultures** 要素は少し異なる形式を必要とします。たとえば、英語 (米国) を既定のカルチャとして使用し、ドイツ語 (ドイツ) およびスペイン語 (スペイン) もサポートする標準的な Windows Phone アプリでは、 **SupportedCultures** 要素は次のようになります。
  
    
    
 `<SupportedCultures>de-DE;es-ES;</SupportedCultures>`
  
    
    
この形式は、SharePoint テンプレートに基づいてローカライズされた Windows Phone アプリを作成するときには使用できません。代わりに, .csproj ファイル内で **SupportedCultures** 要素を検索し、アプリケーションで (既定のカルチャ以外に) サポートする必要がある各カルチャ (言語) の名前を追加します。それぞれの名前はセミコロンで区切ります。プロジェクト内の各 .resx ファイル用のエントリが必要です。
  
    
    
上記の例では、 **SupportedCultures** 要素は次のように記述する必要があります。
  
    
    
 `<SupportedCultures>de;es;</SupportedCultures>`
  
    
    
Windows Phone 用のローカライズされたアプリケーションを作成する手順を追っての説明については、「 [方法: Windows Phone のローカライズしたアプリケーションを構築する](http://msdn.microsoft.com/library/9306a6ed-6efb-4f32-b850-d2e508431eeb%28Office.15%29.aspx)」を参照してください。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 にアクセスする Windows Phone アプリの作成](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [方法: Windows Phone のローカライズしたアプリケーションを構築する](http://msdn.microsoft.com/library/9306a6ed-6efb-4f32-b850-d2e508431eeb%28Office.15%29.aspx).
    
  
-  [Windows Phone のグローバリゼーションとローカリゼーション](http://msdn.microsoft.com/library/e82118a4-6247-4d75-a16f-749677349be4%28Office.15%29.aspx)
    
  

  
    
    

