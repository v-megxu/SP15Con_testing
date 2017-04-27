---
title: モバイルおよびネイティブ デバイス アプリからの SharePoint へのアクセス
ms.prod: SHAREPOINT
ms.assetid: 42014171-5ee5-421d-9cde-413efc3aecef
---


# モバイルおよびネイティブ デバイス アプリからの SharePoint へのアクセス
モバイル アプリとその他のネイティブ デバイス アプリ、および外部 Web アプリケーションから SharePoint にアクセスする方法を説明します。
SharePoint アドイン、ファーム ソリューション、および「コードなし」セキュリティで保護されたソリューション はすべて SharePoint 内部から実行されますが、その他のプラットフォームのアプリも SharePoint クライアント API にアクセスできます。
  
    
    


> **重要**
> 任意のプラットフォームでテストとデバッグを行うには、 **Office 365 の開発者アカウント** が必要です。詳細については、「 [Office 365 開発者向けサイトにサインアップする](http://msdn.microsoft.com/library/b22ce52a-ae9e-4831-9b68-c9210af6dc54%28Office.15%29.aspx)」または「 [既存の Office 365 サブスクリプション内で開発者向けサイトを作成する](http://msdn.microsoft.com/library/2ec857d5-dc6f-4cf6-ba45-adc845ef2a25%28Office.15%29.aspx)」を参照してください。 
  
    
    


## Microsoft 以外のモバイルおよびネイティブ デバイス アプリ

モバイル アプリを含む Microsoft 以外のデバイス アプリは、 **SharePoint データに対する CRUD 操作に SharePoint REST/OData API を使用します** 。
  
    
    

- 基本事項については、「 [SharePoint 2013 REST サービスの概要](get-to-know-the-sharepoint-2013-rest-service.md)」を参照してください。
    
  
- 詳細なリファレンスについては、「 [SharePoint 2013 REST API リファレンス](http://msdn.microsoft.com/library/3514e753-19f9-4b41-a1ae-f35c5ffc17d2%28Office.15%29.aspx)」を参照してください。
    
  
任意のプラットフォームでのモバイル アプリの作成方法の詳細については、「 [SharePoint 2013 を使用して他のプラットフォーム用のモバイル アプリを構築する](build-mobile-apps-for-other-platforms-using-sharepoint-2013.md)」を参照してください。
  
    
    

## SharePoint にアクセスする Windows Phone アプリ
<a name="WinPhone"> </a>

Windows Phone アプリは次のいずれかを使用できます。
  
    
    

- Windows Phone デバイス向けに特化された .NET SharePoint クライアント側オブジェクト モデル (CSOM) バージョン。
    
  
- SharePoint REST/OData API。
    
  
 これらのモバイル アプリは、SharePoint での Microsoft プッシュ通知サービスのサポートと新しい位置情報フィールド タイプを利用できます。
  
    
    
SharePoint にアクセスする Windows Phone アプリの作成の詳細については、「 [SharePoint 2013 にアクセスする Windows Phone アプリの作成](build-windows-phone-apps-that-access-sharepoint-2013.md)」を参照してください。
  
    
    

## SharePoint から開始しない Web アプリケーション
<a name="WinPhone"> </a>

SharePoint から開始しない Web アプリケーションは、厳密には「SharePoint アドイン」ではありませんが、MSDN やその他の資料では SharePoint アドインとして扱われることがあります。こうしたアプリには、Office 365 アプリ起動ツールから実行されるアプリ、Office アドイン、およびブラウザーから直接実行される Web アプリケーションが含まれます。
  
    
    
ASP.NET プラットフォームまたは Microsoft 以外のスタックでこれらのアプリを作成できます。Microsoft 以外のスタックで作成される Web アプリケーションは、Microsoft 以外のデバイス アプリと同様に、CRUD 操作に REST/OData API を使用します。ASP.NET で作成される Web アプリケーションは、 **SharePoint CSOM または REST/OData API を使用できます** 。
  
    
    
このようなアプリは、OAuth Authentication Code フローに準拠して Azure Control Service (ACS) により発行される **アクセス トークンを使用して、SharePoint データへの承認されたアクセス権限を取得します** 。詳細については、「 [SharePoint アドインの認証コード OAuth フロー](http://msdn.microsoft.com/library/e89e91c7-ea39-49b9-af5a-7f047a7e2ab7%28Office.15%29.aspx)」を参照してください。
  
    
    

