---
title: SharePoint 2013 用に Web テンプレートをアップグレードする
ms.prod: SHAREPOINT
ms.assetid: 69048e4c-6d6d-4e4e-b74c-7c72ae444354
---


# SharePoint 2013 用に Web テンプレートをアップグレードする
セルフサービス アップグレードの後で、カスタマイズされた SharePoint 2010 Web テンプレートを SharePoint 2013 で使用できるように更新する方法について説明します。
SharePoint 2013 では、SharePoint サイトの外観を表示する場合に使用する基礎コンポーネントが大幅に変更されました。SharePoint 2010 の既定のコンポーネントに対するカスタマイズでは、スタイル、ページ レイアウト、マスター ページ、およびテーマなどが新たに変更されました。
  
    
    

この記事では、Web テンプレートを新しいフレームワークで使用できるように更新する方法についてのガイダンスを提供します。
## セルフサービス サイトのアップグレード後に可能な動作

サーバーを SharePoint 2010 から SharePoint 2013 にアップグレードすると、サイト コレクションの管理者には、サイトを徐々にアップグレードするか、またはサイト コレクション内のすべてのサイトを一度にアップグレードするためのリンクが表示されます。ユーザーは、カスタマイズが含まれるサイトをアップグレードし、テストすることができます。アップグレード後に発生の可能性がある問題として、以下のようなことが挙げられます。
  
    
    

- サイトに適用されたブランドが変更されたか、一切見当たらない。
    
  
- カスタム コンポーネントが正しく表示されない。
    
  
- ページがまったく表示されず、SharePoint から不明なエラーが返される。
    
  
- 既定で有効であった機能が、アップグレード後に無効になる。
    
  

## サイトをアップグレードする場合の推奨事項

サイトをアップグレードする場合は、評価サイトを使用してコンポーネントをインストールし、その互換性とパフォーマンスについてテストすることをお勧めします。
  
    
    
以下のセクションでは、Web テンプレートで更新する必要があるものについて詳しく説明します。
  
    
    

### マスター ページ参照の更新

SharePoint 2013 へのアップグレードを行うと、Web テンプレートに含まれるカスタム マスター ページ参照はいずれも **seattle.master** という名前の既定のマスター ページに設定されます。SharePoint 2010 で既定のマスター ページをカスタマイズしてある場合、カスタマイズを表示するには、参照を該当するカスタム ページに変更する必要があります。
  
    
    

### 使用できる機能の更新

サイトをアップグレードして SharePoint 2013 Web テンプレートを使用する場合は、既定でテンプレートにアタッチされている機能が削除されます。この結果、アップグレードされたテンプレートで使用できる機能は減少します。
  
    
    
既定の機能をテンプレートに再び追加するには、機能リストが含まれている、Web テンプレート用の Onet.xml ファイルを変更する必要があります。既定の機能を Web テンプレートに再び追加するには、以下の手順に従います。
  
    
    

### Web テンプレートに既定の機能を再び追加するには


1. 更新する Web テンプレートが含まれている Visual Studio プロジェクトを開きます。
    
  
2. [ **ソリューション エクスプローラー**] で、プロジェクト内の Onet.xml ファイルを探します。
    
  
3. XML エディターで Onet.xml を開きます。
    
  
4. 表 1 に示した各機能が **WebFeatures** セクションに表示されていることを確認します。
    
   **表 2 既定の Web テンプレート機能**


|**DisplayName**|**機能 ID**|
|:-----|:-----|
|AccSvcAddAccessApp  <br/> |d2b9ec23-526b-42c5-87b6-852bd83e0364  <br/> |
|AnnouncementsList  <br/> |00bfea71-d1ce-42de-9c63-a44004ce0104  <br/> |
|BaseWeb  <br/> |99fe402e-89a0-45aa-9163-85342e865dc8  <br/> |
|BizAppsListTemplates  <br/> |065c78be-5231-477e-a972-14177cc5b3c7  <br/> |
|ContactsList  <br/> |00bfea71-7e6d-4186-9ba8-c047ac750105  <br/> |
|ContactsList  <br/> |00bfea71-7e6d-4186-9ba8-c047ac750105  <br/> |
|CustomList  <br/> |00bfea71-de22-43b2-a848-c05709900100  <br/> |
|DataConnectionLibrary  <br/> |00bfea71-dbd7-4f72-b8cb-da7ac0440130  <br/> |
|DataSourceLibrary  <br/> |00bfea71-f381-423d-b9d1-da7a54c50110  <br/> |
|DiscussionsList  <br/> |00bfea71-6a49-43fa-b535-d15c05500108  <br/> |
|DocumentLibrary  <br/> |00bfea71-e717-4e80-aa17-d0c71b360101  <br/> |
|EventsList  <br/> |00bfea71-ec85-4903-972d-ebe475780106  <br/> |
|EventsList  <br/> |00bfea71-ec85-4903-972d-ebe475780106  <br/> |
|ExternalList  <br/> |00bfea71-9549-43f8-b978-e47e54a10600  <br/> |
|FollowingContent  <br/> |a7a2793e-67cd-4dc1-9fd0-43f61581207a  <br/> |
|GanttTasksList  <br/> |00bfea71-513d-4ca0-96c2-6a47775c0119  <br/> |
|GettingStarted  <br/> |4aec7207-0d02-4f4f-aa07-b370199cd0c7  <br/> |
|GridList  <br/> |00bfea71-3a1d-41d3-a0ee-651d11570120  <br/> |
|HierarchyTasksList  <br/> |f9ce21f8-f437-4f7e-8bc6-946378c850f0  <br/> |
|IPFSWebFeatures  <br/> |f9ce21f8-f437-4f7e-8bc6-946378c850f0  <br/> |
|IssuesList  <br/> |00bfea71-5932-4f9c-ad71-1557e5751100  <br/> |
|LinksList  <br/> |00bfea71-5932-4f9c-ad71-1557e5751100  <br/> |
|MBrowserRedirect  <br/> |d95c97f3-e528-4da2-ae9f-32b3535fbb59  <br/> |
|MDSFeature  <br/> |87294c72-f260-42f3-a41b-981a2ffce37a  <br/> |
|MobilityRedirect  <br/> |f41cc668-37e5-4743-b4a8-74d1db3fd8a4  <br/> |
|MySiteMicroBlog  <br/> |ea23650b-0340-4708-b465-441a41c37af7  <br/> |
|NoCodeWorkflowLibrary  <br/> |00bfea71-f600-43f6-a895-40c0de7b0117  <br/> |
|PictureLibrary  <br/> |00bfea71-52d4-45b3-b544-b1c71b620109  <br/> |
|PremiumWeb  <br/> |0806d127-06e6-447a-980e-2e90b03101b8  <br/> |
|PromotedLinksList  <br/> |192efa95-e50c-475e-87ab-361cede5dd7f  <br/> |
|ReportListTemplate  <br/> |2510d73f-7109-4ccc-8a1c-314894deeb3a  <br/> |
|SiteFeed  <br/> |15a572c6-e545-4d32-897a-bab6f5846e18  <br/> |
|SiteFeedController  <br/> |5153156a-63af-4fac-b557-91bd8c315432  <br/> |
|SurveysList  <br/> |00bfea71-eb8a-40b1-80c7-506be7590102  <br/> |
|TaskListNewsFeed  <br/> |ff13819a-a9ac-46fb-8163-9d53357ef98d  <br/> |
|TasksList  <br/> |00bfea71-a83e-497e-9ba0-7a5c597d0107  <br/> |
|TeamCollab  <br/> |00bfea71-4ea5-48d4-a4ad-7ea5c011abe5  <br/> |
|WebPageLibrary  <br/> |00bfea71-c796-4402-9f2f-0eb9a6e71b18  <br/> |
|WikiPageHomePage  <br/> |00bfea71-d8fe-4fec-8dad-01c19a6e4053  <br/> |
|WorkflowHistoryList  <br/> |00bfea71-4ea5-48d4-a4ad-305cf7030140  <br/> |
|workflowProcessList  <br/> |00bfea71-2d77-4a75-9fca-76516689e21a  <br/> |
|WorkflowServiceStore  <br/> |2c63df2b-ceab-42c6-aeff-b3968162d4b1  <br/> |
|WorkflowTask  <br/> |57311b7a-9afd-4ff0-866e-9393ad6647b1  <br/> |
|XmlFormLibrary  <br/> |00bfea71-1e1d-4562-b56a-f05371bb0115  <br/> |
   
5. 変更を保存し、通常どおり展開します。
    
  

> **メモ**
> また、サーバーの全体管理ユーティリティで、これらの機能をアクティブにすることが必要な場合もあります。 
  
    
    


## その他の技術情報
<a name="bk_addresources"> </a>


-  [サイトのカスタマイズを SharePoint 2013 用にアップグレードする](upgrade-site-customizations-for-sharepoint-2013.md)
    
  
-  [SharePoint 2010 および Web テンプレート](http://blogs.msdn.com/b/vesku/archive/2010/10/14/sharepoint-2010-and-web-templates.aspx)
    
  
-  [SharePoint 2013 でサイト コレクションのアップグレードを計画する](https://technet.microsoft.com/ja-jp/library/ff191199.aspx)
    
  
-  [SharePoint 2013 でサイト コレクションのアップグレードを計画する](http://technet.microsoft.com/ja-jp/library/ff191199.aspx)
    
  

  
    
    

