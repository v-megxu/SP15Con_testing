---
title: 各種資格情報の設定方法
ms.prod: SHAREPOINT
ms.assetid: eb819681-5a4f-49ae-b7f4-334366c51112
---


# 各種資格情報の設定方法

カスタム アプリケーションを使用して Excel Web Services を呼び出す前に、ユーザーの資格情報を設定する必要があります。既定の資格情報を使用する場合でも、明示的に資格情報を設定する必要があります。Excel Web Services では、Microsoft SharePoint Foundation がサポートする認証スキームを使用します。SharePoint Foundation の認証スキームについて、詳細はこの SDK にある SharePoint Foundation のドキュメントおよび「 [受信クレーム: SharePoint 2013 にサインインする](incoming-claims-signing-into-sharepoint-2013.md)」を参照してください。
  
    
    

資格情報の設定方法を次の例に示します。
## 現在のユーザーの資格情報を使用するには

次のコードでは、Web サービスに対して要求を行うために、現在のユーザーのログオン資格情報を使用しています。 
  
    
    

```cs

//Instantiate the Web service.
    ExcelService xlService = new ExcelService();
//Set credentials for requests.
    xlService.Credentials = System.Net.CredentialCache.DefaultCredentials;

```


```VB.net

'Instantiate the Web service.
Dim xlService As New ExcelService()
'Set credentials for requests.
xlService.Credentials = System.Net.CredentialCache.DefaultCredentials
```


## さまざまな資格情報セットを使用するには

次のコードでは、Web サービスに対して要求するために、現在のユーザーのログオン資格情報を使用しています。 
  
    
    
 **サンプル コードの提供者:** Saif Ullah Baig、Microsoft Corporation
  
    
    



```cs

        protected string farmURL, docLibPath, workbookPath, uiCulture, dataCulture, localTempFolder, authenticationType;
        protected Cookie authCookie;

        protected API.ExcelService api;
        protected Constants.XLS_VER version;
        

        public VariousAuthScheme(Constants.XLS_VER ver, string farmurl, string docLib, string fileName, 
            string uic, string datac,
            string userName, string password, string domain,
            string localTemp, string authType)
        {
            api = new API.ExcelService();

            farmURL = farmurl;

            if (!farmURL.EndsWith("/"))
            {
                farmURL += "/";
            }

            api.Url = farmURL + "_vti_bin/ExcelService.asmx";

            
            version = ver;

            if (!docLib.EndsWith("/"))
            {
                docLib += "/";
            }

            workbookPath = farmURL + docLib + fileName;
            docLibPath = farmURL + docLib;
            uiCulture = uic;
            dataCulture = datac;
            localTempFolder = localTemp;
            authenticationType = authType;

            switch (authType)
            {
                case "Windows-Classic":
                    authenticationType = "Windows-Classic";
                    AuthenticateWindowsClassic(domain, userName, password);
                    break;

                case "Windows-Claims":
                    authenticationType = "Windows-Claims";
                    AuthenticateWindowsClaims();
                    break;

                case "FBA-Claims":
                    authenticationType = "FBA-Claims";
                    if (!AuthenticateFBAClaims(userName, password))
                        throw new Exception("FBA-Claims authentication failed");
                    break;

                case "Anonymous":
                    authenticationType = "Anonymous";
                    break;

                default:
                    throw new Exception ("Undefined authentication type specified: " + authType);
                    break;
            }
        }

        protected void AuthenticateWindowsClassic(string domain, string userName, string password)
        {
            if (userName != null &amp;&amp; userName.Length > 0)
            {
                api.Credentials = new System.Net.NetworkCredential(userName, password, domain);
            }
            else
            {
                api.Credentials = System.Net.CredentialCache.DefaultCredentials;
            }

            // Verify set credentials.
            System.Net.NetworkCredential cred = (System.Net.NetworkCredential) api.Credentials;
            Console.WriteLine(@"Credentials set to: {0}\\{1}", cred.Domain, cred.UserName);
        }

        protected void AuthenticateWindowsClaims()
        {
            throw new Exception ("Windows-Claims Authentication method not implemented");
        }

        protected bool AuthenticateFBAClaims(string userName, string password)
        {
            FBA.Authentication spAuthentication = new FBA.Authentication();
            spAuthentication.Url = farmURL + "_vti_bin/Authentication.asmx";
                          
            spAuthentication.CookieContainer = new CookieContainer();

            FBA.LoginResult loginResult = spAuthentication.Login(userName, password);
            authCookie = new Cookie();
                
            // Determines if login is successful.
            if (loginResult.ErrorCode == FBA.LoginErrorCode.NoError)
            {
                // Get the cookie collection from the authenticating Web service.
                CookieCollection cookies = spAuthentication.CookieContainer.GetCookies(new Uri(spAuthentication.Url));

                // Get the specific cookie that contains the security token.
                authCookie = cookies[loginResult.CookieName];

                // Initialize the cookie container of Excel Web Services.
                api.CookieContainer = new CookieContainer();
                api.CookieContainer.Add(authCookie);

                return true;
            }
            else
            {
                return false;
            }
        

```


## 別の資格情報のセットを使用するには

次のコードでは、Web サービスに対して要求するために、現在のユーザーのログオン資格情報を使用しています。 
  
    
    

```cs

//Instantiate the Web service.
ExcelService xlService = new ExcelService();

public void VerifyCredentials()
   {
    //Check whether the default credentials
    //should be used instead.  
       if (DefaultCredentialsCheckBox.Checked)
 {
     xlService.Credentials =     
        System.Net.CredentialCache.DefaultCredentials;
  }
  else
  {
      //Check whether user-defined credentials
         //should be used instead.
      System.Net.NetworkCredential userDefined = new 
         System.Net.NetworkCredential(
            LoginNameTextBox.Text,
LoginPWDTextBox.Text,
LoginDomainTextBox.Text);

         xlService.Credentials = userDefined;          
      }
}
```


```VB.net

'Instantiate the Web service.
Private xlService As New ExcelService()

Public Sub VerifyCredentials()
    'Check whether the default credentials
    'should be used instead.  
       If DefaultCredentialsCheckBox.Checked Then
     xlService.Credentials = System.Net.CredentialCache.DefaultCredentials
  Else
      'Check whether user-defined credentials
         'should be used instead.
      Dim userDefined As New System.Net.NetworkCredential(LoginNameTextBox.Text, LoginPWDTextBox.Text, LoginDomainTextBox.Text)

         xlService.Credentials = userDefined
  End If
End Sub
```

この例では、 **LoginNameTextBox**、 **LoginPWDTextBox**、 **LoginDomainTextBox** が [ログオン] テキスト ボックスの **Name** プロパティの値です。
  
    
    
 **CredentialCache** クラスと **NetworkCredential** クラスの使用方法、およびこれらを安全に使用する方法について、詳細は Microsoft Visual Studio のドキュメントまたは「 [NetworkCredential Class](http://msdn.microsoft.com/library/60b63419-9606-4fdc-a30f-257ded236f16.aspx)」を参照してください。
  
    
    

## 関連項目


#### 概念


  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
#### その他の技術情報


  
    
    
 [ステップ 1: Web サービス クライアント プロジェクトを作成する](step-1-creating-the-web-service-client-project.md)
  
    
    
 [手順 2: Web 参照を追加する](step-2-adding-a-web-reference.md)
  
    
    
 [手順 3: Web サービスへのアクセス](step-3-accessing-the-web-service.md)
  
    
    
 [手順 4: アプリケーションのビルドとテストを行う](step-4-building-and-testing-the-application.md)
  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
