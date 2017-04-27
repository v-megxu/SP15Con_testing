---
title: SharePoint 2013 中的 eDiscovery
ms.prod: SHAREPOINT
ms.assetid: 45cb324a-75f5-444d-a0fa-5c223df19016
---


# SharePoint 2013 中的 eDiscovery
了解在 SharePoint 2013 中的 eDiscovery 功能。您可以使用 eDiscovery 讓訴訟律師有能力探索電子格式的內容。 
## 介紹 SharePoint 2013 中的 eDiscovery
<a name="SP15_eDiscoveryInSP_IntroductionToeDiscovery"> </a>

eDiscovery 是讓記錄管理員及訴訟律師探索電子格式內容的方式。一般來說， eDiscovery 需要搜尋分布在筆記型電腦、電子郵件伺服器、檔案伺服器和其他來源的文件、網站和電子郵件訊息，並收集符合法律案例準則的內容並針對該內容採取行動。
  
    
    
在 SharePoint Server 2010 中，Microsoft 新增了「保留」和 eDiscovery 功能，使用者就能保留 SharePoint 中的任何網站。記錄管理員可以保留電子信箱中的文件、頁面和清單項目，這能避免使用者刪除或編輯這些項目。 Exchange 2010 介紹如何在信箱中執行法務保存措施、跨多個信箱執行搜尋，和使用 Windows PowerShell cmdlet 來探索信箱。
  
    
    
在 SharePoint 2013 和 中的 eDiscovery 包含的新方式能減少探索的成本與複雜度。這包含了：
  
    
    

- ** eDiscovery 中心**，這個中央 SharePoint 網站是用來管理保留、搜尋、匯出在 SharePoint 伺服器陣列與 Exchange 伺服器之間儲存於 Exchange 和 SharePoint 的內容。 
    
  
- **SharePoint 就地保留**會保留整個 SharePoint 網站。就地保留會保護網站中的所有文件、頁面和清單項目，但容許使用者能繼續編輯與刪除受保留的內容。 
    
  
- **Exchange 就地保留**會保留 Exchange 信箱。就地保留透過保留 SharePoint 網站時所用的同一個 UI 和 API，來保護所有的信箱內容。
    
  
- **查詢式保留**讓使用者能將查詢篩選器套用至一個或多個 Exchange 信箱和 SharePoint 網站，並對保留的內容加以限制。
    
  

## eDiscovery 在 SharePoint 2013 中運作的方式
<a name="SP15_eDiscoveryInSP_HoweDiscoveryWorks"> </a>

eDiscovery 使用搜尋服務應用程式 (SSA) 來搜尋 SharePoint 伺服器陣列。您可以透過各種方式設定 SSA，但最常見的方式是讓中央搜尋服務伺服器陣列搜尋多個 SharePoint 伺服器陣列。您可以使用這個搜尋服務來搜尋所有 SharePoint 內容，或是用來搜尋特定地區的內容，像是歐洲地區的所有 SharePoint 內容。 
  
    
    
若要搜尋 SharePoint 伺服器陣列，首次搜尋時使用服務應用程式 Proxy 來進行連線。eDiscovery 中心使用 proxy 連線，將保留傳送至其他 SharePoint 伺服器陣列中的 SharePoint 網站。
  
    
    

## 必要條件
<a name="SP15_eDiscoveryInSP_Prerequisites"> </a>

在部署 SharePoint Server eDiscovery 功能之前，您應該為組織規劃搜尋服務應用程式基礎結構。例如，若您有兩個不同的 SSA，其中都搜尋了特定的 SharePoint 網站組。您就需要為每一個 SSA 規劃一個 eDiscovery 中心。
  
    
    

## 網站保留
<a name="SP15_eDiscoveryInSP_SiteHolds"> </a>

SharePoint 會保留網站層級的內容。當您保留網站時，也會將其中的清單、資料庫和子網站進行保留。若您保留的是根網站集合，也會保留該網站集合中的所有文件、頁面、清單和子網站。
  
    
    
若要保留網站，請在 eDiscovery 中心中建立 eDiscovery 案例。案例這個容器是用來包含所有與特定訴訟資料關聯的搜尋、內容和保留。在您建立案例之後，建立探索集來指定網站。若要驗證網站，只要輸入其 URL 位址就能進行驗證。
  
    
    
就地保留的功用是保留內容，於探索搜尋完成時產生作用。在編輯或刪除內容項目時，eDiscovery 會將該項目的副本放置於特定的文件庫，其名稱為「文件保留庫」，位於 SharePoint 網站上，也就是修改內容的地方。只有搜尋索引子，和具有網站集合管理員權限或網頁應用程式權限的使用者能夠存取「文件保留庫」。大多數不具權限的使用者看不到資源庫，也不知道它的存在，或那就是將內容進行複製的地方。
  
    
    
若要保留內容，讓其儲存空間降到最低並提高效率，eDiscovery 使用寫入時複製 來管理相同資訊的相同副本。因為大多數保留的內容將不再進行修改，沒有理由建立其副本而將空間填滿。就地保留反而只在項目被刪除時，或是在啟動保留後第一次變更項目時，才建立副本。若文件再次變更，eDiscovery 只會保留存入或刪除的版本，以及在文件一開始保留時建立的版本。
  
    
    
若在網站上已執行多個保留，即使在第一次保留時已複製文件，在下一次編輯文件時系統會再次將其複製。
  
    
    

## eDiscovery 程式撰寫模型
<a name="SP15_eDiscoveryInSP_eDiscoveryProgrammingModel"> </a>

SharePoint 2013 提供的 Microsoft .NET 伺服器撰寫模型，讓您可以用來建立自訂解決方案及包含 eDiscovery 功能的應用程式。表格1 列出使用 **Microsoft.Office.Server.Discovery** 命名空間的類型。
  
    
    

**表格 1. eDiscovery 類型**


|**類型**|**描述**|
|:-----|:-----|
| [Case](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Case.aspx) <br/> |代表 eDiscovery 案例。與特定  [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) 物件關聯的案例能夠在特定的日期或以特定的動作關閉。案例可以包含此 **Case** 物件中特定 ID、查詢、所有來源群組的清單、監管人和位置的來源群組、位置、信箱、監管人、儲存的搜尋、匯出，與匯出設定。 <br/> |
| [Custodian](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Custodian.aspx) <br/> |代表負責記錄 eDiscovery 案例的對象。  <br/> |
| [CustodianCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.CustodianCollection.aspx) <br/> |代表 **Custodian** 物件的集合。 <br/> |
| [DiscoveryDuplicateSourceCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.DiscoveryDuplicateSourceCollection.aspx) <br/> |當 **Source** 物件並非唯一值時，就會擲回例外狀況。 <br/> |
| [DiscoveryException](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.DiscoveryException.aspx) <br/> |eDiscovery API 特有的例外狀況會留下訊息，也會作為內部的例外狀況。  <br/> |
| [Export](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Export.aspx) <br/> |代表與特定 **Case** 物件相關聯的匯出。可以透過 **T:Microsoft.SharePoint.SPListItem** 物件來建構 **Export** 物件。您可以將 **SavedSearch** 物件新增至 **Export** 物件，且選擇性地管理權限與下載 **Export** 物件。 <br/> |
| [ExportCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.ExportCollection.aspx) <br/> |代表 **Export** 物件的集合。 <br/> |
| [ExportStatus](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.ExportStatus.aspx) <br/> |代表匯出的狀態，其表示匯出是否已啟動、未啟動、已完成或是已完成，但有發生錯誤。  <br/> |
| [SavedSearch](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SavedSearch.aspx) <br/> |代表儲存的 eDiscovery 搜尋。可以對 **SavedSearch** 物件進行複製、刪除或更新。可以將與儲存搜尋相關聯的統計資料進行更新。精簡搜尋、Exchange 2013 精簡、來源 ID、來源群組 ID、查詢和篩選器可以與 **SavedSearch** 物件產生關聯。 <br/> |
| [SavedSearchCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SavedSearchCollection.aspx) <br/> |代表 **SavedSearch** 物件的集合。 <br/> |
| [Source](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.Source.aspx) <br/> |代表用於 eDiscovery 作業的資料來源類型。 **Source** 物件會將特定的 **Case** 物件、資料來源類型和篩選器 (也就是識別來源之部分或完整的容器規格) 視為參數。可以傳回與來源相關的資訊，像是其保留狀態、由 SharePoint 編列索引的來源位置以及來源是否為信箱。 <br/> |
| [SourceCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceCollection.aspx) <br/> |代表 **Source** 物件的集合。 <br/> |
| [SourceGroup](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceGroup.aspx) <br/> |代表 **Source** 物件的群組。 <br/> |
| [SourceGroupCollection](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceGroupCollection.aspx) <br/> |代表 **SourceGroup** 物件的集合。 <br/> |
| [SourceManagementType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceManagementType.aspx) <br/> |代表要用來管理來源的級別。選項包含來源、來源群組和所有內容。  <br/> |
| [SourceType](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceType.aspx) <br/> |代表來源的類型。來源類型包含 Exchange 2013，SharePoint Server 的目前版本與舊版本，與檔案共享。  <br/> |
| [SourceValidation](https://msdn.microsoft.com/library/Microsoft.Office.Server.Discovery.SourceValidation.aspx) <br/> |表示來源是否有效。  <br/> |
   

## 其他資源
<a name="SP15_eDiscoveryInSP_AdditionalResources"> </a>


-  [在 SharePoint 2013 的 eDiscovery 及規範的新功能](what-s-new-in-sharepoint-2013-ediscovery-and-compliance.md)
    
  
-  [使用 SharePoint 2013 用戶端程式庫程式碼完成基本作業](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  

