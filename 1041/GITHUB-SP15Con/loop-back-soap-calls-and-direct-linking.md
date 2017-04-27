---
title: SOAP 呼び出しのループバックおよび直接リンク
ms.prod: OFFICE365
ms.assetid: bffc6565-636f-40d4-ba17-2511070ba5db
---


# SOAP 呼び出しのループバックおよび直接リンク

たとえばカスタム Web パーツ、カスタム aspx ページなど、Microsoft SharePoint Foundation 内でコードを記述する場合、Microsoft.Office.Excel.Server.WebServices.dll に対して直接呼び出しをする必要があります。直接呼び出しは、Microsoft.Office.Excel.Server.WebServices.dll に直接リンクして行います。 
  
    
    

Web サーバーから簡易オブジェクト アクセス プロトコルを使用して同じ Web サーバーと通信することは、ループバック SOAP 呼び出しの使用としても知られています。ループバック SOAP 呼び出しは使用しないことを強くお勧めします。SharePoint Foundation 内でコードを記述する場合は、SOAP を使用して Excel Web Services を呼び出さないでください。代わりに、ローカル アセンブリで行うように、ローカルで Microsoft.Office.Excel.Server.WebServices.dll にリンクして呼び出しを行います。
## Microsoft.Office.Excel.Server.WebServices.dll の場所

Microsoft.Office.Excel.Server.WebServices.dll は次の場所のいずれかにあります。
  
    
    

-  _[ドライブ:]_\\Program Files\\Common Files\\Microsoft Shared\\web server extensions\\14\\ISAPI
    
  
- グローバル アセンブリ キャッシュ 
    
  

## Microsoft.Office.Excel.Server.WebServices.dll への参照の追加

プロジェクトで Microsoft.Office.Excel.Server.WebServices.dll に直接リンクしてコードから呼び出すには、参照を追加します。Microsoft SharePoint Server 2010 をインストールしたコンピューター上で、Microsoft Visual Studio の [ **参照の追加**] ダイアログ ボックスを使用すると、次のいずれかを行えます。 
  
    
    

- [ **.NET**] タブの [ **コンポーネント名**] リストから、[ **Excel Web Services**] を選択します。 
    
  
- 
  
    
    
 _[ドライブ:]_\\Program Files\\Common Files\\Microsoft Shared\\web server extensions\\14\\ISAPI にある Microsoft.Office.Excel.Server.WebServices.dll を参照します。
    
  

## 関連項目


#### 概念


  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
  
    
    
 [Excel Services の既知の問題およびヒント](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
#### その他の技術情報


  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
