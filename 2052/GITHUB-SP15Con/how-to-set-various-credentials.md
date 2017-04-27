---
title: 如何：设置各种凭据
ms.prod: OFFICE365
ms.assetid: eb819681-5a4f-49ae-b7f4-334366c51112
---


# 如何：设置各种凭据

您必须为用户设置凭据，然后他们才能使用您的自定义应用程序调用 Excel Web Services。您必须明确设置凭据，即使您想使用默认凭据。Excel Web Services 使用 Microsoft SharePoint Foundation 支持的身份验证方案。有关 SharePoint Foundation 身份验证方案的详细信息，请参阅本 SDK 中的 SharePoint Foundation 文档以及 [传入声明：登录到 SharePoint 2013](incoming-claims-signing-into-sharepoint-2013.md)。
  
    
    

下面的示例演示如何设置凭据。
## 使用当前用户的凭据

以下代码使用当前用户的登录凭据向 Web 服务发出请求。 
  
    
    

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


## 使用不同的凭据集

以下代码使用当前用户的登录凭据向 Web 服务发出请求。 
  
    
    
 **示例代码提供者：** Saif Ullah Baig，Microsoft Corporation
  
    
    



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


## 使用其他凭据集

以下代码使用当前用户的登录凭据向 Web 服务发出请求。 
  
    
    

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

在本示例中， **LoginNameTextBox**、 **LoginPWDTextBox** 和 **LoginDomainTextBox** 是登录文本框的 **Name** 属性值。
  
    
    
有关如何使用 **CredentialCache** 类和 **NetworkCredential** 类，以及如何安全使用的详细信息，请参阅 Microsoft Visual Studio 文档或 [NetworkCredential Class](http://msdn.microsoft.com/library/60b63419-9606-4fdc-a30f-257ded236f16.aspx)。
  
    
    

## 另请参阅


#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
#### 其他资源


  
    
    
 [步骤 1：创建 Web 服务客户端项目](step-1-creating-the-web-service-client-project.md)
  
    
    
 [步骤 2：添加 Web 引用](step-2-adding-a-web-reference.md)
  
    
    
 [步骤 3：访问 Web 服务](step-3-accessing-the-web-service.md)
  
    
    
 [步骤 4：构建和测试应用程序](step-4-building-and-testing-the-application.md)
  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
