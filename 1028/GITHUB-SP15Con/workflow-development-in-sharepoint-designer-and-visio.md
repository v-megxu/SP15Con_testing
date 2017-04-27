---
title: SharePoint Designer 和 Visio 中的工作流程開發
ms.prod: SHAREPOINT
ms.assetid: 496780d5-47d6-4a43-bf14-70aefb8d820c
---


# SharePoint Designer 和 Visio 中的工作流程開發
深入了解不需要任何程式碼，使用 Visio 2013 和 SharePoint Designer 2013 以建立及發佈工作流程至 SharePoint 2013 網站。
## 簡介
<a name="VSSPD_Intro"> </a>

Visio 2013 和 SharePoint Designer 2013 讓商務分析師、流程顧問及 IT 專業人員更方便共同作業和建立 工作流程。Visio Professional 2013 和 SharePoint Designer 2013 中的「視覺化設計工具」提供豐富的工作流程呈現，無論是不是程式設計人員，都能清楚了解。
  
    
    

> **注意事項**
> 如需設定和配置 SharePoint Server 2013 與 Workflow Manager 伺服器的指引，請參閱 [在 SharePoint Server 2013 中設定工作流程](http://technet.microsoft.com/zh-tw/library/jj658586.aspx)。 
  
    
    

藉由使用 Visio 2013，您可以視覺化的方式建立 SharePoint 工作流程、將工作流程匯出至 SharePoint Designer 2013，然後將工作流程發佈至 SharePoint 網站。在 Visio 2013 中建立工作流程之後，必須匯出至 SharePoint Designer 2013。然後，SharePoint 網站擁有者或 IT 專業人員將參數新增至工作流程，方法是使用工作流程文字編輯器或新的 Visual Workflow Designer，這是 Visio 2013 ActiveX 控制項，裝載於 SharePoint Designer 2013。完成工作流程之後，可以發佈至 SharePoint 網站。
  
    
    
這對於已經熟悉 Visio 中的流程圖的商務分析師和流程顧問而言，是很理想的方式，因為它能夠讓這些人員設計出呈現商務邏輯的工作流程。設計工作流程的人員可以將焦點單獨放在工作流程的商業智慧 (BI) 需求上，而不需要是宣告式工作流程方面的專家。
  
    
    

## 關於在 Visio 2013 和 SharePoint Designer 2013 中建立 SharePoint 工作流程
<a name="VSSPD_About"> </a>

Visio 2013 包含 SharePoint 2013 工作流程範本，可用於建立 SharePoint 2013 工作流程。SharePoint 2013 工作流程範本與三個樣板相關聯：SharePoint 2013 工作流程動作、SharePoint 2013 工作流程條件以及 SharePoint 2013 工作流程結束點。這些樣板的圖形對應至可以在 SharePoint 2013 工作流程內使用的特定動作和條件。若要建立工作流程，您只需要將圖形拖曳至 Visio 2013 中的繪圖畫布上，以在工作流程後方形成商務邏輯模型。
  
    
    

### 階段、 迴圈及步驟

SharePoint Designer 2013 中的工作流程現在包含「階段」、「迴圈」及「步驟」的概念。工作流程作者可以將一組個別的動作和條件群組為單一單位，以便更清楚地定義流程。例如，可以有「核准」或「要求意見」階段或步驟。在該階段或步驟內是該流程所需的所有動作。階段或步驟本身可以是較長工作流程的一個節點，允許檢視者查看該階段整體的狀態，而不是個別動作的集合。
  
    
    
包含在 Visio 2013 的 SharePoint 2013 工作流程範本也使用階段、迴圈及步驟，做為建立工作流程的邏輯建立區塊。 
  
    
    

> **重要**
> 因為 Microsoft SharePoint 2010 工作流程範本與 SharePoint 2013 工作流程範本之間的基礎差異，您無法使用其他使用者在其他圖表內的範本所建立的圖形。只有 SharePoint 2013 工作流程動作、SharePoint 2013 工作流程條件及 SharePoint 2013 工作流程結束點樣板的圖形可以用於建立 SharePoint 2013 工作流程。 
  
    
    


### 階段圖形

階段可以包含任意數量的圖形，也可以包含分支。但是，只能有一個路徑進出階段 (和步驟)。工作流程中的所有動作必須包含在階段中。階段圖形是使用容器圖形進行視覺化。階段圖形需要「入口」和「出口」圖形新增至容器的邊緣，以定義進出階段的路徑。Visio 2013 和 SharePoint Designer 2013 中的「視覺化設計工具」會在您第一次放置容器時為您新增「入口」和「出口」圖形。
  
    
    
階段也有下列規則：
  
    
    

- 所有圖表必須至少有一個階段。一個完整具備「入口」、「出口」及「開始」圖形的階段，是預設 SharePoint 2013 工作流程範本的一部份。
    
  
- 當您將新的階段新增至繪圖畫布時，Visio 2013 會在放置階段時新增「開始」和「結束」連接器。
    
  
- 階段不能有透過「入口」和「出口」以外圖形進出的其他任何連接器。
    
  
- 階段容器不能是巢狀的。如果您要在階段內讓子程序形成巢狀，請使用步驟。
    
  
- 階段內可能會有「停止工作流程」圖形存在。
    
  
- 整份圖表的階段外必須有明確的「開始」圖形。階段外則不一定需要明確的「終止」圖形。
    
  
- 在最上層，工作流程只能包含階段、條件圖形及「開始」和「終止」結束點。所有其他圖形必須包含在階段內。
    
  

### 迴圈圖形

迴圈是一系列的連接圖形，會以迴圈形式執行，從系列中的最後一個圖形返回至第一個圖形，直到滿足條件為止。 
  
    
    
迴圈類似階段，是由容器圖形呈現，包含「入口」和「出口」圖形 (在繪圖畫布上放置圖形時新增)。「迴圈」圖形也需要「入口」和「出口」圖形新增至容器邊緣，以定義進出迴圈的路徑。
  
    
    
Visio 2013 和 SharePoint Designer 2013 支援兩種類型的迴圈：迴圈  *n*  次以及迴圈直到 *value1*  等於 *value2*  。
  
    
    
迴圈也必須符合下列規則：
  
    
    

- 迴圈必須在階段內，而階段不能在迴圈內。
    
  
- 步驟可能在迴圈內。
    
  
- 迴圈只能有一個入口點和一個出口點。
    
  

### 步驟圖形

步驟代表群組的一系列連續動作。步驟必須包含在階段內。步驟圖形也必須有「入口」和「出口」圖形，以定義進出圖形的路徑。在畫布上放置圖形時預設會新增兩個圖形。
  
    
    

## 在 Visio 2013 中建立工作流程
<a name="VSSPD_Creating"> </a>

SharePoint 2013 工作流程樣板中的所有主圖形對應至 SharePoint 2013 工作流程內的動作、條件及其他邏輯建構。若要建立工作流程，您可以將圖形拖曳至繪圖畫布，就像 Visio 中的任何其他流程圖一樣。完成在 Visio 2013 中建立工作流程之後，在 SharePoint Designer 2013 可以開啟工作流程之前，先行儲存工作流程。
  
    
    
若要在 Visio 2013 中開啟 SharePoint 2013 工作流程範本，請執行下列動作：
  
    
    

### 若要在 Visio 2013 中開啟 SharePoint 2013 工作流程範本


1. 開啟 Visio 2013.
    
  
2. 選擇 [新建]。
    
  
3. 在 [範本類別] 下，選擇 [流程圖]。
    
  
4. 在 [選擇範本] 下，選擇 [SharePoint 2013 工作流程] ，然後選擇 [建立]。
    
    範本隨即開啟，且繪圖畫布會預先填入「開始」和「階段」圖形。「階段」圖形包含「入口」和「出口」圖形，由單一連接器連接。
    
  
SharePoint 2013 工作流程範本開啟時，將動作、條件及其他圖形拖曳至繪圖畫布，以設計工作流程。如需個別圖形及其意義的詳細資訊，請參閱下列文章： [在 Visio 中 SharePoint Server 工作流程範本的圖形](shapes-in-the-sharepoint-server-workflow-template-in-visio.md)。
  
    
    

> **秘訣**
>  設定工作流程時，請記住下列額外考量：>  若要快速建立工作流程，將動作和條件圖形拖曳至新的階段圖形所包含的內部連接器。Visio 2013 會自動將連接器分割為其他連接器，保持工作流程從「入口」圖形到「出口」圖形的連接。>  請勿使用 SharePoint 2013 工作流程動作、SharePoint 2013 工作流程條件及SharePoint 2013 工作流程結束點樣板以外之樣板的任何圖形。僅使用 SharePoint 2013 工作流程範本提供的「連接器」工具，新增圖形之間的連接。所有其他連接器圖形在 SharePoint 2013 工作流程內無效。>  「動作」圖形、步驟及迴圈必須一律包含在「階段」圖形內。部份條件圖形可以位在階段外。>  「階段」圖形必須確實只具有一個「入口」圖形和一個「出口」圖形。階段內包含的工作流程子流程必須以「入口」圖形開始、以「出口」圖形結束。>  條件圖形必須有兩個連接器離開圖形，一個標示為「是」，另一個標示為「否」。您可以在連接器上按一下滑鼠右鍵，選擇 [是] 或 [否]。>  工作流程只能有一個「開始」圖形。「開始」圖形必須位於階段之外。>  您在工作流程中對圖形新增文字，但是圖形文字不會影響工作流程。
  
    
    


  
    
    
驗證 Visio 2013 中的工作流程，與驗證任何其他連接的圖表類似：Visio 根據規則集檢查圖表，然後傳回在圖表中找到的錯誤清單。請參閱下列文章： [在 Visio 中的 SharePoint Server 工作流程驗證錯誤的疑難排解](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md)，以深入了解如何解決驗證問題。
  
    
    

### 在 Visio 2013 中驗證 SharePoint 2013 工作流程


1. 在 [程序] 索引標籤的 [圖表驗證] 群組中，選擇 [檢查圖表]。
    
  
2. 如果在工作流程中找到任何錯誤，[問題] 窗格隨即在圖表下方開啟。選擇清單中的每個項目，以選取在圖表中造成錯誤的圖形。
    
  
3. 解決 [問題] 清單中列出的每個驗證錯誤。解決所有錯誤之後，再次選擇 [檢查圖表]。如需如何解決 Visio 2013 中驗證問題的詳細資訊，請參閱下列文章： [在 Visio 中的 SharePoint Server 工作流程驗證錯誤的疑難排解](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md)。
    
  
4. 如果工作流程中找不到錯誤，Visio 會顯示訊息，表示圖表驗證已完成且沒有發現任何問題。
    
  
在 Visio 2013 中成功驗證工作流程之後，您可以儲存檔案並且將其匯入 SharePoint Designer 2013。與 Microsoft SharePoint 2010 工作流程範本不同，您可以將 SharePoint 2013 工作流程圖表的副本儲存為預設 Visio 2013 檔案格式 (.vsdx)，SharePoint Designer 2013 可以開啟檔案。 
  
    
    
使用下列程序以將 Visio 2013 中的 SharePoint 2013 工作流程儲存為 Visio 2013 .vsdx 檔案，該檔案可以在 SharePoint Designer 2013 中開啟：
  
    
    

### 在 Visio 2013 中儲存工作流程


1. 選擇 [檔案]，然後選擇 [另存新檔]。
    
  
2. 在 [另存新檔] 底下，選擇 [儲存]，然後選擇 [瀏覽]。
    
  
3. 在 [另存新檔] 對話方塊中，選取要儲存檔案的位置，並且為檔案輸入名稱 ("My SP Workflow")。
    
  
4. 選擇 [儲存]。
    
  

## 在 SharePoint Designer 2013 中自訂及發佈工作流程
<a name="VSSPD_Customizing"> </a>

在 Visio 2013 中為 SharePoint 2013 工作流程建立基礎商務邏輯，並且儲存圖表之後，您可以在 SharePoint Designer 2013 中開啟 Visio .vsdx 檔案，並且開始對 SharePoint 2013 網站設計工作流程。.vsdx 檔案套件包含 XML 文件，SharePoint Designer 2013 可以將該文件轉譯為工作流程。
  
    
    
使用下列程序以在 SharePoint Designer 2013 中開啟 SharePoint 2013 網站：
  
    
    

### 在 SharePoint Designer 2013 中開啟 SharePoint 2013 網站


1. 開啟 SharePoint Designer 2013。
    
  
2. 在 [開啟 SharePoint 網站] 底下，選擇 [開啟網站]。
    
  
3. 在 [開啟網站] 對話方塊中，選取您要開啟的網站。
    
  
4. 選擇 [開啟]。
    
  
SharePoint 2013 網站開啟之後，您可以在 SharePoint Designer 2013 內開啟 Visio 2013 .vsdx 圖表。
  
    
    

### 在 SharePoint Designer 2013 中開啟 Visio Professional 2013 工作流程


1. 選擇 [檔案]，然後選擇 [新增項目]。
    
  
2. 若要建立清單工作流程，請執行下列動作：
    
1. 在 [工作流程] 底下，選擇 [清單工作流程]。
    
  
2. 在 [清單工作流程] 底下的左窗格中，輸入工作流程的名稱 (My First SP2013 Workflow)，然後在您要發佈工作流程的網站上選取清單。
    
  
3. 在 [請選擇新工作流程的工作流程平台] 清單中，選取 [SharePoint 2013 工作流程]。
    
  
4. 選擇 [建立]。
    
  
3. 若要建立網站工作流程，請執行下列動作：
    
1. 在 [工作流程] 底下，選擇 [網站工作流程]。
    
  
2. 在 [網站工作流程] 底下的左窗格中，輸入工作流程的名稱 (My First SP2013 Workflow)。
    
  
3. 在 [請選擇新工作流程的工作流程平台] 清單中，選取 [SharePoint 2013 工作流程]。
    
  
4. 選擇 [建立]。
    
  
4. 在 [工作流程] 索引標籤的 [管理] 群組中，選擇 [工作流程設定]。
    
  
5. 在 [工作流程設定] 索引標籤的 [管理] 群組中，選擇 [從 Visio 匯入]。
    
  
6. 在 [從 Visio 繪圖匯入工作流程] 對話方塊中，瀏覽至 .vsdx 檔案所在的位置。
    
  
7. 選取您要開啟的檔案 (My SP Workflow)，然後選擇 [開啟]。
    
  
當您在 SharePoint Designer 2013 中開啟 .vsdx 檔案時，檔案會在「視覺化設計工具」中顯示，Visio ActiveX 控制項是裝載於 SharePoint Designer。Visio 2013 圖表保留在 Visio 中建立的所有圖形和圖形文字。 
  
    
    

> **注意事項**
> 若要在 SharePoint Designer 2013 中，於「視覺化設計工具」與「宣告式設計工具」之間切換，在 [工作流程] 索引標籤的 [管理] 群組中，選擇 [檢視]。此程序可能需要耗費一些時間，讓 SharePoint Designer 2013 驗證工作流程，然後將工作流程資訊從某個格式轉換為其他格式。在此程序期間，會發生其他圖形層級驗證。如果偵測到圖表的任何錯誤，則會在畫布底端的錯誤窗格中顯示錯誤 (與在 Visio 中類似)。 
  
    
    

「視覺化設計工具」中顯示的圖形也有「動作標記」 (由圖形左下角的「工作流程設定」類型圖示顯示)。當您選擇「動作標記」時，下拉式功能表會顯示工作流程中該動作或條件的屬性 (attribute) 和 **Properties** 屬性 (property)。這些屬性 (property) 會定義要用於該動作的參數值：要從哪些清單提取項目、要使用哪個計算運算子，或要將訊息寄送至哪個電子郵件地址。當您選擇清單中顯示的屬性時，對話方塊隨即顯示，您可以在其中自訂該屬性的設定。
  
    
    
例如，[傳送電子郵件] 圖形有兩個相關聯的屬性： **Create Email** 和 **Properties**，當您選擇 **Create Email** 時，[定義電子郵件訊息] 對話方塊隨即顯示，您可以在其中建立由動作傳送的訊息。如果您選擇 **Properties**，[傳送電子郵件內容] 對話方塊隨即顯示，顯示動作的所有參數。
  
    
    

> **注意事項**
> 如需個別動作、圖形及其屬性的詳細資訊，請參閱下列文章： [在 Visio 中 SharePoint Server 工作流程範本的圖形](shapes-in-the-sharepoint-server-workflow-template-in-visio.md)和 [工作流程動作快速參考 （SharePoint 2013 工作流程平台）](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)。 
  
    
    

在工作流程內設定屬性並且準備發佈之後，您必須先在 SharePoint Designer 2013 中檢查工作流程有無錯誤。當您在功能區的 [視覺化設計工具] 索引標籤中選擇 [發佈] 時，SharePoint Designer 2013 會自動檢查工作流程有無錯誤。如果您想要的話，也可以手動起始錯誤檢查。
  
    
    
使用下列程序在 SharePoint Designer 2013 中檢查 SharePoint 2013 工作流程：
  
    
    

### 在SharePoint Designer 2013 中手動檢查工作流程有無錯誤


1. 在 [視覺化設計工具] 索引標籤的 [儲存] 群組中，選擇 [檢查錯誤]。
    
  
2. 如果在工作流程中找到錯誤，[問題] 窗格會在「視覺化設計工具」畫布下方開啟。選擇清單中的每個項目以選取工作流程中造成問題的動作、條件、連接器、結束點或容器。
    
  
3. 解決 [問題] 清單中列出的每個驗證錯誤。解決了所有錯誤之後，再次選擇 [檢查錯誤] 。 
    
  
4. 如果工作流程中找不到錯誤，則 SharePoint Designer 會顯示訊息，表示工作流程中未發現任何問題。
    
  
已檢查工作流程且未發現任何問題之後，您可以將工作流程發佈至 SharePoint 清單。若要從 SharePoint Designer 2013 發佈工作流程，在 [視覺化設計工具] 索引標籤的 [儲存] 群組中，選擇 [發佈]。如果在發佈程序期間發生任何錯誤，SharePoint Designer 2013 會返回「視覺化設計工具」並且在 [問題] 窗格中顯示錯誤。
  
    
    

## 其他資源
<a name="VSSPD_Additional"> </a>

如需詳細資訊，請參閱下列資源：
  
    
    

-  [工作流程動作快速參考 （SharePoint 2013 工作流程平台）](workflow-actions-quick-reference-sharepoint-2013-workflow-platform.md)
    
  
-  [在 Visio 中 SharePoint Server 工作流程範本的圖形](shapes-in-the-sharepoint-server-workflow-template-in-visio.md)
    
  
-  [在 Visio 中的 SharePoint Server 工作流程驗證錯誤的疑難排解](troubleshooting-sharepoint-server-workflow-validation-errors-in-visio.md)
    
  
-  [在 Visio 2010 中建立、匯入及匯出 SharePoint 工作流程](http://office.microsoft.com/en-us/visio-help/create-import-and-export-sharepoint-workflows-in-visio-HA101888007.aspx)
    
  
-  [SharePoint 開發人員中心](http://msdn.microsoft.com/zh-tw/sharepoint/default.aspx)
    
  
-  [Visio 開發人員中心](http://msdn.microsoft.com/zh-tw/office/aa905478)
    
  

