---
title: カスタム テーマと CSS を SharePoint 2013 にアップグレードする
ms.prod: SHAREPOINT
ms.assetid: 8d1a4e3a-ae6f-41a5-bd80-3398ba541207
---


# カスタム テーマと CSS を SharePoint 2013 にアップグレードする
カスタム CSS、カスタム マスター ページ、SharePoint 2013 で機能するようにカスタマイズを更新する方法など、テーマのカスタマイズに関するアップグレードの問題を説明します。
## テーマのカスタマイズとアップグレードした SharePoint 2013 サイトの概要
<a name="Intro"> </a>

SharePoint 2013 のテーマ エクスペリエンスは再設計され、サイトのレイアウト、カラー パレット、フォント スキーム、および背景画像を変更して、サイトのカスタマイズに関するプロセスが簡易化されました。テーマのユーザー インターフェイスは再設計され、テーマに関連する新しいファイル形式のセットが追加されました。SharePoint 2010 で作成したカスタム テーマは SharePoint 2013 では使用できないため、カスタム テーマを再作成する必要があります。SharePoint 2013 サイトでカスタム CSS ファイルが正常に動作するようにするには、新しいマスター ページ、カラー スロット、およびその他のテーマ設定の変更に対応するように更新する必要があります。
  
    
    
この記事では、新しいテーマ エクスペリエンスでカスタム SharePoint 2010 テーマ、SharePoint 2010 CSS、およびカスタム CSS を使用するときに発生する可能性がある問題について説明します。また、SharePoint 2013 サイトで使用する場合に、カスタムの SharePoint 2010 テーマ、SharePoint 2010 CSS、カスタム CSS の変更が必要な点についても説明します。
  
    
    

> **メモ**
> SharePoint 2010 テーマは、2010 モードで実行しているサイト コレクションで使用できます。サイト コレクション モードの詳細については、「 [SharePoint 2013 でサイト コレクションのアップグレードを計画する](http://technet.microsoft.com/ja-jp/library/ff191199.aspx)」または「 [SharePoint 2013 へのアップグレードを計画する](https://technet.microsoft.com/ja-jp/library/cc303429.aspx)」を参照してください。 
  
    
    

テーマの詳細については、「 [SharePoint 2013 のテーマの概要](themes-overview-for-sharepoint-2013.md)」を参照してください。
  
    
    

## SharePoint 2013 でのカスタム SharePoint 2010 テーマ
<a name="themes"> </a>

SharePoint 2010 では、テーマは THMX ファイルに保存されていました。SharePoint 2013 では、テーマに関連する新しいファイル形式のセットがあります。カラー パレットとフォント スキームは、別の XML ファイルに保存されます (それぞれ .spcolor ファイルと .spfont ファイル)。
  
    
    
THMX ファイルを SharePoint 2010 から SharePoint 2013 にアップグレードすることはできません。カスタム テーマを SharePoint 2010 サイトに適用した場合、SharePoint 2013 にアップグレードするとテーマ ファイルは残りますが、テーマはサイトに適用されなくなり、サイトは既定のテーマに戻ります。SharePoint 2013 サイトで SharePoint 2010 テーマのカスタマイズを使用する場合、SharePoint 2013 のテーマ設定に関するガイダンスを使用して再作成する必要があります。
  
    
    
テーマのカスタマイズの作成方法の詳細については、「 [SharePoint 2013 でカスタム テーマを展開する方法](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)」と「 [SharePoint 2013 のカラー パレットとフォント](color-palettes-and-fonts-in-sharepoint-2013.md)」を参照してください。また、SharePoint のカラー パレット ツールを使用して、SharePoint 設計を作成できます。Microsoft ダウンロード センターから  [SharePoint カラー パレット ツールをダウンロード](http://www.microsoft.com/en-us/download/details.aspx?id=38182)できます。
  
    
    

> **ヒント**
> PowerPoint で THMX ファイルを開いて、カスタム テーマで色がどのように定義されているかを確認できます。その後、カラー パレット ツールを使用して、カラー パレット ファイル (.spcolor ファイル) として色を再作成できます。カラー パレットは、SharePoint サイトで使用される色の組み合わせです。 
  
    
    

プリインストールされた SharePoint 2013 テーマのいずれかを使用することもできます。詳細については、Office.com の「 [発行サイトのテーマを選択する](http://office.microsoft.com/ja-jp/office365-sharepoint-online-enterprise-help/choose-a-theme-for-your-publishing-site-HA102891580.aspx?CTT=1)」を参照してください。
  
    
    

## カスタマイズしたマスター ページをアップグレードする
<a name="MasterPages"> </a>

SharePoint 2010 サイトを SharePoint 2013 にアップグレードすると、サイトは SharePoint 2013 の既定のマスター ページを使用するように構成されます。SharePoint 2010 サイト用のカスタム マスター ページがあった場合は、そのページがサイトに残っているため、SharePoint 2013 サイトに適用することができます。SharePoint ユーザー インターフェイスまたは **SPWeb** クラスを使用して、カスタム マスター ページをアップグレードしたサイトに適用できます。マスター ページを変更する方法の詳細については、「 [[方法]: SharePoint Server 2013 のサイトにマスター ページを適用する](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md)」を参照してください。
  
    
    
SharePoint 2010 のカスタム マスター ページを、アップグレードされた SharePoint 2013 サイトに適用するかどうかを判断する前に、次の点について検討してください。
  
    
    

- **カスタム マスター ページがカスタム CSS ファイルに依存している場合:** カスタム マスター ページをアップグレードされたサイトに適用すると、サイトは元の 2010 エクスペリエンスに戻りますが、SharePoint 2013 テーマをサイトに適用できなくなります。
    
    カスタム マスター ページとカスタム CSS ファイルを SharePoint 2013 テーマ エクスペリエンスで使用するには、新しい SharePoint 2013 カラー スロットを使用するように CSS ファイルを更新する必要があります。テーマのユーザー インターフェイスからカスタム マスター ページにアクセスする場合、マスター ページのプレビュー ファイルも作成する必要があります。詳細については、「 [SharePoint 2013 でのマスター ページ プレビュー ファイルを作成する方法](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)」を参照してください。
    
  
- **カスタム マスター ページが SharePoint 2010 CSS ファイルに依存している場合:** CSS ファイルは SharePoint 2010 から SharePoint 2013 で大幅に変更されました。多くの場合、アップグレードされたサイトへの適用が成功するには、新しいクラスを使用できるように、マスター ページを変更する必要があります。CSS クラスの詳細については、「 [SharePoint アドインの UX 設計ガイドライン](http://msdn.microsoft.com/library/a4a8f53c-27d7-43dc-b6db-aa7b1f1c7d45%28Office.15%29.aspx)」の「 **SharePoint アプリでホスト Web の CSS を使用する** 」セクションを参照してください。
    
  

## SharePoint 2010 CSS とカスタム CSS ファイル
<a name="CSS"> </a>

SharePoint 2010 CSS ファイルとカスタム CSS ファイルを変更しないと、SharePoint 2013 サイトで使用できません。次に、SharePoint 2010 CSS とカスタム CSS ファイルに適用する SharePoint 2013 の変更点について説明します。
  
    
    

- **カラー スロット**。使用できるカラー スロットの数は SharePoint 2013 で大幅に増えました。新しいテーマ エクスペリエンスで SharePoint 2010 CSS ファイルを使用するには、その CSS ファイルのカラー スロットを更新する必要があります。詳細については、「 [SharePoint 2013 のカラー パレットとフォント](color-palettes-and-fonts-in-sharepoint-2013.md)」の「 [カラー スロットのマッピング](color-palettes-and-fonts-in-sharepoint-2013.md#colorSlots)」セクションを参照してください。
    
  
- **フォント スロット**。使用できるフォント スロットの一覧を見直し、SharePoint 2013 で使用する CSS ファイルが、正しいフォント スロットを使用していることを確認します。詳細については、「 [SharePoint 2013 のカラー パレットとフォント](color-palettes-and-fonts-in-sharepoint-2013.md)」の [フォント スロット](color-palettes-and-fonts-in-sharepoint-2013.md#fontSlot)」セクションを参照してください。
    
  
- **新しい注釈**。SharePoint 2013 には、背景画像を置き換えることができる新しい注釈があります。詳細については、「 [SharePoint 2013 でカスタム CSS ファイルをテーマ設定対応にする方法](how-to-make-custom-css-files-themable-in-sharepoint-2013.md)」を参照してください。
    
  
- **新しいクラス**。場合によっては、SharePoint 2013 の新しいクラスを使用できるように CSS ファイルを更新する必要があります。CSS クラス (CSS スタイルとも呼ばれます) の詳細については、「 [SharePoint アドインの UX 設計ガイドライン](http://msdn.microsoft.com/library/a4a8f53c-27d7-43dc-b6db-aa7b1f1c7d45%28Office.15%29.aspx)」の「 **SharePoint アプリでホスト Web の CSS を使用する** 」セクションを参照してください。
    
  

## その他のリソース
<a name="addresources"> </a>


-  [SharePoint 2013 のテーマの概要](themes-overview-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのマスター ページ プレビュー ファイルを作成する方法](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でカスタム テーマを展開する方法](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のカラー パレットとフォント](color-palettes-and-fonts-in-sharepoint-2013.md)
    
  
-  [SharePoint チーム ブログ: SharePoint テーマでスタイルを際立たせる](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  
-  [SharePoint 2013 デザイン マネージャーのブランドおよびデザイン機能](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  

