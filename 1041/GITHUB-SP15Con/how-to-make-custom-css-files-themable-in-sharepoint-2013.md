---
title: SharePoint 2013 でカスタム CSS ファイルをテーマ設定対応にする方法
ms.prod: SHAREPOINT
ms.assetid: b8c82c77-c836-47f9-a11e-6c9c656d436b
---


# SharePoint 2013 でカスタム CSS ファイルをテーマ設定対応にする方法
コメントスタイルのマークアップを CSS ファイルに追加してSharePoint 2013 テーマ設定エンジンで使用できるようにする方法について説明します。
## 注釈の概要
<a name="Intro"> </a>

注釈は、SharePoint テーマ設定エンジンに対して CSS ファイル内のプロパティのテーマ設定方法を指示する特殊なコメントスタイルのマークアップです。サイトにテーマが適用されると、テーマ設定エンジンは CSS のプロパティ値を該当するテーマの値に置き換えます。SharePoint 2013 では、注釈を使用して、色、フォント、または背景イメージを変更することができます。また、イメージの色の変更を行うこともできます。カスタムの CSS ファイルを使用している場合に、SharePoint テーマ設定エンジンで注釈を使用する必要がある場合は、これらの注釈を CSS ファイルに追加する必要があります。カスタムの CSS ファイルを使用しているサイトにテーマを適用して、注釈を追加していなかった場合、CSS プロパティは変更されないため、サイトのデザインがちぐはぐになります。
  
    
    
この記事では、使用可能な注釈と CSS ファイルの登録方法について説明します。
  
    
    
カスタムのテーマの詳細については、「 [SharePoint 2013 でカスタム テーマを展開する方法](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)」および「 [SharePoint 2013 でのマスター ページ プレビュー ファイルを作成する方法](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)」を参照してください。
  
    
    

## カスタム CSS ファイルへの注釈の追加
<a name="annotations"> </a>

注釈は、SharePoint テーマ設定エンジンに対して CSS ファイル内のプロパティのテーマ設定方法を指示します。このセクションでは、使用可能な注釈とその使用方法について説明します。
  
    
    

### ReplaceColor 注釈
<a name="replaceColor"> </a>

 **ReplaceColor** 注釈は、色の値を指定されたテーマの色で置き換えます。これは、 **color** 、 **background-color** 、 **border** などの色の値を定義する CSS プロパティで使用できます。
  
    
    
 **ReplaceColor** 注釈の形式は、次のとおりです。
  
    
    



```

/* [ReplaceColor(themeColor:"ColorSlot"[, themeShade:"ShadeValue"][, themeTint:"TintValue"][, opacity:"OpacityValue"])] */

```

 _ColorSlot_ は使用するカラー スロットの注釈名に置き換えます。使用可能なカラー スロットの一覧については、「 [SharePoint 2013 のカラー パレットとフォント](color-palettes-and-fonts-in-sharepoint-2013.md)」の「 [カラー スロットのマッピング](color-palettes-and-fonts-in-sharepoint-2013.md#colorSlots)」を参照してください。
  
    
    
テーマの色を暗くする場合は、オプションの **themeShade** パラメーターを使用します。 _ShadeValue_ は 0.0 (変更なし) から 1.0 (最も暗い) までの数値に置き換えます。
  
    
    
テーマの色を明るくする場合は、オプションの **themeTint** パラメーターを使用します。 _TintValue_ は 0.0 (変更なし) から 1.0 (最も明るい) までの数値に置き換えます。
  
    
    
テーマの色の透明度を指定する場合は、オプションの **opacity** パラメーターを指定します。 _OpacityValue_ は透明度の設定を指定する数値に置き換えます。透明度の設定は、0.0 (完全に透明) から 1.0 (完全に不透明) の範囲で指定します。
  
    
    
次に、CSS ファイル内での **ReplaceColor** 注釈の使用例を示します。
  
    
    

-  `/* [ReplaceColor(themeColor:"BodyText")] */ color:#444;`
    
  
-  `/* [ReplaceColor(themeColor:"BackgroundOverlay",opacity:"0.5")] */ background-color:#fff;`
    
  
-  `/* [ReplaceColor(themeColor:"EmphasisBackground",themeTint:"0.05")] */ background-color:#f2faff;`
    
  

### ReplaceFont 注釈
<a name="replaceFont"> </a>

 **ReplaceFont** 注釈は、指定されたテーマのフォントを使用可能なフォントのリストに追加します。これは、 **font** および **font-family** の CSS プロパティで使用できます。
  
    
    
 **ReplaceFont** 注釈の形式は、次のとおりです。
  
    
    



```

/* [ReplaceFont(themeFont:"FontSlot")] */
```

 _FontSlot_ を使用するフォント スロットの名前に置き換えます。使用可能なフォント スロットについては、「 [SharePoint 2013 のカラー パレットとフォント](color-palettes-and-fonts-in-sharepoint-2013.md)」の「 [フォント スロット](color-palettes-and-fonts-in-sharepoint-2013.md#fontSlot)」を参照してください。
  
    
    
次に、 **ReplaceFont** 注釈の例を示します。この例では、テーマで **body** フォント スロットが Courier として定義されている場合に、Courier が **Choose the Look**ウィザードの使用可能なフォントの最初の項目として追加されます。
  
    
    

-  `/* [ReplaceFont(themeFont:"body")] */ font-family:"Segoe UI","Segoe",Tahoma,Helvetica,Arial,sans-serif;`
    
  

### ReplaceBGImage 注釈
<a name="replaceBGimage"> </a>

 **ReplaceBGImage** 注釈は、CSS ファイルの背景イメージをテーマの背景イメージに置き換えます。これは、 **background** および **background-image** の CSS プロパティで使用できます。
  
    
    
次に、 **ReplaceBGImage** 注釈の例を示します。 **ReplaceBGImage** 注釈を **AlphaImageLoader** フィルターと組み合わせて使用すると、以前のバージョンの Internet Explorer をサポートできます。
  
    
    



```
/* [ReplaceBGImage] */
```


### RecolorImage 注釈
<a name="replaceBGimage"> </a>

 **RecolorImage** 注釈は、指定されたイメージの色を変更します。
  
    
    
 **RecolorImage** 注釈の形式は、次のとおりです。
  
    
    



```
/* [RecolorImage(themeColor:"ColorSlot"[, method:["Tinting"|"Blending"|"Filling"]][, includeRectangle: {x:x-Setting,y:y-Setting,width:RegionWidth,height:RegionHeight})] */

```

 _ColorSlot_ をカラー スロットの注釈名に置き換えます。使用可能なカラー スロットについては、「 [SharePoint 2013 のカラー パレットとフォント](color-palettes-and-fonts-in-sharepoint-2013.md)」の「 [カラー スロットのマッピング](color-palettes-and-fonts-in-sharepoint-2013.md#colorSlots)」を参照してください。
  
    
    
色の変更方法を指定する場合は、オプションの **method** パラメーターを使用します。
  
    
    
イメージの特定の領域のみの色を変更する場合は、オプションの **includeRectangle** パラメーターを使用します。 _x-Setting_、 _y-Setting_、 _RegionWidth_、および  _RegionHeight_ は、色の変更を行う領域の x 座標、y 座標、幅、高さに置き換えます。
  
    
    
次に、CSS ファイル内での **RecolorImage** 注釈の使用例を示します。
  
    
    

-  `/* [RecolorImage(themeColor:"SubtleBodyText",method:"Tinting")] */ background-image:url("/_layouts/15/images/tabtitlerowbottombg.png?rev=23");`
    
  
-  `/* [RecolorImage(themeColor:"BodyText",method:"Filling",includeRectangle:{x:161,y:178,width:16;height:16})] */ background:url("/_layouts/15/images/spcommon.png?rev=23") no-repeat -161px -178px;`
    
  

## スタイル ライブラリ内の Themable フォルダーへの CSS ファイルのアップロード
<a name="uploadCSS"> </a>

カスタム CSS ファイルは、(マスター ページ ギャラリーの Themable フォルダーではなく) スタイル ライブラリの Themable フォルダーに配置します。スタイル ライブラリの Themable フォルダー格納された CSS ファイルのみが、テーマ設定エンジンで認識されます。Themable フォルダーは、公開サイトに対して自動的に作成されます。自動的に作成されない場合は、Themable フォルダーを適切な場所 (http://  _SiteCollectionName_/Style Library/ _language_/Themable/) に作成することができます。
  
    
    

> **メモ**
>  _language_ フォルダーの名前は、言語とカルチャを識別する 4 桁形式 _ll-cc_ にする必要があります (例:、en-us、ar-sa)。詳細については、「 [Office 2013 の言語識別子と OptionState ID 値](http://technet.microsoft.com/ja-jp/library/cc179219.aspx)」を参照してください。 
  
    
    

CSS ファイルはチェックインして公開する必要があります。CSS ファイルが変更された場合は、変更内容が認識されるようにテーマを再適用する必要があります。
  
    
    

## CSS ファイルの登録
<a name="registerCSS"> </a>

CSS ファイルをテーマ設定エンジンで使用できるようにするには、事前に CSS ファイルをマスター ページに登録する必要があります。これにより、サイトにテーマを適用したときに、マスター ページが CSS ファイルにダイレクトされます。CSS ファイルを登録するには、 **<SharePoint:CssRegistration>** 要素をマスター ページの **<head>** 要素に追加します。 **<SharePoint:CssRegistration>** 要素の形式は、次のとおりです。
  
    
    

```HTML

<SharePoint:CssRegistration Name="CSSFileLocation" runat="server" />
```

 _CSSFileLocation_ を CSS ファイルの場所に置き換えます。
  
    
    
次に、 **<SharePoint:CssRegistration>** 要素の例を示します。
  
    
    



```HTML
<head>
…
<SharePoint:CssRegistration Name="<%$SPUrl:~SiteCollection/Style Library/~language/Themable/MyCustomFile.css%>" runat="server" />
</head>
```


> **メモ**
> **%$SPUrl** トークンは SharePoint Foundation 2013 では使用できません。URL を使用して CSS の場所を指定する必要があります。
  
    
    


## その他の技術情報
<a name="addresources"> </a>


-  [SharePoint 2013 のテーマの概要](themes-overview-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でカスタム テーマを展開する方法](how-to-deploy-a-custom-theme-in-sharepoint-2013.md)
    
  
-  [カスタム テーマと CSS を SharePoint 2013 にアップグレードする](upgrade-custom-themes-and-css-to-sharepoint-2013.md)
    
  
-  [SharePoint 2013 でのマスター ページ プレビュー ファイルを作成する方法](how-to-create-a-master-page-preview-file-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のカラー パレットとフォント](color-palettes-and-fonts-in-sharepoint-2013.md)
    
  
-  [SharePoint チームのブログ: SharePoint テーマでスタイルを際立たせる](http://blogs.office.com/b/sharepoint/archive/2012/10/29/show-off-your-style-with-sharepoint-theming.aspx)
    
  
-  [SharePoint 2013 デザイン マネージャーのブランドおよびデザイン機能](sharepoint-2013-design-manager-branding-and-design-capabilities.md)
    
  

