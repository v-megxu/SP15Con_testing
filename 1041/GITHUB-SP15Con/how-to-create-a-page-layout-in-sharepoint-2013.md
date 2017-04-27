---
title: [方法] SharePoint 2013 でページ レイアウトを作成する方法
ms.prod: SHAREPOINT
ms.assetid: 5447e6a1-2f14-4667-81d0-7514b468be80
---


# [方法]: SharePoint 2013 でページ レイアウトを作成する方法
デザイン マネージャーを使用してページ レイアウトを作成すると、2 つのファイルが作成されます。1 つは SharePoint で使用される .aspx ファイルです。もう 1 つはそのページ レイアウトの HTML バージョンで、これは HTML エディターで編集できます。この HTML ファイルとページ レイアウトは関連付けられているので、HTML ファイルを編集して保存すると、変更内容は関連付けられたページ レイアウトと同期されます。
## ページ レイアウトの概要
<a name="Introduction"> </a>

デザイン マネージャーを使用してページ レイアウトを作成すると、2 つのファイルが作成されます。1 つは SharePoint で使用される .aspx ファイルです。もう 1 つはそのページ レイアウトの HTML バージョンで、これは HTML エディターで編集できます。この HTML ファイルとページ レイアウトは関連付けられているので、HTML ファイルを編集して保存すると、変更内容は関連付けられたページ レイアウトと同期されます。
  
    
    
マスター ページを作成するときは、HTML ファイルをアップロードして、マスター ページに直接変換します。ただし、マスター ページとは異なり、HTML ファイルをページ レイアウトに直接変換することはありません。これは、ページ レイアウトの主な目的がページ フィールドを格納することであり、ページ フィールドはデザイン マネージャーでページ レイアウトを作成するときに追加する必要があるためです。
  
    
    
ページ レイアウトを作成するときは以下のことが行われます。
  
    
    

- 同じ名前の .aspx ファイルと HTML ファイルがマスター ページ ギャラリーに作成されます。
    
  
- ページ レイアウトが正しくレンダリングされるように、SharePoint で必要なすべてのマークアップが .aspx ファイルに追加されます。
    
  
- コメント、 **<div>** タグ、スニペット、コンテンツ プレースホルダーなどの他のマークアップが、HTML ファイルに追加されます。
    
  
- コンテンツ タイプに固有のページ フィールドが、ページ レイアウトに自動的に追加されます。他のページ フィールドは、スニペット ギャラリーのリボンから追加できます。
    
  
- HTML ファイルと .aspx ファイルが関連付けられ、HTML ファイルに対して後で行われる編集が、HTML ファイルを保存するたびに .aspx ファイルに同期されるようになります。コメント、 **<div>** タグ、スニペット、コンテンツ プレースホルダーなどの他のマークアップが、HTML ファイルに追加されます。
    
  

> **メモ**
> 同期は 1 方向にのみ行われます。HTML ページに対する変更は関連付けられている .aspx ファイルに同期されますが, .aspx ファイルを直接編集しても、変更は HTML ファイルに同期されません。すべての HTML ページ レイアウト (および、すべての HTML マスター ページ) には [ **関連付けられているファイル**] という名前のプロパティがあり、既定で **True** に設定されて、ファイル間の関連付けと同期を作成します。
  
    
    

たとえば、関連付けられたファイル (HTML と .aspx) のペアがあり、関連付けを維持して .aspx ファイルを編集した場合, .aspx ファイルの変更は保存されますが, .aspx ファイルをチェックインまたは発行することはできないので、変更を保存しても意味がありません。HTML ファイルに対する変更によって, .ファイルは上書きされます。HTML ファイルをチェックインまたは発行すると、HTML ファイルの変更で, .aspx ファイルに対して行われた変更は上書きされます。.aspx ファイルの変更は失われます。
  
    
    
開発者が ASP.NET で問題なく作業している場合は、ファイル間の関連付けを解除することにより, .aspx ファイルだけで作業できます。HTML ファイルと .aspx ファイルの関連付けを解除するには、デザイン マネージャーで、HTML ファイルの [ **プロパティの編集**] を選択し、[ **関連付けられているファイル**] チェック ボックスをオフにします。後でプロパティを編集してこのチェック ボックスをオンにすることにより、ファイルを再び関連付けることができます。そうすると、HTML ファイルに保存される変更で .aspx ファイルが再び上書きされるようになります。
  
    
    

## ページ フィールドとコンテンツ タイプの関係の概要
<a name="UnderstandingPageFields"> </a>

すべてのページ レイアウトはコンテンツ タイプと関連付けられます。通常は、ページ レイアウト グループ内のコンテンツ タイプの 1 つです。たとえば、アーティクル ページ コンテンツ タイプはアーティクル ページ ページ レイアウトと関連付けられ、どちらも発行サイトに含まれます。
  
    
    
コンテンツ タイプはサイト列で構成され、全体として許可されるデータ型のスキーマを定義しています。ソース列がブランクであることにより、そのサイト列が現在のコンテンツ タイプに固有であることがわかります。つまり、これらのサイト列は現在のコンテンツ タイプによって定義されており、親コンテンツ タイプからは継承されません。
  
    
    
特定のページ レイアウトに関し、コンテンツ タイプを構成するサイト列は、そのページ レイアウトで使用できるページ フィールドに直接対応します。リボンのページ フィールドの最初のグループは、ページ レイアウトを作成すると自動的に追加されるページフィールドです。これらのフィールドはそのコンテンツ タイプに固有であり、一般的な SharePoint メタデータとは違って、ページ レイアウトで作成されることを特に目的として作成されているので、SharePoint はこれらのフィールドを自動的に追加します。
  
    
    
デザイン マネージャーでページ レイアウトを作成する前に、そのページ レイアウトで使用するページ フィールドを定義するコンテンツ タイプの作成が必要な場合があります。
  
    
    

## ページ レイアウトのコンテンツ プレースホルダーとマスター ページの関係の概要
<a name="UnderstandingContentPlaceholders"> </a>

ページ レイアウトが正しくレンダリングされるためには、ページ レイアウトとマスター ページのコンテンツ プレースホルダーのセットが一致している必要があります。デザイン マネージャーを使用してマスター ページとページ レイアウトを作成する場合は、正しいコンテンツ プレースホルダー セットが作成時にすべてのファイルに追加されるので、これは問題になりません。これにより、すべてのページ レイアウトが異なるマスター ページを使用するすべてのチャネルで動作することが保証されます。これらのコンテンツ プレースホルダーのほとんどについては、理解したり作業したりする必要はありません。これらは、ページを正しくレンダリングするために SharePoint で必要とされるので存在しています。
  
    
    
しかし、手作業で HTML ページ レイアウトを編集してコンテンツ プレースホルダーを追加する場合は、そのページ レイアウトで動作する必要のあるすべてのマスター ページに、同じコンテンツ プレースホルダーを追加する必要があります。これは一般的なシナリオではありません。
  
    
    
デザイン マネージャーを使用してページ レイアウトとマスター ページを作成する場合の最も一般的なシナリオでは、以下のコンテンツ プレースホルダーの作業のみを行います。
  
    
    

- **PlaceHolderMain** マスター ページには `ID="PlaceholderMain"` であるコンテンツ プレースホルダーが含まれ、それには **DefaultContentBlock** **<div>** タグおよび [ **この領域には、ページ レイアウトで作成したコンテンツが入力されます**] と表示される黄色いボックスが含まれます。マスター ページのこのプレースホルダーには、どのようなコンテンツも入れないでください。ページ レイアウトには、同じ ID を持つコンテンツ プレースホルダーがあります。ページ レイアウトでは、このプレースホルダーの内部にのみマークアップを配置し、このプレースホルダーの外部にはマークアップを配置しないようにする必要があります。2 つのプレースホルダーの ID ( **PlaceholderMain**) は一致している必要があります。
    
  
- **PlaceHolderAdditionalPageHead** ページ レイアウトの作業を行うとき、通常は、ページ レイアウトの **<head>** タグには要素を挿入しません。代わりに、 `id="PlaceHolderAdditionalPageHead"` であるコンテンツ プレースホルダーに要素を追加します。コンテンツ ページがブラウザーでレンダリングされるときに、この追加ページ ヘッダーがマスター ページのヘッダーの最後に組み込まれます。
    
  

## ページ レイアウトを作成する
<a name="CreatePageLayout"> </a>

始める前に、ページ レイアウトが関連付けられるコンテンツ タイプとマスター ページを確認しておく必要があります。
  
    
    

### ページ レイアウトを作成するには


1. 発行サイトに移動します。
    
  
2. ページの右上隅で、歯車アイコンを選択し、[ **デザイン マネージャー**] を選択します。
    
   **歯車アイコン メニュー**

  

![発行サイトで歯車アイコンをクリックすると開くメニュー。1 つの項目は、[デザイン マネージャー] です。](images/43a35ca2-2c93-4323-a169-769c3a54fa38.PNG)
  

  

  
3. デザイン マネージャーの左側のナビゲーション ウィンドウで、[ **ページ レイアウトの編集**] を選択します。
    
  
4. [ **ページ レイアウトの作成**] を選択します。
    
  
5. [ **ページ レイアウトの作成**] ダイアログ ボックスで、ページ レイアウトの名前を入力します。
    
  
6. マスター ページを選択します。
    
    ここで選択したマスター ページが、このページ レイアウトのプレビューで表示されます。また、このマスター ページにより、ページ レイアウトに追加されるコンテンツ プレースホルダーが決まります。
    
    > **メモ**
      > このマスター ページを選択した後では、異なるマスター ページを実際のサイトに適用した後であっても、ページ レイアウトを異なるマスター ページでプレビューすることはできません。 
7. コンテンツ タイプを選択します。このページ レイアウトのコンテンツ タイプにより、スニペット ギャラリーでこのページ レイアウトに対して使用できるページ フィールドが決まります。
    
  
8. [ **OK**] をクリックします。
    
    この時点で、SharePoint は同じ名前の HTML ファイルと .aspx ファイルを作成します。
    
    デザイン マネージャーに HTML ファイルが表示され、[状態] 列には次の 2 つの状態のどちらかが表示されます。
    
  - **警告とエラーが発生しています**
    
  
  - **正常に変換されました**
    
  
9. ファイルをプレビューしたり、マスター ページに関するエラーまたは警告を表示したりするには、[状態] 列のリンクをクリックします。
    
    プレビュー ページは、ページ レイアウトの実際のサーバー側プレビューです。プレビューの先頭には、HTML ファイルを HTML エディターで編集して解決することが必要な場合がある警告またはエラーが表示されます。プレビューでページ レイアウトが正しく表示されるためには、エラーを修正する必要があります。
    
    エラーと警告への対応の詳細については、「 [SharePoint 2013 でページをプレビューしているときのエラーと警告を解決する方法](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md)」を参照してください。
    
    ページ レイアウトのプレビューの詳細については、「 [方法: SharePoint 2013 デザイン マネージャーでプレビュー ページを変更する](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)」を参照してください。
    
    プレビュー ページの右上隅には [ **スニペット**] リンクもあります。このリンクをクリックするとスニペット ギャラリーが開き、デザイン内の模擬表示を動的な SharePoint コントロールに置き換えることができます。詳細については、「 [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md)」を参照してください。
    
  
10. エラーを修正するには、マップされたドライブの HTML ファイルを HTML エディターで開いて編集することにより、サーバー上に直接存在する HTML ファイルを編集します。HTML ファイルを保存するたびに、関連付けられている .aspx ファイルに変更が同期されます。
    
  
11. ページ レイアウトのプレビューでは、ページ レイアウトに自動的に追加されたページ フィールドが表示されます。これらのページ フィールドは、現在のコンテンツ タイプに固有のサイト列です。この時点では、元の HTML 模擬表示に従ってページ レイアウトのスタイルを設定できる状態になっています。
    
  

## ページ レイアウトのスタイルの実現方法の決定
<a name="WhereStyles"> </a>

サイトの HTML 模擬表示を作成するときは、アーティクル ページや、カタログの 1 つのアイテムに関する詳細を表示する Web パーツを含むアイテムの詳細ページなど、異なるページのクラスを表す HTML ファイルがある場合があります。そのページのクラスを表すページ レイアウトを作成した後は、HTML 模擬表示から、ページ レイアウトの HTML バージョンに、スタイルを転送できるようになります。
  
    
    
1 つ以上のページ レイアウトのスタイルを、マスター ページがリンクしている同じスタイル シートに格納するだけでもかまいません。しかし、ページごとに読み込まれる CSS の重さを最小限にする必要がある場合は、異なるページ レイアウトには異なるスタイル シートを使用することもできます。その場合、スタイル シートに対するリンクをページ レイアウトの **<head>** タグに入れることはできないことを理解しておくことが重要です。リンクは **PlaceHolderAdditionalPageHead** という名前のコンテンツ プレースホルダーに入れる必要があります。
  
    
    

> **メモ**
> このマークアップでは、属性  `ms-design-css-conversion="no"` によりスタイル シートはテーマから除外されます。また、スタイル シートへのリンクは、 **<!--SPM** とコメント化された行の後に出現する必要があります。
  
    
    




```HTML

<!--MS:<asp:ContentPlaceHolder id="PlaceHolderAdditionalPageHead" runat="server">-->
            <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
            <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<link href="MyPageLayout.css" rel="stylesheet" type="text/css" ms-design-css-conversion="no" />
        <!--ME:</asp:ContentPlaceHolder>-->

```

サイト閲覧者がこのページ レイアウトを使用するページを閲覧すると、この追加ページ ヘッダーがマスター ページのヘッダーの最後に組み込まれて、ページ レイアウトのスタイルはマスター ページのスタイルの後で適用されるようになります。
  
    
    
このようにして、各ページ レイアウトは独自のスタイル シートを持つことができます。たとえば、 `id="xyz"` である **<div>** を、左側に表示されるページ レイアウトと、右側に表示される別のページ レイアウトで使用できます。
  
    
    
また、各ページ レイアウトでは、1 つ以上のデバイス チャネル固有スタイル シートを使用することもできます。たとえば、電話用とデスクトップ用でレイアウトが異なるページ レイアウトを使用できます。そのためには、1 つ以上のデバイス チャネル パネルを **PlaceHolderAdditionalPageHead** の内部に配置し、各チャネル パネルにはチャネル固有のスタイルのスタイル シートへのリンクを追加します。これにより、たとえば、 `id="abc"` である **<div>** を使用して、あるチャネルでは大きいテキストを表示し、別のチャネルでは小さいテキストを表示できます。
  
    
    
以下では、ページ レイアウトに対するスタイル シート リンクの配置場所に関する一般的なシナリオを示します。
  
    
    

### マスター ページからスタイルにリンクする

最も単純なシナリオは、マスター ページからリンクしている 1 つのスタイル シートに 1 つ以上のページ レイアウトのスタイルを含めるものです。マスター ページでは, .css ファイルの終了 **</head>** タグの直前にリンクを配置し、corev15.css などの既定の SharePoint スタイル シートをオーバーライドします。
  
    
    

```HTML

<head>
…
<link rel="stylesheet" type="text/css" href="MyStyleSheet.css" />
</head>

```


### ページ レイアウトからスタイルにリンクする

各ページで読み込まれる CSS の重さを最小限にする場合は、ページ レイアウトごとに CSS ファイルを分けることができます。このシナリオでは、ページ レイアウトのスタイルは **PlaceHolderAdditionalPageHead** という名前のコンテンツ プレースホルダーに配置します。
  
    
    

```HTML

<!--MS:<asp:ContentPlaceHolder id="PlaceHolderAdditionalPageHead" runat="server">-->
            <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
            <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
<link href="MyPageLayout.css" rel="stylesheet" type="text/css" ms-design-css-conversion="no" />
        <!--ME:</asp:ContentPlaceHolder>-->

```


### デバイス チャネルごとのページ レイアウトでスタイルにリンクする

複数のデバイス チャネルがある場合、チャネルごとにページ レイアウトのレンダリングを変えることがあります。このシナリオでは、1 つ以上のデバイス チャネル パネルを **PlaceHolderAdditionalPageHead** の内部に配置し、チャネル固有の CSS ファイルへのリンクを各チャネル パネル内に追加します。
  
    
    

```HTML

<!--MS:<asp:ContentPlaceHolder id="PlaceHolderAdditionalPageHead" runat="server">-->
<div data-name="DeviceChannelPanel">
    <!--CS: Start Device Channel Panel Snippet-->
    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:DeviceChannelPanel runat="server" IncludedChannels="Channel1">-->
…..
<link rel="stylesheet" type="text/css" href="MyStyleSheet.css" ms-design-css-conversion="no" />
    <!--ME:</Publishing:DeviceChannelPanel>-->
    <!--CE: End Device Channel Panel Snippet-->
</div><div data-name="DeviceChannelPanel">
    <!--CS: Start Device Channel Panel Snippet-->
    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:DeviceChannelPanel runat="server" IncludedChannels="Channel2">-->
…..
<link rel="stylesheet" type="text/css" href="CSS5.css" />
    <!--ME:</Publishing:DeviceChannelPanel>-->
    <!--CE: End Device Channel Panel Snippet-->
</div>

```


## HTML ページ レイアウト内のマークアップの概要
<a name="UnderstandMarkup"> </a>

ページ レイアウトを作成すると、SharePoint が使用する .aspx ファイルが作成され、ページ レイアウトの HTML バージョンにいくつかの HTML マークアップが追加されます。HTML ページ レイアウトを HTML エディターで編集するときは、このマークアップの一部の目的を理解していると役に立つことがあります。ほとんどのマークアップは、HTML マスター ページに追加されるマークアップと似ています。詳細については、「 [方法: SharePoint 2013 で HTML ファイルをマスター ページに変換する](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)」を参照してください。
  
    
    
ページ レイアウトに固有のマークアップは、ページ レイアウトが関連付けられているコンテンツ タイプに基づいてページ レイアウトに追加されるページ フィールドです。ページ フィールドは、 `id="PlaceHolderMain"` であるコンテンツ プレースホルダーの内部に出現します。たとえば、 **PlaceHolderMain** に対する次のマークアップには、関連付けられているコンテンツ タイプの **Title** フィールドおよび **Page Image** フィールドを表す 2 つのページ フィールドが含まれます。
  
    
    



```HTML

<!--MS:<asp:ContentPlaceHolder ID="PlaceHolderMain" runat="server">-->
            <div>
                <!--CS: Start Page Field: Title Snippet-->
                <!--SPM:<%@Register Tagprefix="PageFieldTextField" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
                <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
                <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
                    <!--MS:<PageFieldTextField:TextField FieldName="fa564e0f-0c70-4ab9-b863-0177e6ddd247" runat="server">-->
                    <!--ME:</PageFieldTextField:TextField>-->
                <!--ME:</Publishing:EditModePanel>-->
                <!--CE: End Page Field: Title Snippet-->
            </div>
            <div>
                <!--CS: Start Page Field: Page Image Snippet-->
                <!--SPM:<%@Register Tagprefix="PageFieldRichImageField" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
                <!--MS:<PageFieldRichImageField:RichImageField FieldName="3de94b06-4120-41a5-b907-88773e493458" runat="server">-->
                    <!--PS: Start of READ-ONLY PREVIEW (do not modify)--><div id="ctl02_label" style="display:none">Page Image</div><div id="ctl02__ControlWrapper_RichImageField" class="ms-rtestate-field" style="display:inline" aria-labelledby="ctl02_label"><div align="left" class="ms-formfieldcontainer"><div class="ms-formfieldlabelcontainer" nowrap="nowrap"><span class="ms-formfieldlabel" nowrap="nowrap">Page Image</span></div><div class="ms-formfieldvaluecontainer"><div class="ms-rtestate-field"><img alt="" src="/_layouts/images/home.gif" style="BORDER: px solid; " /></div></div></div></div><!--PE: End of READ-ONLY PREVIEW-->
                <!--ME:</PageFieldRichImageField:RichImageField>-->
                <!--CE: End Page Field: Page Image Snippet-->
            </div>
        <!--ME:</asp:ContentPlaceHolder>-->

```


## その他の技術情報
<a name="AdditionalResources"> </a>


-  [SharePoint 2013 のデザイン マネージャーの概要](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [方法: SharePoint 2013 で HTML ファイルをマスター ページに変換する](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md)
    
  

