---
title: 操作方法：將 HTML 檔案轉換成在 SharePoint 2013 中的主版頁面
ms.prod: SHAREPOINT
ms.assetid: a76ab289-3256-45de-ac63-d5112a74e3c7
---


# 操作方法：將 HTML 檔案轉換成在 SharePoint 2013 中的主版頁面
使用 [設計管理員]，您可以將 an.html 檔案轉換成 SharePoint 2013 主版頁面 (.master 檔案)。轉換後，HTML 檔案與主版頁面會互相關聯，所以當您編輯並儲存 HTML 檔案時，所做的變更會同步到關聯的主版頁面。
## 簡介轉換主版頁面
<a name="Introduction"> </a>

 使用 [設計管理員]，您可以將 an.html 檔案轉換成 SharePoint 2013 主版頁面 (.master 檔案)。轉換後，HTML 檔案與主版頁面會互相關聯，所以當您編輯並儲存 HTML 檔案時，所做的變更會同步到關聯的主版頁面。
  
    
    
您要轉換 HTML 檔案，而不是從頭開始建立 .master 檔案嗎？在 SharePoint 2013 中主版頁面的作用，就如同在 ASP.NET 中的一模一樣，但 SharePoint 也需要在頁面上有某些元素 (例如 SharePoint 特定的控制項和內容版面配置區)，以讓 SharePoint 正確地呈現該主版頁面的頁面。藉由使用設計管理員將 HTML 檔案轉換成正常運作的 SharePoint 主版頁面，您不需要了解 ASP.NET 或 SharePoint 特定的標記；相反地，您可以專心以 HTML、CSS 及 JavaScript 來設計您的網站。
  
    
    
將 HTML 檔案轉換成主版頁面時：
  
    
    

- [主版頁面圖庫] 中，會建立與您的 HTML 檔案同名的 .master 的檔案。
    
  
- SharePoint 2013 所需的所有標記，都會加入 .master 檔案，讓主版頁面正確呈現。
    
  
- 標記例如註解、 **<div>** 標籤、程式碼片段及內容版面配置區等，會新增至原始的 HTML 檔案內。
    
  
- HTML 檔案與主版頁面會互相關聯，所以當儲存 HTML 檔案時，任何稍後對 HTML 檔案的編輯，都將會同步到 .master 檔案。
    
  

> **注意事項**
> 同步處理只有單向。HTML 主版頁面的變更會同步到相關聯的 .master 檔案，但如果您選擇要直接編輯 .master 檔案，所做的變更將不會同步到 HTML 檔案。每個 HTML 主版頁面 (和每個 HTML 頁面配置) 都有一個名為 **關聯檔案**的屬性，預設狀況下設定為 **True** 以建立關聯，並在檔案間進行同步處理。
  
    
    

如果您有一對相關的檔案 (HTML 和 .master)，您可以編輯 .master 檔案而不會中斷關聯，對 .master 檔案所做的變更將會儲存，但您不能簽入或發佈 .master 檔案，因此這些變更的儲存並無太大意義。對 HTML 檔案的任何變更都會覆寫 .master 檔案。如果您簽入或發佈 HTML 檔案，HTML 檔案的變更會覆寫對 .master 檔案所做的任何變更。對 .master 檔案所做的變更都會遺失。
  
    
    
如果您是可以放心使用 ASP.NET 的程式開發人員，您可以選擇藉由中斷檔案之間的關聯，只使用 .master 檔案作業。若要中斷 HTML 檔案和 .master 檔案之間的關聯，請在 [設計管理員] 中選擇 HTML 檔案的 **編輯屬性**，然後清除 **關聯檔案**核取方塊。您可以稍後藉由編輯屬性並選取此核取方塊，重新建立檔案的關聯，在這種情況下，HTML 檔案將再次覆寫 .master 檔案，對 .master 檔案所做的變更都將遺失。
  
    
    

## 準備要進行轉換的 HTML 檔案
<a name="Prepare"> </a>

您在轉換您的 HTML 檔案之前，這裡是一些最佳作法和指引，請考慮︰
  
    
    

- 請考慮 SharePoint 網頁模型。如需詳細資訊，請參閱  [SharePoint 2013 頁面模型概觀](overview-of-the-sharepoint-2013-page-model.md)。當您設計網站的 HTML 模型圖樣時，您可能需要數個不同類型網頁 (例如文章頁面或包含 Web 組件，從目錄顯示項目類別的分類頁面) 的 HTML 檔案。但是，只有一個 HTML 檔案會轉換成主版頁面。HTML 檔案可以轉換成主版頁面，但 HTML 檔案無法直接轉換成頁面配置，因為頁面配置需要頁面欄位。
    
  
- 請確定您的 HTML 檔案與 XML 相容。若要轉換成功，HTML 檔案必須與 XML 相容。不幸的是，這項需求會覆寫某些 HTML 5 標準 - 例如，在 HTML 5 中您可以指定 **doctype** 為小寫，但是在 XML 中 **doctype** 必須是大寫。此外，您應該移除任何 HTML 檔案中的 **<form>** 標籤。請考慮在轉換之前，透過外部的 XML 驗證程式，先執行您的 HTML 檔案，來識別 XML 錯誤。
    
  
- 請考慮下列 CSS 參考的重要指引︰
    
  - 不要在 **<head>** 標籤中放置 **<style>** 區塊。轉換期間會移除這些樣式。相反地，從您的 HTML 檔案連結到外部 CSS 檔案。
    
  
  - 如果您使用網頁字型，新增  `ms-design-css-conversion="no"` 到 **<CSS link>** 標籤。
    
  
  - 小心將樣式套用至一般的 HTML 標籤，就像 **<body>**、 **<div>** 和 **< img>**。您 SharePoint 中的所有設計，包括功能區的資料，都在 **<body>** 標籤內。對於通常會套用到 **<body>** 標籤的樣式，您可以考慮將其改為套用到 **<div id="s4-bodyContainer">**，也就是 SharePoint 2013 用於頁面本文的標籤。此外，SharePoint 2013 使用許多影像，會受到任何套用到 **<img>** 標籤的樣式影響。
    
  
  - 因為會將類別套用到 **<ul>** 和 **<li>** 元素，所以許多瀏覽設計工具樣式會因此受到影響。但是，SharePoint 2013 會使用動態的瀏覽控制項，您可以從程式碼片段圖庫新增至您的主版頁面。SharePoint 2013 瀏覽控制項有您需要覆寫的預設套用的樣式。
    
  
- 請考慮這些可能與檔案命名有關的問題︰
    
  - 如果您有 Index.html 和 Index.htm，這些檔案會具有相同的 .master 檔案。
    
  
  - 如果您有 Design/Index.html 和 Design/SubDesign/Index.html，這些檔案都適用於轉換成各自獨立的個別 .master 檔案，但它們在「設計管理員」中的主版頁面清單中，會同時顯示為 Index.html。若要使它們清楚，按一下或選取每個檔案的 [省略] 按鈕，以查看完整的路徑。
    
  
- 如果您正在新增 JavaScript Widget，請確定 **<script>** 起始標籤都位於本身那一行。
    
  ```
  
<script>
(function( …

  ```


    不要將它們放在同一行，就像這樣。
    


  ```
  
<Script> (function( …
  ```

- JQuery 程式庫的參考 (外部參考) 應位於 **</head>** 標籤之前。
    
  

## 將 HTML 檔案轉換成主版頁面
<a name="Convert"> </a>

您將 HTML 檔案轉換之前，首先必須上載所有您設計的檔案，包括您的 HTML 檔案。如需詳細資訊，請參閱  [操作方法： 將網路磁碟機對應至 SharePoint 2013 主版頁面圖庫](how-to-map-a-network-drive-to-the-sharepoint-2013-master-page-gallery.md)。
  
    
    

### 將 HTML 檔案轉換成 .master 檔案


1. 瀏覽您發佈的網站。
    
  
2. 在頁面的右上角，選擇 **[設定]**，然後選擇 **[設計管理員]**。
    
  
3. 在 [設計管理員] 中，左邊的瀏覽窗格內，選擇 **[編輯主版頁面]**。
    
  
4. 選擇 **[將 HTML 檔案轉換為 SharePoint 的主版頁面]**。
    
  
5. 在 **[選取資產]** 對話方塊中，瀏覽並選取您想要轉換的 HTML 檔案。
    
    > **注意事項**
      > 當您上載您設計的檔案時，您應該將與某個單一設計相關的所有檔案，都放在 [主版頁面圖庫] 中它們自己的資料夾內。當您可將您的設計資料夾複製到對應的網路磁碟機中時，[主版頁面圖庫] 將會保留任何您所建立的資料夾結構。 
6. 選擇 **[插入]**。
    
    此時，SharePoint 2013 會將您的 HTML 檔案轉換成具有相同名稱的 .master 檔案。
    
    在 [設計管理員] 中，您的 HTML 檔案現在會出現 [狀態] 欄，顯示兩個可能的狀態的其中一個︰
    
  - 錯誤
    
  
  - **轉換成功**
    
  
7. 依循 [狀態] 欄中的連結以預覽檔案，並檢視任何關於主版頁面的錯誤或警告。
    
    錯誤
    
    如需有關如何解決錯誤和警告的詳細資訊，請參閱  [操作方法： 解決預覽在 SharePoint 2013 中的頁面時出現的錯誤與警告](how-to-resolve-errors-and-warnings-when-previewing-a-page-in-sharepoint-2013.md)。
    
    如需有關預覽不同頁面的主版頁面的詳細資訊，請參閱  [操作方法： 變更 SharePoint 2013 設計管理員中的預覽頁面](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)。
    
    預覽網頁也會在右上角中包含 [程式碼片段] 的連結。此連結會開啟 [程式碼片段庫]，您可在其中開始以動態 SharePoint 控制項，來取代靜態或原型控制項。如需詳細資訊，請參閱  [SharePoint 2013 設計管理員片段 (英文)](sharepoint-2013-design-manager-snippets.md)。
    
  
8. 若要修正任何錯誤，使用 HTML 編輯器以直接在伺服器上，開啟並編輯對應的磁碟機中的 HTML 檔案。每次儲存 HTML 檔案時，任何變更都會同步到關聯的 .master 檔案。
    
  
9. 您的主版頁面預覽成功之後，您會看到 **<div>** 標籤加入到您的 HTML 檔案中。您可能要捲動頁面到底端以檢視 **<div>** 標籤。
    
    **<div>** 是主要的內容區塊。它位於名為 **ContentPlaceHolderMain** 的內容版面配置區內。在執行階段，當訪客瀏覽您的網站，並要求網頁時，此物件的內容版面配置區，會由頁面配置中的內容所填滿 (包含相符的內容區域中的內容)。您應該將 **<div>** 的位置放在您想要在主版頁面上頁面配置出現的地方。
    
    如果您的 HTML 檔案包含在網頁本文中的靜態或原型內容，現在您可開始移除 HTML 主版頁面中的靜態內容，並將這些樣式套用到 SharePoint 網頁模型的其他元素，例如頁面配置、頁面欄位控制項、程式碼片段，以及顯示範本。如需範例，請參閱  [操作方法： 在 SharePoint 2013 中建立頁面配置](how-to-create-a-page-layout-in-sharepoint-2013.md)。
    
  

## 瞭解轉換後的 HTML 檔案
<a name="Understand"> </a>

當您將 HTML 檔案轉換成主版頁面時，標記的行數會新增到您的 HTML 檔案中。您可以放心地忽略此標記，且當您在瀏覽器中檢視原始檔時，雖然此標記絕大部分不會出現在您網站的最終標記內，但是它卻是將您的 HTML 檔案轉換成 SharePoint 實際使用的 .master 檔案的關鍵。每次儲存 HTML 檔案的變更時，此 SharePoint 標記可對關聯的 .master 檔案，在背景進行相同的變更。
  
    
    
標記會新增包含 **<head>** 中和之前的標籤、程式碼片段和內容版面配置區。大部分的標記會括在註解標籤中︰每次儲存 HTML 檔案的變更時，轉換程序會剔除註解以使用其中的 ASP.NET 標記。
  
    
    

### 標記類型

下列是會加入到 HTML 檔案的標記類型之分解：
  
    
    

- **文件屬性** **<mso>** 標籤包含 SharePoint 中繼資料，包括檔案本身的相關資訊，以及成功轉換成 .master 檔案所需的某些屬性。
    
  ```HTML
  
<mso:CustomDocumentProperties>
<mso:HtmlDesignFromMaster msdt:dt="string"></mso:HtmlDesignFromMaster>
<mso:HtmlDesignStatusAndPreview msdt:dt="string">http://[server_name]/sites/PubSite/_catalogs/masterpage/[site_name]/index.html, Conversion successful.</mso:HtmlDesignStatusAndPreview>
<mso:ContentTypeId msdt:dt="string">0x0101000F1C8B9E0EB4BE489F09807B2C53288F0054AD6EF48B9F7B45A142F8173F171BD10003D357F861E29844953D5CAA1D4D8A3A0084F0F9C7FCB65541A59990D173DA60FA</mso:ContentTypeId>
<mso:HtmlDesignAssociated msdt:dt="string">1</mso:HtmlDesignAssociated>
<mso:HtmlDesignConversionSucceeded msdt:dt="string">True</mso:HtmlDesignConversionSucceeded>
</mso:CustomDocumentProperties>
  ```

- **SharePoint 命名空間登錄** **<SPM>** 標籤 ("SharePoint 標記") 提供一行以註冊SharePoint 命名空間。
    
  ```HTML
  
<!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
  ```

- **註解** **<CS>** 和 **<CE>** ("註解開頭" 和 "註解結尾") 標籤在轉換期間都會被忽略。這些標籤會協助您剖析標記行。
    
  ```HTML
  
<!--CS: Start Page Head Contents Snippet-->
…
<!--CE: End Page Head Contents Snippet-->

  <!--CS: Start Ribbon Snippet-->
…
<!--CE: End Ribbon Snippet-->

<!--CS: Start PlaceHolderMain Snippet-->
…
<!--CE: End PlaceHolderMain Snippet-->
  ```

- **程式碼片段** **<MS>** 和 **<ME>** ("標記開頭" 和 "標記結尾") 標籤用來代表 SharePoint 控制項或程式碼片段的開始和結束。程式碼片段是 SharePoint 控制項，可將 SharePoint 功能加入至您的頁面。您可以使用 [程式碼片段庫] 自行新增程式碼片段。如需詳細資訊，請參閱 [SharePoint 2013 設計管理員片段 (英文)](sharepoint-2013-design-manager-snippets.md)。
    
  ```HTML
  
<!--MS:<SharePoint:RobotsMetaTag runat="server">-->
        <!--ME:</SharePoint:RobotsMetaTag>-->
        <!--MS:<SharePoint:PageTitle runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitle" runat="server">-->
                <!--MS:<SharePoint:ProjectProperty Property="Title" runat="server">-->
                <!--ME:</SharePoint:ProjectProperty>-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:PageTitle>-->
        <!--MS:<SharePoint:StartScript runat="server">-->
        <!--ME:</SharePoint:StartScript>-->
        <!--MS:<SharePoint:CssLink runat="server" Version="15">-->
        <!--ME:</SharePoint:CssLink>-->
        <!--MS:<SharePoint:CacheManifestLink runat="server">-->
        <!--ME:</SharePoint:CacheManifestLink>-->
        <!--MS:<SharePoint:PageRenderMode runat="server" RenderModeType="Standard">-->
        <!--ME:</SharePoint:PageRenderMode>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="core.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="menu.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="callout.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="sharing.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="suitelinks.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:CustomJSUrl runat="server">-->
        <!--ME:</SharePoint:CustomJSUrl>-->
        <!--MS:<SharePoint:SoapDiscoveryLink runat="server">-->
        <!--ME:</SharePoint:SoapDiscoveryLink>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaPlaceHolderAdditionalPageHead" Container="false" runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderAdditionalPageHead" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
            <!--MS:<SharePoint:DelegateControl runat="server" ControlId="AdditionalPageHead" AllowMultipleControls="true">-->
            <!--ME:</SharePoint:DelegateControl>-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderBodyAreaClass" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:AjaxDelta>-->
        <!--MS:<SharePoint:CssRegistration Name="Themable/corev15.css" runat="server">-->
        <!--ME:</SharePoint:CssRegistration>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaSPWebPartManager" runat="server">-->
            <!--MS:<WebPartPages:SPWebPartManager runat="server">-->
            <!--ME:</WebPartPages:SPWebPartManager>-->
        <!--ME:</SharePoint:AjaxDelta>-->
  ```

- **預覽區塊** **<PS>** 和 **<PE>** ("預覽開頭" 和 "預覽結尾") 標籤會環繞您不應該編輯的 (因為此區段只會影響設計階段預覽) HTML 程式碼區段。這些預覽區段是插入程式碼片段時 SharePoint 控制項的快照。預覽可以讓您使用用戶端的 HTML 編輯器，更有意義地作業 HTML 檔案。但是，在預覽中變更內容或樣式，對 (SharePoint 最後要使用的) .master 檔案沒有持續影響。若要設定程式碼片段的樣式，您必須以自己的自訂 CSS，識別並覆寫 SharePoint 樣式。
    
  ```HTML
  
<!--PS: Start of READ-ONLY PREVIEW (do not modify) -->
<div class="DefaultContentBlock" style="background:rgb(0, 114, 198); color:white; width:100%; padding:8px; height:64px; overflow:hidden;">The SharePoint ribbon will be here when your file is either previewed on or applied to your site.</div>
<!--PE: End of READ-ONLY PREVIEW -->
  ```

- **SharePoint ID** 在轉換期間加入您 HTML 檔案的程式碼片段 ( [頁首內容] 程式碼片段和 SharePoint 功能區) 具有相關聯的 SharePoint ID 或 SID (分別為 00 和 02)。這些 ID 可縮短程式碼片段，並讓網頁的 HTML 更容易閱讀。
    
  ```HTML
  
<!--SID:00 -->

<!--SID:02 {Ribbon}-->
  ```


### 已加入的程式碼片段

請務必了解關於加入到您 HTML 檔案的兩個程式碼片段。在轉換期間，會自動加入這些程式碼片段，但您不能從 [程式碼片段庫] 中新增。
  
    
    

- **功能區**要讓內容作者能夠在 SharePoint 網站上建立頁面和作者內容，您的主版頁面需要功能區和「套裝瀏覽」(SharePoint 2013 的新功能)。功能區包含在安全性調整程式碼片段中，因此當訪客瀏覽您的網站時，功能區只會顯示給已驗證的使用者，而不是匿名的使用者。您可以將功能區移動到頁面上不同的位置，或藉由覆寫預設的 CSS 類別，來設定功能區樣式，但我們不建議移動或重新調整包含在功能區內的元件 (如 [網站動作] 功能表) 順序。
    
  ```HTML
  
<!--MS:<SharePoint:SPSecurityTrimmedControl runat="server" AuthenticationRestrictions="AnonymousUsersOnly">-->
<!--MS:<wssucw:Welcome runat="server" EnableViewState="false">-->
<!--ME:</wssucw:Welcome>-->
<!--ME:</SharePoint:SPSecurityTrimmedControl>-->
  ```

- **ContentPlaceHolderMain** **<div id="s4-bodyContainer">** 標籤的底部，結尾 **</body>** 標籤前，轉換程序會插入名為 **PlaceHolderMain** 的內容版面配置區。在此程式碼片段內是黑色邊框的黃色 **<div>**，會出現在您的 HTML 編輯器的設計檢視中，或在 [設計管理員] 的伺服器端預覽中。
    
    這 **<div>** 代表您的頁面配置所指定的內容和頁面會去的地方的區域。您應將 **PlaceHolderMain** 程式碼片段移動到您的主版頁面內，將會由頁面配置填入的位置 - 該區域在您的網站設計的所有頁面中，並不是一律相同。
    


  ```HTML
  
<!--CS: Start PlaceHolderMain Snippet-->
                    <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
                    <!--MS:<SharePoint:AjaxDelta ID="DeltaPlaceHolderMain" IsMainContent="true" runat="server">-->
                        <!--MS:<asp:ContentPlaceHolder ID="PlaceHolderMain" runat="server">-->
                            <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
            This div, which you should delete, represents the content area that your Page Layouts and pages will fill. Design your Master Page around this content placeholder.
        
                            </div>
                        <!--ME:</asp:ContentPlaceHolder>-->
                    <!--ME:</SharePoint:AjaxDelta>-->
                    <!--CE: End PlaceHolderMain Snippet-->
  ```


## 範例
<a name="Reference"> </a>

下列的範例是在轉換成主版頁面之後，新增到 HTML 檔案的標記。
  
    
    

### 加入到 < head > 標籤的標記


```HTML

<head>
        <meta http-equiv="X-UA-Compatible" content="IE=10" />
        <!--CS: Start Page Head Contents Snippet-->
        <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SPM:<%@Register Tagprefix="WebPartPages" Namespace="Microsoft.SharePoint.WebPartPages" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SID:00 -->
        <meta name="GENERATOR" content="Microsoft SharePoint" />
        <meta http-equiv="Content-type" content="text/html; charset=utf-8" />
        <meta http-equiv="Expires" content="0" />
        <!--MS:<SharePoint:RobotsMetaTag runat="server">-->
        <!--ME:</SharePoint:RobotsMetaTag>-->
        <!--MS:<SharePoint:PageTitle runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderPageTitle" runat="server">-->
                <!--MS:<SharePoint:ProjectProperty Property="Title" runat="server">-->
                <!--ME:</SharePoint:ProjectProperty>-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:PageTitle>-->
        <!--MS:<SharePoint:StartScript runat="server">-->
        <!--ME:</SharePoint:StartScript>-->
        <!--MS:<SharePoint:CssLink runat="server" Version="15">-->
        <!--ME:</SharePoint:CssLink>-->
        <!--MS:<SharePoint:CacheManifestLink runat="server">-->
        <!--ME:</SharePoint:CacheManifestLink>-->
        <!--MS:<SharePoint:PageRenderMode runat="server" RenderModeType="Standard">-->
        <!--ME:</SharePoint:PageRenderMode>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="core.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="menu.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="callout.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="sharing.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:ScriptLink language="javascript" name="suitelinks.js" OnDemand="true" runat="server" Localizable="false">-->
        <!--ME:</SharePoint:ScriptLink>-->
        <!--MS:<SharePoint:CustomJSUrl runat="server">-->
        <!--ME:</SharePoint:CustomJSUrl>-->
        <!--MS:<SharePoint:SoapDiscoveryLink runat="server">-->
        <!--ME:</SharePoint:SoapDiscoveryLink>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaPlaceHolderAdditionalPageHead" Container="false" runat="server">-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderAdditionalPageHead" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
            <!--MS:<SharePoint:DelegateControl runat="server" ControlId="AdditionalPageHead" AllowMultipleControls="true">-->
            <!--ME:</SharePoint:DelegateControl>-->
            <!--MS:<asp:ContentPlaceHolder id="PlaceHolderBodyAreaClass" runat="server">-->
            <!--ME:</asp:ContentPlaceHolder>-->
        <!--ME:</SharePoint:AjaxDelta>-->
        <!--MS:<SharePoint:CssRegistration Name="Themable/corev15.css" runat="server">-->
        <!--ME:</SharePoint:CssRegistration>-->
        <!--MS:<SharePoint:AjaxDelta id="DeltaSPWebPartManager" runat="server">-->
            <!--MS:<WebPartPages:SPWebPartManager runat="server">-->
            <!--ME:</WebPartPages:SPWebPartManager>-->
        <!--ME:</SharePoint:AjaxDelta>-->
        <!--CE: End Page Head Contents Snippet-->
        <meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
        <!--DC:Business Solutions-->
        <link rel="stylesheet" href="css/style.css" type="text/css" charset="utf-8" />
        <!--[if lte IE 7]>
  <link rel="stylesheet" href="css/ie.css" type="text/css" charset="utf-8"/> 
 <![endif]-->
        <!--[if gte mso 9]><xml>
<mso:CustomDocumentProperties>
<mso:HtmlDesignFromMaster msdt:dt="string"></mso:HtmlDesignFromMaster>
<mso:HtmlDesignStatusAndPreview msdt:dt="string">http://[server_name]/sites/PubSite/_catalogs/masterpage/[site_name]/index.html, Conversion successful.</mso:HtmlDesignStatusAndPreview>
<mso:ContentTypeId msdt:dt="string">0x0101000F1C8B9E0EB4BE489F09807B2C53288F0054AD6EF48B9F7B45A142F8173F171BD10003D357F861E29844953D5CAA1D4D8A3A0084F0F9C7FCB65541A59990D173DA60FA</mso:ContentTypeId>
<mso:HtmlDesignAssociated msdt:dt="string">1</mso:HtmlDesignAssociated>
<mso:HtmlDesignConversionSucceeded msdt:dt="string">True</mso:HtmlDesignConversionSucceeded>
</mso:CustomDocumentProperties>
</xml><![endif]-->
    </head>

```


### 加入到起始 <body> 標籤之後的標記


#### 功能區程式碼片段


```HTML

<!--CS: Start Ribbon Snippet-->
        <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
        <!--SPM:<%@Register Tagprefix="wssucw" TagName="Welcome" Src="~/_controltemplates/15/Welcome.ascx"%>-->
        <!--MS:<SharePoint:SPSecurityTrimmedControl runat="server" HideFromSearchCrawler="true" EmitDiv="true">-->
            <div id="TurnOnAccessibility" style="display:none" class="s4-notdlg noindex">
                <a id="linkTurnOnAcc" href="#" class="ms-accessible ms-acc-button" onclick="SetIsAccessibilityFeatureEnabled(true);UpdateAccessibilityUI();document.getElementById('linkTurnOffAcc').focus();return false;">
                    <!--MS:<SharePoint:EncodedLiteral runat="server" text="&amp;lt;%$Resources:wss,master_turnonaccessibility%&amp;gt;" EncodeMethod="HtmlEncode">-->
                    <!--ME:</SharePoint:EncodedLiteral>-->
                </a>
            </div>
            <div id="TurnOffAccessibility" style="display:none" class="s4-notdlg noindex">
                <a id="linkTurnOffAcc" href="#" class="ms-accessible ms-acc-button" onclick="SetIsAccessibilityFeatureEnabled(false);UpdateAccessibilityUI();document.getElementById('linkTurnOnAcc').focus();return false;">
                    <!--MS:<SharePoint:EncodedLiteral runat="server" text="&amp;lt;%$Resources:wss,master_turnoffaccessibility%&amp;gt;" EncodeMethod="HtmlEncode">-->
                    <!--ME:</SharePoint:EncodedLiteral>-->
                </a>
            </div>
        <!--ME:</SharePoint:SPSecurityTrimmedControl>-->
        <div id="ms-designer-ribbon">
            <!--SID:02 {Ribbon}-->
            <!--PS: Start of READ-ONLY PREVIEW (do not modify) --><div class="DefaultContentBlock" style="background:rgb(0, 114, 198); color:white; width:100%; padding:8px; height:64px; overflow:hidden;">The SharePoint ribbon will be here when your file is either previewed on or applied to your site.</div><!--PE: End of READ-ONLY PREVIEW -->
        </div>
        <!--MS:<SharePoint:SPSecurityTrimmedControl runat="server" AuthenticationRestrictions="AnonymousUsersOnly">-->
            <!--MS:<wssucw:Welcome runat="server" EnableViewState="false">-->
            <!--ME:</wssucw:Welcome>-->
        <!--ME:</SharePoint:SPSecurityTrimmedControl>-->
        <!--CE: End Ribbon Snippet-->

```


#### 兩個 SharePoint < div > 標籤


```HTML

<div id="s4-workspace">
            <div id="s4-bodyContainer">

```


### 加入到結尾 </body> 標籤和兩個結尾 </div> 之前的標記


```HTML

<div data-name="ContentPlaceHolderMain">
                    <!--CS: Start PlaceHolderMain Snippet-->
                    <!--SPM:<%@Register Tagprefix="SharePoint" Namespace="Microsoft.SharePoint.WebControls" Assembly="Microsoft.SharePoint, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"%>-->
                    <!--MS:<SharePoint:AjaxDelta ID="DeltaPlaceHolderMain" IsMainContent="true" runat="server">-->
                        <!--MS:<asp:ContentPlaceHolder ID="PlaceHolderMain" runat="server">-->
                            <div class="DefaultContentBlock" style="border:medium black solid; background:yellow; color:black; margin:20px; padding:10px;">
            This div, which you should delete, represents the content area that your Page Layouts and pages will fill. Design your Master Page around this content placeholder.
        
                            </div>
                        <!--ME:</asp:ContentPlaceHolder>-->
                    <!--ME:</SharePoint:AjaxDelta>-->
                    <!--CE: End PlaceHolderMain Snippet-->
                </div>

```


## 其他資源
<a name="Additional"> </a>


-  [設計管理員的概觀 in SharePoint 2013](overview-of-design-manager-in-sharepoint-2013.md)
    
  
-  [操作方法： 在 SharePoint 2013 中建立頁面配置](how-to-create-a-page-layout-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 設計管理員片段 (英文)](sharepoint-2013-design-manager-snippets.md)
    
  

