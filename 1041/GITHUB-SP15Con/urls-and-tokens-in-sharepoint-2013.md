---
title: SharePoint 2013 の URL とトークン
ms.prod: SHAREPOINT
ms.assetid: 161418d7-8123-4c4e-91a1-97e43c17f0e6
---



# SharePoint 2013 の URL とトークン
SharePoint 2013 で URL を作成する方法、および URL トークンを使用する方法を説明します。
|||
|:-----|:-----|
|**この記事の内容**          [SharePoint 2013 の URL の種類](#TypesOfURLs)           [画像の URL について推奨される方法](#GoodPracticeImageURL)           [SharePoint 2013 の URL トークン](#URLtokens)           [その他の技術情報](#SP15URLS_addlresources)||
   

## SharePoint 2013 の URL の種類
<a name="TypesOfURLs"> </a>

SharePoint 2013 は URL 文字列を解析し、指定されたプロトコル (たとえば、 **http:**) または文字列内のスラッシュ (/) の位置に基づいて URL の形式を特定します。個々のメンバに応じて、以下の URL の形式を使用できます。
  
    
    

- **絶対 URL** は、最初にプロトコルを指定して、完全なパスを指定します。たとえば、 `http://` _domain_or_server_/[ `sites/`] _Web_Site_/ `Lists`/ _List_Title_/ `AllItems.aspx` のようになります。
    
  
- **ドメイン相対 URL** は、ドメイン (サーバーの名前の場合もある) アドレスを基準とし、常にスラッシュで始まります。これは、最上位の Web サイトからファイル名までの完全なパスを指定します。たとえば、/[ `sites/`] _Web_Site_/ `Lists`/ _List_Title_/ `AllItems.aspx` のようになります。
    
  
- **Web サイト相対 URL** は、Web サイト オブジェクト ( [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) ) のアドレスを基準とします。これは、最初にスラッシュを _含めず_に、Web サイト アドレスからファイル名までの完全なパスを指定します。たとえば、 `Lists/` _List_Title_/ `AllItems.aspx` のようになります。
    
  
- **ファイルまたはフォルダーに対する相対 URL** は、ファイルを含むフォルダーを基準として、スラッシュを _一切_含めずにファイルの名前だけを指定します。たとえば、 `AllItems.aspx` のようになります。
    
  

> **メモ**
> "サイト コレクション相対 URL" という考え方はありません。そのような URL を渡すと、コードが失敗する可能性があります。 
  
    
    


## 画像の URL について推奨される方法
<a name="GoodPracticeImageURL"> </a>

%ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS\\1033\\IMAGES ディレクトリ内の画像ファイルへの URL を作成する場合は、サイト コレクションのルート Web サイトを使用するパスを指定し、パス内にサブサイトを含めないようにします。たとえば、画像ファイルには、/MySubsite/_layouts/images/MyImage.gif ではなく、/_layouts/images/MyImage.gif を使用してください。これは、サブサイト URL はそれが使用されている場所によって解決方法が異なるためです。ルート Web サイト相対 URL を常に使用すれば、このような違いは無視されます。
  
    
    

## SharePoint 2013 の URL トークン
<a name="URLtokens"> </a>

SharePoint 2013 は、SharePoint アドイン またはファーム ソリューションにおいて以下の表に挙げられているトークンの使用をサポートします。いくつかのトークンはアプリでのみ使用可能です。これらについての詳細は、 [SharePoint アドインの URL 文字列とトークン](http://msdn.microsoft.com/library/800ec8cd-a448-46bc-b41e-d4030eeb4048%28Office.15%29.aspx) を参照してください。
  
    
    
このセクションの表に示されたトークンは、カスタム アクションやカスタム ページのリンクなど、SharePoint を開発する際のさまざまな状況の URL で使用できます。場合によっては、使用できないトークンもあります。一部のトークンのみが使用できる 3 つの重要な場所として、アプリの開始ページ、ホスト Web のカスタム アクション、およびアプリ パーツの  [Src](https://msdn.microsoft.com/library/Microsoft.SharePoint.WebControls.SPAppIFrame.Src.aspx) プロパティがあります。これらについては別の列で説明されていますが、トークンを使用できるのはこれら 3 つの場所だけではありません。
  
    
    
" **StartPage** " 列では、アプリ マニフェストの **StartPage** 要素にトークンを使用できるかどうかを指定します。" **カスタム アクション** " 列では、ホスト Web のカスタム アクションの URL にトークンを使用できるかどうかを指定します。" **アプリ パーツ** " 列では、アプリ パーツの [Src](https://msdn.microsoft.com/library/Microsoft.SharePoint.WebControls.SPAppIFrame.Src.aspx) プロパティにトークンを使用できるかどうかを指定します。
  
    
    

**URL の先頭で使用できるトークン**


|**トークン**|**解決される結果**|**StartPage**|**カスタム アクション**|**アプリ パーツ**|**注釈**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|~controlTemplates  <br/> |現在の Web サイトの ControlTemplates 仮想フォルダーの URL  <br/> |いいえ  <br/> |いいえ  <br/> |いいえ  <br/> ||
|~layouts  <br/> |現在の Web サイトの Layouts 仮想フォルダーの URL  <br/> |いいえ  <br/> |いいえ  <br/> |いいえ  <br/> ||
|~site  <br/> |現在の Web サイトの URL  <br/> |いいえ  <br/> |いいえ  <br/> |はい  <br/> ||
|~sitecollection  <br/> |現在の Web サイトの親サイト コレクションの URL  <br/> |いいえ  <br/> |いいえ  <br/> |はい  <br/> ||
   
特記がない場合、次の表にあるこれらのトークンは、アプリ パーツの  [Src](https://msdn.microsoft.com/library/Microsoft.SharePoint.WebControls.SPAppIFrame.Src.aspx) プロパティ値の *path*  部分に使用できません。" **アプリ パーツ** " は、値の *クエリ文字列*  部分での使用を示しています。
  
    
    

**URL の途中で使用できるトークン**


|**トークン**|**解決される結果**|**StartPage**|**カスタム アクション**|**アプリ パーツ**|**注釈**|
|:-----|:-----|:-----|:-----|:-----|:-----|
|{ControlTemplates}  <br/> |現在の Web サイトの ControlTemplates 仮想フォルダーの URL  <br/> |いいえ  <br/> |いいえ  <br/> |いいえ  <br/> ||
|{ItemId}  <br/> |リストまたはライブラリ内の項目の ID (整数)。  <br/> |いいえ  <br/> |はい  <br/> |いいえ  <br/> ||
|{ItemUrl}  <br/> |作用対象のアイテムの URL  <br/> |いいえ  <br/> |はい  <br/> |いいえ  <br/> ||
|{Layouts}  <br/> |現在の Web サイトの Layouts 仮想フォルダーの URL  <br/> |いいえ  <br/> |いいえ  <br/> |いいえ  <br/> ||
|{ListId}  <br/> |現在のリストの ID (GUID)  <br/> |いいえ  <br/> |はい  <br/> |いいえ  <br/> ||
|{RecurrenceId}  <br/> |再帰イベントの再帰インデックス  <br/> |いいえ  <br/> |はい  <br/> |いいえ  <br/> |このトークンは、リスト アイテムのコンテキスト メニューでの使用がサポートされていません。  <br/> |
|{Site}  <br/> |現在の Web サイトの URL  <br/> |いいえ  <br/> |はい  <br/> |はい  <br/> ||
|{SiteCollection}  <br/> |現在の Web サイトの親サイトの URL  <br/> |いいえ  <br/> |はい  <br/> |はい  <br/> ||
|{SiteUrl}  <br/> |現在の Web サイトの URL  <br/> |いいえ  <br/> |はい  <br/> |いいえ  <br/> ||
|{Source}  <br/> |HTTP 要求の URL。  <br/> |いいえ  <br/> |はい  <br/> |いいえ  <br/> ||
   

## その他の技術情報
<a name="SP15URLS_addlresources"> </a>


-  [SharePoint 2013 でのファーム ソリューションの作成](build-farm-solutions-in-sharepoint-2013.md)
    
  
-  [高度なエクストラネット サポート](http://msdn.microsoft.com/library/21d67796-23c5-4339-8f0e-124208d21ab2%28Office.15%29.aspx)
    
  
-  [サイト、Web アプリケーション、およびその他の主要オブジェクトへの参照を取得する](http://msdn.microsoft.com/library/8623ef1d-e3cc-426c-84a3-6379e0ae284f%28Office.15%29.aspx)
    
  
-  [Working with List Objects and Collections (英語)](http://msdn.microsoft.com/library/d4167b10-6f1e-49f1-8b22-16ce20012a27%28Office.15%29.aspx)
    
  
-  [サンプル オブジェクト モデルのタスク](http://msdn.microsoft.com/library/94d6898d-6a0f-43a7-ad06-1b27ec6916ea%28Office.15%29.aspx)
    
  
