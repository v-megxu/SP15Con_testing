---
title: SharePoint 2013 で CSS を使ってスニペットをブランド化する方法
ms.prod: SHAREPOINT
ms.assetid: d18d07b6-1a6b-4589-a65c-932b67cef595
---


# SharePoint 2013 で CSS を使ってスニペットをブランド化する方法
スニペットのスタイルを設定するには、既定のスタイルをカスタム CSS で上書きします。要素に適用されるすべての既定スタイルを上書きするには、CSS ID と要素セレクターを使用します。または、HTML エディターや、Internet Explorer の F12 開発者ツールなどのツールを使用して、特定の既定スタイルの識別や上書きを行うこともできます。
## CSS を使用したスニペットのスタイル設定の概要
<a name="Introduction"> </a>

HTML マスター ページを変換したり、HTML ページ レイアウトを作成したら、デザイン マネージャーのサーバー側のプレビューでそのページをプレビューすることができます。プレビュー ページからスニペット ギャラリーに移動し、スニペットを自分の HTML ファイルにコピーできます。スニペットとは、トップ ナビゲーション コントロールや検索ボックスなど、SharePoint コントロールを HTML で表現したものです。
  
    
    
マップされたドライブの HTML ファイルにスニペットをコピーして、変更を保存した後、HTML ファイルのサーバー側プレビューを更新して、コントロールがどのように表示されるか確認できます。スニペットには、デザイン時に HTML エディターでプレビューできるマークアップがあります。ただし、このマークアップは読み取り専用で、サーバーでどのようにレンダリングされるかに影響を与えないため、このマークアップを編集することはできません。それに対して、サーバー側のプレビューでは、使用できる場合はライブ データを使用して、完全に忠実なプレビューを表示します。たとえば、ナビゲーション コントロールでは、管理ナビゲーション用の SharePoint 用語ストアなどのデータ ソースのライブ データを使用して、サイトの現在のナビゲーション構成を表示します。
  
    
    

> **メモ**
> ネットワーク ドライブのマッピングの詳細については、「 [[方法]: SharePoint 2013 マスター ページ ギャラリーへのネットワーク ドライブの割り当て](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)」を参照してください。 
  
    
    

既定では、スニペットは corev15.css などの SharePoint 2013 スタイル シートからスタイルを継承します。スニペットのスタイルを設定するには、既定のスタイルをカスタム CSS で上書きする必要があります。そのためには、次の操作を実行します。
  
    
    

- CSS ID と要素セレクターを使用して、選択した要素に適用する規定のスタイルを完全に上書きします。
    
  
- Internet Explorer の F12 開発者キットなど、ブラウザ ベースのツールを使用して、デザイン マネージャーのサーバー側のプレビューに表示されている既定のスタイルを調べ、上書きする特定のスタイルを識別します。
    
  
- HTML エディターの機能を使用してスニペットの読み取り専用プレビューで既定のスタイルを調べ、上書きする特定のスタイルを識別します。 
    
  
Internet Explorer の開発者ツールを使用して既定のスタイルを識別するには、デザイン マネージャーのサーバー側のプレビューを使用して、HTML マスター ページまたはページ レイアウトを表示する必要があります。 **F12** キーを押すと、開発者ツールが起動します。[ **検索**] メニューを選択し、[ **クリックで要素を選択**] を選択します。これにより、ページ上の要素をクリックし、HTML マスター ページまたはページ レイアウトがリンクされているカスタム スタイル シートに CSS を追加することで、上書きされるスタイルがどのように表示されるかを正確に確認することができます。
  
    
    
既定の SharePoint 2013 スタイル シートには多くのスタイルが含まれているため、特定のスタイルを識別することが困難になることがあります。ブラウザベースのツールの代替として、スニペット ギャラリーから HTML ファイルにスニペットをコピーし、HTML エディターを使って、スタイルを特定することができます。使用する HTML エディターによっては、この方法の方が簡単なことがあります。スニペット ギャラリーで [ **更新**]、[ **クリップボードにコピー**] の順に選択すると、スニペットにそのスニペットの HTML プレビューが含まれます。スニペットを HTML ファイルにコピーしたら、スニペットに含まれている、読み取り専用のプレビューで使用されるスタイルを確認することができます。このようにして、既定のスタイルのより小さなサブセットを分析します。
  
    
    
スニペットとカスタマイズの規模によっては、上書きする特定の既定スタイルを選択する代わりに、CSS ID と要素セレクターを使って、既定のスタイルをすべて選択し、完全に上書きすることをお勧めします。次の例では、この方法を使って、トップ ナビゲーション スニペットにカスタム スタイルを適用する方法を説明します。
  
    
    

## 例: トップ ナビゲーション スニペットのスタイル設定
<a name="Example"> </a>

トップ ナビゲーション スニペットは、最も一般的に使われるスニペットの 1 つで、最も一般的なブランドのスニペットの 1 つです。SharePoint 2013 サイトでは、用語ストアがトップ ナビゲーション スニペットのデータ ソースとなるように、管理ナビゲーションを使用するオプションを選択します。このように、[ **サイトの設定**] の用語ストア管理ツールを使用して、ナビゲーション用語の追加や削除を行ったり、トップ ナビゲーション スニペットによって表示されるナビゲーションの分類を管理したりできます。 
  
    
    
この例では、トップ ナビゲーション コントロールによって、用語ストアからエントリを取得できるように、サイトで管理ナビゲーションが使用されています。 **コンピューター**など、トップ ナビゲーション用語にカーソルを合わせると、1 つのレベルのフライアウトが表示されます。このセクションでは、これらのカスタム スタイルがどのように既定の SharePoint スタイルを上書きするかを説明します。
  
    
    

### サンプル 1: HTML モックアップ ファイルからのナビゲーション

マスター ページ用に HTML モックアップを設計する場合、多くの場合はデザイン マネージャーを使用する前に、HTML と CSS を使用して機能上のトップ ナビゲーション要素を作成します。この HTML サンプルでは、トップ ナビゲーション用の基本構造 (ID とクラス名を持つ **<div>** 要素、トップ ナビゲーション エントリのリスト、各フライアウト サブメニューの入れ子のリストなど) が使用されています。
  
    
    

```HTML

<div id="navigation" class="msax-Navigation">
   <ul>
      <li><a href="#">Cameras</a>
         <ul>
            <li><a href="#">Camcorders</a></li>
            <li><a href="#">Digital cameras</a></li>
            <li><a href="#">Disposable cameras</a></li>
            <li><a href="#">Film cameras</a></li>
         </ul>
      </li>
      <li><a href="#">Computers</a>
         <ul>
            <li><a href="#">Desktops</a></li>
            <li><a href="#">Laptops</a></li>
            <li><a href="#">Netbooks</a></li>
            <li><a href="#">Tablets</a></li>
         </ul>
      </li>
      <li><a href="#">Media</a>
         <ul>
            <li><a href="#">Movies</a></li>
            <li><a href="#">Music</a></li>
            <li><a href="#">TV shows </a></li>
            <li><a href="#">Video games </a></li>
         </ul>
      </li>
      <li></li>
   </ul>
</div>

```


### サンプル 2: カスタム CSS を使用してスタイル設定されたナビゲーション

モックアップ HTML ファイルで既定の SharePoint スタイルを上書きするには、最後の **</head>** タグの直前に、CSS ファイルへの標準リンク `(<link rel="stylesheet" type="text/css" href="URLtoYourCustomCSSFile"/>`) を記述します。
  
    
    
これらの HTML および CSS のサンプルでは、次の点に注意してください。
  
    
    

- ナビゲーション エントリは、 **<ul>** タグまたは **<li>** タグにクラスを直接適用するのではなく、 `.msax-Navigation ul li` という形式を使用して、スタイル設定されます。
    
  
- スタイルは  `.msax-Navigation ul>li` ではなく、 `.msax-Navigation ul li` という構文を使用します。これはスニペット マークアップでは選択した要素の間に **<div>** タグが含まれる可能性があるためです。
    
  
- HTML モックアップには空の **<li></li>** 要素が最上位の **<ul>** の最後のエントリとして含まれています。これは、管理ナビゲーションをオンにした場合、SharePoint がトップ ナビゲーションへの最後のエントリとして [ **リンクの編集**] コマンドを追加し、最終的にサイトは通常、このオプションを表示する必要がないためです。CSS サンプルは  `.msax-Navigation ul li:last-child` を使用してこのエントリを選択し、表示値を `none` に設定します。HTML ファイル内の空の **<li></li>** 要素は、既定の [ **リンクの編集**] のエントリに一時的に置き換えられます。サイトで管理ナビゲーションを使用し、CSS で任意の  `li:last-child` セレクターを使用している場合は、この最後の **<li>** 要素に注意してください。
    
  



```HTML

.msax-Navigation {
margin: 10px 0px; top: 0px; position: relative;
z-index:200;
}
.msax-Navigation a {
margin: 0px; padding: 0px; border: 0px currentColor;
}
.msax-Navigation ul {
list-style: none; margin: 0px; padding: 0px; font-size: 16px; z-index:200;
}
.msax-Navigation ul li {
padding: 10px; display: inline-block; position: relative; z-index:200;
}
.msax-Navigation ul li:first-child {
margin: 0px;
}
.msax-Navigation ul li:last-child {
margin: 0px; padding: 0px; display: none;
}
.msax-Navigation ul li a.selected, .msax-Navigation ul li.selected {
background-color: rgb(58,60,62) !important;
color:rgb(255,255,255) !important;
}
.msax-Navigation ul li a {
width: 100%; color: rgb(58,60,62); font-size: 16px;
}
.msax-Navigation ul li:hover {
background-color: rgb(58,60,62);
color:rgb(255,255,255) !important;
}
.msax-Navigation ul li a:hover {
text-decoration: none;
color:rgb(255,255,255) !important;
}
.msax-Navigation li ul {
left: 0px; top: 35px; display: none; position: absolute; min-width: 100px; box-shadow: 5px 5px 10px 0px rgb(0,0,0); background-color: rgb(58,60,62);
}
.msax-Navigation li:hover ul {
display: block; z-index: 150;
}
.msax-Navigation li li {
margin: 0px; padding: 5px 10px 5px 0px; border-top-width: 0px; display: block; min-width: 100px;
}
.msax-Navigation li li:last-child {
margin: 0px; padding: 5px 10px 5px 0px; border-top-width: 0px; display: block; min-width: 100px;
}
.msax-Navigation li li a {
width: 100%; padding-left: 10px; display: block; color:rgb(255,255,255) !important;
}
.msax-Navigation li li:hover {
background-color: rgb(120, 120, 120);
}

```


### 例 3: トップ ナビゲーション スニペットの読み取り専用プレビュー

カスタム スタイルを HTML モックアップに実装し、機能上のトップ HTML を設定したら、次の一般的な手順を実行してください。
  
    
    

1. ネットワーク ドライブをマッピングします。
    
  
2. デザイン ファイルをアップロードします。
    
  
3. HTML ファイルをマスター ページに変換します。
    
  
4. プレビューし、問題があれば修正します。
    
  
5. スニペット ギャラリーを使用して、トップ ナビゲーション スニペットを HTML マスター ページに追加します。
    
  
トップ ナビゲーション スニペットのプロパティを設定する場合、スニペット ギャラリーで次の点に注意してください。
  
    
    

- トップの **重要な**セクションでは、 **CssClass** プロパティを変更しないでください。
    
  
- **AjaxDelta** 見出しの下のプロパティを変更しないでください。これらのプロパティは SharePoint が HTML を対応する ASP.NET スニペットに変更するために使用する MDS スニペットに関連しているためです。これは、トップ ナビゲーション スニペットだけでなく、すべてのスニペットに該当します。
    
  
- 既定の SharePoint スタイルを上書きする場合は、スニペット ギャラリーの [ **AspMenu**] の下の [ **Behavior**] セクション (スニペットに委任コントロールなど複数のコントロールが含まれている場合、複数の **Behavior** セクションが存在していることがあります) で、 **ClientIDMode** を **Static** に設定してください。 **ClientIDMode** 設定を既定の **Inherit** のままにすると、スニペットの適用済み CSS クラスは、ページ上のスニペットの順番に基づいて変更されます。 **ClientIDMode** の詳細については、「 [Control.ClientIDMode プロパティ](http://msdn.microsoft.com/ja-jp/library/system.web.ui.control.clientidmode.aspx)」を参照してください。
    
    たとえば既定では、トップ ナビゲーション コントロールは、既定の SharePoint ID 属性 ( **zz5_TopNavigationMenu**、 **zz6_RootAspMenu** など) を使用します。 **ClientIDMode** を **Static** に変更することで、これらの既定の ID を独自の CSS のセレクターとして使用し、既定の SharePoint スタイルを上書きすることができます。
    
  
- 一部のプロパティは、既定の動的 CSS と JavaScript の動作 (たとえば既定では、 **UseSimpleRendering** は **True** に、 **MaximumDynamicDisplayLevels** は **0** に設定されています) を削除することで、トップ ナビゲーション スニペットを簡単にブランド化するように設定済みです。トップ ナビゲーションの特定のプロパティの詳細については、「 [AspMenu プロパティ](http://msdn.microsoft.com/ja-jp/library/ms412476.aspx)」と「 [Menu プロパティ](http://msdn.microsoft.com/ja-jp/library/282668a1.aspx)」を参照してください。
    
  
スニペット ギャラリーでトップ ナビゲーション スニペットを構成した後、[ **更新**]、[ **クリップボードにコピー**] の順に選択します。HTML マスター ページで、モックアップ コントロールを含んでいるナビゲーション  `<div id="navigation" class="msax-Navigation">` の内容を削除し ( **<div>** タグの内容だけを削除します。 **<div>** タグ自体は削除しません)、スニペットをナビゲーション **<div>** にコピーします。必要に応じて、ナビゲーション **<div>** を再配置します。通常は `<div id="s4-bodyContainer">` タグの開始直後で、 `PlaceHolderMain` を含んでいる **<div>** の前です。
  
    
    
前述のナビゲーション **<div>** の HTML と簡単に比較するため、次のサンプルにトップ ナビゲーション スニペットのナビゲーション **<div>** 部を含めました。これはスニペット全体ではないという点に注意してください。
  
    
    



```HTML

<div id="zz7_TopNavigationMenu" class=" noindex ms-core-listMenu-horizontalBox">
     <ul id="zz9_RootAspMenu" class="root ms-core-listMenu-root static">
          <li class="static">
          <a accesskey="1" class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras" tabindex="0">
          <span class="additional-background ms-navedit-flyoutArrow">
          <span class="menu-item-text">Cameras</span></span></a><ul class="static">
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/camcorders" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Camcorders</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/digital-cameras" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Digital cameras</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/disposable-cameras" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Disposable cameras</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/cameras/film-cameras" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Film cameras</span></span></a></li>
          </ul>
          </li>
          <li class="static">
          <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers" tabindex="0">
          <span class="additional-background ms-navedit-flyoutArrow">
          <span class="menu-item-text">Computers</span></span></a><ul class="static">
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/desktops" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Desktops</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/laptops" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Laptops</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/netbooks" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Netbooks</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/computers/tablets" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Tablets</span></span></a></li>
          </ul>
          </li>
          <li class="static">
          <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media" tabindex="0">
          <span class="additional-background ms-navedit-flyoutArrow">
          <span class="menu-item-text">Media</span></span></a><ul class="static">
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/movies" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Movies</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/music" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Music</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/tv-shows" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">TV shows</span></span></a></li>
               <li class="static">
               <a class="static menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" href="/sites/PubSite/media/video-games" tabindex="0">
               <span class="additional-background ms-navedit-flyoutArrow">
               <span class="menu-item-text">Video games</span></span></a></li>
          </ul>
          </li>
          <li class="static ms-verticalAlignTop ms-listMenu-editLink ms-navedit-editArea">
          <span id="zz7_TopNavigationMenu_NavMenu_Edit" class="ms-navedit-editSpan">
          <a id="zz7_TopNavigationMenu_NavMenu_EditLinks" class="ms-navedit-editLinksText" href="#" onclick="g_QuickLaunchMenu = null; EnsureScriptParams('quicklaunch.js', 'QuickLaunchInitEditMode', 'zz7_TopNavigationMenu', 2, 0, 0, ''); cancelDefault(event); return false;">
          <span class="ms-displayInlineBlock">
          <span class="ms-navedit-editLinksIconWrapper ms-verticalAlignMiddle">
          <img class="ms-navedit-editLinksIcon" src="/_layouts/15/images/spcommon.png?rev=23" /></span><span class="ms-metadata ms-verticalAlignMiddle">Edit Links</span></span></a><span id="zz7_TopNavigationMenu_NavMenu_Loading" class="ms-navedit-menuLoading ms-hide"><a id="zz7_TopNavigationMenu_NavMenu_GearsLink" href="#" onclick="HideGears(); return false;" title="This animation indicates the operation is in progress. Click to remove this animated image."><img id="zz7_TopNavigationMenu_NavMenu_GearsImage" src="/_layouts/15/images/loadingcirclests16.gif?rev=23" /></a></span><div id="zz7_TopNavigationMenu_NavMenu_ErrorMsg" class="ms-navedit-errorMsg">
          </div>
          </span></li>
     </ul>
</div>

```

カスタム スタイルだけを使用する代わりに、特定のスタイルだけを上書きするシナリオも考えられます。たとえば、[ **リンクの編集**] ノードを非表示にするには、既定の ID **zz7_TopNavigationMenu_NavMenu_Edit** を使用するカスタム スタイルを作成し、表示設定を `none` に設定することができます。
  
    
    

## その他の技術情報
<a name="Additional"> </a>


-  [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md)
    
  
-  [SharePoint 2013 のデザイン マネージャーの概要](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [方法: SharePoint 2013 で HTML ファイルをマスター ページに変換する](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のサイト デザインの開発](develop-the-site-design-in-sharepoint-2013.md)
    
  

