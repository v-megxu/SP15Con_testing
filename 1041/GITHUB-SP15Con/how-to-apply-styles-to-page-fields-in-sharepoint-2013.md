---
title: SharePoint 2013 でページ フィールドにスタイルを適用する方法
ms.prod: SHAREPOINT
ms.assetid: e227613d-0e4d-4312-924d-bb55e1fe4293
---


# SharePoint 2013 でページ フィールドにスタイルを適用する方法
ページ レイアウトでは、ページ フィールドにスタイルを適用できます。また、ページ レイアウトからページを作成する場合、これらのスタイルはコンテンツ作成者によって追加されるすべてのコンテンツに適用されます。
## ページ フィールドへのスタイルの適用の概要
<a name="Introduction"> </a>

デザイナーとして、ページ レイアウトおよびページ レイアウトから作成されたページで、ページ フィールドの配置およびスタイル指定を最終的に制御します。コンテンツ作成者がブラウザーからページを作成する場合、ページのページ フィールドを移動したり、デザイナーが指定したスタイルを上書きすることはできません。これにより、ブランドはサイトのすべてのページで整合性を保持できます。
  
    
    
スタイルをページ フィールドに適用する場合、検討するフィールド型には 2 つの基本カテゴリがあります。
  
    
    

- **RichHtmlField 以外のフィールド型** ページ レイアウトを構成しているページ フィールドは、そのページ レイアウトのコンテンツ タイプに一致します。ページ フィールドは、テキストの 1 行 (TextField) またはテキストの複数行 (NoteField) などの多くの種類である場合があります。デザイナーは、ページ レイアウト上のページ フィールドにスタイルを適用して、同様の方法でこれらのページ フィールドのすべてにスタイルを適用できます。
    
  
- **RichHtmlField** リッチ HTML フィールド コントロール (発行 HTML フィールドとも呼ばれる) は、ページ レイアウトで最も強力であり頻繁に使用されるコントロールの 1 つです。既定では、リッチ HTML フィールドでは、コンテンツ作成者はリボンを使用し、書式設定してスタイルをコンテンツに適用し、表、イメージやビデオなどのメディア、および Web パーツを挿入します。このフィールド型は、制御可能なパラメータ内のコンテンツをコンテンツ作成者が自由に追加およびスタイル指定できるようにする場合に便利です。次の 2 つの方法で RichHtmlField を制御できます。
    
  - **カスタム スタイル シートの作成** 既定では、RichHtmlField のリボンに使用できるスタイルは、HtmlEditorStyles.css という名前のスタイル シートから渡されます。自分のカスタム スタイルが、それを使用するコンテンツ作成者のリボンに表示されるように、このスニペットの **PrefixStyleSheet** プロパティを設定できます。
    
  
  - **Allow プロパティの設定** RichHtmlField のスニペットには、 **Allow** で始まる使用可能な 28 個のプロパティがあり、これらのプロパティを使用し、リボン上の特定のコマンドまたはコマンドのグループをコンテンツ作成者が使用できないようにすることができます。たとえば、 **AllowFontsMenu** プロパティを **False** に設定した場合、作成者はテキストに適用されたフォントの変更にリボンのフォント メニューを使用できず、デザイナーが指定した CSS スタイルのみを使用できます。
    
  
RichHtmlField をはじめとするページ フィールドのすべてのタイプにおいて、デザイナーはどのようにコンテンツのスタイルを指定するかを決定します。RichHtmlField を使用すると、コンテンツ作成者が自由にリッチ コンテンツを挿入してスタイルを適用できるようにすることができるようになりますが、最終的には、追加できるコンテンツおよび適用できるスタイルはデザイナーが制御します。
  
    
    

## RichHtmlField 以外のページ フィールドへのスタイルの適用
<a name="Applying"> </a>

ページ フィールド コントロールを使用すると、コンテンツで使用されるスタイルを定義できます。作成者はコンテンツをページに追加できますが、これらのコントロールに適用された CSS を介してコンテンツを表示する方法はデザイナーが制御します。
  
    
    
HTML ページ レイアウトでは、各ページ フィールドは **<div>** タグで囲まれます。スタイルをページ フィールドに適用するには、スタイルを **<div>** に追加するだけです (例: `<div style="font-weight:bold"`)。しかし、より一般的で便利なシナリオは、 **id** 属性をページ レイアウトの各ページ フィールドの **<div>** に追加し、外部スタイル シートにあるスタイルのセレクターとして **id** を使用します。このようにして、複数のデバイス チャネルがあり、チャネルごとに独自のスタイル シートがある場合、チャネルごとの各ページ フィールドに異なるスタイルを適用できます。たとえば、次の TextField (複数行テキストとも呼ばれる) タイプのページ フィールドには、 **<div>** タグに **id** 属性のみがある場合があります。
  
    
    



```HTML

<div id="ShortSummaryPageField">
<!--CS: Start Page Field: ShortSummary Snippet-->
<!--SPM:<%@Register Tagprefix="PageFieldNoteField" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<PageFieldNoteField:NoteField FieldName="a5249942-2dc5-4917-85e2-661d019ad548" runat="server">-->
<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><div align="left" class="ms-formfieldcontainer"><div class="ms-formfieldlabelcontainer" nowrap="nowrap"><span class="ms-formfieldlabel" nowrap="nowrap">ShortSummary</span></div><div class="ms-formfieldvaluecontainer"><div class="ms-rtestate-field">ShortSummary field value.</div></div></div><!--PE: End of READ-ONLY PREVIEW-->
<!--ME:</PageFieldNoteField:NoteField>-->
<!--CE: End Page Field: ShortSummary Snippet-->
</div>
```

ページ レイアウトのスタイルおよびスタイル参照の場所に関する詳細については、「 [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)」を参照してください。
  
    
    

## RichHtmlField のリボンのオプションの無効化
<a name="Disabling"> </a>

コンテンツ作成者がページを作成または編集し、ブラウザーを使用して RichHtmlField にコンテンツを追加する場合、そのフィールドのリボンのコマンドを使用し、リッチ コンテンツおよびメディアの書式設定、スタイル設定、または挿入を行うことができます。 
  
    
    
スニペット ギャラリーでは、RichHtmlField タイプのページ フィールドのプロパティを設定して、作成者がリボンの特定のコマンドまたはコマンドのグループを使用できないようにすることができます。たとえば、 **AllowFontSizesMenu** プロパティを **False** に設定して、リボンの **Font Size** メニューを無効にできます。 **AllowFonts** プロパティを **False** に設定して、リボンの [ **フォント**] グループ全体を無効にできます。
  
    
    
スニペット ギャラリーのこれらのプロパティを設定し、スニペットを更新すると、プロパティは  `<!--MS:>` コメント内のスニペット マークアップに表示されます。
  
    
    



```HTML

<div data-name="Page Field: ArticleBody">
<!--CS: Start Page Field: ArticleBody Snippet-->
<!--SPM:<%@Register Tagprefix="PageFieldRichHtmlField" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<PageFieldRichHtmlField:RichHtmlField runat="server" AllowFonts="False" FieldName="db3168db-8778-4fb6-a48f-57f598497388">-->
<!--PS: Start of READ-ONLY PREVIEW (do not modify)--><div id="ctl02_label" style="display:none">ArticleBody</div><div id="ctl02__ControlWrapper_RichHtmlField" class="ms-rtestate-field" style="display:inline" aria-labelledby="ctl02_label"><div align="left" class="ms-formfieldcontainer"><div class="ms-formfieldlabelcontainer" nowrap="nowrap"><span class="ms-formfieldlabel" nowrap="nowrap">ArticleBody</span></div><div class="ms-formfieldvaluecontainer"><div class="ms-rtestate-field">ArticleBody field value. Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div></div></div></div>
<!--PE: End of READ-ONLY PREVIEW-->
<!--ME:</PageFieldRichHtmlField:RichHtmlField>-->
<!--CE: End Page Field: ArticleBody Snippet-->
</div>
```


> **メモ**
> **AllowFonts** を **False** に設定した場合、コンテンツ作成者はテキストの書式設定をするために Ctrl+B (強調) などのキーボード ショートカットを引き続き使用できます。作成者がテキストにスタイルを追加できないように、 **AllowTextMarkup** を **False** に設定できます。この設定でコンテンツ作成者がテキストに適用されたスタイルを含めてコンテンツを保存しようとすると、ブラウザーの HTML エディターはエラーを返し、無効なマークアップを削除するよう作成者にプロンプトを表示します。
  
    
    

RichHtmlField ページ フィールドには 28 個のさまざまな **Allow** プロパティがあります。特定のプロパティが制御する内容に関する詳細については、「 [RichHtmlField プロパティ](http://msdn.microsoft.com/ja-jp/library/microsoft.sharepoint.publishing.webcontrols.richhtmlfield_properties)」を参照してください。スニペットの追加および設定の詳細については、「 [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md)」を参照してください。
  
    
    

## RichHtmlField で使用できるスタイルの制御
<a name="Controlling"> </a>

RichHtmlField では、コンテンツ作成者はリボンのオプションを使用し、コンテンツを書式設定できます。これらの書式設定オプションは CSS を使用して実装されます。また、これらのスタイルは、次の場所のいずれかのサーバーにある HtmlEditorStyles.css という名前の SharePoint スタイル シートに定義されています。
  
    
    

- C:\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\TEMPLATE\\LAYOUTS\\1033\\STYLES 
    
  
- C:\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\TEMPLATE\\FEATURES\\PublishingLayouts\\ja-jp
    
  
ブラウザーの RichHtmlField は CSS を使用してスタイルを実装するため、サイトのブランドと整合性のある独自のスタイルを作成し、コンテンツ作成者のリボンでこれらのスタイルを使用できるようにすることができます。既定のスタイルを少し変更するには、HtmlEditorStyles.css からページ レイアウトが参照するスタイル シートに既存のスタイルをコピーし、CSS プロパティおよび値 (セレクターは除く) を変更してスタイルを変更できます。既定のスタイルをスタイル シートにコピーし、 `display:none` を設定することで、既定のスタイルをリボンで非表示にすることもできます。
  
    
    
また、カスタムのスタイルを実装するには、RichHtmlField スニペットの **PrefixStyleSheet** プロパティを変更することによって、ゼロからスタイル シートを作成できます。既定では、このプロパティは **ms-rte** に設定されており、それぞれの既定のスタイル シート HtmlEditorStyles.css のスタイルはこのプレフィックスで開始されます。たとえば、以下のようになります。
  
    
    



```HTML

H1. ms-rteElement-H1
{
-ms-name:"Heading 1";
-ms-element:"true";
}
```

 **PrefixStyleSheet** プロパティの値を変更する場合、既存の **ms-rte** スタイルはリッチ HTML エディターでは使用できません。コンテンツ作成者は、新しいプレフィックスを使用して作成したスタイルのみを使用できます。つまり、既定のスタイルの一部を使用する場合は、新しいプレフィックスを使用できるように、既存のスタイルをスタイル シートにコピーして変更する必要があるということです。
  
    
    

> **メモ**
> **PrefixStyleSheet** プロパティは RichHtmlField ページ フィールドごとに定義されますが、複数のページ フィールドがこのプロパティに同じ値を使用できます。そのため、複数のページ レイアウトが同じスタイル シートを参照する場合、ページ レイアウトの複数の RichHtmlFields が同じスタイル プレフィックスを持ち、同じスタイルを参照することができます。
  
    
    


### RichHtmlField に新しいスタイルのリストを定義するには


1. 発行サイトに移動します。
    
  
2. ページの右上隅で [ **設定**] を選択し、[ **デザイン マネージャー**] を選択します。
    
  
3. [デザイン マネージャー]の左側のナビゲーション ウィンドウで、[ **ページ レイアウトの編集**] を選択します。
    
  
4. RichHtmlField ページ フィールドを置くページ レイアウトを選択します。
    
  
5. サーバー側プレビューの右上隅で、[ **スニペット ギャラリー**] を選択します。
    
  
6. リボンで [ **ページ フィールド**] を選択し、[ **RichHtmlField**] タイプのページ フィールドを選択します。
    
  
7. プロパティ グリッドで [ **その他**] セクションを展開し、 **PrefixStyleSheet** プロパティを **ms-rte** 以外の値に変更します。たとえば、値を **customstyle** に変更します。
    
    > **重要**
      > このプロパティ値はすべて小文字である必要があります。 
8. [ **更新**] を選択します。
    
  
9. スニペット ギャラリーの左側で、[ **クリップボードにコピー**] を選択します。
    
  
10. コンピューター上のマップされたネットワーク ドライブでは、HTML エディターで HTML ページ レイアウトを開きます。
    
    > **メモ**
      > 詳細については、「 [[方法]: SharePoint 2013 マスター ページ ギャラリーへのネットワーク ドライブの割り当て](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)」を参照してください。 
11. HTML ページ レイアウトでは、HTML スニペットを **PlaceHolderMain** 内に貼り付けます。
    
  
12. HTML ページ レイアウトを保存します。HTML ファイルへの変更は、関連する .aspx ページ レイアウトと同期されます。
    
    この時点で、コンテンツ作成者がこのページ レイアウトを基にしてページを作成または編集する場合、HTML エディターのリボンで使用できるスタイルはありません。この特定のページ フィールドは新しいプレフィックス **customstyle** で始まるスタイルのみを使用しますが、これらのスタイルがまだ定義されていないためです。
    
  
13. サーバーで次の場所を参照し、HtmlEditorStyles.css を開きます。
    
    C:\\Program Files\\Common Files\\Microsoft Shared\\Web Server Extensions\\15\\TEMPLATE\\LAYOUTS\\1033\\STYLES
    
    これは既定のスタイルを表示したり、それがどのように書かれているかを理解したり、またスタイル シートにコピーして変更することで既定のスタイルの一部を再利用したりする際に便利です。これを実行する場合、既定の **ms-rte** プレフィックスを自分独自のプレフィックスに置換します。
    
    > **重要**
      > 既定のスタイル シート (HtmlEditorStyles.css) を変更しないでください。このスタイル シートはファームの RichHtmlField すべてにスタイルを提供します。また、サービスの更新またはアップグレードは、このファイルを上書きする可能性があり、その場合は変更が失われることになります。 
14. スタイル シートで、新しいプレフィックスで始まる新しいスタイルのリストを作成します。
    
    たとえば、 **customstyle** が新しいプレフィックスの場合、スタイル シートには次のスタイルが含まれる可能性があります。
    


  ```HTML
  
H2.customstyleElement-H2
{
-ms-name:"Heading 2";
-ms-element:"true";
}
customstyleElement-H2
{
font-weight: bold;
font-family: Cambria;
font-size: 16pt;
} 

  ```


    わかりやすくするため、リボンに表示されるクラス名やスタイルの名前は、スタイル プロパティで個別に定義されます。この例では、 **H2** はスタイルの要素セレクターであり、 **customstyleElement-H2** はスタイルのクラス名です。クラス名は次の 2 つの部分から構成されます。 **customstyle** はこのページ フィールドに指定したプレフィックスであり、 **Element** はこのスタイルが HTML エディターのリボンの [ **スタイル**] ギャラリーの [ **ページ要素**] セクションに表示されることを指定します。 **-ms-name** プロパティは、スタイル ギャラリーでコンテンツ作成者に表示する表示名を設定します。
    
    SharePoint は、プレフィックスの直後のクラス名を解析してこれらの文字列の 1 つを探すことにより、リボンのメニューまたはコマンドにスタイルをマップします。
    
  - **Element**: スタイル ギャラリーの [ページ要素] セクション
    
  
  - **Style**: スタイル ギャラリーの [テキスト スタイル ] セクション
    
  
  - **FontSize**: [フォント サイズ] メニュー
    
  
  - **ThemeFontFace**: [フォント] メニュー
    
  
  - **ForeColor**: [フォントの色] メニュー
    
  
  - **BackColor**: [強調色] メニュー
    
  
  - **Image**: [イメージ] メニュー
    
  
  - **Table**: [テーブル] メニュー
    
  
  - **Position**: 段落グループの [整列] ボタン
    
  

    ページ レイアウトのスタイルを置かなければならない場所の詳細については、「 [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)」を参照してください。
    
  

## その他の技術情報
<a name="Additional"> </a>


-  [SharePoint 2013 のデザイン マネージャーの概要](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md)
    
  

