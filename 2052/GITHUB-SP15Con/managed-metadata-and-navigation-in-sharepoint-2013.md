---
title: SharePoint 2013 中的托管元数据和导航
ms.prod: SHAREPOINT
ms.assetid: b66d4ec1-a2ef-49cc-8ca5-a6b516bff02e
---


# SharePoint 2013 中的托管元数据和导航

  
    
    
![概念概述主题](images/mod_icon_badge_conoverview.png)
  
    
    

  
    
    

  
    
    
了解 SharePoint 2013 中的企业管理元数据 (EMM) 和导航功能。
## SharePoint 2013 中的管理元数据功能增强（针对开发人员）
<a name="SP15_ManagedMetadataAndNav_ManagedMetadataFeatureEnhancements"> </a>

您可以使用管理元数据构建符合特定、详细业务需求的分类和标记策略。在 SharePoint 2013 中，扩展并增强了基本管理元数据 API 集，以便提供更多功能和方案支持。
  
    
    

## .NET 客户端对象模型 (CSOM) 支持管理原始 API
<a name="SP15_ManagedMetadataAndNav_CSOMSupport"> </a>

SharePoint 2013 CSOM 支持分类自定义和开发。分类在 .NET 客户端 (CSOM)、Silverlight 和 JavaScript 编程模型中均可用。用它进行开发在逻辑上类似于用 .NET 服务器编程模型进行开发。您可能会发现开发支持如下方案的 CSOM 解决方案非常有用：其中读取内容比创作或管理内容更为常见。您需要使用 CSOM 来启用用于云方案（如 SharePoint Online）中或内部可用的方案的子集的分类。
  
    
    
您想要在使用分类功能的 Visual Studio 中新建 CSOM 项目时，请设置以下引用：
  
    
    

- Microsoft.SharePoint.Client.dll
    
  
- Microsoft.SharePoint.Client.Runtime.dll
    
  
- Microsoft.SharePoint.Client.Taxonomy.dll
    
  
用 CSOM 开发自定义项极其类似于开发 .NET 服务器分类解决方案：获取对该会话所需的 **TaxonomySession** 对象和 **TermStore** 对象、 **Group** 对象、 **TermSet** 对象和 **Term** 对象的引用。
  
    
    

### 代码示例：对分类 CSOM 的基本操作
<a name="SP15_ManagedMetadataAndNav_ExampleBasicOperations"> </a>

您可以使用以下代码示例完成对 CSOM 的基本操作。第一个示例创建 **Group** 对象、 **TermSet** 对象和 **Term** 对象。第二个示例迭代 **Group** 对象并写入其内容。
  
    
    

```cs

       private void CreateColorsTermSet(string siteUrl)
        {
           ClientContext clientContext = new ClientContext(siteUrl);
 
           TaxonomySession taxonomySession = TaxonomySession.GetTaxonomySession(clientContext);
            clientContext.Load(taxonomySession,
                ts => ts.TermStores.Include(
                    store => store.Name,
                    store => store.Groups.Include(
                        group => group.Name
                        )
                    )
                );
            clientContext.ExecuteQuery();
 
           if( taxonomySession != null )
            {
               TermStore termStore = taxonomySession.GetDefaultSiteCollectionTermStore();
               if (termStore != null)
                {
                   //
                   //  Create group, termset, and terms.
                   //
                   TermGroup myGroup = termStore.CreateGroup("MyGroup",Guid.NewGuid());
                   TermSet myTermSet = myGroup.CreateTermSet("Color",Guid.NewGuid(), 1033);
                    myTermSet.CreateTerm("Red", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Orange", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Yellow", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Green", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Blue", 1033,Guid.NewGuid());
                    myTermSet.CreateTerm("Purple", 1033,Guid.NewGuid());
 
                    clientContext.ExecuteQuery();
                }
            }
        }
 
       private void DumpTaxonomyItems(string siteUrl)
        {
           ClientContext clientContext = new ClientContext(siteUrl);
 
           //
           // Load up the taxonomy item names.
           //
            TaxonomySession taxonomySession =TaxonomySession.GetTaxonomySession(clientContext);
           TermStore termStore = taxonomySession.GetDefaultSiteCollectionTermStore();
            clientContext.Load(termStore,
                    store => store.Name,
                    store => store.Groups.Include(
                        group => group.Name,
                        group => group.TermSets.Include(
                            termSet => termSet.Name,
                            termSet => termSet.Terms.Include(
                                term => term.Name)
                        )
                    )
            );
            clientContext.ExecuteQuery();
 
 
           //
           //Writes the taxonomy item names.
           //
           if( taxonomySession != null )
            {
               if (termStore != null)
                {
                   foreach( TermGroup groupin termStore.Groups)
                    {
                       Console.WriteLine("Group " + group.Name);
 
                       foreach( TermSet termSetin group.TermSets )
                        {
                           Console.WriteLine("TermSet " + termSet.Name);
 
                            foreach(Term term in termSet.Terms)
                            {
                               //Writes root-level terms only.
                               Console.WriteLine("Term " + term.Name);
                            }
                        }
                    }
                }
            }
 
        }

```


  
    
    

## 固定
<a name="SP15_ManagedMetadataAndNav_Pinning"> </a>

在 Microsoft SharePoint Server 2010 中，用户可以再使用术语层次结构中其他位置的术语（及嵌套在再使用术语下的所有术语）。再使用这些术语后，可以对其进行修改，并且可以在再使用这些术语的地方看到这些更改。SharePoint 2013 引入了术语固定。固定的术语就像再使用的术语，只是固定的术语为只读且在再使用该术语的位置无法进行更改。有关示例，请参阅 [如何：在 SharePoint 2013 中使用代码将术语固定到导航术语集](how-to-use-code-to-pin-terms-to-navigation-term-sets-in-sharepoint-2013.md)。
  
    
    

  
    
    

## 数据表视图支持管理元数据列类型
<a name="SP15_ManagedMetadataAndNav_DatasheetViewSupport"> </a>

在 SharePoint 2013 中，数据表视图功能已更改。现在，数据表使用双击操作打开标准网格编辑视图。现在您可以使用编辑单个项时可用的功能来编辑元数据列。
  
    
    

## 管理导航
<a name="SP15_ManagedMetadataAndNav_ManagedNav"> </a>

管理导航使用管理元数据功能（如，用术语标记项和在术语库中管理术语的功能）来提供高度自定义化的网站导航。SharePoint 2013 中还提供有赖于 SharePoint 基础架构的结构性导航。
  
    
    

## 友好型 URL
<a name="SP15_ManagedMetadataAndNav_FriendlyURLs"> </a>

友好型 URL 是显示在大多数 SharePoint 发布页（包括网站的"欢迎"页）的地址栏中的较短 URL 格式。这些 URL 都是 SEO 友好型的，并且出现在搜索结果中。 
  
    
    

## 支持新方案
<a name="SP15_ManagedMetadataAndNav_SupportForNewScenarios"> </a>

术语库管理器可以根据 中的更灵活且更强大的管理元数据功能增强和扩展术语使用模型。
  
    
    

- 链接至其他网站集和查看其他人的术语。如果您想要使您的术语集可供连接到管理元数据服务的其他网站集使用。请创建一个 **global term set**。如果您想要创建一个当其存储在管理元数据服务中时仅对特定网站集可用的私人术语集，请创建一个 **local term set**。 
    
  
- 阻止用户使用特定术语集之外的关键字
    
  
- 获取其他多语种支持，包括自持自动翻译和灵活的 LCID。 
    
  

## 使用自定义网站定义时不受支持的方案
<a name="SP15_ManagedMetadataAndNav_UnsupportedScenarios"> </a>


- SharePoint 2013 不支持通过 XML 定义以声明方式创建分类字段（托管元数据网站栏）。
    
  
- SharePoint 2013 不支持在网站模板中使用分类字段（托管元数据网站栏）。
    
  
- 有关详细信息，请参阅 Microsoft 支持文章 #898631： [受支持和不受支持的方案](http://support2.microsoft.com/default.aspx?scid=kb;EN-US;898631
)
    
  

## 其他资源
<a name="SP15_ManagedMetadataAndNav_AdditionalResources"> </a>


-  [SharePoint 2013 中的托管导航](managed-navigation-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的内容搜索 Web 部件](content-search-web-part-in-sharepoint-2013.md)
    
  

