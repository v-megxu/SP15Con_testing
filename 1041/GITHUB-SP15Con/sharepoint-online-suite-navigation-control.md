---
title: SharePoint Online Suite Navigation コントロール
ms.prod: SHAREPOINT
ms.assetid: ba93e5c0-e591-48d0-a716-a08ec7ef6cea
---


# SharePoint Online Suite Navigation コントロール
SharePoint Online の Suite Navigation コントロールで使用するマスター ページ マークアップについて説明します。 
{概要コンテンツの挿入}
  
    
    


## SharePoint Online Suite Navigation コントロール

Suite Navigation コントロールは、SharePoint Online でナビゲーション バーを常に上部に表示します。現在、このコントロールはインストール後にカスタマイズされていない状態のすべてのマスター ページで表示されます。
  
    
    
マスター ページをカスタマイズすると、この新しい Suite Navigation コントロールはマスター ページに表示されなくなります。カスタム マスター ページにこのコントロールを追加するには、 `suiteBar` `<div>` をサイトのタイプに対応するマークアップで置き換えます。
  
    
    
新しい Suite Navigation コントロールは、サイトに適用されるすべてのテーマをサポートします。上部のナビゲーション バーの色を変更しようと思うなら、それに見合ったテーマを適用すればよいという訳です。
  
    
    

> **重要**
> サイトをカスタマイズする場合のベスト プラクティスは、テーマを適用することです。カスタム CSS をサイトに適用することもできますが、将来 Suite Navigation コントロールのサービスが再度更新されるときに、カスタム CSS がうまく表示されなくなる可能性があります。 
  
    
    


> **注意**
> この新しいコントロールを使用しない場合は、マスター ページから Suite Navigation マークアップを削除して、カスタム マークアップを追加します。ただし、カスタマイズされたマスター ページを使用するなら、既定のマスター ページのコントロールの更新やカスタマイズされたマスター ページに追加された新機能を認識しなくなる恐れがあることに注意してください。カスタマイズされたマスター ページを使用することには、サービス更新時にサイトの機能やスタイルが損なわれるリスクが伴います。 
  
    
    


### イントラネット サイト用の Suite Navigation コントロール

イントラネット サイトの場合、Suite Navigation コントロール用に次のマスター ページ マークアップを使用します。Suite Navigation コードで使用される Web コントロールが、表 1 にリストされています。
  
    
    

**表 1. イントラネット サイト用の Suite Navigation Web コントロール**


|**Web コントロール**|**説明**|
|:-----|:-----|
|SharePoint:Menu  <br/> |ASP.NET Web ページにメニューを表示します。  <br/> |
|SharePoint:MenuItemTemplate  <br/> |ドロップダウン メニューの項目を作成するコントロールを表します。  <br/> |
   

```

<SharePoint:AjaxDelta runat="server" id="suiteBarDelta" BlockElement="true" CssClass="ms-dialogHidden ms-fullWidth noindex">
<div id="suiteMenuData" class="ms-hide">
<wssuc:Welcome id="IdWelcomeData" runat="server" EnableViewState="false" RenderDataOnly="true"/>
   <span class="ms-siteactions-root" id="siteactiontd">
   <SharePoint:SiteActions runat="server" accesskey="<%$Resources:wss,tb_SiteActions_AK%>"
id="SiteActionsMenuMainData"
PrefixHtml=""
SuffixHtml=""
ImageUrl="/_layouts/15/images/spcommon.png?rev=32"
ThemeKey="spcommon"
MenuAlignment="Right"
LargeIconMode="false"
>
<CustomTemplate>
<SharePoint:Menu runat="server" Visible="false"/>
<SharePoint:FeatureMenuTemplate runat="server"
FeatureScope="Site"
Location="Microsoft.SharePoint.StandardMenu"
GroupId="SiteActions"
UseShortId="true"
>
  <SharePoint:MenuItemTemplate runat="server"
  id="MenuItem_ShareThisSite"
  Text="<%$Resources:wss,siteactions_sharethissite%>"
  Description="<%$Resources:wss,siteactions_sharethissitedescription%>"
  MenuGroupId="100"
  Sequence="110"
  UseShortId="true"
  PermissionsString="ViewPages"
  PermissionMode="Any" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_EditPage"
  Text="<%$Resources:wss,siteactions_editpage15%>"
  Description="<%$Resources:wss,siteactions_editpagedescriptionv4%>"
  ImageUrl="/_layouts/15/images/ActionsEditPage.png?rev=32"
  MenuGroupId="200"
  Sequence="210"
  PermissionsString="EditListItems"
  ClientOnClickNavigateUrl="javascript:ChangeLayoutMode(false);" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_CreatePage"
  Text="<%$Resources:wss,siteactions_addpage15%>"
  Description="<%$Resources:wss,siteactions_createpagedesc%>"
  ImageUrl="/_layouts/15/images/NewContentPageHH.png?rev=32"
  MenuGroupId="200"
  Sequence="220"
  UseShortId="true"
  ClientOnClickScriptContainingPrefixedUrl="OpenCreateWebPageDialog('~siteLayouts/createwebpage.aspx')"
  PermissionsString="AddListItems, EditListItems"
  PermissionMode="All" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_Create"
  Text="<%$Resources:wss,siteactions_addapp15%>"
  Description="<%$Resources:wss,siteactions_createdesc%>"
  MenuGroupId="200"
  Sequence="230"
  UseShortId="true"
  ClientOnClickScriptContainingPrefixedUrl="GoToPage('~siteLayouts/addanapp.aspx')"
  PermissionsString="ManageLists, ManageSubwebs"
  PermissionMode="Any" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_ViewAllSiteContents"
  Text="<%$Resources:wss,quiklnch_allcontent_15%>"
  Description="<%$Resources:wss,siteactions_allcontentdescription%>"
  ImageUrl="/_layouts/15/images/allcontent32.png?rev=32"
  MenuGroupId="200"
  Sequence="240"
  UseShortId="true"
  ClientOnClickNavigateUrl="~siteLayouts/viewlsts.aspx"
  PermissionsString="ViewFormPages"
  PermissionMode="Any" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_ChangeTheLook"
  Text="<%$Resources:wss,siteactions_changethelook15%>"
  Description="<%$Resources:wss,siteactions_changethelookdesc15%>"
  MenuGroupId="300"
  Sequence="310"
  UseShortId="true"
  ClientOnClickNavigateUrl="~siteLayouts/designgallery.aspx"
  PermissionsString="ApplyThemeAndBorder,ApplyStyleSheets,Open,ViewPages,OpenItems,ViewListItems"
  PermissionMode="All" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_Settings"
  Text="<%$Resources:wss,siteactions_settings15%>"
  Description="<%$Resources:wss,siteactions_sitesettingsdescriptionv4%>"
  ImageUrl="/_layouts/15/images/settingsIcon.png?rev=32"
  MenuGroupId="300"
  Sequence="320"
  UseShortId="true"
  ClientOnClickScriptContainingPrefixedUrl="GoToPage('~siteLayouts/settings.aspx')"
  PermissionsString="EnumeratePermissions,ManageWeb,ManageSubwebs,AddAndCustomizePages,ApplyThemeAndBorder,ManageAlerts,ManageLists,ViewUsageData"
  PermissionMode="Any" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_SwitchToMobileView"
  Visible="false"
  Text="<%$Resources:wss,siteactions_switchtomobileview%>"
  Description="<%$Resources:wss,siteactions_switchtomobileviewdesc%>"
  MenuGroupId="300"
  Sequence="330"
  UseShortId="true"
  ClientOnClickScript="STSNavigate(StURLSetVar2(ajaxNavigate.get_href(), 'mobile', '1'));" />
</SharePoint:FeatureMenuTemplate>
</CustomTemplate>
  </SharePoint:SiteActions></span>
</div>
<SharePoint:ScriptBlock runat="server">
var g_navBarHelpDefaultKey = "HelpHome";
</SharePoint:ScriptBlock>
<SharePoint:DelegateControl id="ID_SuiteBarDelegate" ControlId="SuiteBarDelegate" runat="server" />
</SharePoint:AjaxDelta>
```


#### 一般向けサイト用の Suite Navigation Web コントロールの説明

一般向けサイトの場合、Suite Navigation コントロール用に次のマスター ページ マークアップを使用します。Suite Navigation コードで使用される Web コントロールが、表 2 にリストされています。
  
    
    

**表 2. 一般向けサイト用の Suite Navigation Web コントロール**


|**Web コントロール**|**説明**|
|:-----|:-----|
|SharePoint:DelegateControl  <br/> |ASP.NET Web コントロールを表示します。委任コントロールにより、使用するコントロールがプラグ可能およびトレース可能になります。  <br/> |
|SharePoint:FeatureMenuTemplate  <br/> |ドロップダウン メニューのテンプレートを作成するコントロールを表します。  <br/> |
|SharePoint:Menu  <br/> |ASP.NET Web ページにメニューを表示します。  <br/> |
|SharePoint:MenuItemTemplate  <br/> |ドロップダウン メニューの項目を作成するコントロールを表します。  <br/> |
|SharePoint:ScriptBlock  <br/> |ページ上のスクリプト ブロック コントロールを表します。  <br/> |
|SharePoint:SiteActions  <br/> |Site Action メニューのテンプレート コントロールを表します。  <br/> |
|SharePoint:SPSecurityTrimmedControl  <br/> |現在のユーザーが **PermissionString** に定義されている権限を持っている場合にのみ、現在のユーザーに対して条件付きでコントロールのコンテンツを表示します。 <br/> |
   

### 一般向けサイト用の Suite Navigation コントロール


```

<SharePoint:AjaxDelta runat="server" id="suiteBarDelta" BlockElement="true" CssClass="ms-dialogHidden ms-fullWidth noindex">
  <SharePoint:SPSecurityTrimmedControl runat="server" AuthenticationRestrictions="AuthenticatedUsersOnly" EmitDiv="true">
<div id="suiteMenuData" class="ms-hide">
<wssuc:Welcome id="IdWelcomeData" runat="server" EnableViewState="false" RenderDataOnly="true"/>
   <span class="ms-siteactions-root" id="siteactiontd">
   <SharePoint:SiteActions runat="server" accesskey="<%$Resources:wss,tb_SiteActions_AK%>"
id="SiteActionsMenuMainData"
PrefixHtml=""
SuffixHtml=""
ImageUrl="/_layouts/15/images/spcommon.png?rev=32"
ThemeKey="spcommon"
MenuAlignment="Right"
LargeIconMode="false"
>
<CustomTemplate>
<SharePoint:Menu runat="server" Visible="false"/>
<SharePoint:FeatureMenuTemplate runat="server"
FeatureScope="Site"
Location="Microsoft.SharePoint.StandardMenu"
GroupId="SiteActions"
UseShortId="true"
>
  <SharePoint:MenuItemTemplate runat="server"
  id="MenuItem_ShareThisSite"
  Text="<%$Resources:wss,siteactions_sharethissite%>"
  Description="<%$Resources:wss,siteactions_sharethissitedescription%>"
  MenuGroupId="100"
  Sequence="110"
  UseShortId="true"
  PermissionsString="ViewPages"
  PermissionMode="Any" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_EditPage"
  Text="<%$Resources:wss,siteactions_editpage15%>"
  Description="<%$Resources:wss,siteactions_editpagedescriptionv4%>"
  ImageUrl="/_layouts/15/images/ActionsEditPage.png?rev=32"
  MenuGroupId="200"
  Sequence="210"
  PermissionsString="EditListItems"
  ClientOnClickNavigateUrl="javascript:ChangeLayoutMode(false);" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_CreatePage"
  Text="<%$Resources:wss,siteactions_addpage15%>"
  Description="<%$Resources:wss,siteactions_createpagedesc%>"
  ImageUrl="/_layouts/15/images/NewContentPageHH.png?rev=32"
  MenuGroupId="200"
  Sequence="220"
  UseShortId="true"
  ClientOnClickScriptContainingPrefixedUrl="OpenCreateWebPageDialog('~siteLayouts/createwebpage.aspx')"
  PermissionsString="AddListItems, EditListItems"
  PermissionMode="All" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_Create"
  Text="<%$Resources:wss,siteactions_addapp15%>"
  Description="<%$Resources:wss,siteactions_createdesc%>"
  MenuGroupId="200"
  Sequence="230"
  UseShortId="true"
  ClientOnClickScriptContainingPrefixedUrl="GoToPage('~siteLayouts/addanapp.aspx')"
  PermissionsString="ManageLists, ManageSubwebs"
  PermissionMode="Any" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_ViewAllSiteContents"
  Text="<%$Resources:wss,quiklnch_allcontent_15%>"
  Description="<%$Resources:wss,siteactions_allcontentdescription%>"
  ImageUrl="/_layouts/15/images/allcontent32.png?rev=32"
  MenuGroupId="200"
  Sequence="240"
  UseShortId="true"
  ClientOnClickNavigateUrl="~siteLayouts/viewlsts.aspx"
  PermissionsString="ViewFormPages"
  PermissionMode="Any" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_ChangeTheLook"
  Text="<%$Resources:wss,siteactions_changethelook15%>"
  Description="<%$Resources:wss,siteactions_changethelookdesc15%>"
  MenuGroupId="300"
  Sequence="310"
  UseShortId="true"
  ClientOnClickNavigateUrl="~siteLayouts/designgallery.aspx"
  PermissionsString="ApplyThemeAndBorder,ApplyStyleSheets,Open,ViewPages,OpenItems,ViewListItems"
  PermissionMode="All" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_Settings"
  Text="<%$Resources:wss,siteactions_settings15%>"
  Description="<%$Resources:wss,siteactions_sitesettingsdescriptionv4%>"
  ImageUrl="/_layouts/15/images/settingsIcon.png?rev=32"
  MenuGroupId="300"
  Sequence="320"
  UseShortId="true"
  ClientOnClickScriptContainingPrefixedUrl="GoToPage('~siteLayouts/settings.aspx')"
  PermissionsString="EnumeratePermissions,ManageWeb,ManageSubwebs,AddAndCustomizePages,ApplyThemeAndBorder,ManageAlerts,ManageLists,ViewUsageData"
  PermissionMode="Any" />
  <SharePoint:MenuItemTemplate runat="server" id="MenuItem_SwitchToMobileView"
  Visible="false"
  Text="<%$Resources:wss,siteactions_switchtomobileview%>"
  Description="<%$Resources:wss,siteactions_switchtomobileviewdesc%>"
  MenuGroupId="300"
  Sequence="330"
  UseShortId="true"
  ClientOnClickScript="STSNavigate(StURLSetVar2(ajaxNavigate.get_href(), 'mobile', '1'));" />
</SharePoint:FeatureMenuTemplate>
</CustomTemplate>
  </SharePoint:SiteActions></span>
</div>
<SharePoint:ScriptBlock runat="server">
var g_navBarHelpDefaultKey = "HelpHome";
</SharePoint:ScriptBlock>
<SharePoint:DelegateControl id="ID_SuiteBarDelegate" ControlId="SuiteBarDelegate" runat="server" />
  </SharePoint:SPSecurityTrimmedControl>
```


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint サイトの構築](build-sites-for-sharepoint.md)
    
  
-  [SharePoint 2013 サイト開発の新機能](what-s-new-with-sharepoint-2013-site-development.md)
    
  
-  [Menu control overview (ASP.NET)](http://msdn.microsoft.com/ja-jp/library/ecs0x9w5%28v=vs.90%29.aspx.aspx)
    
  

