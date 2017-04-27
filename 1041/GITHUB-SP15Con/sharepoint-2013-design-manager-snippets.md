---
title: SharePoint 2013 デザイン マネージャー スニペット
ms.prod: SHAREPOINT
ms.assetid: 68caef4c-5941-4a88-b34b-f88122801cef
---


# SharePoint 2013 デザイン マネージャー スニペット
スニペットとは、ナビゲーション バーや Web パーツといった SharePoint のコンポーネントまたはコントロールを HTML で表現したものです。デザイン マネージャーでスニペット ギャラリーを使用することにより、HTML のマスター ページやページ レイアウトに SharePoint の機能を簡単に追加できます。
## スニペットおよびスニペット ギャラリーの概要
<a name="Introduction"> </a>

マスター ページを変換するか、ページ レイアウトを作成すると、ページの HTML バージョンが作成されます。スニペット ギャラリーを使用すると、SharePoint の特定の機能 (検索、ナビゲーション、デバイス チャネル パネルなど) を、マスター ページまたはページ レイアウトに関連付けられた HTML ファイルに簡単に追加できます。スニペット ギャラリーはデザイン マネージャー内のページであり、以下のことが可能です。
  
    
    

- リボンで使用できる SharePoint コンポーネントから選択します。
    
  
- そのコンポーネントのプロパティを構成します。
    
  
- コンポーネントの外観をブラウザーでプレビューします。
    
  
- HTML コード スニペットをクリップボードにコピーします。そこからは、HTML ファイル内の適当な場所にスニペットを貼り付けることができます。
    
  
スニペット ギャラリーのリボンには、マスター ページまたはページ レイアウトのどちらを編集しているかにより、異なるオプションが表示されます。たとえば、ナビゲーション コントロールはマスター ページに対してのみ表示され、Web パーツ領域とページ フィールド コントロールはページ レイアウトに対してのみ表示されます。また、ページ レイアウトを編集しているときに使用できるページ フィールドは、編集しているページ レイアウトのコンテンツ タイプに依存します。
  
    
    
スニペットを HTML ファイルに貼り付けた後は、スニペットで提供される HTML からデザインタイム プレビューが得られます。また、デザイン マネージャーでサーバー側プレビューを使用して、実際のサイトでコントロールがどのように表示されるかを見ることもできます。デザインタイム プレビューには静的なサンプル データを含めることができますが、サーバー側プレビューでは実際のデータを使用します (使用できる場合)。たとえば、用語セットからのナビゲーション リンクを描画するナビゲーション コントロールは、サーバー側プレビューでは用語を動的に表示しますが、デザインタイム プレビューではスニペットを作成した時点での用語の静的なスナップショットを使用します。ただし、多くの Web パーツを含む一部のスニペットでは、サーバー側プレビューで実際のデータを使用できません。その場合は、サーバー側プレビューに [ **プレビューを使用できません**] と表示されることがあります。
  
    
    

> **メモ**
> スニペットには HTML エディターでデザインタイム プレビューを提供する HTML マークアップが含まれますが、"プレビュー開始" コメントおよび "プレビュー終了" コメントに含まれる HTML マークアップは、デザインタイム プレビューのみに影響し、SharePoint によるそのスニペットの最終的なレンダリングには影響しないので、編集しないようにする必要があります。スニペットのスタイルを設定するには、通常、スニペットに適用される既定の SharePoint スタイルを識別してオーバーライドする必要があります。 
  
    
    


  
    
    

## スニペット ギャラリーからスニペットを挿入する
<a name="InsertSnippet"> </a>

スニペット ギャラリーに表示されるオプションは、編集中のファイルによって異なります。たとえば、ページ レイアウトが異なると、レイアウトで使用できるページ フィールドのセットが異なります。そのため、スニペット ギャラリーに移動するには、最初に編集するマスター ページまたはページ レイアウトを選択する必要があります。
  
    
    

### スニペットを挿入するには


1. 発行サイトに移動します。
    
  
2. ページの右上隅で、歯車の形の [設定] アイコンをクリックし、[ **デザイン マネージャー**] をクリックします。
    
  
3. デザイン マネージャーの左のナビゲーション ウィンドウで、編集しているファイルの種類によって、[ **マスター ページの編集**] または [ **ページ レイアウトの編集**] をクリックします。
    
  
4. スニペットを追加するマスター ページまたはページ レイアウトの名前を選択します。
    
  
5. スニペット ギャラリーを開くには、サーバー側プレビューの右上隅で、[ **スニペット**] をクリックします。
    
  
6. リボンの [ **デザイン**] タブで、ページに追加するスニペットを選択します。
    
    スニペットを選択すると、スニペット ギャラリーが更新されて、そのスニペットのプレビュー、そのスニペットで使用できるプロパティ、および HTML マスター ページまたはページ レイアウトにコピーできる HTML コード スニペットが、ページに表示されるようになります。
    
  
7. スニペット ギャラリーの右側の [ **このコンポーネントについて**] の下で、セクション ヘッダーをクリックまたは選択して、プロパティのグループを展開するか、折りたたむかして、必要なカスタム設定を構成します。
    
    スニペットの主要な目的にとって最も重要なプロパティは、先頭の [重要] セクションに表示されます。スニペットを使用するときは、これらの重要なプロパティを理解しておく必要があります。
    
    
    
    > **メモ**
      > プロパティ グリッドに AjaxDelta で終わるヘッダーがある場合、それらはダウンロード最小化戦略に関係のあるコントロールに適用されるものであり、デザイン マネージャーで作成されるマスター ページおよびページ レイアウトではダウンロード最小化戦略は無効になっているので、これらのプロパティは無視する必要があります。 
8. プロパティを構成した後、[ **更新**] をクリックします。これによって、ページの左側のプレビューと HTML スニペットが更新され、マークアップにカスタム設定が反映されます。いつでも [ **リセット**] をクリックして、すべてのプロパティを既定の設定に戻すことができます。
    
  
9. スニペット ギャラリーの左側で、[ **HTML スニペット**] の下の [ **クリップボードにコピー**] をクリックします。
    
  
10. HTML エディターで、コンピューター上のマップされたネットワーク ドライブを開き、スニペットを追加するマスター ページまたはページ レイアウトの HTML ファイルを開きます。
    
  
11. HTML ファイルの中の、マークアップを表示する場所にスニペットを貼り付けます。
    
    各スニペットには、コンポーネントとサンプル データの視覚的プレビューを提供する HTML が含まれます。 **<!--PS>** タグおよび **<!--PE>** タグの内部の読み取り専用プレビューに対するこの HTML は、変更しないでください。このマークアップは、スニペットのデザインタイム プレビューにのみ影響し、実際のサイトでのスニペットの表示には影響しません。
    
  
12. スニペットのサーバー側プレビューを表示するには、HTML ファイルを保存して、変更を関連する ASP.NET ファイルに同期した後、デザイン マネージャーでサーバー側プレビューの表示を更新します。
    
    デザインタイム プレビューとは異なり、サーバー側プレビューでは SharePoint によってレンダリングされたコントロールが表示されます。
    
  

## HTML スニペットのマークアップの概要
<a name="UnderstandMarkup"> </a>

スニペットには 4 つの基本セクションが含まれます。
  
    
    

- **ヘッダー**は、 **<div>** および **<!--CS>** タグで開始します (カスタム ASP.NET スニペットは例外で、 **<div>** タグにラップされません)
    
  
- **SharePoint マークアップ**は、スニペットが **<!--MS>** 開始タグと **<!--ME>** 終了タグで囲まれています
    
  
- **HTML プレビュー**は、 **<!--PS>** 開始タグと **<!--PE>** 終了タグで囲まれています
    
  
- **フッター**は、 **<!--CE>** および **</div>** タグで終了します
    
  
HTML プレビューを除くスニペットのすべてのセクションは、HTML コメントで囲まれて、ドキュメント オブジェクト モデル (DOM) および既存のスタイルと相互作用できないようになっています。スニペットは、コンポーネントの名前で開始し、その後に実際の ASP.NET マークアップおよびデザインタイム レンダリング用の HTML プレビューが含まれ、終了タグで終了します。ASP.NET マークアップはコメント化されていますが、HTML ファイルが .master ファイルまたは .aspx ファイルに同期されると、SharePoint によってコメント タグが除去されて、このマークアップが使用されます。ASP.NET についての知識がある場合は、スニペット内のこのマークアップをカスタマイズできます。
  
    
    
例として、編集モード パネルの既定のマークアップを次に示します。このパネルは、他のコンテンツやコントロールを条件付きで表示する単純なコンテナーです。
  
    
    

### ヘッダー


```HTML

<div data-name="EditModePanelShowInEdit">
    <!--CS: Start Edit Mode Panel Snippet-->
```


### SharePoint マークアップ


```HTML

<!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
```


### HTML プレビュー


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
        <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
        You should replace this div with content that renders based on your Edit Mode Panel Properties.
    
        </div>
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)--><!--PE: End of READ-ONLY PREVIEW-->
```


### フッター


```HTML

<!--ME:</Publishing:EditModePanel>-->
    <!--CE: End Edit Mode Panel Snippet-->
</div>
```

次に示すのは、トップ ナビゲーション スニペットの既定のマークアップです。このスニペットはもう少し複雑であり、複数の異なるコントロールが含まれ、一部は相互にネストしており、ナビゲーション用語のデータ ソース、委任コントロール、コンテンツ プレースホルダーが含まれます。
  
    
    

> **メモ**
> コンテンツ プレースホルダーなどの一部のコントロールは、ページ上で視覚的な表現を必要としない要素なので、HTML プレビュー用のタグが空になっています。 
  
    
    


### ヘッダー


```HTML

<div data-name="TopNavigationNoFlyoutWithStartNode">
<!--CS: Start Top Navigation Snippet-->    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
```


### SharePoint マークアップ


```HTML

<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<SharePoint:AjaxDelta ID="DeltaTopNavigation" BlockElement="true" CssClass="ms-displayInline ms-core-navigation ms-dialogHidden" runat="server">-->
```


### HTML プレビュー


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint マークアップ


```HTML

<!--MS:<SharePoint:DelegateControl runat="server" ControlId="TopNavigationDataSource" Id="topNavigationDelegate">-->
```


### HTML プレビュー


```HTML
<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<span style="display:none">
<table cellpadding="4" cellspacing="0" style="font:messagebox;color:buttontext;background-color:buttonface;border: solid 1px;border-top-color:buttonhighlight;border-left-color:buttonhighlight;border-bottom-color:buttonshadow;border-right-color:buttonshadow">
<tr><td nowrap="nowrap">
<span style="font-weight:bold">PortalSiteMapDataSource</span> - topSiteMap</td></tr><tr><td></td></tr></table></span>
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint マークアップ


```HTML

<!--MS:<Template_Controls>-->
<!--MS:<asp:SiteMapDataSource ShowStartingNode="True" SiteMapProvider="SPNavigationProvider" ID="topSiteMap" runat="server" StartingNodeUrl="sid:1002">-->
```


### SharePoint マークアップ


```HTML

<!--ME:</asp:SiteMapDataSource>-->
<!--ME:</Template_Controls>-->
<!--ME:</SharePoint:DelegateControl>--><a name="startNavigation"></a>
```


### SharePoint マークアップ


```HTML

<!--MS:<asp:ContentPlaceHolder ID="PlaceHolderTopNavBar" runat="server">-->
<!--MS:<SharePoint:AspMenu ID="TopNavigationMenu" runat="server" EnableViewState="false" DataSourceID="topSiteMap" AccessKey="&amp;#60;%$Resources:wss,navigation_accesskey%&amp;#62;" UseSimpleRendering="true" UseSeparateCss="false" Orientation="Horizontal" StaticDisplayLevels="2" AdjustForShowStartingNode="false" MaximumDynamicDisplayLevels="0" SkipLinkText="">-->
```


### HTML プレビュー


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<link rel="stylesheet" type="text/css" href="/_layouts/15/1033/styles/menu-21.css" />
<div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox">
<ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static">
<li class="static">
<a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" tabindex="0" title="Default Publishing Site" href="/sites/PubSite/Pages/default.aspx" accesskey="1">
<span class="additional-background ms-navedit-flyoutArrow">
<span class="menu-item-text">Default Publishing Site</span></span></a></li></ul></div>
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint マークアップ


```HTML

<!--ME:</SharePoint:AspMenu>-->
<!--ME:</asp:ContentPlaceHolder>-->
```


### HTML プレビュー


```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
<!--PE: End of READ-ONLY PREVIEW-->
```


### SharePoint マークアップ


```HTML

<!--ME:</SharePoint:AjaxDelta>-->
```


### フッター


```HTML
<!--CE: End Top Navigation Snippet-->
</div>
```


### マークアップの種類

ここでは、スニペットに含まれるマークアップの種類を詳細に示します。
  
    
    
 **SharePoint 名前空間登録** SPM ("SharePoint マークアップ") は、SharePoint 名前空間を登録する行を示します。
  
    
    



```HTML

<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
```

 **コメント** CS および CE ("コメント開始" および "コメント終了") は、マークアップの行の解析に役立ちます。
  
    
    



```HTML
<!--CS: Start Top Navigation Snippet-->
…
<!--CE: End Top Navigation Snippet-->

```

 **スニペット** MS および ME ("マークアップ開始" および "マークアップ終了") は、SharePoint コントロールまたはスニペットの開始と終了を示します。リボンや前記のトップ ナビゲーション コントロールなどの一部のスニペットには、単一のスニペット内にネストされた複数のコントロールが含まれます。
  
    
    



```HTML

<!--MS:<SharePoint:DelegateControl runat="server" ControlId="TopNavigationDataSource" Id="topNavigationDelegate">-->
…
<!--ME:</SharePoint:DelegateControl>--><a name="startNavigation"></a>

<!--MS:<Template_Controls>-->
…
<!--ME:</Template_Controls>-->

<!--MS:<asp:SiteMapDataSource ShowStartingNode="True" SiteMapProvider="SPNavigationProvider" ID="topSiteMap" runat="server" StartingNodeUrl="sid:1002">-->
…
<!--ME:</asp:SiteMapDataSource>-->

```

 **プレビュー ブロック** PS および PE ("プレビュー開始" および "プレビュー終了") は、編集してはならない HTML コードのセクションを囲みます。これらのプレビュー セクションは、そのスニペットが挿入している SharePoint コントロールのスナップショットです。プレビューにより、クライアント側 HTML エディターで HTML ファイルをいっそう意味のあるものにできます。ただし、プレビューでコンテンツまたはスタイルを変更しても、SharePoint が最終的に使用する .master ファイルにその効果は残りません。スニペットのスタイルを設定するには、SharePoint のスタイルを識別し、カスタム CSS でオーバーライドする必要があります。
  
    
    



```HTML

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><span style="display:none"><table cellpadding="4" cellspacing="0" style="font:messagebox;color:buttontext;background-color:buttonface;border: solid 1px;border-top-color:buttonhighlight;border-left-color:buttonhighlight;border-bottom-color:buttonshadow;border-right-color:buttonshadow"><tr><td nowrap="nowrap"><span style="font-weight:bold">PortalSiteMapDataSource</span> - topSiteMap</td></tr><tr><td></td></tr></table></span><!--PE: End of READ-ONLY PREVIEW-->

<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><link rel="stylesheet" type="text/css" href="/_layouts/15/1033/styles/menu-21.css" /><div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox"><ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static"><li class="static"><a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" tabindex="0" title="Default Publishing Site" href="/sites/PubSite/Pages/default.aspx" accesskey="1"><span class="additional-background ms-navedit-flyoutArrow"><span class="menu-item-text">Default Publishing Site</span></span></a></li></ul></div><!--PE: End of READ-ONLY PREVIEW-->
```


## その他の技術情報
<a name="Resources"> </a>


-  [方法: SharePoint 2013 で HTML ファイルをマスター ページに変換する](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [SharePoint Server 2013 での編集モード パネル スニペットを追加する方法](how-to-add-an-edit-mode-panel-snippet-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でセキュリティによるトリミングのスニペットを追加する方法](how-to-add-a-security-trim-snippet-in-sharepoint-2013.md)
    
  

