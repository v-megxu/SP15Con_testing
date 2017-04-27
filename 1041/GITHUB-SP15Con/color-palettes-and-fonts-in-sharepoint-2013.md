---
title: SharePoint 2013 のカラー パレットとフォント
ms.prod: SHAREPOINT
ms.assetid: c17d375b-151f-48ae-ac32-f2ce9e68d63f
---


# SharePoint 2013 のカラー パレットとフォント
このリファレンスを使用して、SharePoint 2013 で使用されるカラー パレットまたはフォント パターンを定義します。
## カラー パレット
<a name="color"> </a>

カラー パレットは、SharePoint サイトで使用される色の組み合わせです。SharePoint サイトのカラー パレットは、カラー パレット ファイルで定義されます。またカラー スロットは、サイトのサムネイルおよびプレビュー イメージを生成するため、マスター ページ プレビュー ファイルによっても使われます。次に、カラー パレット ファイルとマスター ページ プレビュー ファイルの構造について説明します。
  
    
    

- **カラー パレット ファイル (.spcolor)**
    
    カラー パレット ファイルは、 **外観の変更**ウィザードで使用されます。このウィザードで SharePoint テーマ ユーザー インターフェイスを使用して、サイトの外観を変更できます。既定では、SharePoint 2013 では 32 のカラー パレット ファイルがインストールされます。カラー パレット ファイルを追加作成することもできます。次の例では、カラー パレット ファイルの形式を示します。
    


  ```XML
  
<s:colorPalette isInverted="InvertedSetting" previewSlot1="Slot1" previewSlot2="Slot2" previewSlot3="Slot3" xmlns:s="http://schemas.microsoft.com/sharepoint/">
    <s:color name="ColorSlot" value="Color" />
    <!--additional color slots-->
</s:colorPalette>
  ```


    カラー パレット ファイルでは、次のプレース ホルダーが置き換えられます。
    
  -  _InvertedSetting_ はブール値です。カラー パレットが一般的に暗い背景に明るいテキストの場合は **true** です。カラーパレットが一般的に明るい背景に暗いテキストの場合は **false** です。
    
  
  -  _Slot1_ は、テーマ エクスペリエンスのカラー パレット選択のパレット アイコンの最初のブロックとして使用される、カラー スロットの注釈名です。
    
  
  -  _Slot2_ は、テーマ エクスペリエンスのカラー パレット選択のパレット アイコンの第 2 ブロックとして使用される、カラー スロットの注釈名です。
    
  
  -  _Slot3_ は、テーマ エクスペリエンスのカラー パレット選択のパレット アイコンの第 3 ブロックとして使用される、カラー スロットの注釈名です。
    
  
  -  _ColorSlot_ は、定義するカラー スロットの注釈名 (SiteTitle など) です。
    
  
  -  _Color_ は、指定されたカラー スロットに使用する色の 16 進数値です。 この値は 6 桁 (RRGGBB) の場合も 8 桁 (AARRGGBB) の場合もあります。16 進数値が 8 桁の場合、最初の 2 桁は透明度レベル (00 ～ FF。これは 0 ～ 255 にマッピングされます) を表します。16 進数値が 6 桁の場合、既定の透明度は 100％ (FF) です。
    
  

    カラー パレット ファイルはルート サイトのテーマ ギャラリー内に格納されています。これは **15** フォルダー (http:// _SiteCollectionName_/_catalogs/theme/15/) 内のサイト コレクションにあります。SharePoint ユーザー インターフェイスからテーマ ギャラリーにアクセスするには、[ **サイトの設定**] ページの [ **Web デザイナー ギャラリー**] で、[ **テーマ**] を選択し、[ **15**] を選択します。
    
  
- **マスター ページ プレビュー ファイル (.preview)**
    
    マスター ページ プレビュー ファイルは、 **外観の変更**ウィザードの使用時に、サムネイル イメージとプレビュー イメージの生成に使用されます。マスター ページには、 **外観の変更**ウィザードで使用される、対応するプレビュー ファイルが存在する必要があります。プレビュー ファイルは特殊な形式のファイルで、既定のカラー パレット、既定のフォント パターン、トークン化された CSS およびトークン化された HTML の各セクションが存在します。このファイルは文字列トークンを使用して、カラー スロットの値、フォント名、およびローカライズされた UI 文字列を取得します。次の例では、マスター ページ プレビュー ファイルで使用されるカラー スロットを示します。
    


  ```HTML
  
[ID] #dgp-pageContainer
{
    background-color: [T_THEME_COLOR_PAGEBACKGROUND];
    color: [T_THEME_COLOR_BODYTEXT];
    width: 100%;
    height:100%;     
    background-image: url('[T_IMAGE]');       
    background-size: cover;
    font-family: [T_BODY_FONT];   
}
  ```


    詳細については、「 [SharePoint 2013 でのマスター ページ プレビュー ファイルを作成する方法](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)」を参照してください。
    
  

> **ヒント**
> SharePoint デザインの作成を支援する、SharePoint カラー パレット ツールが使用できます。Microsoft ダウンロード センターから、 [SharePoint カラー パレット ツールをダウンロード](http://www.microsoft.com/en-us/download/details.aspx?id=38182) することができます。
  
    
    


### カラー スロットのマッピング
<a name="colorSlots"> </a>

表 1 では使用可能なカラー スロットを説明し、SharePoint サイトのどこでカラー スロットが使用されるかを示します。
  
    
    

> **メモ**
>  ナビゲーション アイテムについて説明する場合、押されたは、ナビゲーション アイテムをクリックまたはタッチするときに適用します。選択されたは、ユーザーが特定のページに移動したときに適用します。 >  次に、アクションのフローと、各ステップにおいてナビゲーション アイテム リンクに適用されるカラー スロットについて要約します。>  ナビゲーション アイテム リンクの基本テキスト: HeaderNavigationText>  ナビゲーション アイテム リンクの上にカーソルを合わせます: HeaderNavigationHoverText>  ナビゲーション アイテム リンクをクリック、タッチ、または選択します: HeaderNavigationPressedText>  選択したページに移動します。ユーザーが現在アクセスしているページのナビゲーション アイテムに適用されるカラー スロット: HeaderNavigationSelectedText
  
    
    


**表 1 カラー スロット**


|**注釈名**|**色が UI のどこで使用されるか**|**トークン名**|
|:-----|:-----|:-----|
|BodyText  <br/> |通常の本文テキスト。  <br/> |[T_THEME_COLOR_BODYTEXT]  <br/> |
|SubtleBodyText  <br/> |通常より明るい必要がある本文テキスト。メタデータ テキストなどがその例です。  <br/> |[T_THEME_COLOR_SUBTLEBODYTEXT]  <br/> |
|StrongBodyText  <br/> |通常の本文テキストよりも目立つ必要があるテキストの本文テキストの色。  <br/> |[T_THEME_COLOR_STRONGBODYTEXT]  <br/> |
|DisabledText  <br/> |無効化されたテキスト。メニューで使用できないアイテムなどがその例です。  <br/> |[T_THEME_COLOR_DISABLEDTEXT]  <br/> |
|SiteTitle  <br/> |ページ タイトルのテキストの色。  <br/> |[T_THEME_COLOR_SITETITLE]  <br/> |
|WebPartHeading  <br/> |Web パーツの見出しのテキストの色。  <br/> |[T_THEME_COLOR_WEBPARTHEADING]  <br/> |
|ErrorText  <br/> |必要に応じてエラーのテキスト、枠線、および背景に使用される、主要なエラーの色。  <br/> |[T_THEME_COLOR_ERRORTEXT]  <br/> |
|AccentText  <br/> |アクセント付き本文テキストのテキストの色。  <br/> |[T_THEME_COLOR_ACCENTTEXT]  <br/> |
|SearchURL  <br/> |検索結果で検出された URL のテキストの色。新しいアイテムまたは成功したステータス通知にも使用されます。  <br/> |[T_THEME_COLOR_SEARCHURL]  <br/> |
|Hyperlink  <br/> |ハイパーリンクのテキストの色。  <br/> |[T_THEME_COLOR_HYPERLINK]  <br/> |
|HyperlinkFollowed  <br/> |表示済みのハイパーリンクのテキストの色。  <br/> |[T_THEME_COLOR_HYPERLINKFOLLOWED]  <br/> |
|HyperlinkActive  <br/> |押した場合のハイパーリンクの色。  <br/> |[T_THEME_COLOR_HYPERLINKACTIVE]  <br/> |
|CommandLinks  <br/> |サイズが原因で、本文テキストの色より少し明るい必要がある、大きなコマンド リンク。  <br/> |[T_THEME_COLOR_COMMANDLINKS]  <br/> |
|CommandLinksSecondary  <br/> |小さいため、目立つためにはっきりした色で示されるリンクのコマンド リンクの色。  <br/> |[T_THEME_COLOR_COMMANDLINKSSECONDARY]  <br/> |
|CommandLinksHover  <br/> |ポイントされている場合のコマンド リンクの色。  <br/> |[T_THEME_COLOR_COMMANDLINKSHOVER]  <br/> |
|CommandLinksPressed  <br/> |押された場合のコマンド リンクの色。  <br/> |[T_THEME_COLOR_COMMANDLINKSPRESSED]  <br/> |
|CommandLinksDisabled  <br/> |コマンド リンクが無効の場合のコマンド リンクの色。  <br/> |[T_THEME_COLOR_COMMANDLINKSDISABLED]  <br/> |
|BackgroundOverlay  <br/> |オプションのバックグラウンド イメージとページ コンテンツ間で表示される、主要な背景色。  <br/> |[T_THEME_COLOR_BACKGROUNDOVERLAY]  <br/> |
|DisabledBackground  <br/> |ブラウザー コントロール (たとえば入力ボックス、ボタン以外の選択ボックス)など、無効化された要素の背景。  <br/> |[T_THEME_COLOR_DISABLEDBACKGROUND]  <br/> |
|PageBackground  <br/> |ページの背景色。オプションの背景イメージの後ろに表示されます。  <br/> |[T_THEME_COLOR_PAGEBACKGROUND]  <br/> |
|HeaderBackground  <br/> |ページのヘッダー領域の背景色。  <br/> |[T_THEME_COLOR_HEADERBACKGROUND]  <br/> |
|FooterBackground  <br/> |ページのフッター領域の背景色。  <br/> |[T_THEME_COLOR_FOOTERBACKGROUND]  <br/> |
|SelectionBackground  <br/> |選択されたリスト アイテムとドロップダウン メニュー アイテムの背景色。  <br/> |[T_THEME_COLOR_SELECTIONBACKGROUND]  <br/> |
|HoverBackground  <br/> |ポイントされているリスト アイテムとドロップダウン メニュー アイテムの背景色。  <br/> |[T_THEME_COLOR_HOVERBACKGROUND]  <br/> |
|RowAccent  <br/> |選択されたリスト アイテムのアクセント付きの左側の枠線。  <br/> |[T_THEME_COLOR_ROWACCENT]  <br/> |
|StrongLines  <br/> |ポイントされているブラウザー コントロールの枠線。  <br/> |[T_THEME_COLOR_STRONGLINES]  <br/> |
|Lines  <br/> |ブラウザー コントロールの枠線。  <br/> |[T_THEME_COLOR_LINES]  <br/> |
|SubtleLines  <br/> |薄い枠線の色。たとえば、インライン編集用の枠線など。  <br/> |[T_THEME_COLOR_SUBTLELINES]  <br/> |
|DisabledLines  <br/> |入力ボックスや選択ボックスなど、無効化されたブラウザー コントロールの枠線の色。  <br/> |[T_THEME_COLOR_DISABLEDLINES]  <br/> |
|AccentLines  <br/> |選択されたブラウザー コントロールのフォーカスされた枠線の色。  <br/> |[T_THEME_COLOR_ACCENTLINES]  <br/> |
|DialogBorder  <br/> |ダイアログ ボックスの枠線の色。  <br/> |[T_THEME_COLOR_DIALOGBORDER]  <br/> |
|Navigation  <br/> |水平方向と垂直方向のナビゲーション アイテムのテキストの色。  <br/> |[T_THEME_COLOR_NAVIGATION]  <br/> |
|NavigationAccent  <br/> |選択された水平方向のナビゲーション アイテムのテキストの色。  <br/> |[T_THEME_COLOR_NAVIGATIONACCENT]  <br/> |
|NavigationHover  <br/> |ポイントされているナビゲーション テキストの色。最上位のナビゲーションと、水平モードのクイック起動に適用されます。  <br/> |[T_THEME_COLOR_NAVIGATIONHOVER]  <br/> |
|NavigationPressed  <br/> |押された場合のナビゲーション アイテムのテキストの色。最上位のナビゲーションと、水平モードのクイック起動に適用されます。  <br/> |[T_THEME_COLOR_NAVIGATIONPRESSED]  <br/> |
|NavigationHoverBackground  <br/> |ナビゲーション アイテムをポイントしている場合の、垂直モードのクイック起動アイテムの背景色。  <br/> |[T_THEME_COLOR_NAVIGATIONHOVERBACKGROUND]  <br/> |
|NavigationSelectedBackground  <br/> |ナビゲーション アイテムを選択した後の、垂直モードのクイック起動アイテムの背景色。  <br/> |[T_THEME_COLOR_NAVIGATIONSELECTEDBACKGROUND]  <br/> |
|EmphasisText  <br/> |強調された背景の上に表示されるテキストの色。  <br/> |[T_THEME_COLOR_EMPHASISTEXT]  <br/> |
|EmphasisBackground  <br/> |強調されたテキストの背景に直接表示される、アクセント付き背景色。  <br/> |[T_THEME_COLOR_EMPHASISBACKGROUND]  <br/> |
|EmphasisHoverBackground  <br/> |強調された背景を使用している要素に対して、ポイントされた背景色。  <br/> |[T_THEME_COLOR_EMPHASISHOVERBACKGROUND]  <br/> |
|EmphasisBorder  <br/> |強調された背景を使用している要素の枠線の色。  <br/> |[T_THEME_COLOR_EMPHASISBORDER]  <br/> |
|EmphasisHoverBorder  <br/> |強調された背景を使用している要素をポイントしたときの枠線の色。  <br/> |[T_THEME_COLOR_EMPHASISHOVERBORDER]  <br/> |
|SubtleEmphasisText  <br/> |弱く強調された背景の上に表示されるテキスト。  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISTEXT]  <br/> |
|SubtleEmphasisCommandLinks  <br/> |弱く強調された背景の上に表示されるリンクのコマンド リンクの色。  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISCOMMANDLINKS]  <br/> |
|SubtleEmphasisBackground  <br/> |弱く強調されたテキストの後ろに直接表示される背景。  <br/> |[T_THEME_COLOR_SUBTLEEMPHASISBACKGROUND]  <br/> |
|TopBarText  <br/> |ウェルカム メニュー、クイック アクセス ツールバー アイコン、および閉じたリボン タブのテキストとグリフの色。  <br/> |[T_THEME_COLOR_TOPBARTEXT]  <br/> |
|TopBarBackground  <br/> |トップ バーの背景色。トップ バーは、スィート ナビゲーションの下と右側に表示されます。  <br/> |[T_THEME_COLOR_TOPBARBACKGROUND]  <br/> |
|TopBarHoverText  <br/> |ウェルカム メニュー、クイック アクセス ツールバー アイコン、および閉じたリボン タブをポイントした場合のテキストとグリフの色  <br/> |[T_THEME_COLOR_TOPBARHOVERTEXT]  <br/> |
|TopBarPressedText  <br/> |ウェルカム メニュー、クイック アクセス ツールバー アイコン、および閉じたリボン タブを押した場合のテキストとグリフの色  <br/> |[T_THEME_COLOR_TOPBARPRESSEDTEXT]  <br/> |
|HeaderText  <br/> |ヘッダー領域内の全アイテムの基本テキストの色。  <br/> |[T_THEME_COLOR_HEADERTEXT]  <br/> |
|HeaderSubtleText  <br/> |ヘッダー領域内の検索ボックスのヘルプ テキスト。  <br/> |[T_THEME_COLOR_HEADERSUBTLETEXT]  <br/> |
|HeaderDisableText  <br/> |ヘッダー領域内で検索ボックスが無効化されている場合の検索ボックスのテキスト。  <br/> |[T_THEME_COLOR_HEADERDISABLETEXT]  <br/> |
|HeaderNavigationText  <br/> |ヘッダー領域内のナビゲーション リンクの基本テキストの色。  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONTEXT]  <br/> |
|HeaderNavigationHoverText  <br/> |リンクをポイントした場合の、ヘッダー領域内のナビゲーション リンクのテキストの色。  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONHOVERTEXT]  <br/> |
|HeaderNavigationPressedText  <br/> |リンクを押した場合の、ヘッダー領域内のナビゲーション リンクのテキストの色。  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONPRESSEDTEXT]  <br/> |
|HeaderNavigationSelectedText  <br/> |リンクを選択した後の、ヘッダー領域内のナビゲーション リンクのテキストの色。  <br/> |[T_THEME_COLOR_HEADERNAVIGATIONSELECTEDTEXT]  <br/> |
|HeaderLines  <br/> |ヘッダー領域内の検索ボックスの線。  <br/> |[T_THEME_COLOR_HEADERLINES]  <br/> |
|HeaderStrongLines  <br/> |ヘッダー領域内の検索ボックスをポイントした場合の検索ボックスの線。  <br/> |[T_THEME_COLOR_HEADERSTRONGLINES]  <br/> |
|HeaderAccentLines  <br/> |ヘッダー領域内の検索ボックスをフォーカスした場合の検索ボックスの線。  <br/> |[T_THEME_COLOR_HEADERACCENTLINES]  <br/> |
|HeaderSublteLines  <br/> |ヘッダー領域内で検出された薄い線。既定の CSS では使われません。  <br/> |[T_THEME_COLOR_HEADERSUBTLELINES]  <br/> |
|HeaderDisabledLines  <br/> |ヘッダー領域で検索ボックスが無効にされている場合の検索ボックスの線。  <br/> |[T_THEME_COLOR_HEADERDISABLEDLINES]  <br/> |
|HeaderDisabledBackground  <br/> |ヘッダー領域で検索ボックスが無効にされている場合の検索ボックスの背景。  <br/> |[T_THEME_COLOR_HEADERDISABLEDBACKGROUND]  <br/> |
|HeaderFlyoutBorder  <br/> |ヘッダー領域から生成された場合のドロップダウン メニューの枠線。  <br/> |[T_THEME_COLOR_HEADERFLYOUTBORDER]  <br/> |
|HeaderSiteTitle  <br/> |ヘッダー領域内のサイト タイトルのテキストの色。  <br/> |[T_THEME_COLOR_HEADERSITETITLE]  <br/> |
|SuiteBarBackground  <br/> |スィート ナビゲーションの背景色。  <br/> |[T_THEME_COLOR_SUITEBARBACKGROUND]  <br/> |
|SuiteBarHoverBackground  <br/> |スィート ナビゲーションをポイントした場合の背景色。  <br/> |[T_THEME_COLOR_SUITEBARHOVERBACKGROUND]  <br/> |
|SuiteBarText  <br/> |スィート ナビゲーション アイテムのテキストとグリフの色。  <br/> |[T_THEME_COLOR_SUITEBARTEXT]  <br/> |
|SuiteBarDisabledText  <br/> |無効化されたスィート アイテムのテキストとグリフの色。既定の CSS では使われません。  <br/> |[T_THEME_COLOR_SUITEBARDISABLEDTEXT]  <br/> |
|ButtonText  <br/> |ボタンのテキストの色。  <br/> |[T_THEME_COLOR_BUTTONTEXT]  <br/> |
|ButtonDisabledText  <br/> |無効化されたボタンのテキストの色。  <br/> |[T_THEME_COLOR_BUTTONDISABLEDTEXT]  <br/> |
|ButtonBackground  <br/> |ボタンの背景色。  <br/> |[T_THEME_COLOR_BUTTONBACKGROUND]  <br/> |
|ButtonHoverBackground  <br/> |ボタンをポイントした場合の背景色。  <br/> |[T_THEME_COLOR_BUTTONHOVERBACKGROUND]  <br/> |
|ButtonPressedBackground  <br/> |ボタンを押している間のボタンの背景色。  <br/> |[T_THEME_COLOR_BUTTONPRESSEDBACKGROUND]  <br/> |
|ButtonDisabledBackground  <br/> |無効化されたボタンの背景色。  <br/> |[T_THEME_COLOR_BUTTONDISABLEDBACKGROUND]  <br/> |
|ButtonBorder  <br/> |ボタンの枠線の色。  <br/> |[T_THEME_COLOR_BUTTONBORDER]  <br/> |
|ButtonHoverBorder  <br/> |ボタンをポイントした場合の枠線の色。  <br/> |[T_THEME_COLOR_BUTTONHOVERBORDER]  <br/> |
|ButtonPressedBorder  <br/> |ボタンを押した場合の枠線の色。  <br/> |[T_THEME_COLOR_BUTTONPRESSEDBORDER]  <br/> |
|ButtonDisabledBorder  <br/> |ボタンを無効化した場合の枠線の色。  <br/> |[T_THEME_COLOR_BUTTONDISABLEDBORDER]  <br/> |
|ButtonGlyph  <br/> |ボタンに表示されるグリフのグリフ色。  <br/> |[T_THEME_COLOR_BUTTONGLYPH]  <br/> |
|ButtonGlyphActive  <br/> |ボタンに表示されるグリフをポイントした場合のグリフの色。  <br/> |[T_THEME_COLOR_BUTTONGLYPHACTIVE]  <br/> |
|ButtonGlyphDisabled  <br/> |無効化したボタンのグリフの色。  <br/> |[T_THEME_COLOR_BUTTONGLYPHDISABLED]  <br/> |
|TileText  <br/> |タイル背景オーバーレイの上に表示されるテキスト。  <br/> |[T_THEME_COLOR_TILETEXT]  <br/> |
|TileBackgroundOverlay  <br/> |タイルの背景オーバーレイの色。  <br/> |[T_THEME_COLOR_TILEBACKGROUNDOVERLAY]  <br/> |
|ContentAccent1  <br/> |リッチ テキスト エディターの色選択から選択できる、最初のアクセント色。  <br/> |[T_THEME_COLOR_CONTENTACCENT1]  <br/> |
|ContentAccent2  <br/> |リッチ テキスト エディターの色選択から選択できる、2 番目のアクセント色。  <br/> |[T_THEME_COLOR_CONTENTACCENT2]  <br/> |
|ContentAccent3  <br/> |リッチ テキスト エディターの色選択から選択できる、3 番目のアクセント色。  <br/> |[T_THEME_COLOR_CONTENTACCENT3]  <br/> |
|ContentAccent4  <br/> |リッチ テキスト エディターの色選択から選択できる、4 番目のアクセント色。  <br/> |[T_THEME_COLOR_CONTENTACCENT4]  <br/> |
|ContentAccent5  <br/> |リッチ テキスト エディターの色選択から選択できる、5 番目のアクセント色。  <br/> |[T_THEME_COLOR_CONTENTACCENT5]  <br/> |
|ContentAccent6  <br/> |リッチ テキスト エディターの色選択から選択できる、6 番目のアクセント色。  <br/> |[T_THEME_COLOR_CONTENTACCENT6]  <br/> |
   

## フォント パターン
<a name="font"> </a>

フォントは、指定された SharePoint サイトのフォント パターン (.spfont ファイル) とマスター ページ プレビュー (.preview ファイル) で定義されます。フォント パターンは、4 つの領域 (タイトル、ナビゲーション、見出し、本文) で使用されるフォントを定義します。SharePoint 2013 には 7 つのフォント パターンが含まれています。追加のフォント パターンを作成することもできます。フォント パターンのファイルは、サイト コレクションのルート サイトにあるテーマ ギャラリーの **15** サブフォルダー (http:// _SiteCollectionName_/_catalogs/theme/15/) に格納されています。SharePoint ユーザー インターフェイスからテーマ ギャラリーにアクセスするには、[ **サイトの設定**] ページの [ **Web デザイナー ギャラリー**] で、[ **テーマ**] を選択し、[ **15**] を選択します。
  
    
    
次の例では, .spfont ファイルの形式について説明します。
  
    
    



```XML

<?xml version="1.0" encoding="utf-8"?>
<s:fontScheme name="FontSchemeName" previewSlot1="Slot1" previewSlot2="Slot2" xmlns:s="http://schemas.microsoft.com/sharepoint/">
  <s:fontSlots>
    <s:fontSlot name="FontSlotName">
      <s:latin typeface="LatinScriptFont" />
      <s:ea typeface="EAScriptFont"/>
      <s:cs typeface="CSFont" />
      <s:font script="Language" typeface="ScriptFont" />
      <!--Additional fonts-->
  </s:fontSlots>
  <!--Additional font slots-->
</s:fontScheme>
```

.spfont ファイルでは、次のプレースホルダーが置き換えられます。
  
    
    

-  _FontSchemeName_ は、フォント パターンの名前です。
    
  
-  _Slot1_ は、 **外観の変更**ウィザードのフォント パターン選択のフォント アイコンの最初のブロックとして使用するフォント スロットの名前です。
    
  
-  _Slot2_ は、 **外観の変更**ウィザードのフォント パターン選択のフォント アイコンの第 2 ブロックとして使用するフォント スロットの名前です。
    
  
-  _FontSlotName_ は、定義するフォント スロットの名前 (タイトルなど) です。
    
  
-  _LatinScriptFont_ は、ラテン系言語に使用するフォントです。このフォントは代替フォントでもあります。つまり、フォント パターンで明示的にスクリプトが設定されていない言語に使用されるフォントです。
    
    > **メモ**
      > フォント パターンで Web フォントを使用するには、追加情報を提供する必要があります。詳細については、この記事の「 [Web フォント](#webFont)」セクションを参照してください。 
-  _EAScriptFont_ は、東アジア系言語に使用するフォントです。SharePoint では現在、 **<s:ea>** 要素は使用されていません。ただし、フォント パターンでは引き続き **<s:ea>** 要素が必要です。
    
  
-  _CSFont_ は、コンプレックス スクリプトに使用するフォントです。SharePoint では現在、 **<s:cs>** 要素は使用されていません。ただし、フォント パターンでは引き続き **<s:cs>** 要素が必要です。
    
  
-  _Language_ は言語スクリプトです。
    
  
-  _ScriptFont_ は、指定された言語スクリプトで使用されるフォントです。
    
  
次の例では, .spfont ファイルの一部を示します。
  
    
    



```XML

<s:fontScheme name="Georgia" previewSlot1="title" previewSlot2="body" xmlns:s="http://schemas.microsoft.com/sharepoint/">
    <s:fontSlots>
        <s:fontSlot name="title">
            <s:latin typeface="Georgia"/>
            <s:ea typeface=""/>
            <s:cs typeface="Segoe UI Light" />
            <s:font script="Arab" typeface="Tahoma" />
            <s:font script="Deva" typeface="Mangal" />
            <s:font script="Grek" typeface="Segoe UI Light" />
            <s:font script="Hang" typeface="Malgun Gothic" />
            <s:font script="Hans" typeface="Microsoft YaHei" />
            <s:font script="Hant" typeface="Microsoft JhengHei" />
            <s:font script="Hebr" typeface="Tahoma" />
            <s:font script="Hira" typeface="Meiryo" />
            <s:font script="Thai" typeface="Tahoma" />
            <s:font script="Armn" typeface="Tahoma" />
            <s:font script="Beng" typeface="Vrinda" />
            <s:font script="Cher" typeface="Plantagenet Cherokee" />
            <s:font script="Ethi" typeface="Nyala" />
            <s:font script="Geor" typeface="Sylfaen" />
            <s:font script="Gujr" typeface="Shruti" />
            <s:font script="Guru" typeface="Raavi" />
            <s:font script="Knda" typeface="Tunga" />
            <s:font script="Khmr" typeface="DaunPenh" />
            <s:font script="Laoo" typeface="DokChampa" />
            <s:font script="Mlym" typeface="Kartika" />
            <s:font script="Mymr" typeface="Myanmar Text" />
            <s:font script="Orya" typeface="Kalinga" />
            <s:font script="Sinh" typeface="Iskoola Pota" />
            <s:font script="Syrc" typeface="Estrangelo Edessa" />
            <s:font script="Taml" typeface="Latha" />
            <s:font script="Telu" typeface="Gautami" />
            <s:font script="Thaa" typeface="MV Boli" />
            <s:font script="Tibt" typeface="Cordia New" />
            <s:font script="Yiii" typeface="Microsoft Yi Baiti" />
        </s:fontSlot>
…
```

SharePoint 2013 には、Web フォントに対するサポートが含まれます。フォント パターンで Web フォントを使用するには、追加情報を提供する必要があります。詳細については、この記事の「 [Web フォント](#webFont)」セクションを参照してください。
  
    
    

### Web-safe フォント
<a name="websafeFont"> </a>

Web-safe フォントは、既定でほとんどのデバイスで広く使用されているフォントのセットです。フォント パターンで Web-safe フォントを指定するには、フォント スロットの **typeface** 属性にフォント名を含めます。次の例では、フォント パターンで使用される Web-safe フォントを示します。
  
    
    

```XML

<s:fontSlot name="title">
  <s:latin typeface="Georgia"/>
…
</s:fontSlot>
```


### Web フォント
<a name="webFont"> </a>

Web フォントは、インターネットで使用できるフォントです。Web フォントを使用しているサイトを表示すると、Web ブラウザーはページの他の部分と一緒に、必要なフォント ファイルをダウンロードします。Web フォントを指定するには、(さまざまなブラウザーをサポートするための) 4 種類のフォント形式の Web フォント ファイルへの URL と、フォント パターン選択でフォント名のレンダリングに使用される大小のサムネイル イメージを指定する必要があります。
  
    
    
次の例では、 **<s:latin>** 要素で Web フォントを使用するために必要な情報について説明します。
  
    
    



```XML

<s:latin typeface="FontName"
  eotsrc="EotFile"
  woffsrc="WoffFile"
  ttfsrc="TtfFile"
  svgsrc="SvgFile"
  largeimgsrc="LargeImgFile"
  smallimgsrc="SmallImgFile" />

```

Web フォントを使用するこの例では、次のプレースホルダーが置き換えられます。
  
    
    

-  _FontName_ は、Web フォントの名前です。
    
  
-  _EotFile_ は、Embedded Open Type フォント ファイルへの相対 URL です。
    
  
-  _WoffFile_ は、Web Open Font Format フォント ファイルへの相対 URL です。
    
  
-  _TtfFile_ は、TrueType フォント ファイルへの相対 URL です。
    
  
-  _SvgFile_ は、Scalable Vector Graphics フォント ファイルへの相対 URL です。
    
  
-  _LargeImgFile_ は、フォント パターン選択で使用する大きなサムネール イメージへの相対パスです。
    
  
-  _SmallImgFile_ は、フォント パターン選択で使用する小さなサムネール イメージへの相対パスです。
    
  

### フォント スロット
<a name="fontSlot"> </a>

表 1 には、使用可能なフォント スロットと、フォント スロットがページ内のどこで使用されるかを示します。
  
    
    

**表 1 フォント スロット**


|**フォント スロット名**|**説明**|
|:-----|:-----|
|タイトル  <br/> |ページ タイトルに使用されます。  <br/> |
|ナビゲーション  <br/> |ページの水平方向と垂直方向のナビゲーション要素に使用されます。  <br/> |
|大見出し  <br/> |H1 見出しに使用されます。  <br/> |
|見出し  <br/> |H2 と H3 見出し、Web パーツ タイトル、ダイアログ ボックス タイトル、およびコールアウト タイトルに使用されます。  <br/> |
|小見出し  <br/> |H4 見出しに使用されます。  <br/> |
|大きな本文  <br/> |大きな本文テキスト (15 ピクセルと 19 ピクセル) に使用されます。  <br/> |
|本文  <br/> |ページ内のその他のすべての部分で使用される基本フォントです。  <br/> |
   

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 のテーマの概要](themes-overview-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でカスタム テーマを展開する方法](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [カスタム テーマと CSS を SharePoint 2013 にアップグレードする](upgrade-custom-themes-and-css-to-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのマスター ページ プレビュー ファイルを作成する方法](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [SharePoint チームのブログ: SharePoint テーマでスタイルを際立たせる](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  
-  [SharePoint 2013 デザイン マネージャーのブランドおよびデザイン機能](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  

  
    
    

