---
title: 使用 SharePoint 2013 为其他平台生成移动应用程序
ms.prod: SHAREPOINT
ms.assetid: 017df869-44fb-4ffe-82fb-4654e01329ad
---


# 使用 SharePoint 2013 为其他平台生成移动应用程序
了解如何使用代表性状态传输 (REST) 创建用于任何平台的 SharePoint 2013 移动应用程序。
移动设备如今已变得日益强大且易于使用。用户可借助笔记本电脑、上网本、平板电脑和移动电话访问完成其工作所需的信息和应用程序。现在，开发用于移动设备的应用程序比以往任何时候都容易。因此，在越来越多的业务方案中，均要求将客户端应用程序与其业务流程相集成。本文介绍如何将移动客户端应用程序与 SharePoint 2013 进行集成。您可以创建一个移动应用程序，以便从任何位置浏览 SharePoint 内容，并与 SharePoint 列表和库建立连接以访问相关数据。
  
    
    

若要开发与 SharePoint 2013 交互的移动应用程序，您可以使用可通过开放协议访问的常见服务。SharePoint Foundation 2010 引入了客户端对象模型，以便开发人员能够通过所选择的 Web 编程技术（.NET Framework、Microsoft Silverlight 或 JavaScript）与 SharePoint 进行远程通信。SharePoint 2013 引入了代表性状态传输 (REST) 服务，此服务可以媲美于客户端对象模型。在 SharePoint 2013 中，客户端对象模型中的几乎每个 API 都具有相应的 REST 终结点。现在，开发人员可以使用支持 REST Web 请求的任何技术与 SharePoint 对象模型进行远程交互。您要用于移动应用程序开发的任何编程语言均可以使用 REST。
您可以使用 SharePoint 2013 提供的 REST 接口执行基本的创建、读取、更新和删除 (CRUD) 操作。REST 公开所有的 SharePoint 实体和在其他 SharePoint 客户端 API 中可用的操作。使用 REST 的优点之一是您不必添加对任何 SharePoint 2013 库或客户端程序集的引用。相反，您向适当的终结点发出 HTTP 请求来检索或更新 SharePoint 实体，如网站、列表和列表项。请参阅 [使用 SharePoint 2013 REST 服务进行编程](use-odata-query-operations-in-sharepoint-rest-requests.md)，它全面介绍了 SharePoint 2013 REST 接口及其体系结构。
  
    
    


## SharePoint 2013 中的 REST 终结点
<a name="BuildMobileAppsInSharePoint2013ForNonWindowsPhone_REST_EndpointsInSharePoint2013"> </a>

若要使用 SharePoint 2013 中内置的 REST 功能，您可以使用开放数据协议 (OData) 标准创建一个与所需客户端对象模型 API 对应的 RESTful HTTP 请求。client.svc Web 服务将处理该 HTTP 请求并为 Atom 或 JavaScript 对象表示法 (JSON) 格式的适当响应提供服务。客户端应用程序随后必须分析该响应。图 1 显示了 SharePoint REST 体系结构的概览。
  
    
    

**图 1. SharePoint REST 体系结构**

  
    
    

  
    
    
![SharePoint REST 体系结构](images/SP15Con_BuildSharePointAppsForMobileDevices_Fig2.png)
  
    
    
SharePoint 2013 REST 服务中的终结点对应于 SharePoint 客户端对象模型中的类型和成员。通过使用 HTTP 请求，您可以使用这些 REST 终结点对 SharePoint 项目（如列表和网站）执行典型的 CRUD 操作。
  
    
    
通常：
  
    
    

- 表示读取操作的终结点将映射到 HTTP **GET** 命令。
    
  
- 表示更新操作的终结点将映射到 HTTP **POST** 命令。
    
  
- 表示更新或插入操作的终结点将映射到 HTTP **PUT** 命令。
    
  
在选择要使用的 HTTP 请求时，还应考虑：
  
    
    

- 使用 **POST** 创建项目，如列表和网站。SharePoint 2013 REST 服务支持将包含对象定义的 **POST** 命令发送到表示集合的终结点。
    
  
- 对于 **POST** 操作，任何不需要的属性将设置为其默认值。如果您尝试在 **POST** 操作过程中设置只读属性，则服务将返回异常。
    
  
- 使用 **PUT**、 **PATCH** 和 **MERGE** 操作可以更新现有 SharePoint 对象。任何表示对象属性 **set** 操作的服务终结点均支持 **PUT** 请求和 **MERGE** 请求。对于 **MERGE** 请求，设置属性是可选的；任何未明确设置的属性将保留其当前属性。但是，对于 **PUT** 命令，任何未明确设置的属性将设置为其默认属性。此外，如果您在使用 HTTP **PUT** 命令时未在对象更新中指定所有可设置的属性，则 REST 服务将返回异常。
    
  
- 对特定终结点 URL 使用 HTTP **DELETE** 命令可删除该终结点表示的 SharePoint 对象。对于可循环的对象（例如，列表、文件和列表项），这将导致 **Recycle** 操作。有关详细信息，请参阅 [开始使用 SharePoint 2013 REST 服务](get-to-know-the-sharepoint-2013-rest-service.md)。
    
  

## 向 SharePoint 验证用户身份
<a name="BuildMobileAppsInSharePoint2013ForNonWindowsPhone_AuthenticatingNonWindowsAppForSharePoint"> </a>

若要向 SharePoint 验证您的移动应用程序，可使用 MS-OFBA 协议。有关详细信息，请参阅  [[MS-OFBA]：基于 Office 表单的身份验证协议规范](http://msdn.microsoft.com/library/30c7bbe9-b284-421f-b866-4e7ed4866027%28Office.15%29.aspx)。该协议客户端配置为存储和传送 Cookie。该协议客户端依赖远程协议服务器来将用户标识设置为一个或多个 HTTP Cookie。在建立用户标识后，客户端随后会将每个 Cookie 与每个后续 HTTP 请求一起发送。
  
    
    
当用户登录到 SharePoint 2013 时，系统会验证用户令牌并使用该令牌登录到 SharePoint。用户令牌是一个由身份提供程序发布的安全令牌。SharePoint 2013 支持多种身份验证。有关详细信息，请参阅  [SharePoint 2013 中的身份验证、授权和安全性](authentication-authorization-and-security-in-sharepoint-2013.md)。若要验证用户身份，可使用 REST 接口。授权过程验证经过身份验证的使用者（应用程序或该应用程序运行时所代表的用户）是否有权执行某些操作或访问特定资源（例如，列表或 SharePoint 文档文件夹）。
  
    
    
您可以利用 OData 通过浏览特别构造的 URL 来访问数据源（如数据库）。这将允许采用一种简化的方法来连接到组织内承载的数据源并使用这些数据源。OData 是一种使用 HTTP、Atom 和 JavaScript 对象表示法 (JSON) 的协议，它使开发人员能够编写与数量不断增加的数据源进行通信的应用程序。Microsoft 支持创建此标准，以将其作为一种在应用程序与可从 Web 访问的数据存储之间实现数据交换的方法。新 OData 连接器支持 SharePoint 与 OData 提供程序进行通信。有关详细信息，请参阅 [开放数据协议](http://www.odata.org)。
  
    
    
下面的代码演示如何使用 REST 终结点向 SharePoint 2013 验证您的应用程序，以实现基本身份验证或基于表单的身份验证。下面的代码示例是用 C# 编写的，您也可以使用其他任何编程语言，根据平台要求创建 HTTP 请求。
  
    
    



```cs

string SharePointUrl = "https://Target SharePoint site";

private void AuthenticateToSharePoint(object sender, RoutedEventArgs e)
{
    ODataAuthenticator odataAt = new ODataAuthenticator("<Username>", "<password>");
    odataAt.CookieCachingEnabled = true;
    odataAt.AuthenticationCompleted += new EventHandler<AuthenticationCompletedEventArgs>(odataAt_AuthenticationCompleted);
    odataAt.Authenticate(new Uri(SharePointUrl, UriKind.Absolute));
}

void odataAt_AuthenticationCompleted(object sender, AuthenticationCompletedEventArgs e)
{
    HttpWebRequest endpointRequest = (HttpWebRequest)HttpWebRequest.Create(SharePointUrl.ToString() + "/_api/web/lists");
    endpointRequest.Method = "GET";
    endpointRequest.Accept = "application/json;odata=verbose";
          endpointRequest.CookieContainer = (sender as ODataAuthenticator).CookieContainer;
    
    endpointRequest.BeginGetResponse(new AsyncCallback((IAsyncResult res) =>
    {
        HttpWebRequest webReq = res.AsyncState as HttpWebRequest;
        WebResponse response = webReq.EndGetResponse(res);

        HttpWebResponse httpResponse = response as HttpWebResponse;
        HttpStatusCode code = httpResponse.StatusCode;
        this.Dispatcher.BeginInvoke(() =>
        {
            MessageBox.Show(code.ToString());
        });
    }), endpointRequest);
}

```

若要向终结点验证 **HttpWebrequest**，应首先使用 **ODataAuthenticator** 类向 SharePoint 进行验证。在调用 **Authenticate** 方法之前，需向 **AuthenticationCompleted** 事件注册 **ODataAuthenticator** 对象。
  
    
    
在 **OnAuthenticationCompleted** 事件内完成身份验证后，您可以使用 **ODataAuthenticator** 对象中的 **CookieContainer** 属性，该对象可附加到 **HttpWebRequest** 对象中，以便向 SharePoint 验证 REST 调用。
  
    
    

## 使用 REST 处理 SharePoint 列表项
<a name="BuildMobileAppsInSharePoint2013ForNonWindowsPhone_WorkingWithTheSharePointListItemUsingREST"> </a>

以下示例显示如何"检索"列表的所有项。
  
    
    

```

url: http://site url/_api/web/lists/GetByTitle('Test')/items
method: GET
headers:
// MS-OFBA protocol returns a cookie.
  Cookie: cookie


    accept: "application/json;odata=verbose" or "application/atom+xml"

```

以下示例显示如何"检索"特定列表项。
  
    
    



```

url: http://site url/_api/web/lists/GetByTitle('Test')/items(item id)
method: GET
headers:
    
// MS-OFBA protocol return a cookie.
  Cookie: cookie
    accept: "application/json;odata=verbose" or "application/atom+xml"

```

以下 XML 显示当您请求 XML 内容类型时返回的列表项属性的示例。
  
    
    



```XML

<content type="application/xml">
        <m:properties>
        <d:FileSystemObjectType m:type="Edm.Int32">0</d:FileSystemObjectType>
        <d:Id m:type="Edm.Int32">1</d:Id>
        <d:ID m:type="Edm.Int32">1</d:ID>
        <d:ContentTypeId>0x010049564F321A0F0543BA8C6303316C8C0F</d:ContentTypeId>
        <d:Title>an item</d:Title>
        <d:Modified m:type="Edm.DateTime">2012-07-24T22:47:26Z</d:Modified>
        <d:Created m:type="Edm.DateTime">2012-07-24T22:47:26Z</d:Created>
        <d:AuthorId m:type="Edm.Int32">11</d:AuthorId>
        <d:EditorId m:type="Edm.Int32">11</d:EditorId>
        <d:OData__UIVersionString>1.0</d:OData__UIVersionString>
        <d:Attachments m:type="Edm.Boolean">false</d:Attachments>
        <d:GUID m:type="Edm.Guid">eb6850c5-9a30-4636-b282-234eda8b1057</d:GUID>
    </m:properties>
</content>
```

以下示例显示如何"创建"列表项。
  
    
    

> **注释**
> 若要执行此操作，您必须知道列表的 **ListItemEntityTypeFullName** 属性并将它作为 HTTP 请求正文中的 **type** 的值传递。
  
    
    




```

url: http://site url/_api/web/lists/GetByTitle('Test')/items
method: POST
body: { '__metadata': { 'type': 'SP.Data.TestListItem' }, 'Title': 'Test'}
headers:
    
// MS-OFBA protocol returns a cookie.
  Cookie: cookie
     X-RequestDigest = form digest value
    accept: "application/json;odata=verbose"
    content-type: "application/json;odata=verbose"
    content-length:length of post body
```

以下示例显示如何"更新"列表项。
  
    
    

> **注释**
> 若要执行此操作，您必须知道列表的 **ListItemEntityTypeFullName** 属性并将它作为 HTTP 请求正文中的 **type** 的值传递。
  
    
    




```

url: http://site url/_api/web/lists/GetByTitle('Test')/items(item id)
method: POST
body: { '__metadata': { 'type': 'SP.Data.TestListItem' }, 'Title': 'TestUpdated'}
headers:
// MS-OFBA protocol returns a cookie.
  Cookie: cookie
     X-RequestDigest = form digest value
    "IF-MATCH": etag or "*"
    "X-HTTP-Method":"MERGE",
    accept: "application/json;odata=verbose"
    content-type: "application/json;odata=verbose"
    content-length:length of post body
```

以下示例显示如何"删除"列表项。
  
    
    



```

url: http://site url/_api/web/lists/GetByTitle('Test')/items(item id)
method: POST
headers:
// MS-OFBA protocol returns a cookie.
  Cookie: cookie
     X-RequestDigest = form digest value
    "IF-MATCH": etag or "*"
    "X-HTTP-Method":"DELETE"

```

有关详细信息，请参阅 [使用 SharePoint 2013 REST 终结点完成基本操作](http://msdn.microsoft.com/library/e3000415-50a0-426e-b304-b7de18f2f7d9%28Office.15%29.aspx)。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [构建访问 SharePoint 2013 的 Windows Phone 应用程序](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 REST 服务](e1ff2979-1c16-4cb0-a57e-9168dfe20a7c.md)
    
  
-  [构建访问 SharePoint 2013 的 Windows Phone 应用程序](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 REST 服务进行编程](use-odata-query-operations-in-sharepoint-rest-requests.md)
    
  
-  [开始使用 SharePoint 2013 REST 服务](get-to-know-the-sharepoint-2013-rest-service.md)
    
  
-  [对 SharePoint 2013 使用 C# 和 JavaScript 进行 REST 调用](http://www.microsoft.com/resources/msdn/en-us/office/media/video/video.mdl?cid=sdc&amp;from=mscomsdc&amp;VideoID=4e4cc094-ff69-405b-852f-2ac7c41293c5)
    
  
-  [对 SharePoint 2013 演示版使用 C# 和 JavaScript 进行 REST 调用](http://www.microsoft.com/resources/msdn/en-us/office/media/video/video.mdl?cid=sdc&amp;from=mscomsdc&amp;VideoID=b1e7c9c5-0f62-4a78-bb7b-8e283c86145c)
    
  
-  [开放数据协议](http://www.odata.org/)
    
  
-  [SharePoint 外接程序的授权和身份验证](http://msdn.microsoft.com/library/bde5647a-fff1-4b51-b67b-2139de79ce4a%28Office.15%29.aspx)
    
  
-  [Windows Phone SDK 2.0](http://www.microsoft.com/zh-cn/download/details.aspx?id=35471)
    
  
-  [适用于 Windows Phone 8 的 Microsoft SharePoint SDK](http://www.microsoft.com/zh-cn/download/details.aspx?id=36818)
    
  

