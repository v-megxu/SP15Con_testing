---
title: SharePoint Online Suite Navigation 控件
ms.prod: SHAREPOINT
ms.assetid: ba93e5c0-e591-48d0-a716-a08ec7ef6cea
---


# SharePoint Online Suite Navigation 控件
了解 SharePoint Online 中的 Suite Navigation 控件的母版页标记。 
{插入介绍性内容}
  
    
    


## SharePoint Online Suite Navigation 控件

Suite Navigation 控件在 SharePoint Online 中呈现一致的顶部导航栏。该控件现在是所有未自定义的现成母版页的一部分。
  
    
    
如果母版页已自定义，它将不会使用新的 Suite Navigation 控件。要将此控件添加到您的自定义母版页，请将  `suiteBar` `<div>` 替换为与您使用的网站类型对应的标记。
  
    
    
新的 Suite Navigation 控件支持适用于网站的任何主题。如果您想更改顶部导航栏的颜色，请应用一个主题。
  
    
    

> **重要信息**
> 自定义网站时，最好的做法是应用主题。您可以将自定义 CSS 应用到网站，但如果将来在服务中再次更新 Suite Navigation 控件，自定义 CSS 可能会中断。 
  
    
    


> **警告**
> 如果您不想使用新控件，请将 Suite Navigation 标记从母版页中移除，并添加自定义标记。但是请注意，运行自定义母版页存在风险，即不会将更新应用到默认母版页控件，也不会应用添加到未自定义母版页的新功能。使用自定义母版页会导致服务更新破坏网站功能或样式的风险。 
  
    
    


### 适用于 Intranet 网站的 Suite Navigation 控件

对于 Intranet 网站，请对 Suite Navigation 控件使用以下母版页标记。表 1 列出了 Suite Navigation 代码中使用的 Web 控件。
  
    
    

**表 1. 适用于 Intranet 网站的 Suite Navigation Web 控件**


|**Web 控件**|**说明**|
|:-----|:-----|
|SharePoint:Menu  <br/> |在 ASP.NET 网页中显示菜单。  <br/> |
|SharePoint:MenuItemTemplate  <br/> |表示在下拉菜单中创建项目的控件。  <br/> |
   

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


#### 了解用于面向公众的网站的 Suite Navigation Web 控件

对于面向公众的网站，请对 Suite Navigation 控件使用以下母版页标记。表 2 列出了 Suite Navigation 代码中使用的 Web 控件。
  
    
    

**表 2. 用于面向公众的网站的 Suite Navigation Web 控件**


|**Web 控件**|**说明**|
|:-----|:-----|
|SharePoint:DelegateControl  <br/> |呈现 ASP.NET Web 控件。委派控件使其候选控件可插入且可跟踪。  <br/> |
|SharePoint:FeatureMenuTemplate  <br/> |表示为下拉菜单中创建模板的控件。  <br/> |
|SharePoint:Menu  <br/> |在 ASP.NET 网页中显示菜单。  <br/> |
|SharePoint:MenuItemTemplate  <br/> |表示在下拉菜单中创建项目的控件。  <br/> |
|SharePoint:ScriptBlock  <br/> |表示页面上的脚本块控件。  <br/> |
|SharePoint:SiteActions  <br/> |表示"网站操作"菜单的模板控件。  <br/> |
|SharePoint:SPSecurityTrimmedControl  <br/> |向当前用户有条件地呈现控件内容，前提是仅当当前用户具有 **PermissionString** 中定义的权限时。 <br/> |
   

### 面向公众的网站的 Suite Navigation 控件


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


## 其他资源
<a name="bk_addresources"> </a>


-  [为 SharePoint 构建网站](build-sites-for-sharepoint.md)
    
  
-  [SharePoint 2013 网站开发的新增内容](what-s-new-with-sharepoint-2013-site-development.md)
    
  
-  [Menu control overview (ASP.NET)](http://msdn.microsoft.com/zh-cn/library/ecs0x9w5%28v=vs.90%29.aspx.aspx)
    
  

