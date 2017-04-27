---
title: SharePoint 2013 でカタログベースのサイトのページ レイアウトをカスタマイズする方法
ms.prod: SHAREPOINT
ms.assetid: 21d8db99-73b3-4429-b6cb-04e375af9f55
---


# SharePoint 2013 でカタログベースのサイトのページ レイアウトをカスタマイズする方法
SharePoint Server 2013 クロスサイト発行サイト用にカテゴリ ページとカタログ アイテム ページのレイアウトを作成し、カスタマイズする方法について説明します。
## カタログベース サイトのページ レイアウトを作成しカスタマイズするための前提条件
<a name="bk_prereqs"> </a>

以下の例に示す手順を実行するには、次のものが必要です。
  
    
    

- HTML エディター
    
  
- SharePoint Server 2013 クロスサイト発行環境
    
  
SharePoint クロスサイト発行環境の設定方法の詳細については、「 [SharePoint Server 2013 でのクロスサイト発行の設定](http://technet.microsoft.com/ja-jp/library/jj656774.aspx)」を参照してください。
  
    
    

### カタログベース サイトのページ レイアウトを作成しカスタマイズするために知っておく必要がある中心概念

表 1 に、カタログベース サイトのページ レイアウトを作成しカスタマイズする際の概念および手順を理解するのに役に立つ記事を示します。
  
    
    

**表 1 カタログベース サイトのページ レイアウトを作成しカスタマイズするための中心概念**


|**記事のタイトル**|**説明**|
|:-----|:-----|
| [SharePoint Server 2013 でのクロスサイト発行の概要](http://technet.microsoft.com/ja-jp/library/jj635883.aspx) <br/> |クロスサイト発行および検索 Web パーツを使用して適応性のある SharePoint インターネット、イントラネット、およびエクストラネット サイトを作成する方法を説明します。  <br/> |
| [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md) <br/> |SharePoint Server 2013 でのページ レイアウトの作成方法について説明します。  <br/> |
| [SharePoint 2013 でページをプレビューしているときのエラーと警告を解決する方法](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md) <br/> |サーバー側のプレビューにページが表示されない問題の解決方法について説明します。  <br/> |
| [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md) <br/> |スニペットを使用して SharePoint 機能を HTML マスター ページまたはページ レイアウトに追加する方法について説明します。  <br/> |
   

## カテゴリ ページ レイアウトとカタログ アイテム ページ レイアウトの概要
<a name="bk_introduction"> </a>

カテゴリ ページおよびカタログ アイテム ページは、構造化カタログ コンテンツをサイト全体で統一感を持たせて表示する場合に使用するページ レイアウトです。既定では、SharePoint Server 2013 によって、カタログ接続ごとに、カテゴリ ページ レイアウトが 1 つと、カタログ アイテム ページ レイアウトが 1 つ自動的に作成されます。このようなレイアウトをベースとするページは、サイトをカタログに接続したときに、発行サイトのページ ライブラリ内に作成されます。ページ レイアウトの詳細については、「 [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)」を参照してください。カテゴリ ページ レイアウトおよびカタログ アイテム ページ レイアウトに固有の機能の詳細については、 [SharePoint Server 2013 でのクロスサイト発行の概要](http://technet.microsoft.com/ja-jp/library/jj635883.aspx)を参照してください。
  
    
    
既定では、カテゴリ ページ レイアウトとカタログ アイテム ページ レイアウトは、発行サイトをカタログに接続すると、自動的に作成されます。また、デザイン マネージャーを使用すれば、発行サイトをカタログに接続するとき、または発行サイトでナビゲーション条件セットを設定するときに選択可能な、カテゴリ ページ レイアウトおよびカタログ アイテム ページ レイアウトを作成することもできます。
  
    
    

## カテゴリ ページ レイアウトの作成
<a name="bk_createCategoryPage"> </a>

カテゴリ ページ レイアウトを作成またはカスタマイズするには、 **マスター ページ ギャラリー**を指すマップ済みネットワークドライブを事前に作成しておくことをお勧めします。詳細については、「 [[方法]: SharePoint 2013 マスター ページ ギャラリーへのネットワーク ドライブの割り当て](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)」を参照してください。
  
    
    
カテゴリ ページ レイアウトを作成する最も簡単な方法は、発行サイトをカタログに接続したときに、SharePoint にページ レイアウトを自動的に作成させ、既存のカテゴリ ページ レイアウトをカスタマイズしてページ デザインで要求されるようにマークアップを変更するというものです。あるいは、デザイン マネージャーを使用して、新しいカテゴリ ページ レイアウトを最初から作成することもできます。
  
    
    

### SharePoint によって自動的に作成された既存のカテゴリ ページ レイアウトをカスタマイズするには


1. Windows エクスプローラーを使用して、マスター ページ ギャラリーを指すマップ済みネットワーク ドライブを開きます。
    
  
2. カテゴリ ページ レイアウトをカスタマイズするには、HTML エディターを使用して、マップ済みドライブ内の HTML ファイルを開いて編集することにより、サーバーに直接置かれている HTML ファイルを編集します。HTML ファイルを保存するたびに、変更内容が関連付けされている .aspx ファイルと同期されます。
    
  
3. **id="PlaceHolderMain"** を持つコンテンツ プレースホルダー内のマークアップを、ページ レイアウト内で使用するマークアップに置き換えます。
    
    > **重要**
      > カテゴリ ページに検索結果を表示できるように、コンテンツ検索スニペット マークアップを保持する必要があります。 
4. ページに追加するスニペット用に HTML を設定してコピーするには、「 [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md)」の「スニペット ギャラリーからスニペットを挿入する」に記載されている手順 1 ～ 手順 11 に従います。
    
  
5. マークアップに必要なその他の変更を行い、ファイルを保存します。
    
  
6. 「 [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)」の「ページ レイアウトの作成」に記載されている手順 9 ～ 手順 11 に従って、ファイルの状態をチェックし、ページ レイアウトをプレビューし、エラーを修正します。
    
  

### デザイン マネージャーを使用してカテゴリ ページ レイアウトを作成するには


1. 「 [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)」の「ページ レイアウトの作成」に記載されている手順 1 ～ 手順 6 に従います。
    
  
2. 手順 7 で、[ **記事ページ**] コンテンツ タイプを選択します。
    
  
3. [ **OK**] をクリックします。
    
    この時点で、SharePoint によって、同じ名前を持つ HTML ファイルと .aspx ファイルが作成されます。
    
    デザイン マネージャーに、HTML ファイルが表示されると共に、[ **状態**] 列に次の 2 つの状態のうちいずれかが表示されます。
    
  - エラー
    
  
  - **正常に変換されました**
    
  
4. Windows エクスプローラーを使用して、マスター ページ ギャラリーを指すマップ済みネットワーク ドライブを開きます。
    
  
5. カテゴリ ページ レイアウトをカスタマイズするには、HTML エディターを使用して、マップ済みドライブ内の HTML ファイルを開いて編集することにより、サーバー上に直接置かれている HTML ファイルを編集します。HTML ファイルを保存するたびに、変更内容が、関連付けされている .aspx ファイルと同期されます。
    
  
6. **<head>** タグの、 **id="PlaceHolderPageTitle"** を持つコンテンツ プレースホルダーを以下の内容で置き換えます。
    
  ```HTML
  
<!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitle" runat="server">-->
<!--CS: Start Taxonomy TermProperty Snippet-->
<!--SPM:<%@Register Tagprefix="Taxonomy"  Namespace="Microsoft.SharePoint.Taxonomy" Assembly="Microsoft.SharePoint.Taxonomy, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c" %>-->
<!--MS:<Taxonomy:TermProperty Property="Name" runat="server">-->
<!--ME:</Taxonomy:TermProperty>-->
<!--ME:</asp:ContentPlaceHolder>-->
  ```

7. **id="PlaceHolderPageTitleInTitleArea"** を持つコンテンツ プレースホルダーを探し、それを以下の内容で置き換えます。
    
  ```HTML
  
<!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitleInTitleArea" runat="server">-->
<!--SPM:<asp:SiteMapPath runat="server" ParentLevelsDisplayed="1" SiteMapProvider="CurrentNavigationSwitchableProvider"/>-->
<!--ME:</asp:ContentPlaceHolder>-->
  ```

8. **id="PlaceHolderMain"** を持つコンテンツ プレースホルダー内のマークアップを、ページ レイアウト内で使用するマークアップで置き換えます。
    
  
9. ページに追加する、コンテンツ検索スニペットおよびその他のスニペット用に HTML ファイルを設定しコピーするには、「 [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md)」の「スニペット ギャラリーからスニペットを挿入する 」に記載されている手順 1 ～ 手順 11 に従います。
    
    > **メモ**
      > コンテンツ検索スニペットをページ レイアウトに追加する場合は、発行サイトをカタログに接続したときに作成された検索先を使用するようにクエリを変更してください。詳細については、「 [SharePoint Server 2013 で Web コンテンツ管理用の検索先を構成する](http://technet.microsoft.com/ja-jp/library/jj715262.aspx)」を参照してください。 
10. マークアップに対してその他の必要な変更を行い、ファイルを保存します。
    
  
11. 「 [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)」の「ページ レイアウトの作成」に記載されている手順 9 ～ 手順 11 に従って、ファイルの状態をチェックし、ページ レイアウトをプレビューし、エラーがあれば修正します。
    
  

## HTML カテゴリ ページ レイアウト内のマークアップを理解する
<a name="bk_CategoryPageMarkup"> </a>

1 つのページ レイアウトを作成すると、SharePoint が使用する .aspx ファイルが 1 つ作成され、ページ レイアウトの HTML バージョンにいくつかの HTML マークアップが追加されます。 カテゴリ ページ レイアウトには、クロスサイト コレクション発行機能に基づくページ レイアウトに追加され、カテゴリ ページ レイアウトごとに固有のマークアップ コンポーネントがあります。HTML カテゴリ ページ レイアウトを HTML エディターで編集するときは、このマークアップの一部を理解していると役に立つことがあります。
  
    
    

### ブラウザー ウィンドウ ページ タイトル

 **id="PlaceHolderPageTitle"** を持つコンテンツ プレースホルダー内に表示されるコンポーネントには、ブラウザー ウィンドウのページ タイトルとして、標準的なページ フィールド値を使用するのでなく、条件プロパティを使用するように SharePoint に指示するマークアップが含まれます。以下のコードは、ブラウザー ウィンドウ ページ タイトル用のマークアップを示しています。
  
    
    

```HTML

<!--CS: Start Taxonomy TermProperty Snippet-->
<!--SPM:<%@Register Tagprefix="Taxonomy"  Namespace="Microsoft.SharePoint.Taxonomy" Assembly="Microsoft.SharePoint.Taxonomy, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c" %>-->
<!--MS:<Taxonomy:TermProperty Property="Name" runat="server">-->
<!--ME:</Taxonomy:TermProperty>-->
```


### ページ タイトル

 **id="PlaceHolderPageTitleInTitleArea"** を持つコンテンツ プレースホルダー内に表示されるコンポーネントには、ページ上のページ タイトルとして、 **SPTitleBreadcrumb** スニペットおよび標準的なページ タイトル フィールド値を使用するのでなく、条件プロパティを使用するように SharePoint に指示するマックアップが含まれます。以下のコードは、ページ タイトル用のマークアップを示しています。
  
    
    

```HTML

<!--SPM:<asp:SiteMapPath runat="server" ParentLevelsDisplayed="1" SiteMapProvider="CurrentNavigationSwitchableProvider"/>-->"
```


### コンテンツ検索スニペット

ページ コンテンツ スニペットの後に表示されるコンポーネントには、 **id="PlaceHolderMain"** を持つコンテンツ プレースホルダーの内部で、Web パーツ ゾーンを 4 つ含む Web パーツ ゾーン スニペット用のマークアップが含まれます。最初の Web パーツ ゾーンには、ページ上にコンテンツ検索 Web パーツを表示するコンテンツ検索スニペットが含まれます。またこのスニペットには、コンテンツ検索 Web パーツが検索先をクエリしてページに結果を表示するのを支援する情報が含まれます。残りの 3 つの Web パーツ ゾーンは空です。独自のカテゴリ ページ レイアウトを作成する場合は、コンテンツ検索スニペット用のマークアップをページ レイアウト用の HTML ファイルに含める必要があります。以下のコードは、コンテンツ検索スニペット用のマークアップを示しています。 _ResultSourceID_ を検索先の GUID に置き換え、 _CatalogURL_ をカタログの URL に置き換えます。
  
    
    

> **メモ**
> スニペットをページ レイアウトに追加すると、 **ID** および **__WebPartId** 用の GUID が SharePoint によってランダムに生成されます。
  
    
    


```HTML
<!--
CS: Start Content Search Snippet-->
<!--SPM:<%@Register Tagprefix="a781102493" Namespace="Microsoft.Office.Server.Search.WebControls" Assembly="Microsoft.Office.Server.Search, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c"%>-->
<!--MS:<a781102493:ContentBySearchWebPart runat="server" DataProviderJSON="{&amp;#34;QueryTemplate&amp;#34;:&amp;#34;&amp;#34;,&amp;#34;SourceID&amp;#34;
:&amp;#34;ResultSourceID&amp;#34;,&amp;#34;PropertiesJson&amp;#34;:&amp;#34;
{'Tag':'{Term.IDWithChildren}','Scope':'CatalogURL'}&amp;#34;}" ResultsPerPage="3" RenderTemplateId="~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/Control_ListWithPaging.js" 
ItemTemplateId="~sitecollection/_catalogs/masterpage/Display Templates/Content Web Parts/Item_PictureOnTop.js" SelectedPropertiesJson="[&amp;#34;WorkId&amp;#34;,&amp;#34;Rank&amp;#34;,&amp;#34;Title&amp;#34;,&amp;#34;Author&amp;#34;,&amp;#34;
Size&amp;#34;,&amp;#34;Path&amp;#34;,&amp;#34;Description&amp;#34;,&amp;#34;Write&amp;#34;,&amp;#34;CollapsingStatus&amp;#34;,&amp;#34;
HitHighlightedSummary&amp;#34;,&amp;#34;HitHighlightedProperties&amp;#34;,&amp;#34;ContentClass&amp;#34;,&amp;#34;
PictureThumbnailURL&amp;#34;,&amp;#34;ServerRedirectedURL&amp;#34;,&amp;#34;ServerRedirectedEmbedURL&amp;#34;,&amp;#34;
ServerRedirectedPreviewURL&amp;#34;,&amp;#34;FileExtension&amp;#34;,&amp;#34;ContentTypeId&amp;#34;,&amp;#34;ParentLink&amp;#34;,&amp;#34;
ViewsLifeTime&amp;#34;,&amp;#34;ViewsRecent&amp;#34;,&amp;#34;SectionNames&amp;#34;,&amp;#34;SectionIndexes&amp;#34;,&amp;#34;
SiteLogo&amp;#34;,&amp;#34;SiteDescription&amp;#34;,&amp;#34;deeplinks&amp;#34;,&amp;#34;importance&amp;#34;]" ShouldHideControlWhenEmpty="True" FrameType="None" SuppressWebPartChrome="False" Description="$Resources:Microsoft.Office.Server.Search,CBS_Description;" IsIncluded="True" 
ZoneID="" PartOrder="0" FrameState="Normal" AllowRemove="True" AllowZoneChange="True" 
AllowMinimize="True" AllowConnect="True" AllowEdit="True" AllowHide="True" IsVisible="True" 
DetailLink="" HelpLink="" HelpMode="Modeless" Dir="Default" PartImageSmall="" IsIncludedFilter="" ExportControlledProperties="True" ConnectionID="00000000-0000-0000-0000-000000000000" ID="g_54e35103_6f29_4dd9_b93b_8d4c863834af" ChromeType="None" ExportMode="All" __MarkupType="vsattributemarkup" __WebPartId="54e35103-6f29-4dd9-b93b-8d4c863834af" 
WebPart="true" Height="" Width="" Title="$Resources:cms,WebPartZoneTitle_Dynamic;">-->
<!--ME:</a781102493:ContentBySearchWebPart>-->
<!--CE: End Content Search Snippet-->

```


## カタログ アイテム ページ レイアウトの作成
<a name="bk_createCatItemPage"> </a>

カタログ アイテム ページ レイアウトを作成またはカスタマイズするには、マスター ページ ギャラリーを指すマップ済みネットワークドライブを事前に作成しておくことをお勧めします。 詳細については、「 [[方法]: SharePoint 2013 マスター ページ ギャラリーへのネットワーク ドライブの割り当て](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)」を参照してください。
  
    
    
カテゴリ ページ レイアウトの場合と同様に、カタログ アイテム ページ レイアウトを作成する最も簡単な方法は、発行サイトをカタログに接続したときに、SharePoint にページ レイアウトを自動的に作成させ、既存のカタログ アイテム ページ レイアウトをカスタマイズしてページ デザインに必要な追加のマークアップを追加するというものです。あるいは、デザイン マネージャーを使用して、新しいカタログ アイテム ページ レイアウトを最初から作成することもできます。
  
    
    

### SharePoint によって自動的に作成された既存のカタログ アイテム ページ レイアウトをカスタマイズするには


1. Windows エクスプローラーを使用して、マスター ページ ギャラリーを指すマップ済みネットワーク ドライブを開きます。
    
  
2. カタログ アイテム ページ レイアウトをカスタマイズするには、HTML エディターを使用して、マップされているドライブ内の HTML ファイルを開いて編集することにより、サーバー上に直接存在する HTML ファイルを編集します。HTML ファイルを保存するたびに、変更内容が、関連付けされている .aspx ファイルと同期されます。
    
  
3. **id="PlaceHolderMain"** を持つコンテンツ プレースホルダー内で、ページ レイアウトで使用するマークアップを追加します。
    
  
4. ページ レイアウトで使用しないスニペットを削除し、残りのスニペットは、プロパティ値を表示するマークアップ内の場所に移動します。
    
    > **注意**
      > 既定では、カタログアイテム再利用スニペットを含む Web パーツ ゾーン スニペットがページ レイアウトに追加されます。このスニペットには、ページ上で他のすべてのスニペットによって使用されるクエリ結果を返すデータ プロバイダーが含まれます。カタログアイテム再利用スニペットを、この既定の Web パーツ ゾーン スニペット内に保持することを推奨します (カタログアイテム再利用スニペットは Web パーツ ゾーンの外に移動することができ、表示されるプロパティを変更することができます。ただし、カタログアイテム再利用スニペットはページ レイアウト内に維持する必要があります。) 詳細については、この記事の中で後述する「 [ページ フィールド](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md#bk_pagefields)」を参照してください。 
5. ページで使用するスニペット用に HTML スニペットを設定しコピーするには、「 [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md)」の「スニペット ギャラリーからスニペットを挿入する」に記載されている手順 1 ～ 手順 11 に従います。
    
  
6. マークアップに対してその他の必要な変更を行い、ファイルを保存します。
    
  
7. 「 [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)」の「ページ レイアウトの作成」に記載されている手順 9 ～ 手順 11 に従って、ファイルの状態をチェックし、ページ レイアウトをプレビューし、エラーがあれば修正します。
    
  

### デザイン マネージャーを使用してカタログ アイテム ページ レイアウトを作成するには


1. 「 [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)」の「ページ レイアウトの作成」に記載されている手順 1 ～ 手順 6 に従います。
    
  
2. 手順 7 で、[ **リモート カタログ**] を選択し、ページに表示されるデータが含まれているカタログを選択します。
    
  
3. [ **OK**] をクリックします。
    
    この時点で、SharePoint によって、同じ名前を持つ HTML ファイルと .aspx ファイルが作成されます。
    
    デザイン マネージャーに、HTML ファイルが表示されると共に、[ **状態**] 列に次の 2 つの状態のうちいずれかが表示されます。
    
  - エラー
    
  
  - **正常に変換されました**
    
  
4. Windows エクスプローラーを使用して、マスター ページ ギャラリーを指すマップ済みネットワーク ドライブを開きます。
    
  
5. カタログ アイテム ページ レイアウトをカスタマイズするには、HTML エディターを使用して、マップされているドライブ内の HTML ファイルを開き編集することにより、サーバー上に直接存在する HTML ファイルを編集します。HTML ファイルを保存するたびに、変更内容が、関連付けされている .aspx ファイルと同期されます。
    
  
6. **id="PlaceHolderMain"** を持つコンテンツ プレースホルダー内で、ページ レイアウトで使用するマークアップを追加します。
    
  
7. ページ レイアウトで使用しないスニペットを削除し、残りのスニペットは、プロパティ値を表示するマークアップ内の場所に移動します。
    
    > **注意**
      > 既定では、カタログアイテム再利用スニペットを含む Web パーツ ゾーン スニペットがページ レイアウトに追加されます。このスニペットには、ページ上で他のすべてのスニペットによって使用されるクエリ結果を返すデータ プロバイダーが含まれます。カタログアイテム再利用スニペットを、この既定の Web パーツ ゾーン スニペット内に保持することを推奨します (カタログアイテム再利用スニペットは Web パーツ ゾーンの外に移動することができ、表示されるプロパティを変更することができます。ただし、カタログアイテム再利用スニペットはページ レイアウト内に維持する必要があります。) 詳細については、この記事の中で後述する「 [ページ フィールド](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md#bk_pagefields)」を参照してください。 
8. ページで使用するスニペット用に HTML スニペットを設定しコピーするには、「 [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md)」の「スニペット ギャラリーからスニペットを挿入する」に記載されている手順 1 ～ 手順 11 に従います。
    
  
9. マークアップに対してその他の必要な変更を行い、ファイルを保存します。
    
  
10. 「 [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)」の「ページ レイアウトの作成」に記載されている手順 9 ～ 手順 11 に従って、ファイルの状態をチェックし、ページ レイアウトをプレビューし、エラーがあれば修正します。
    
  

## HTML カタログ アイテム ページ レイアウト内のマークアップを理解する
<a name="bk_CatItemMarkup"> </a>

ページ レイアウトを 1 つ作成すると、SharePoint が使用する .aspx ファイルが 1 つ作成され、ページ レイアウトの HTML バージョンにいくつかの HTML マークアップが追加されます。 カタログ アイテム ページ レイアウトには、クロスサイト コレクション発行機能に基づくページ レイアウトに追加され、カタログ アイテム ページ レイアウトごとに固有のマークアップ コンポーネントがあります。HTML カタログ アイテム ページ レイアウトを HTML エディターで編集するときは、このマークアップの一部を理解していると役に立つことがあります。
  
    
    

### ブラウザー ウィンドウ ページ タイトル

 **id="PlaceHolderPageTitle"** を持つコンテンツ プレースホルダー内に表示されるコンポーネントには、ブラウザー ウィンドウ内のページ タイトルとして、標準的なページ タイトル フィールド値を使用するのでなく、カタログ アイテムの名前を使用するように SharePoint に指示するカタログアイテム再利用スニペットが含まれます。以下のコードは、ブラウザー ウィンドウ ページ タイトル用のマークアップを示しています。
  
    
    

> **メモ**
> スニペットをページ レイアウトに追加すると、 **ID** および **__WebPartId** 用の GUID が SharePoint によってランダムに生成されます。
  
    
    


```HTML

<!--CS: [Title] Start Catalog-Item Reuse Snippet-->
<!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;Title&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_863912c1_c849_46dc_8781_2920ee2bc83f" __WebPartId="{863912c1-c849-46dc-8781-2920ee2bc83f}">-->
<!--SPM:<RenderFormat>-->
<!--DC:Renders value from search without any additional formatting.-->
<!--SPM:</RenderFormat>-->
<!--SPM:</cc1:CatalogItemReuseWebPart>-->
<!--CE:End Catalog-Item Reuse Snippet-->

```


### ページ フィールド
<a name="bk_pagefields"> </a>

 **id="PlaceHolderMain"** を持つコンテンツ プレースホルダー内に表示されるコンポーネントには、 **Title**、 **Page Content**、および **Catalog-Item URL** フィールド用のスニペットが含まれます。これらのスニペットのいずれかをページ レイアウトから削除してもかまいません。以下のコードは、ページ フィールド用のマークアップを示しています。
  
    
    

```HTML

<div>
    <!--CS: Start Page Field: Title Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldTextField" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, 
Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--SPM:<%@Register Tagprefix="Publishing" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<Publishing:EditModePanel runat="server" CssClass="edit-mode-panel">-->
        <!--MS:<PageFieldTextField:TextField FieldName="fa564e0f-0c70-4ab9-b863-0177e6ddd247" 
runat="server">-->
        <!--ME:</PageFieldTextField:TextField>-->
    <!--ME:</Publishing:EditModePanel>-->
    <!--CE: End Page Field: Title Snippet-->
</div>
<div>
    <!--CS: Start Page Field: Page Content Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldRichHtmlField" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<PageFieldRichHtmlField:RichHtmlField FieldName="f55c4d88-1f2e-4ad9-aaa8-819af4ee7ee8" runat="server">-->
        <!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
            <div id="ctl02_label" style="display:none">Page Content</div>
            <div id="ctl02__ControlWrapper_RichHtmlField" class="ms-rtestate-field" style="display:inline" aria-labelledby="ctl02_label">
                <div align="left" class="ms-formfieldcontainer">
                    <div class="ms-formfieldlabelcontainer" nowrap="nowrap">
                        <span class="ms-formfieldlabel" nowrap="nowrap">Page Content</span>
                    </div>
                    <div class="ms-formfieldvaluecontainer">
                        <div class="ms-rtestate-field">Page Content field value. Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.</div>
                    </div>
                </div>
            </div>
        <!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</PageFieldRichHtmlField:RichHtmlField>-->
    <!--CE: End Page Field: Page Content Snippet-->
</div>
<div>
    <!--CS: Start Page Field: Catalog-Item URL Snippet-->
    <!--SPM:<%@Register Tagprefix="PageFieldCatalogSourceFieldControl" Namespace="Microsoft.SharePoint.Publishing.WebControls" Assembly="Microsoft.SharePoint.Publishing, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--MS:<PageFieldCatalogSourceFieldControl:CatalogSourceFieldControl FieldName="75772bbf-0c25-4710-b52c-7b78344ad136" runat="server">-->
    <!--PS: Start of READ-ONLY PREVIEW (do not modify)-->
        <div align="left" class="ms-formfieldcontainer">
            <div class="ms-formfieldlabelcontainer" nowrap="nowrap">
                <span class="ms-formfieldlabel" nowrap="nowrap">Catalog-Item URL</span>
            </div>
            <div class="ms-formfieldvaluecontainer">
                <a href="http://www.example.com">Link to sample web site.</a>
            </div>
        </div>
    <!--PE: End of READ-ONLY PREVIEW-->
    <!--ME:</PageFieldCatalogSourceFieldControl:CatalogSourceFieldControl>-->
    <!--CE: End Page Field: Catalog-Item URL Snippet-->
</div>

```

発行サイトをカタログに接続したとき、またはページ レイアウト作成中にリモート カタログを選択することにより発行サイトを作成したときに、カタログ アイテム ページ レイアウトが自動的に作成された場合、ページ レイアウトには、ページのデータ プロバイダーを登録するカタログアイテム再利用スニペットが入っている Web パーツ ゾーン スニペットも含まれます。カタログアイテム再利用スニペットには、 **UseSharedDataProvider** プロパティが含まれ、このプロパティは **False** に設定されます。Web パーツ ゾーン スニペットは、ページ レイアウトから削除できますが、ページにカタログ アイテムを表示するためには、ページ レイアウト マークアップにカタログアイテム再利用スニペットが保持されている必要があります。このページ レイアウトを使用するページを作成する場合は、Web パーツを設定して、ユーザーがページを閲覧したときにそれが非表示になるようにします。
  
    
    

> **重要**
> 新しいカタログ アイテム ページ レイアウトを作成する場合、かつリモート カタログでなくコンテンツ タイプを選択する場合は、カタログアイテム再利用スニペットをページ レイアウトに含める必要があります。以下のコードは、カタログアイテム再利用スニペットが Web パーツ ゾーン スニペット内にある場合の、カタログアイテム再利用スニペットに対するマークアップを示しています。 _ManagedPropertyName_ を、表示する管理プロパティの名前に置換し、 _ResultSourceID_ を検索先の GUID に置換し、 _CatalogURL_ をカタログの URL に置換します。
  
    
    




```HTML

<div>
    <!--CS: Start Web Part Zone Snippet-->
    <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, 
Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
    <!--SPM:<%@Register Tagprefix="cc1"  Namespace="Microsoft.Office.Server.Search.WebControls" Assembly="Microsoft.Office.Server.Search, Version=15.0.0.0, Culture=neutral, 
PublicKeyToken=71e9bce111e9429c" %>-->
    <!--MS:<WebPartPages:WebPartZone runat="server" Title="&amp;#60;%$Resources:cms,WebPartZoneTitle_Body%&amp;#62;" AllowPersonalization="False" FrameType="TitleBarOnly" ID="Body" Orientation="Vertical">-->
        <!--MS:<ZoneTemplate>-->
            <!--CS: [ManagedPropertyName] Start Catalog-Item Reuse Snippet-->
            <!--DC:To render the search property using a rendering template, change the "UseServerSideRenderFormat" property to "False".-->
            <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" AddSEOPropertiesFromSearch="True" LogAnalyticsViewEvent="True" UseSharedDataProvider="False" OverwriteResultPath="False" DataProviderJSON="{&amp;#34;QueryTemplate&amp;#34;:&amp;#34;ListItemID:{URLTOKEN.1}&amp;#34;,&amp;#34;SourceID&amp;#34;:&amp;#34; ResultSourceID&amp;#34;,&amp;#34;PropertiesJson&amp;#34;:&amp;#34;{&amp;#39;Scope&amp;#39;:&amp;#39;  CatalogURL&amp;#39;,&amp;#39;Tag&amp;#39;:&amp;#39;{Term}&amp;#39;}&amp;#34;}" ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;ManagedPropertyName&amp;#34;]" Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" MissingAssembly="Cannot import this Web Part." ID="g_d63eebe7_207f_4e8c_9566_7381acc80cc7" __WebPartId="{d63eebe7-207f-4e8c-9566-7381acc80cc7}">-->
            <!--SPM:<RenderFormat>-->
            <!--DC:Renders value from search without any additional formatting.-->
            <!--SPM:</RenderFormat>-->
            <!--SPM:</cc1:CatalogItemReuseWebPart>-->
        <!--ME:</ZoneTemplate>-->
    <!--ME:</WebPartPages:WebPartZone>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>

```

発行サイトをカタログに接続したとき、またはページ レイアウト作成中にリモート カタログを選択することにより発行サイトを作成したときにカタログ アイテム ページ レイアウトが自動的に作成された場合、ページの他の部分には、認証サイト上のカタログからの管理プロパティに対応するカタログアイテム再利用スニペットが含まれます。このような管理プロパティは、カタログ アイテム ページ レイアウトを使用することによって表示される特定のカタログ アイテムの詳細を表示します。これらのカタログアイテム再利用スニペットは Web パーツ ゾーンの外側に表示され、カテゴリ ページでアイテムが選択されると、ページ上に直接表示されます。表 2 に、カタログ アイテム ページ レイアウトに自動的に含まれる管理プロパティを示します。
  
    
    

> **メモ**
> 一部の管理プロパティは、カタログがページ ライブラリである場合にのみ含まれます。表 2 の **使用元**列は、ページ ライブラリとリストの両方で使用される管理プロパティと、ページ ライブラリのみで使用される管理プロパティを示します。 
  
    
    


**表 2. 既定の管理プロパティのカタログアイテム再利用スニペット**


|**管理プロパティ**|**説明**|**使用元**|
|:-----|:-----|:-----|
|**AuthorOWSUSER** <br/> |ページを作成したユーザーの名前です。  <br/> |ページ ライブラリのみ  <br/> |
|**CreatedOWSDATE** <br/> |ページまたはリスト アイテムが作成された日付です。  <br/> |ページ ライブラリとリスト  <br/> |
|**EditorOWSUSER** <br/> |ページまたはリスト アイテムを最後に変更したユーザーの名前です。  <br/> |ページ ライブラリとリスト  <br/> |
|**ListItemID** <br/> |ページまたはリスト アイテムの ID です。  <br/> |ページ ライブラリとリスト  <br/> |
|**ModifiedOWSDATE** <br/> |ページまたはリスト アイテムが最後に変更された日付です。  <br/> |ページ ライブラリとリスト  <br/> |
|**PublishingContactOWSUSER** <br/> |連絡先は発行機能により作成されるサイト列です。これは、ページの連絡窓口であるユーザーまたはグループとして、ページ コンテンツ タイプで使用されます。  <br/> |ページ ライブラリのみ  <br/> |
|**PublishingIsFurlPageOWSBOOL** <br/> |ページがわかりやすい URL に関連付けられているかどうかを示すブール値です。  <br/> |ページ ライブラリのみ  <br/> |
|**PublishingPageContentOWSHTML** <br/> |ページの HTML コンテンツです。  <br/> |ページ ライブラリのみ  <br/> |
|**PublishingPageLayoutOWSURLH** <br/> |ページの作成に使用されたページ レイアウトの URL です。  <br/> |ページ ライブラリのみ  <br/> |
|**Title** <br/> |ページまたはリスト アイテムのタイトルです。  <br/> |ページ ライブラリとリスト  <br/> |
   
また、ページ ライブラリまたはリストに追加するカスタム列の管理プロパティも、カタログアイテム再利用スニペットに含められます。管理プロパティ名は、サイト列を作成するときに使用するサイト列タイプに基づいて変化します。詳細については、 [SharePoint Server 2013 で自動的に作成される管理プロパティ](http://technet.microsoft.com/ja-jp/library/jj613136.aspx)、および [SharePoint Server 2013 の検索スキーマの概要](http://technet.microsoft.com/ja-jp/library/jj219669.aspx)を参照してください。
  
    
    

> **重要**
> ページ ライブラリ内の **Page Image** サイト列は、 **PublishingImage** 管理プロパティにマップされます。ただし、 **PublishingImage** 管理プロパティは、カテゴリアイテム ページ レイアウトに自動的に取り込まれません。ページ レイアウトにイメージを取り込むには、 **PublishingImage** 管理プロパティ用のカタログアイテム再利用スニペットを追加する必要があります。以下の HTML を使用してカタログアイテム再利用スニペットを追加することで、 **PublishingImage** 管理プロパティの値をページ レイアウトに表示します。 _UniqueID_ をスニペットの各インスタンスに固有の GUID に置き換えます。
  
    
    




```HTML

<div>
<!--CS: [PublishingImage] Start Catalog-Item Reuse Snippet-->
<!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;PublishingImage&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_UniqueID" __WebPartId="{UniqueID}">-->
<!--SPM:<RenderFormat>-->
<!--SPM:<Format Type="HTML"> -->
<!--SPM:<Picture>-->True<!--SPM:</Picture>-->
<!--SPM:</Format> -->
<!--SPM:</RenderFormat>-->
<!--SPM:</cc1:CatalogItemReuseWebPart>-->
<!--CE:End Catalog-Item Reuse Snippet-->
</div>

```

デザイン マネージャーを使用して新しいカタログ アイテム ページ レイアウトを作成する場合、およびリモート カタログでなくコンテンツ タイプを選択する場合は、スニペット ギャラリーを使用して、カタログアイテム再利用スニペットをページに追加することができます。以下のコードは、 **Title**、 **PublishingPageContentOWSHTML**、 **CreatedOWSDATE**、および **owstaxIdPageCategory** 管理プロパティのカタログアイテム再利用スニペットのマークアップを示しています。
  
    
    

> **メモ**
> スニペットをページ レイアウトに追加すると、 **ID** および **__WebPartId** 用の GUID が SharePoint によってランダムに生成されます。
  
    
    




```HTML

<div>
    <!--CS: [Title] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;Title&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_0dc23bb8_8d34_4f9f_8085_5a6ac286cb9e" 
__WebPartId="{0dc23bb8-8d34-4f9f-8085-5a6ac286cb9e}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [PublishingPageContentOWSHTML] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;PublishingPageContentOWSHTML&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_25253a49_a9a6_4277_bf9d_416961024cee" 
__WebPartId="{25253a49-a9a6-4277-bf9d-416961024cee}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [CreatedOWSDATE] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;CreatedOWSDATE&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." 
ID="g_4e1f180b_12f8_4e50_84d7_c72b0ee3793f" 
__WebPartId="{4e1f180b-12f8-4e50-84d7-c72b0ee3793f}">-->
    <!--SPM:<RenderFormat>-->
    <!--SPM:<Format Type="DateTime"> -->
    <!--DC:To render Date and Time, change this value to False.-->
    <!--SPM:<DateOnly>-->True<!--SPM:</DateOnly>-->
    <!--SPM:</Format> -->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>
<div>
    <!--CS: [owstaxIdPageCategory] Start Catalog-Item Reuse Snippet-->
    <!--SPM:<cc1:CatalogItemReuseWebPart runat="server" UseServerSideRenderFormat="True" 
ResultType="" NumberOfItems="1" UseSharedDataProvider="True" OverwriteResultPath="False" 
ResultsPerPage="1"  SelectedPropertiesJson="[&amp;#34;owstaxIdPageCategory&amp;#34;]" 
Title="$Resources:Microsoft.Office.Server.Search,CBSItem_Title;" 
Description="$Resources:Microsoft.Office.Server.Search,CBSItem_Description;" 
MissingAssembly="Cannot import this Web Part." ID="g_22e39e9d_1b25_42c7_bf2a_7ebca37616d4" 
__WebPartId="{22e39e9d-1b25-42c7-bf2a-7ebca37616d4}">-->
    <!--SPM:<RenderFormat>-->
    <!--DC:Renders value from search without any additional formatting.-->
    <!--SPM:</RenderFormat>-->
    <!--SPM:</cc1:CatalogItemReuseWebPart>-->
    <!--CE:End Catalog-Item Reuse Snippet-->
</div>

```


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 のサイト デザインの開発](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のデザイン マネージャーの概要](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 ページ モデルの概要](overview-of-the-sharepoint-2013-page-model.md)
    
  
-  [[方法]: SharePoint 2013 でページ レイアウトを作成する方法](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 デザイン マネージャー表示テンプレート](sharepoint-2013-design-manager-display-templates.md)
    
  

