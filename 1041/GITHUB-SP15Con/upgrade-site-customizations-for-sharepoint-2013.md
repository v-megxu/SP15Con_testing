---
title: サイトのカスタマイズを SharePoint 2013 用にアップグレードする
ms.prod: SHAREPOINT
ms.assetid: 4b515860-69ae-4af8-8013-cd071c0ddca6
---


# サイトのカスタマイズを SharePoint 2013 用にアップグレードする
SharePoint 2010 サイトのカスタマイズを SharePoint 2013 にアップグレードする場合の潜在的な問題と推奨事項について説明します。
SharePoint 2013 では、ユーザー インターフェイス (UI) が大幅に変更され、より高速かつ軽快なコンポーネントを使用してサイトのカスタマイズができるようになりました。しかし、SharePoint 2010 からのアップグレードを行うと、UI に実施された改良点を処理するために SharePoint 2013 に組み込まれている新しいコンポーネントでいくつかの問題が発生する可能性があります。
  
    
    

この記事は、SharePoint 開発者および SharePoint 2010 からのアップグレード プロセス管理の担当者が、アップグレード後に発生する可能性のある問題点を識別するのに役に立ちます。
## アップグレードにおける一般的な推奨事項

一般には、カスタマイズをテストし、SharePoint 2013 環境に合わせてそのカスタマイズを再設計することが可能な「評価」サイトを新たに作成することをお勧めします。評価サイト コレクションの作成の詳細については、「 [サイト コレクションをアップグレードする](http://office.microsoft.com/ja-jp/office365-sharepoint-online-enterprise-help/upgrade-a-site-collection-HA102865473.aspx?CTT=5&amp;origin=HA104034491)」を参照してください。
  
    
    

### カスタム コンポーネントのアップグレード

表 1 に、カスタム コンポーネントについてアップグレード後に発生する可能性のある問題と、発生した問題に対処する方法について説明します。
  
    
    

**表 1 SharePoint 2013 へのアップグレードの影響を受けるカスタム コンポーネント**


|**カスタマイズの項目**|**発生する可能性がある問題**|
|:-----|:-----|
|CSS スタイル  <br/> |アップグレード中に、サイトが、default.master ページで参照される CSS ファイルに切り替わります。この結果、ページの外観に対して行ったカスタマイズが変化し、既定のインストールで検出された既定のスタイルを使用してページが表示されます。  <br/> |
|テーマ  <br/> |SharePoint 2010 の場合、サイト全体に対してコーポレート ブランドを定義するカスタム テーマを作成する場合があります。このようなテーマは .thmx ファイルとして作成されます。ファイルはサイト コレクションにアップロードでき、管理者によって適用されます。  <br/> SharePoint 2013 では、柔軟性の向上および機能強化を実現し、将来的なアップグレードにも容易に対応できるように、テーマ エンジンが全面的に再設計されました。この再設計の結果として、SharePoint 2010 テーマから SharePoint 2013 テーマへのアップグレードはサポートされていないので、SharePoint 2013 用にテーマを再作成する必要があります。  <br/> |
|Web テンプレート  <br/> |SharePoint 2010 では Web テンプレートが導入され、機能、レイアウト、スタイル、およびその他のコンポーネントをパッケージ化し、そのパッケージを新しい Web の作成に使用できるようにするための手段が用意されています。Web テンプレートは機能的にはサイト定義を作成することに似ていますが、Web テンプレートを使用することで発行機能を追加できます。  <br/> SharePoint 2013 で実施された変更が原因で、カスタマイズ済みの Web テンプレートはアップグレードしてもすぐには機能しません。  <br/> Web テンプレートに加えられた変更を確認し、この変更に起因する問題を解決するには、推奨事項とベスト プラクティスが記載されている「 [SharePoint 2013 用に Web テンプレートをアップグレードする](upgrade-web-templates-for-sharepoint-2013.md)」を参照してください。  <br/> |
|マスター ページ  <br/> |アップグレード中に、作成済みのカスタム マスター ページへの参照が切り替わり、default.master ページに戻ってしまいます。この状況では、カスタム ページで参照するコンポーネントが見つからないために、SharePoint でエラーが発生する場合があります。  <br/> この問題を解決するには、カスタム マスター ページへの参照を変更する必要があります。  <br/> |
   

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 でサイト コレクションのアップグレードを計画する](https://technet.microsoft.com/ja-jp/library/ff191199.aspx)
    
  
-  [SharePoint 2013 にアップグレードした場合に発生する可能性があるブランドの問題](http://office.microsoft.com/ja-jp/office365-sharepoint-online-enterprise-help/branding-issues-that-may-occur-when-upgrading-to-sharepoint-2013-HA104052656.aspx?CTT=5&amp;origin=HA104034491)
    
  
-  [サイト コレクションをアップグレードする](http://office.microsoft.com/ja-jp/office365-sharepoint-online-enterprise-help/upgrade-a-site-collection-HA102865473.aspx?CTT=5&amp;origin=HA104034491)
    
  
-  [サイト コレクションのアップグレードに関する問題のトラブルシューティング](http://office.microsoft.com/ja-jp/office365-sharepoint-online-enterprise-help/troubleshoot-site-collection-upgrade-issues-HA104037311.aspx?CTT=5&amp;origin=HA104034491)
    
  

