---
title: 受信クレーム SharePoint 2013 にサインインする
ms.prod: SHAREPOINT
ms.assetid: 08c687aa-e485-4269-aea8-4333da3588a5
---


# 受信クレーム: SharePoint 2013 にサインインする

## SharePoint にサインインする

ユーザーが SharePoint Server にサインインするときに、ユーザーのトークンが検証され、ユーザーはそのトークンを使用して SharePoint にサインインします。ユーザーのトークンは、クレーム プロバイダーによって発行されるセキュリティ トークンです。
  
    
    

> **メモ**
> 単一 SharePoint ファームおよびファーム間の SharePoint クレーム認証については、TechNet の「 [認証方法を計画する (SharePoint Server 2010)](http://technet.microsoft.com/ja-jp/library/cc262350.aspx)」を参照してください。 
  
    
    


### Windows クレーム モードでのサインイン

Windows クレーム モードのサインインでは、ネゴシエート (NTLM/Kerberos) を使用して統合 Windows 認証チャレンジでサインインが行われます。ただし、Windows ユーザーを表す  [WindowsIdentity](https://msdn.microsoft.com/library/System.Security.Principal.WindowsIdentity.aspx) オブジェクトが作成された後で、SharePoint Server によって [WindowsIdentity](https://msdn.microsoft.com/library/System.Security.Principal.WindowsIdentity.aspx) オブジェクトは、ユーザーのクレームベースの表現を表す [ClaimsIdentity](https://msdn.microsoft.com/library/Microsoft.IdentityModel.Claims.ClaimsIdentity.aspx) オブジェクトに変換されます。
  
    
    
SharePoint Server はその後クレーム オーグメントを行い、SharePoint Server によって発行された結果トークンを処理します。つまり、SharePoint Server がネイティブ Windows ログイン モードであるとクライアントによって見なされていても、SharePoint Server の一部の機能 (サービス アプリケーションのマルチテナント サポート、カスタム クレーム プロバイダーなど) が動作します。Windows クレーム モードでのサインインは、SharePoint Server に組み込まれている既定の動作です。
  
    
    
クレーム サインインのすべて種類が、パッシブ サインインに依存しています。パッシブ サインインは、Windows チャレンジを使用して行われますが、302 のリダイレクトを介して届く別のログイン ページから行われます。このモードは、複数のサインイン方法が有効になっており、サポートされているクレーム プロバイダーをユーザーが選択しなければならないときに役に立ちます。Win32 クライアントは、Office クライアントで実装されているフォーム ベース認証をサポートしている必要があります。Office クライアントの中には、異なるプロトコルに従うものもあります。
  
    
    

### SAML パッシブ サインイン モード

SAML (Security Assertion Markup Language) パッシブ サインインでは、ユーザーがサインインするときに、クライアント (Web ページの場合があります) が指定されたクレーム プロバイダー (Windows Live ID クレーム プロバイダーなど) にリダイレクトされます。クレーム プロバイダーがユーザーを認証した後で、SharePoint Server は、クレーム プロバイダーによって提供された SAML トークンを取得して処理し、クレームを拡張します。
  
    
    
Active Directory フェデレーション サービス (ADFS)、Windows Live ID クレーム プロバイダーなど、SAML ベースのクレーム プロバイダーについては、SAML パッシブ サインイン モードを使用したサインインのみがサポートされています。SAML パッシブ サインインは SharePoint オンライン ID モデルです。
  
    
    

> **メモ**
> SAML パッシブ サインインには、サインインのプロセスが記述されています。Web アプリケーションのサインインが、信頼済みログイン プロバイダーからトークンを受け取るように構成されている場合、この種類のサインインは SAML パッシブ サインインと呼ばれます。信頼済みログイン プロバイダーは、SharePoint が信頼する外部 (つまり、SharePoint 外の) セキュリティ トークン サービス (STS) です。 
  
    
    

Win32 クライアントは、Office クライアントで実装されているフォーム ベース認証をサポートしている必要があります。
  
    
    

### ASP.NET メンバーシップおよびロール パッシブ サインイン

ASP.NET メンバーシップおよびロール パッシブ サインインでは、クライアントを、ASP.NET ログイン コントロールがホストされている Web ページにリダイレクトすることによってサインインが行われます。ユーザー ID を表す ID オブジェクトが作成された後で、そのオブジェクトは、SharePoint Server によってユーザーのクレームベースの表現を表す  [ClaimsIdentity](https://msdn.microsoft.com/library/Microsoft.IdentityModel.Claims.ClaimsIdentity.aspx) オブジェクトに変換されます。
  
    
    
SharePoint Server はその後、クレーム オーグメントを行います。Win32 クライアントは、Office クライアントで実装されているフォーム ベース認証をサポートしている必要があります。
  
    
    

### Windows クラシック モードでのサインイン

Windows クラシック モードでのサインインは、このリリースでは使用できません。Windows クラシック モードのサインインでは、ネゴシエート (NTLM/Kerberos) を使用して統合 Windows 認証チャレンジでサインインが行われます。このモードを使用してユーザーがサインインすると、クレーム オーグメントが行われないので、一部の機能 (サービス アプリケーションのマルチテナント サポート、カスタム クレーム プロバイダーなど) が動作しません。
  
    
    
サービス アプリケーションの中には、一部の機能でクレーム モードを必要とする場合があります。
  
    
    

### 匿名アクセス

Web アプリケーションの匿名アクセスを有効にできます。Web アプリケーション内のサイトの管理者が匿名アクセスを許可できます。匿名ユーザーがセキュリティ保護されているリソースにアクセスするには、ログオン ボタンをクリックして資格情報を送信します。
  
    
    
SharePoint Server はその後、クレーム オーグメントを行います。Win32 クライアントは、Office クライアントで実装されているフォーム ベース認証をサポートしている必要があります。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 でのクレームベース ID](claims-based-identity-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のクレーム プロバイダー](claims-provider-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 でクレーム プロバイダーを作成する](how-to-create-a-claims-provider-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 でクレーム プロバイダーを展開する](how-to-deploy-a-claims-provider-in-sharepoint-2013.md)
    
  

