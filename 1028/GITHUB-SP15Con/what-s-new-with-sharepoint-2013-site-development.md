---
title: SharePoint 2013 網站開發新功能
ms.prod: SHAREPOINT
ms.assetid: ac1e9891-5ce9-4707-84e5-6e2fc02fda6b
---


# SharePoint 2013 網站開發新功能
了解 SharePoint 2013 中，可讓您建立發佈網站的新網站製作與發佈模型。
## SharePoint 2013 中適用於設計人員與開發人員的網站發佈簡介
<a name="SP15_WhatsNewSiteDevelopment_IntroductionToSitePublishing"> </a>

以下功能是 SharePoint 2013 的新增功能，並支援發佈網站的企業內容管理 (ECM) 網站建立工作流程。
  
    
    

### 用於發佈網站開發的用戶端程式設計模型

在 SharePoint 2013 中，您可以使用 .NET 用戶端物件模型 (CSOM)、Silverlight 和 JavaScript 程式設計模型來開發自訂網站、網站元件、品牌元素和操作行為。.NET 伺服器程式設計可用的大部分 API 都能用於相對應的 .NET 用戶端 (CSOM)、Silverlight 和 JavaScript 組件。在某些情況下，對應的 API 也適用於 Windows Phone 程式庫。
  
    
    
若想瞭解詳細資訊，請參閱參考首頁中  [.NET 伺服器](http://msdn.microsoft.com/library/8a93e838-234c-41d8-b990-7ac1a415dd5e%28Office.15%29.aspx)、 [.NET 用戶端](http://msdn.microsoft.com/library/e6542022-a459-4c3b-aee0-e350c6397139%28Office.15%29.aspx)和  [JavaScript](http://msdn.microsoft.com/library/1ead2f8d-a541-4a50-89fa-f195f2ba14e5%28Office.15%29.aspx) 的網站和內容。或者，如果您想從頭開始接著探索每個程式設計型的內容，請從 [參考首頁](http://msdn.microsoft.com/library/7940ba4e-f6f0-4bc0-b995-ceb2d358ca0d%28Office.15%29.aspx)開始。
  
    
    

### 將發佈和分類 API 用於新的 SharePoint 應用程式模型

您可以在 SharePoint Add-ins中撰寫自訂用戶端和伺服器程式碼，擴充透過使用者介面 (UI) 提供的 SharePoint 發佈和分類功能。 
  
    
    
可以增強網站發佈功能的部分開發應用程式構想包括意見調查、帳戶管理應用程式、電子商務支援、將社交功能和外部資料整合至發佈網站的應用程式、將外包內容新增至您的網站以及行動分享應用程式。
  
    
    

## 製作、設計和建立品牌功能
<a name="SP15_WhatsNewSiteDevelopment_AuthoringAndBranding"> </a>

SharePoint 2013 包含的功能和 API 可讓您用來製作、設計、建立品牌與擴充網站、網站設計、品牌元素和操作行為。 
  
    
    

### 設計管理員

在舊版 SharePoint 中，建立網站品牌需要特定的專業技術，例如主版頁面上所需的內容版面配置區、主版頁面如何實作某些樣式類別等。SharePoint 2013 引進 [設計管理員](overview-of-design-manager-in-sharepoint-2013.md)這是一個全新介面與樞紐中心，可以管理建立 SharePoint 網站品牌的所有面向。您可在網站集合的最上層網站中找到設計管理員，它屬於 SharePoint 2013 的「發佈入口網站」網站集合範本。
  
    
    
設計管理員提供建立設計資產的逐步方式，供您用來建立網站品牌。上傳設計資產  影像、HTML、CSS 等等，然後建立您的主版頁面和版面配置。在設計期間，您可以在用戶端程式碼編輯器或伺服器上預覽您的設計外觀。您可以使用設計管理員 UI 來新增自訂 SharePoint 元件及功能區元素。設計管理員會產生可供任何 Web 設計工具使用的 HTML  [程式碼片段](sharepoint-2013-design-manager-snippets.md)，它會轉譯 HTML 並忽略 ASP.NET 和 SharePoint 標記 (而 SharePoint 則是僅轉譯 ASP.NET 和 SharePoint 標記並忽略 HTML)。
  
    
    
您可以運用本身的 HTML、CSS 及 JavaScript 專業在 HTML 中設計主版頁面，並以您所選擇的 HTML 編輯器來設計 HTML 網頁版面配置。若要將您最愛的製作與設計工具連接至 SharePoint 網站，請 [對應網路磁碟機](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)，並以本機檔案的方式編輯 SharePoint 檔案。完成網站設計後，上傳 HTML 和支援檔案並使用設計管理員 [將 HTML 檔案轉換為 ASP.NET 主版頁面 (.master) 檔案](how-to-convert-an-html-file-into-a-master-page-in-sharepoint-2013.md)。現在，  [套用主版頁面至](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md) SharePoint 網站。使用設計管理員 [建立新的版面配置](how-to-create-a-page-layout-in-sharepoint-2013.md)，其 HTML 版本會自動關聯至 SharePoint 解譯的對應 ASP.NET 網頁 (.aspx 檔案)。 
  
    
    
轉換 HTML 檔案之後，您可以使用 HTML 編輯器繼續改善設計、預覽檔案以及儲存檔案。每次儲存主版頁面或頁面版面配置檔案的 HTML 版本時，SharePoint 2013 都會自動更新相關聯的 SharePoint 主版頁面和頁面版面配置以反映您的變更。 
  
    
    
使用設計管理員，您只需編輯 HTML 檔案 (當然您可以運用您的 ASP.NET 和 SharePoint 開發技能，繼續撰寫自訂的主版頁面和版面配置)，不需擁有 SharePoint 開發人員等級的專業知識，設計管理員就能讓您設計出絕佳的網站。
  
    
    
如果您喜歡，SharePoint 2013 也提供數個主版頁面和版面配置的 HTML 版本供您做為起始範本。如果您想從這些檔案開始，請先建立一份 HTML 檔案副本 (系統會為您處理關聯的 ASP.NET 檔案)，接著以平常方式編輯 HTML 檔案。您也可以使用 [ **最小範本的主版頁面**] 選項從基本範本開始進行，此選項會自動建立關聯的 .master 檔案。
  
    
    

### 程式碼片段庫

SharePoint 2013 包含許多已可使用的元件，例如網頁組件和控制項，供您新增至您的網站頁面。例如，將搜尋方塊或瀏覽控制項等 SharePoint 元件插入至您的 HTML 主版頁面，就可以快速、輕鬆地在網頁中建立許多功能。
  
    
    
在功能區的 [ **程式碼片段庫**] 群組中，您可以選取元件、設定其屬性和更新程式碼片段、複製所產生的 HTML 程式碼片段，並將該 HTML 程式碼片段貼到您的 HTML 檔案中。HTML 程式碼片段可在伺服器端預覽和您選擇的 HTML 編輯器中提供高逼真度的元件預覽。將 SharePoint 元件加入 HTML 檔案之後，您可以使用 CSS 據以完整建立品牌。就如同對 HTML 檔案進行更新，新增 SharePoint 元件並建立品牌後，所做的變更會自動同步至相關聯的主版頁面或版面配置。HTML 程式碼片段會自動轉換為 SharePoint 元件。
  
    
    
 無論您的 HTML 檔案是主版頁面或是版面配置，程式碼片段庫都會顯示您需要的元件。如果沒看到您需要的程式碼片段，您可以建立 ASP.NET 標記的 HTML 程式碼片段，並將其加入至您的 HTML 主版頁面或版面配置。
  
    
    
設計管理員會產生可供任何 Web 設計工具使用的 HTML 程式碼片段，它只會轉譯 HTML 並忽略 ASP.NET 和 SharePoint 標記。而 SharePoint 則是僅轉譯 ASP.NET 和 SharePoint 標記並忽略 HTML。
  
    
    

### 裝置通道

在設計管理員中，您可以建立 [裝置通道](sharepoint-2013-design-manager-device-channels.md)，然後使用每個連入裝置之使用者代理字串的子字串，將裝置通道對應到行動裝置或瀏覽器。裝置可以隸屬於多個通道，因此可以排名通道。例如，如果您建立「智慧型手機」和「Windows Phone 8」的裝置通道，便可以排名通道，讓執行 Windows Phone 8 的裝置取得專門指派給它們的通道，而所有其他智慧型手機則取得與「智慧型手機」通道相關聯的內容。
  
    
    
定義通道後，將主版頁面對應至每一個通道。此主版頁面可以參考預設通道之主版頁面以外的其他 CSS 檔案。您建立的所有版面配置都會使用您建立的所有通道；若要區分不同通道的版面配置設計，請使用 [ **裝置通道面板**] 控制項。
  
    
    
SharePoint 2013 中的發佈網站會針對行動開發予以最佳化。您可以使用裝置通道功能，為一或多個裝置定義通道，您可以精細地控制您網站的行動使用者經驗。您可以指派替代主版頁面給每個通道，提供獨特的組件區塊。您可以選擇在通道中加入或排除任一部分的版面配置，並在開發期間預覽行動通道設計的處理情形。裝置通道的設計過程與搜尋引擎最佳化 (SEO) 密切結合。您可以用來轉換現有頁面的外觀以便支援行動裝置。
  
    
    
您可以使用通道，強制在特定裝置上顯示特定的轉譯方式，這稱為「強制」通道。當您已針對特定的行動裝置定義最佳轉譯方式時，這個功能會很有用。
  
    
    

### 裝置通道面板控制項

裝置通道面板是一個新控制項，可以加入版面配置中，用來控制在哪些通道中轉譯哪些內容。裝置通道面板是一個對應到一或多個通道的容器：如果在轉譯頁面時，有一或多個通道正在作用中，則會轉譯裝置通道面板的所有內容。裝置通道面板可協助您決定何時要加入特定通道的特定內容。
  
    
    

### 顯示範本
<a name="SP15_BuildSitesForSP2013_DisplayTemplates"> </a>

您可能會想要控制網站搜尋結果的格式及呈現方式。您可以使用顯示範本來達到這個目的，此功能擴充透過使用者介面可用於自訂搜尋結果的選項，而不只是對應您想要顯示的預先定義欄位。
  
    
    
有三個情形適用於對搜尋結果使用顯示範本：當您想要對應搜尋結果之整體結構的呈現方式、當您想要顯示結果群組，以及當您想要顯示每個結果或項目在結果集中的顯示方式。以上分別稱為控制項、 群組及項目範本。
  
    
    
若想深入了解顯示範本，請參閱  [SharePoint 2013 設計管理員顯示範本](sharepoint-2013-design-manager-display-templates.md)。
  
    
    

### 影像轉譯
<a name="SP15_BuildSitesForSP2013_DisplayTemplates"> </a>

使用 [影像轉譯](sharepoint-2013-design-manager-image-renditions.md)，可以用預先定義的大小、寬度和裁剪來顯示上傳的影像。您可以建立來源影像檔的多個轉譯，這表示您只需設定一次顯示特性，就能將其套用至任意數目的影像。例如，名為 **Article_image** 的轉譯會在文章中顯示完整大小的影像，而名為 **Thumbnail_small** 的轉譯則在您定義的內容中顯示較小版本的影像。
  
    
    
使用影像轉譯之前，請務必先啟用伺服器上的 BLOB 快取，此步驟可在 Internet Information Services (IIS) 的管理工具中進行。在那裡找到您的 **web.config** 檔案並啟用 BLOB 快取。重新整理頁面，影像轉譯即可使用。
  
    
    

## SharePoint 2013 中的受管理中繼資料和導覽
<a name="SP15_WhatsNewSiteDevelopment_MetadataAndNavigation"> </a>

 引進的 Enterprise Managed Metadata (EMM) 功能在 SharePoint 2013 中已獲得改善及擴充，以提供較佳效能、更容易透過 UI 存取，並提供分類式導覽 (稱為「受管理導覽」)。
  
    
    

### 受管理導覽

受管理導覽是傳統 SharePoint 導覽功能 (稱為「結構化導覽」，以 SharePoint 結構為基礎) 的分類型替代方法。 [受管理導覽](managed-navigation-in-sharepoint-2013.md)功能可讓您設計以受管理中繼資料為導向的網站導覽方式。受管理導覽會建立衍生自受管理導覽結構的 SEO 易記 URL。因為受管理導覽為分類式，因此可在不變更網站或網站元件結構的前提下，根據重要的商務概念而設計網站導覽方式。
  
    
    

### 內容搜尋網頁組件
<a name="SP15_BuildSitesForSP2013_ContentSearchWebPart"> </a>

您可以使用 [內容搜尋網頁組件 (CSWP)](content-search-web-part-in-sharepoint-2013.md) 在您的網頁上顯示搜尋資料。它的作用類似於內容查詢網頁組件，但提供不同的網站設計目的。CSWP 樣式比內容查詢網頁組件樣式更容易加以自訂。CSWP 以 JSON 格式傳回用戶端結果。在伺服器上，您可以使用顯示範本來自訂結果。
  
    
    

### 其他網站受管理中繼資料的改進功能
<a name="SP15_BuildSitesForSP2013_ContentSearchWebPart"> </a>

SharePoint 2013 對受管理中繼資料 UI 和功能進行了多項改進。若要瞭解詳細資訊，請參閱  [SharePoint 2013 中的受管理中繼資料和導覽](managed-metadata-and-navigation-in-sharepoint-2013.md)。
  
    
    

## 在 SharePoint 2013 中發佈內容
<a name="SP15_WhatsNewSiteDevelopment_Publishing"> </a>

SharePoint 2013 提供新的內容發佈功能，可讓您開發能支援更有彈性、更複雜的新拓樸和案例的發佈網站。 
  
    
    

### 設計套件

如果您是專業的網頁設計人員，在交出設計成品或將其安裝至其他網站集合之前，您可能會想先在自己的環境或網站集合中建立並測試設計。如果是使用跨網站發佈在網站集合間共用內容，您可能會想要封裝設計並在每個網站上安裝相同的設計。
  
    
    
在舊版 SharePoint 中，如果想要重複使用設計，您必須使用 Visual Studio 建立 SharePoint 方案套件 (.wsp 檔案)，然後在目的地網站中，將套件上傳至方案庫再加以執行。現在，在 SharePoint 2013 中，完成網站的設計後，您可以在設計管理員中選擇 [ **匯出套件**]，匯出一個稱為「 [設計套件](sharepoint-2013-design-manager-design-packages.md)」的 .wsp 檔案。匯出設計套件時，SharePoint 2013 會將您在主版頁面圖庫、樣式庫、主題庫、裝置通道清單以及頁面內容類型中新增或變更的所有內容，自動封裝至設計套件中。 
  
    
    

> **注意事項**
> 設計套件不包含頁面、導覽設定或字詞庫。 
  
    
    

若是 Office 365 公用網站，設計套件不會覆寫現有檔案。安裝設計套件會在設計資產單獨存在的主版頁面圖庫、樣式庫和主題庫中建立新的資料夾。 
  
    
    
匯入設計套件時，套件中的設計資產會覆寫任何現有檔案並套用為目前的網站設計。網站的預設值及系統主版頁面、主題和其他 CSS 設定都會從設計套件的檔案加以設定。透過設計套件，一個環境中內建的設計可以輕鬆地套用至另一個不同環境。
  
    
    

### 目錄

SharePoint 2013 網站發佈引進「目錄」，可讓您在發佈網站中納入清單。目錄可以在網站集合間發佈內容  跨網站發佈功能必須依賴目錄。使用目錄可以在各個網站之間，以及跨越內部網路網站、網際網路網站和外部網路網站的界限，真正重複使用內容。若是預先定義的搜尋查詢，搜尋中會對目錄加以標示。您可以使用 [內容搜尋網頁組件 (CSWP)](content-search-web-part-in-sharepoint-2013.md)，顯示跨網站集合目錄中儲存的內容。您可以撰寫自訂程式碼來填入目錄、將產品目錄連接至網站，以及使用自訂版面配置、網頁組件和只出現在已定義內容中的 HTML 內容來組織個別網頁。
  
    
    

### 用戶端轉譯控制項

SharePoint 2013 的所有新控制項都會轉譯至用戶端。身為設計人員或開發人員，您可以控制頁面上內容的轉譯方式，您也可以使用內容搜尋網頁組件和顯示範本等功能，運用各種設計技巧在已發佈網頁上取得您要的外觀和操作行為。資料會以用戶端 JSON 陣列寫入控制項，而您可以使用 JavaScript、CSS 和範本來顯示內容。 
  
    
    

### 跨網站發佈

Microsoft SharePoint 2013 引進跨網站發佈功能，可讓您在多個網站集合間重複使用內容。此功能使用內建搜尋功能來提供發佈案例和架構。這是史上第一次，您能夠設計跨 SharePoint 伺服器陣列的網站  讓您的網站可以跨越內部網路和網際網路之間的界限。 
  
    
    
使用主題頁面功能可以自訂跨網站發佈內容的登陸頁面經驗。使用 SEO 易記 URL 可以管理以及更輕鬆地保存和維護廣泛案例的網站結構，包括複雜的多語言網站拓樸。
  
    
    
若要深入了解跨網站發佈，請參閱 [案例：使用 SharePoint Server 2013 的跨網站發佈建立 SharePoint 網站](http://technet.microsoft.com/zh-tw/sharepoint/jj872721)。若要深入了解跨網站發佈的開發選項，請參閱  [跨網站發佈 SharePoint 2013 的](cross-site-publishing-in-sharepoint-2013.md)。
  
    
    

### SEO 增強功能

許多商業網站使用者會被 Bing 之類的大型搜尋引擎及其全球競爭對手引薦到網際網路商務網站。SharePoint 2013 提供易記 URL、首頁重新導向、XML 網站地圖、自訂 SEO 屬性等功能，供您彈性定義瀏覽器標題和 **<Meta>** 標記描述及關鍵字，以及多語言網站變化版本更容易了解的 URL。
  
    
    
在 Office 365 中，在網站發生變更的 24 小時內，網站基礎結構就會為您產生更新的 XML 網站地圖。使用內部部署安裝時，您還可以調整網站地圖的有效期限，並指定當我們更新網站地圖時要讓 Microsoft 偵測的搜尋引擎。
  
    
    
您朋友在 Facebook 上按的讚，會影響 Bing 及其他大型搜尋引擎傳回之搜尋結果中的所見內容。您可以使用 SharePoint 2013 程式設計模型中的 API 來自訂您網站最適合的搜尋方式。
  
    
    

### 分析與建議

您可以使用已與搜尋引擎深入整合的 SharePoint 2013 分析功能，追蹤人們使用發佈網站及其元件的方式。分析功能會提供對內容的建議，並以 Managed 屬性將計算方式插入至搜尋索引中。搜尋分析提供的建議 (包括頁面檢視和每日唯一項目) 可能會影響搜尋結果的相關性。
  
    
    
分析使用匿名資料，每隔 15 天彙總一次。分析每隔 15 天清除一次事件，3 年後每個月清除一次。此外，一定會保留存留期檢視。分析將彙總資料推入到報表資料庫前會先修剪最少瀏覽的內容。您可以使用自訂程式碼，從報表資料庫匯出資料至 Excel、自訂 **View** 事件的權數，以及建立自訂事件  包括 JavaScript 送出的事件。
  
    
    

### 變化和多語言網站

您可以使用 SharePoint 2013 的變化功能來建立多語言網站或其他您想要改變內容呈現的網站。變化功能限制用於一個網站集合。也就是說，您可以在同一個 SharePoint 網站集合內的目前網站上，建立來源語言/地區設定的目標語言/地區設定「變化」。變化支援易記 URL，也可以匯出或匯入由協力廠商提供的  [XLIFF 檔案格式](the-xliff-interchange-file-format-in-sharepoint-2013.md)翻譯內容。您可以在匯出套件中加入標籤、翻譯和複寫頁面、各種清單項目 (例如文件庫) 以及導覽。 
  
    
    

## 其他資源
<a name="SP15_WhatsNewSiteDevelopment_AdditionalResources"> </a>


-  [使用 SharePoint 2013 用戶端程式庫程式碼完成基本作業](http://msdn.microsoft.com/library/5a69c9e3-73bf-4ed5-bc19-182056bdb394%28Office.15%29.aspx)
    
  
-  [使用 SharePoint 2013 中的 JavaScript 程式庫程式碼完成基本作業](http://msdn.microsoft.com/library/29089af8-dbc0-49b7-a1a0-9e311f49c826%28Office.15%29.aspx)
    
  
-  [操作方法： 在 SharePoint 2013 中的目錄式網站自訂頁面](how-to-customize-page-layouts-for-a-catalog-based-site-in-sharepoint-2013.md)
    
  
-  [操作方法： 變更 SharePoint 2013 設計管理員中的預覽頁面](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [操作方法： 解決預覽在 SharePoint 2013 中的頁面時出現的錯誤與警告](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 的佈景主題概觀 (英文)](themes-overview-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 中的受管理中繼資料和導覽](managed-metadata-and-navigation-in-sharepoint-2013.md)
    
  
-  [適用於開發人員的 SharePoint 2013 搜尋中新功能](what-s-new-in-sharepoint-2013-search-for-developers.md)
    
  

