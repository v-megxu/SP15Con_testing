---
title: SharePoint 2013 中的托管导航
ms.prod: SHAREPOINT
ms.assetid: c9da5011-3c73-4b83-8e00-e7a03a71ed02
---


# SharePoint 2013 中的托管导航

  
    
    
![概念概述主题](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
了解 SharePoint 2013 中的分类法驱动托管导航功能。
## 托管导航简介
<a name="SP15_ManagedNav_Introducing"> </a>

设计完善的导航可告诉您网站的用户大量有关网站所提供业务、产品和服务的信息。通过更新导航背后的分类法，可以推动业务并保持更新，而不必在过程中重新创建其网站导航。在 SharePoint 2013 中，可以使用托管导航功能来设计由托管元数据驱动的网站导航以及创建源自于托管导航结构的 SEO 友好 URL。托管导航可以代替基于 SharePoint 结构的传统 SharePoint 导航功能（结构化导航）。因为托管导航由分类驱动，所以您可以用它来设计围绕重要业务理念的网站导航，而无需更改网站或网站组件的结构。
  
    
    

## 托管导航工作原理
<a name="SP15_ManagedNav_HowManagedNavWorks"> </a>

托管导航为动态生成的页面提供一个框架并提供关联 SEO 友好 URL。生成的每个页面都用导航层次结构表示。该框架提供模板和集成机制来为每个导航链接创建登录页面，而不要求在分类法中为每种类别撰写单独的页面。您可以使用主题页面功能来自定义登陆页面体验。
  
    
    
托管导航 API 内置于 SharePoint 2013 中的分类法和出版库。术语集和术语库等托管元数据组件用于对您的网站启用分类法驱动导航。在 .NET 服务器类库中， [Microsoft.SharePoint.Publishing.Navigation](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.Navigation.aspx) 命名空间包含术语、术语集和其他将 **Term** 类和 **TermSet** 类反映到 [Microsoft.SharePoint.Taxonomy](https://msdn.microsoft.com/library/Microsoft.SharePoint.Taxonomy.aspx) 导航命名空间中的类对象，并提供专用于使这些元数据项与导航元素关联的方法和属性。其他类（如 [TaxonomySiteMapNode](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.Navigation.TaxonomySiteMapNode.aspx) ）允许您提供具有各种网站导航元素的元数据（如站点映射节点和您网站导航的其他部分）。其他类支持缓存和托管导航上下文。
  
    
    
您可以将分类法驱动导航链接显示到"整体导航"中。"整体导航"是始终存在一层或多层的导航层，通常出现在网站的顶部并显示顶层内容类别。您还可以将这些链接显示到通常出现在页面左侧的当前导航控件中。当前导航控件表示"整体导航"中所选类别层次结构的下一层，或隶属于该类别的链接集。
  
    
    

## 友好 URL 和托管导航提供程序
<a name="SP15_ManagedNav_FriendlyURLs"> </a>

首次浏览到 SharePoint 2013 网站时，您可能会注意到 URL 格式有所变化。页 URL 仅以  `/` 结束，而不再是具有 `/Pages/default.aspx` 扩展的地址。托管导航为友好 URL 提供一种在整个网站、类别和项页一致的方案。
  
    
    
托管导航提供程序支持此体验。当您导航至任何使用托管导航提供程序的网站的根目录时，"网站欢迎页面"设置将控制浏览器中登录并显示的页面，但您看到的 URL（搜索结果中出现的）被重写为此友好格式。
  
    
    
任何页面（包括您网站的"欢迎页面"）都有友好 URL。根据您网站的配置方式，大多数页面会自动获取友好 URL。友好 URL 可以本地化。
  
    
    

## 托管导航 API
<a name="SP15_ManagedNav_ManagedNavAPIs"> </a>

在 SharePoint 2013 中，分类法 API 提供几种新的方法和属性，您可以使用这些方法和属性来自定义要用于网站导航方案的术语存储中的术语、术语集和其他元数据元素。这些 API 以 .NET 客户端, .NET 服务器、Silverlight 和 JavaScript 编程模型提供。
  
    
    

## 代码示例：使用 .NET 客户端对象模型 (CSOM) API 自定义托管导航
<a name="SP15_ManagedNav_CustomizingManagedNavWithNETCSOM"> </a>

将 .NET 客户端对象模型用于分类法时，您可以创建新的导航术语集（如果当前网站集合存在术语存储），也可以将现有术语集转换为支持托管导航的术语集。
  
    
    

  
    
    



```cs

///Create a navigation term set.
public class NavigationTermSetTests
    {
      public void CreateNavigationTermSet()
              {
               ClientContext clientContext = new ClientContext(TestConfig.ServerUrl);
            
                 TaxonomySession taxonomySession = TaxonomySession.GetTaxonomySession(clientContext);
                 taxonomySession.UpdateCache();

                 clientContext.Load(taxonomySession, ts => ts.TermStores);
                 clientContext.ExecuteQuery();

                 if (taxonomySession.TermStores.Count == 0)
                 throw new InvalidOperationException("The Taxonomy Service is offline or missing");

                 TermStore termStore = taxonomySession.TermStores[0];
                 clientContext.Load(termStore, 
                 ts => ts.Name, 
                 ts => ts.WorkingLanguage);

                 // Does the TermSet object already exist?
                 TermSet existingTermSet;

                 // Handles an error that occurs if the return value is null.
                 ExceptionHandlingScope exceptionScope = new ExceptionHandlingScope(clientContext);
             using (exceptionScope.StartScope())
                 {
                 using (exceptionScope.StartTry())
                 {
                 existingTermSet = termStore.GetTermSet(TestConfig.NavTermSetId);
                 }
                 using (exceptionScope.StartCatch())
                {
                }
                }
                clientContext.ExecuteQuery();

                if (!existingTermSet.ServerObjectIsNull.Value)
                {
                Log("CreateNavigationTermSet(): Deleting old TermSet");
                existingTermSet.DeleteObject();
                termStore.CommitAll();
                clientContext.ExecuteQuery();
                }

                Log("CreateNavigationTermSet(): Creating new TermSet");

               // Creates a new TermSet object.
            TermGroup siteCollectionGroup = termStore.GetSiteCollectionGroup(clientContext.Site, 
                createIfMissing: true);
            TermSet termSet = siteCollectionGroup.CreateTermSet("Navigation Demo", TestConfig.NavTermSetId, 
                termStore.WorkingLanguage);

            termStore.CommitAll();
            clientContext.ExecuteQuery();

            NavigationTermSet navTermSet = NavigationTermSet.GetAsResolvedByWeb(clientContext,
                termSet, clientContext.Web, "GlobalNavigationTaxonomyProvider");

            navTermSet.IsNavigationTermSet = true;
            navTermSet.TargetUrlForChildTerms.Value = "~site/Pages/Topics/Topic.aspx";

            termStore.CommitAll();
            clientContext.ExecuteQuery();

            NavigationTerm term1 = navTermSet.CreateTerm("Term 1", NavigationLinkType.SimpleLink, Guid.NewGuid());
            term1.SimpleLinkUrl = "http://www.bing.com/";

            Guid term2Guid = new Guid("87FAA433-4E3E-4500-AA5B-E04330B12ACD");
            NavigationTerm term2 = navTermSet.CreateTerm("Term 2", NavigationLinkType.FriendlyUrl,
                term2Guid);

            NavigationTerm childTerm = term2.CreateTerm("Term 2 child", NavigationLinkType.FriendlyUrl, Guid.NewGuid());

            childTerm.GetTaxonomyTerm().TermStore.CommitAll();
            clientContext.ExecuteQuery();
}


```


## 代码示例：使用 .NET 服务器对象模型 API 自定义托管导航
<a name="SP15_ManagedNav_CustomizingManagedNavNETServerObjectModel"> </a>

您可以在  [Microsoft.SharePoint.Taxonomy](https://msdn.microsoft.com/library/Microsoft.SharePoint.Taxonomy.aspx) 和 [Microsoft.SharePoint.Publishing.Navigation](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.Navigation.aspx) 命名空间中使用 .NET 服务器分类法类和方法，以创建新的导航术语集。
  
    
    

  
    
    



```cs

///Create a navigation term set.
using (SPSite site = new SPSite(TestConfig.ServerUrl))
            {
                using (SPWeb web = site.OpenWeb())
                {
                    TaxonomySession taxonomySession = new TaxonomySession(site, updateCache: true);

                    /// Use the first TermStore object in the list.
                    if (taxonomySession.TermStores.Count == 0)
                        throw new InvalidOperationException("The Taxonomy Service is offline or missing");

                    TermStore termStore = taxonomySession.TermStores[0];

                    /// Does the TermSet object already exist?
                    TermSet existingTermSet = termStore.GetTermSet(TestConfig.NavTermSetId);
                    if (existingTermSet != null)
                    {
                        Log("CreateNavigationTermSet(): Deleting old TermSet");
                        existingTermSet.Delete();
                        termStore.CommitAll();
                    }

                    Log("CreateNavigationTermSet(): Creating new TermSet");

                    /// Create a new TermSet object.
                    Group siteCollectionGroup = termStore.GetSiteCollectionGroup(site);
                    TermSet termSet = siteCollectionGroup.CreateTermSet("Navigation Demo", TestConfig.NavTermSetId);

                    NavigationTermSet navTermSet = NavigationTermSet.GetAsResolvedByWeb(termSet, web,
                        StandardNavigationProviderNames.GlobalNavigationTaxonomyProvider);

                    navTermSet.IsNavigationTermSet = true;
                    navTermSet.TargetUrlForChildTerms.Value = "~site/Pages/Topics/Topic.aspx";

                    NavigationTerm term1 = navTermSet.CreateTerm("Term 1", NavigationLinkType.SimpleLink);
                    term1.SimpleLinkUrl = "http://www.bing.com/";

                    Guid term2Guid = new Guid("87FAA433-4E3E-4500-AA5B-E04330B12ACD");
                    NavigationTerm term2 = navTermSet.CreateTerm("Term 2", NavigationLinkType.FriendlyUrl,
                        term2Guid);

                    /// Verify that the NavigationTermSetView is being applied correctly.
                    Assert.AreEqual(web.ServerRelativeUrl + "/term-2", term2.GetResolvedDisplayUrl(null).ToString());

                    string expectedTargetUrl = web.ServerRelativeUrl 
                        + "/Pages/Topics/Topic.aspx?TermStoreId=" + termStore.Id.ToString() 
                        + "&amp;TermSetId=" + TestConfig.NavTermSetId.ToString()
                        + "&amp;TermId=" + term2Guid.ToString();
                    Assert.AreEqual(expectedTargetUrl, term2.GetResolvedTargetUrl(null, null).ToString());

                    NavigationTerm childTerm = term2.CreateTerm("Term 2 child", NavigationLinkType.FriendlyUrl);
                    Assert.AreEqual(web.ServerRelativeUrl + "/term-2/term-2-child", childTerm.GetResolvedDisplayUrl(null).ToString());

                    /// Commit changes.
                    childTerm.GetTaxonomyTerm().TermStore.CommitAll();
                }
            }
```


## 其他资源
<a name="SP15_ManagedNav_AdditionalResources"> </a>


-  [SharePoint 2013 中的内容搜索 Web 部件](content-search-web-part-in-sharepoint-2013.md)
    
  

