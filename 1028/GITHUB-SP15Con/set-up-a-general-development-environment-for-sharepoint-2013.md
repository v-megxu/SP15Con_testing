---
title: 設定 SharePoint 2013 的一般開發環境
keywords: install sharepoint 2013,set up sharepoint 2013,setup SharePoint 2013
f1_keywords:
- install sharepoint 2013,set up sharepoint 2013,setup SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 08e4e4e1-d960-43fa-85df-f3c279ed6927
---


# 設定 SharePoint 2013 的一般開發環境
利用安裝 SharePoint 和 SharePoint 來了解設定 Visual Studio 開發環境的步驟。
## 如何決定您需要的 SharePoint 開發環境
<a name="SP15_bk_determinedevenv"> </a>

首先，決定您想要建置的項目 (若要深入了解 SharePoint Add-ins，請參閱  [SharePoint Add-ins](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx))：
  
    
    

- 如果您要建立 伺服器陣列解決方案，我們提供本文中的步驟。
    
  
- 如果您要建立 SharePoint Add-ins，請參閱  [工具及開發 SharePoint 的增益集的環境](http://msdn.microsoft.com/library/6906eb86-8270-4098-8106-1e8d0d3c212e%28Office.15%29.aspx)。
    
  

## 在 Microsoft Azure 虛擬機器上建立 SharePoint 開發環境。
<a name="SP15_bk_devenvazure"> </a>

如果您有訂閱 MSDN，則可以在 Azure 中快速佈建虛擬機器。
  
    
    
如果尚未啟動 MSDN 訂閱隨附的 Microsoft Azure 權益，您可以在此深入了解： [MSDN 訂閱者的 Microsoft Azure 權益](http://azure.microsoft.com/zh-tw/pricing/member-offers/msdn-benefits/)。
  
    
    

> **注意事項**
> Microsoft Azure 影像圖庫不再提供預先安裝 SharePoint 和 Visual Studio 的影像。然而，對於開發電腦來說，Microsoft Azure VM 仍是一個不錯的選擇。 > 登入  [Microsoft Azure 管理入口網站](https://manage.windowsazure.com)。 > 使用 Windows Server 2008 R2 Service Pack 1 x64，Windows Server 2012 (或更新版本) 圖庫中其中一個影像來建立 VM。依照虛擬機器建立精靈所提供的指示。我們建議對 SharePoint 開發使用 **X-Large** VM 大小。> 電腦佈建完成且執行後，使用與下列章節「內部部署建立 SharePoint 開發環境」相同的程序完成設定。(跳過關於安裝作業系統的章節)。 > 一旦設定開發環境之後，您就可以使用 Azure 點對網站連線，在虛擬機器上透過 Visual Studio 存取原始檔控制。如需如何進行此作業的指示，請參閱 [設定虛擬網路的點對站 VPN 連線](https://azure.microsoft.com/zh-tw/documentation/articles/vpn-gateway-point-to-site-create/)。 
  
    
    


## 建立內部部署 SharePoint 開發環境
<a name="SP15_bk_devenvazure"> </a>


  
    
    

### 為您的 SharePoint Add-ins 開發環境安裝作業系統
<a name="SP15_bk_InstallOS"> </a>

相較於實際執行環境的需求，SharePoint 安裝的開發環境需求較不嚴格且成本較低。在任何開發環境中，您應該使用配備 x64 CPU 並且至少 16 GB RAM 的電腦，以便安裝及執行 SharePoint；最好有 24 GB RAM。根據您的特定需求和預算，可以選擇以下其中一個選項：
  
    
    

- 在 Windows Server 2008 R2 Service Pack 1 x64 或 Windows Server 2012 (或更新版本) 上安裝 SharePoint。
    
  
- 使用 Microsoft Hyper-V 並在執行 Windows Server 2008 R2 Service Pack 1 x64 或 Windows Server 2012 客體作業系統的虛擬機器上安裝 SharePoint。如需為 SharePoint 設定 Microsoft Hyper-V 虛擬機器的相關指示，請參閱  [使用 SharePoint 2013 虛擬機器與 Hyper-V 環境的最佳做法設定](http://technet.microsoft.com/zh-tw/library/ff621103%28v=office.15%29.aspx)。
    
  

### 安裝作業系統和 SharePoint 2013 的應用程式開發必要條件
<a name="SP15_bk_prereqsOS"> </a>

SharePoint 要求您的作業系統要有特定安裝的先決條件，才能開始進行安裝。基於這個理由，SharePoint 包含一個會安裝所有先決條件的 PrerequisiteInstaller.exe 工具。請在執行 Setup.exe 工具之前先執行此工具。
  
    
    

1. 執行 PrerequisiteInstaller.exe 工具。
    
  
2. 執行包含在您的安裝檔案中的 Setup.exe 工具。
    
  
3. 接受 Microsoft 軟體授權條款。
    
  
4. 在 [選擇您要的安裝] 頁面上，選擇 [獨立]。
    
   **圖 2：安裝類型選擇**

  

![SharePoint 2013 Installation Server Type](images/SP15_app_ServerType.gif)
  

  

  
5. 如果安裝中發生任何錯誤，請檢閱記錄檔。若要尋找記錄檔，開啟 [命令提示字元] 視窗，並在命令提示字元中輸入下列命令。安裝完成時，也會出現記錄檔的連結。
    
  ```
  
cd %temp
dir /od *.log
  ```

6. 安裝完成後，系統會提示您啟動「SharePoint 產品及技術設定精靈」。
    
    > **注意事項**
      > 如果您使用已加入網域，但未連線到網域控制站的電腦，則「SharePoint 產品及技術設定精靈」可能會失敗。發生此錯誤時，請直接透過虛擬私人網路 (VPN) 連線來連線到網域控制站，或使用電腦上具有系統管理權限的本機帳戶登入。 
7. 設定精靈完成之後，您會看到新 SharePoint 網站的 [範本選擇] 頁面。
    
   **圖 3：選擇網站範本頁面**

  

![SharePoint 2013 site templates](images/SP15_app_ChooseSiteTemplates.gif)
  

  

  

### 安裝 Visual Studio
<a name="SP15_bk_installVS"> </a>

安裝 Visual Studio 時，您會獲得在本機電腦上開發 SharePoint 所需的所有範本、工具和組件。
  
    
    
如需安裝 Visual Studio 的指示，請參閱 [安裝 Visual Studio](http://msdn.microsoft.com/zh-tw/library/e2h7fzkw.aspx)。
  
    
    

#### Visual Studio 中的詳細資訊記錄

如果您想要開啟詳細資訊記錄，請遵循下列步驟：
  
    
    

1. 開啟登錄並瀏覽至 **HKEY_CURRENT_USER\\Software\\Microsoft\\VisualStudio\\ _nn.n_\\SharePointTools** ，其中 _nn.n_ 是Visual Studio 的版本，例如 12.0 或 14.0。
    
  
2. 加入名為 **EnableDiagnostics** 的 DWORD 機碼。
    
  
3. 將機碼的值設為 **1** 。
    
  
在未來版本的 Visual Studio 中，登錄路徑將會變更。
  
    
    

## 後續步驟
<a name="SP15_bk_devenvazure"> </a>

如果您要繼續進行工作流程，請繼續 [安裝及設定 SharePoint 2013 工作流程管理員](set-up-and-configure-sharepoint-2013-workflow-manager.md)。
  
    
    

## 其他資源
<a name="SP15_bk_AddlResources"> </a>


-  [安裝 Visual Studio](http://msdn.microsoft.com/zh-tw/library/e2h7fzkw%28v=vs.110%29.aspx)
    
  
-  [工具及開發 SharePoint 的增益集的環境](http://msdn.microsoft.com/library/6906eb86-8270-4098-8106-1e8d0d3c212e%28Office.15%29.aspx)
    
  

  
    
    

