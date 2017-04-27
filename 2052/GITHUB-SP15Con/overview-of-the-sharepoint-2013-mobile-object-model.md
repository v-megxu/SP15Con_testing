---
title: SharePoint 2013 移动对象模型概述
ms.prod: SHAREPOINT
ms.assetid: 72319846-d02d-49e7-b830-48eb8f5715cb
---


# SharePoint 2013 移动对象模型概述
了解 SharePoint 2013 服务器对象模型和用于为 SharePoint 2013 和 Windows Phone 7.5 开发集成解决方案的 Silverlight 客户端对象模型中的新公共类。
## 移动 Silverlight 的客户端对象模型
<a name="SP15OM_ClientOM"> </a>

本节中的所有类都在 **Microsoft.SharePoint.Client** 命名空间中。除了本节中的 API 之外，"SharePoint 移动性的服务器对象模型"一节中的大部分类和成员在客户端对象模型中也是可调用的。对于以"SP"开头的类，客户端对象模型名称中删除了"SP"。在其他情况下，指定了客户端对象模型名称。除非另行指定，否则成员名称在客户端对象模型中是相同的。
  
    
    

### AlternateUrl 类

表示 Web 应用程序的备用 URL 及其应用到的区域。
  
    
    

```cs

public class AlternateUrl
```


#### 属性

 **Uri**（只读）
  
    
    
获取备用 URL 的 URI。
  
    
    



```cs
public String Uri
```

 **UrlZone**（只读）
  
    
    
获取备用 URL 的区域。
  
    
    



```
public UrlZone UrlZone
```

UrlZone 类是服务器对象模型中的 SPUrlZone 类的客户端对象模型版本。有关该类的详细信息，请参阅 [SharePoint 2010 软件开发工具包 (SDK)](http://msdn.microsoft.com/zh-cn/library/ee557253.aspx).
  
    
    

### AuthenticationCompletedEventArgs 类

提供有关 **AuthenticationCompleted** 事件的数据。
  
    
    

```cs
public sealed class AuthenticationCompletedEventArgs : AsyncCompletedEventArgs

```


#### 构造函数

初始化AuthenticationCompletedEventArgs 类的新实例。
  
    
    

```cs

public AuthenticationCompletedEventArgs(Exception error, bool canceled, HttpStatusCode userState)
```

 **参数**
  
    
    

-  _error_ 在身份验证尝试引发异常时为异常对象。
    
  
-  _canceled_ 在身份验证尝试可能成功或失败前取消该尝试时为 true。
    
  
-  _userState_ 是服务器返回的 HttpStatusCode。
    
  

#### 属性

 **HttpStatusCode**（只读）
  
    
    
获取服务器在身份验证尝试后返回的状态。
  
    
    



```cs
public HttpStatusCode HttpStatusCode
```


### AuthenticationStatus 枚举

指定身份验证尝试的当前状态。
  
    
    

- **NotStarted**
    
  
- **InProgress**
    
  
- **CompletedSuccess**
    
  
- **CompletedException**
    
  

### Authenticator 类

提供在 SharePoint 网站上对用户进行身份验证的方法。
  
    
    

```
public class Authenticator : ICredentials
```


#### 构造函数

初始化该类的新实例。
  
    
    

```cs
public Authenticator()

public Authenticator(Uri uagServerUrl)
```

 **参数**
  
    
    
 _uagServerUrl_ 是统一接入网关 (UAG) 服务器的绝对 URL。
  
    
    



```cs

public Authenticator(string userName, string password)
```

 **参数**
  
    
    
 _userName_ 是凭据的名称。
  
    
    
 _password_ 是凭据的密码。
  
    
    



```cs
public Authenticator(string userName, string password, string domain)
```

 **参数**
  
    
    
 _userName_ 是凭据的名称。
  
    
    
 _password_ 是凭据的密码。
  
    
    
 _domain_ 是已验证凭据的域（通常是当前用户的域）或计算机的名称。
  
    
    



```cs
public Authenticator(string userName, string password, Uri uagServerUrl)
```

 **参数**
  
    
    
 _userName_ 是凭据的名称。
  
    
    
 _password_ 是凭据的密码。
  
    
    
 _uagServerUrl_ 是统一接入网关 (UAG) 服务器的绝对 URL。
  
    
    



```cs
public Authenticator(string userName, string password, string domain, Uri uagServerUrl)
```

 **参数**
  
    
    
 _userName_ 是凭据的名称。
  
    
    
 _password_ 是凭据的密码。
  
    
    
 _domain_ 是已验证凭据的域（通常是当前用户的域）或计算机的名称。
  
    
    
 _uagServerUrl_ 是统一接入网关 (UAG) 服务器的绝对 URL。
  
    
    

#### 方法

 **ClearAllApplicationSettings**
  
    
    
从缓存清除所有 Cookie、凭据和 UAG 设置。
  
    
    



```cs
public static void ClearAllApplicationSettings
```

 **ClearAllCookies**
  
    
    
清除存储的所有 Cookie，并将所有 **Authenticator** 对象的 **Status** 属性设置为 **NotStarted**。
  
    
    



```cs
public static void ClearAllCookies()
```

 **ClearAllCredentials**
  
    
    
从缓存清除所有 Cookie，并将所有 **Authenticator** 对象的 **Status** 属性设置为 **NotStarted**。
  
    
    



```cs
public static void ClearAllCredentials()
```

 **GetCredential**
  
    
    
获取指定 URI 的凭据对象和身份验证类型。
  
    
    



```
public NetworkCredential GetCredential(Uri uri, string authType)
```

 **参数**
  
    
    

-  _uri_ 是客户端为其提供身份验证的 URI（包括端口）。
    
  
-  _authType_ 是请求的身份验证的类型。
    
  
此方法仅用于匿名身份验证。如果  _authType_ 不是"Basic"，则返回一个空对象。有关 **NetworkCredential** 类的详细信息，请参阅 [NetworkCredential 类](http://msdn.microsoft.com/zh-cn/library/system.net.networkcredential.aspx)。
  
    
    
 **IsRequestUnauthorized**
  
    
    
如果身份验证请求因无效的 Cookie 或凭据而失败，则返回 true。
  
    
    



```cs
public static bool IsRequestUnauthorized(ClientRequestFailedEventArgs failedEventArgs)
```


#### 属性

 **AllowSmartRouting**
  
    
    
获取或设置是否启用智能传送的指示符。
  
    
    



```
public bool AllowSmartRouting
```

启用智能传送时， **Authenticator** 对象尝试连接到运行 SharePoint 的服务器和 UAG 服务器，并使用先响应的服务器作为其信道。如果没有 UAG 服务器，则忽略此属性。默认值为 **true**。如果设置为 **false**，则始终使用 UAG 服务器。
  
    
    
 **AuthenticatorMode**
  
    
    
获取或设置身份验证模式。
  
    
    



```cs
public ClientAuthenticationMode AuthenticationMode
```

有关 **ClientAuthenticationMode** 枚举的详细信息，请参阅本文档后面的内容。
  
    
    
 **CookieCachingEnabled**
  
    
    
获取或设置是否缓存 Cookie 的指示符。
  
    
    



```
public bool CookieCachingEnabled
```

如果启用 Cookie 的缓存，请考虑 Cookie 在某个时候过期。如果它们在调用 **ExecuteQueryAsync** 时过期，则调用失败并运行失败回调。因此，如果将此属性设置为 true，则必须将代码添加到在情况发生时清除缓存的失败回调。例如， `execQueryArgs` 的类型为 **ExecuteQueryAsync** 的失败回调中传递的 **ClientRequestFailedEventArgs**。
  
    
    



```cs
if (Authenticator.IsRequestUnauthorized(execQueryArgs))
{
    (sender as Authenticator).ClearCookies();
}
```

 **CredentialCachingEnabled**
  
    
    
获取或设置是否缓存凭据的指示符。
  
    
    



```cs

public bool CredentialCachingEnabled
```

 **Domain**
  
    
    
获取或设置凭据的域（通常是当前用户的域）或计算机。
  
    
    



```cs
public string Domain
```

此属性设置为一个新值时， **Status** 属性设置为 NotStarted。
  
    
    
 **NavigateBackAfterAuthentication**
  
    
    
获取或设置是否应使用户从登录页面导航回前一页的指示符。
  
    
    



```cs
public bool NavigateBackAfterAuthentication
```

 **Password**
  
    
    
获取或设置凭据的密码。
  
    
    



```cs
public string Password
```

此属性设置为一个新值时， **Status** 属性设置为 **NotStarted**。
  
    
    
 **PromptOnFailure**
  
    
    
获取或设置是否应在初始身份验证失败时提示用户输入名称和密码的指示符。
  
    
    



```cs
public bool PromptOnFailure
```

 **Status**（只读）
  
    
    
获取身份验证的尝试的状态。
  
    
    



```cs
public AuthenticationStatus Status
```

有关 **AuthenticationStatus** 类的信息，请参阅本文档之前的部分。
  
    
    
 **UagServerUrl**
  
    
    
获取或设置 UAG 服务器的 URL。
  
    
    



```cs
public Uri UagServerUrl
```

 **UserName**
  
    
    
获取或设置凭据的用户名。
  
    
    



```cs
public string UserName
```

此属性设置为一个新值时， **Status** 属性设置为 **NotStarted**。
  
    
    

#### 事件

 **AuthenticationCompleted**
  
    
    
在身份验证尝试完成时激发，而无论该尝试是否成功。
  
    
    



```cs
public event EventHandler<AuthenticationCompletedEventArgs> AuthenticationCompleted;
```


### ClientAuthenticationMode 枚举

为 **Authenticator** 对象指定身份验证模式。这是已向其添加新值 **BrowserBasedAuthentication** 的现有枚举。
  
    
    


|**默认**||
|:-----|:-----|
|**FormsAuthentication** <br/> |表示基于表单的身份验证模式  <br/> |
|**Anonymous** <br/> |表示匿名访问模式  <br/> |
|**BrowserBasedAuthentication** <br/> |表示基于 Microsoft Office 表单的身份验证 (MSOFBA) 模式  <br/> |
   

### ODataAuthenticator 类

提供在 SharePoint 网站上对用户进行身份验证的方法。
  
    
    

```cs
public class ODataAuthenticator : Authenticator
```


#### 构造函数

该构造函数与父类构造函数相同。有关详细信息，请参阅本文档前面的"Authenticator 类"。
  
    
    

#### 方法

 **Authenticate**
  
    
    
对指定网站的用户进行身份验证。
  
    
    



```cs
public new void Authenticate(Uri serverUrl)
```

使用  `new` 关键字，因为父类包含具有相同名称的内部方法。
  
    
    

#### 属性

 **CookieContainer**（只读）
  
    
    
使用对网站的请求的 Cookie 获取容器。
  
    
    



```cs
public new CookieContainer CookieContainer
```

使用  `new` 关键字，因为父类包含具有相同名称的内部方法。
  
    
    
 **ResolvedUrl**（只读）
  
    
    
获取使用 **ODataAuthenticator** 时用于对运行 SharePoint 的服务器通信的 URL。这可能是 UAG 服务器上公布的 URL（如果 **AllowSmartRouting** 属性为 true）或 SharePoint intranet URL（如果调用 **Authenticate** 方法时首先到达此 URL）。
  
    
    



```cs
public Uri ResolvedUrl
```


### ServerSettings 类

提供用于获取包含网站的 Web 应用程序的备用 URL 的方法。
  
    
    

```cs
public static class ServerSettings
```


#### 方法

 **GetAlternateUrls**
  
    
    
获取指定网站的备用 URL。
  
    
    



```cs
public static ClientObjectList<AlternateUrl> GetAlternateUrls(ClientRuntimeContext context)
```

 **参数**
  
    
    
 _context_ 是表示当前客户端上下文的对象。
  
    
    
有关 **AlternateUrl** 类的信息，请参阅本文档之前的部分。
  
    
    

## SharePoint 移动性的服务器对象模型
<a name="SP15OM_ServerOM"> </a>

本节中的所有类都在 **Microsoft.SharePoint** 命名空间中。 除非另行指定，否则这些类在客户端对象模型中也可用。对于以"SP"开头的类，客户端对象模型名称中删除了"SP"。在其他情况下，指定了客户端对象模型名称。除非另行指定，否则成员名称在客户端对象模型中是相同的。
  
    
    

### GeolocationFieldControl 类

（在客户端对象模型中不可用）。 
  
    
    
控制 **SPFieldGeolocation** 字段的呈现。此类型的对象用作 **SPFieldGeolocation** 对象的 **FieldRenderingControl** 属性值。
  
    
    



```cs
public class GeolocationFieldControl : BaseFieldControl
```

关于此类，另请注意有两个呈现模板，一个用于"显示"模式，另一个用于"新建"和"编辑"模式。它们在文件 %SHAREPOINTROOT%\\TEMPLATE\\ControlTemplates\\DefaultTemplates.ascx 中定义。
  
    
    

#### 字段

以下内容用于在"新建"和"编辑"模式中呈现字段。
  
    
    

```cs
protected TextBox m_latitudeBox;
protected TextBox m_longitudeBox;
protected Label m_longitudeLabel;
protected Label m_latitudeLabel;
```


#### 方法

没有随此类一起引入任何非派生公共属性。存在一些派生方法的标准重写，如下表所示。
  
    
    


|**方法**|**此重写…**|
|:-----|:-----|
|CreateChildControls  <br/> |创建包含用于"显示"模式的 JavaScript 地图控件的子控件。  <br/> |
|Focus  <br/> |将焦点移到经度文本框子控件。  <br/> |
|OnPreRender  <br/> |调用基方法。  <br/> |
|Validate  <br/> |验证用户界面 (UI) 中显示的经度和纬度值。这不验证基础 **SPFieldGeolocatonValue** 对象的 **Longitude** 和 **Latitude** 属性，如果用户在 UI 中更改了一个或多个这些值且尚未保存更改，则这些值将有所不同。 <br/> |
   

#### 属性

没有随此类一起引入任何非派生公共属性。存在一些派生属性的标准重写，如下表所示。
  
    
    


|**属性**|**此重写…**|
|:-----|:-----|
|CssClass  <br/> |就像父实现一样行事。  <br/> |
|DefaultTemplateName  <br/> |返回"GeolocationField"  <br/> |
|DisplayTemplateName  <br/> |返回"GeolocationDisplayField"  <br/> |
|值  <br/> |获取或设置通过使用 **SPFieldGeolocationValue** 对象呈现的值。 <br/> |
   

### SPFieldGeolocation 类

表示保留由经度、纬度和可能的海拔定义的地球上的位置的字段（列表）。
  
    
    

```cs

public class SPFieldGeolocation : SPField
```

对于此类型， **Geolocation** 字段类型在 % _SHAREPOINTROOT%_\\TEMPLATE\\XML\\fldtypes.xml 中定义。
  
    
    

#### 构造函数（重载）

初始化 **SPFieldGeolocation** 类的新实例。
  
    
    

```cs
public SPFieldGeolocation(SPFieldCollection fields, string fieldName)
public SPFieldGeolocation(SPFieldCollection fields, string fieldName, string displayName)
```

 **参数**
  
    
    

-  _fields_ 是新字段类型对象添加到的字段类型的集合。
    
  
-  _fieldName_ 是新字段类型的内部名称。
    
  
-  _displayName_ 是新字段类型的友好名称。
    
  

#### 方法

 **GetFieldValueForClientRender**
  
    
    
获取字段的值以便其可在客户端上呈现。
  
    
    



```cs

public override object GetFieldValueForClientRender(SPItem item, SPControlMode mode)
```

参数
  
    
    

-  _item_ 是当前列表项。
    
  
-  _mode_ 是当前呈现模式，如"新建"、"编辑"或"显示"。
    
  
 **GetJsonClientFormFieldSchema**
  
    
    
获取作为 JavaScript 对象表示法 (JSON) 的字段架构。
  
    
    



```cs
public override Dictionary<string, object> GetJsonClientFormFieldSchema(SPControlMode mode)
```

 **参数**
  
    
    
 _mode_ 是当前呈现模式，如"新建"、"编辑"或"显示"。
  
    
    
 **ValidateAndParseValue**
  
    
    
验证指定列表项不为空，然后验证字符串的结构符合开放地理空间信息联盟 (OGC) 标准，并作为可转换为 **SPFieldGeolocationValue** 类型的对象返回。
  
    
    



```cs
public override object ValidateAndParseValue(SPListItem item, string value)
```

 **参数**
  
    
    

-  _item_ 是要更新值的列表项。
    
  
-  _value_ 是地理位置值的字符串表示。
    
  
以下方法是 SharePoint 2010 中的继承方法的标准重写。下表中是此类的特定信息。
  
    
    


|**方法**|**此重写…**|
|:-----|:-----|
|GetFieldValue(String s)  <br/> |返回指定值作为可转换为 SPFieldGeolocationValue 的对象。  <br/> |
|GetFieldValueAsText(Object o)  <br/> |包装 GetValidatedString。  <br/> |
|GetValidatedString(Object o)  <br/> |验证指定值的结构符合开放地理空间信息联盟 (OGC) 标准，并作为字符串返回。  <br/> |
   

#### 属性

 **JSLink**
  
    
    
获取或设置呈现 **SPFieldGeolocation** 类型的字段的 JavaScript 文件。
  
    
    

> **注释**
> 调查列表或事件列表不支持 JSLink 属性。SharePoint 日历是事件列表。 
  
    
    




```cs
public override string JSLink
```

默认值是"clienttemplates.js|Geolocationfieldtemplate.js|sp.map.js"。
  
    
    
 **FieldRenderingMobileWebControl**
  
    
    
获取呈现字段的 **SPMobileGeolocationField** 对象。
  
    
    



```cs
public override SPMobileBaseFieldControl FieldRenderingMobileControl
```

此属性替换过时的 **FieldRenderingMobileControl**。
  
    
    
其他属性是 SharePoint 2010 中的继承属性的标准重写。下表中是此类的特定信息。
  
    
    


|**属性**|**该重写…**|
|:-----|:-----|
|FieldValueType  <br/> |返回 **typeof(SPFieldGeolocationValue)**。  <br/> |
|FieldRenderingControl  <br/> |返回 **GeolocationFieldControl** 对象。 <br/> |
|Filterable  <br/> |返回 **false**。  <br/> |
|Sortable  <br/> |返回 **false**。  <br/> |
|[已过时]  <br/> FieldRenderingMobileControl  <br/> |返回 **SPMobileGeolocationField** 对象。 <br/> |
   

### SPFieldGeolocationValue 类

也表示由经度、纬度和可能的海拔定义的地球上的位置。
  
    
    

```cs
public class SPFieldGeolocationValue : SPFieldGeographyValue
```


#### 构造函数（重载）

初始化 **SPFieldGeolocationValue** 类的新实例。
  
    
    

```cs
public SPFieldGeolocationValue()
public SPFieldGeolocationValue(string fieldValue)
public SPFieldGeolocationValue(double latitude, double longitude)
public SPFieldGeolocationValue(double latitude, double longitude, double altitude, double measure)

```

 **参数**
  
    
    

-  _fieldValue_ 是采用以下熟知文本 (WKT) 格式之一的字符串：
    
  - "点（ _经度_ _纬度_）"，其中， _经度_和 _纬度_是一个或多个数字的字符串，可选择包括一个句点（看做一个小点的），并可选择以连字号开始（看做负号）。
    
  
  - "点（ _经度_ _纬度_ _海拔_ _度量值_）"，其中， _经度_、 _纬度_、 _海拔_和 _度量值_是一个或多个数字的字符串，可选择包括一个句点（看做一个小点的），并可选择以连字号开始（看做负号）。
    
  
-  _latitude_ 表示纬度，必须在 -90.0 到 90.0 之间。
    
  
-  _longitude_ 表示经度，必须在 -180.0 到 180.0 之间。
    
  
-  _altitude_ 表示海拔。
    
  
-  _measure_ 是该点的备用指定。有关详细信息，请参阅本部分后面的 **Measure** 属性。
    
  

#### 方法

 **ToString**
  
    
    
根据是否已向 **Altitude** 或 **Measure** 属性分配非空值，此重写返回以下各项之一。
  
    
    

- 如果未向"海拔"和"度量值"分配非空值：
    
    "点（ _经度_ _纬度_）"，其中， _经度_和 _纬度_是一个或多个数字的字符串，可选择包括一个句点（看做一个小点的），并可选择以连字号开始（看做负号）。
    
  
- 否则（至少向一个 **Altitude** 或 **Measure** 分配了非空值）：
    
    "点（经度 纬度 海拔 度量值）"，其中， _经度_、 _纬度_、 _海拔_和 _度量值_是一个或多个数字的字符串，可选择包括一个句点（看做一个小点的），并可选择以连字号开始（看做负号）。 如果未向 **Altitude** 或 **Measure** 分配非空值，则在 **WellKnownText** 属性的值中报告为"0"。但反之则不然：如果 **Altitude** 或 **Measure** 报告为 0，则这可能是因为从未分配非空值，但也可能是因为向其分配 0。
    
  



```cs

public override string ToString()
```

 **ToWellKnownText**
  
    
    
包装 **ToString**。
  
    
    



```cs
public string ToWellKnownText()
```


#### 属性

 **Altitude**
  
    
    
获取或设置位置的海拔。可选择使用此属性，并且假设的测量单位（例如，米）和零点（例如，海平面或地心）由用户定义 Use of this property is optional and the assumed unit-of-measure (for example, meters) and zero-point (for example, sea level or center-of-the-earth) is user-defined.
  
    
    



```cs
public double Altitude
```

 **Latitude**
  
    
    
获取或设置位置的纬度。
  
    
    



```cs
public double Latitude
```

该值必须在 -90.0 到 90.0 之间。
  
    
    
 **Longitude**
  
    
    
获取或设置位置的经度。
  
    
    



```cs
public double Longitude
```

该值必须在 -180.0 到 180.0 之间。
  
    
    
 **Measure**
  
    
    
获取或设置用户定义的位置点的备用指定。例如，如果该点沿着带有里程碑标记的高速公路，则此属性可用于保留最接近该店的里程碑数。如果该点位于具有编号的露营营地的露营区，则此属性可用于保留最近的露营营地的数量。属性的语义完全由用户确定，并且其使用是可选的。
  
    
    



```cs
public double Measure
```


### SPFieldType 枚举

已向此枚举添加新值：
  
    
    

```cs
Geolocation
```


### SPPhoneNotificationContent 类

表示电话通知的内容的类的基类。派生类必须声明一个或多个用于保留内容的字段或属性，并且必须实现 **PreparePayload** 方法以将内容转换为字节数组。
  
    
    

```cs
public abstract class SPPhoneNotificationContent
```


#### 方法

 **PreparePayload**
  
    
    
在派生类中实现时，将内容转换为字节数组，并通过线路发送到通知服务。不存在默认实现，因此派生类必须实现此方法。
  
    
    



```cs
protected internal abstract byte[] PreparePayload();
```


#### 属性

 **NotificationType**（只读）
  
    
    
获取内容针对的通知的类型（例如，瓷砖或吐司）。
  
    
    



```cs
public SPPhoneNotificationType NotificationType

```

有关 **SPPhoneNotificationType** 的信息，请参阅本文档后面的内容。
  
    
    
 **SubscriberType**（只读）
  
    
    
获取订阅者的设备的类型，如 Windows Phone。
  
    
    



```cs

public SPPhoneNotificationSubscriberType SubscriberType
```

有关 **SPPhoneNotificationSubscriberType** 的信息，请参阅本文档后面的内容。
  
    
    

### SPPhoneNotificationResponse 类

表示发送通知的尝试的结果。
  
    
    

```cs
public class SPPhoneNotificationResponse
```


#### 方法

 **Create**
  
    
    
创建 **SPPhoneNotificationResponse** 对象。
  
    
    



```cs
public static SPPhoneNotificationResponse
Create(SPPhoneNotificationSubscriberType subscriberType, 
SPPhoneNotificationType notificationType, HttpWebResponse response)
```

 **参数**
  
    
    

-  _subscriberType_ 表示设备，如 Windows Phone 7.5。
    
  
-  _notificationType_ 是通知的类型，如吐司或瓷砖。
    
  
-  _response_ 是服务器生成的 HTTP 响应对象。
    
  
有关 **SPPhoneNotificationSubscriberType** 和 **SPPhoneNotificationType** 的详细信息，请参阅本文档后面的内容。
  
    
    

#### 属性

 **NotificationType**（只读）
  
    
    
获取通知的类型（例如，吐司或瓷砖）。
  
    
    



```cs

public SPPhoneNotificationType NotificationType
```

有关 SPPhoneNotificationType 的信息，请参阅本文档后面的内容。
  
    
    
 **ServiceToken**（只读）
  
    
    
获取通知中使用的通知服务的标记。
  
    
    



```cs
public string ServiceToken
```

 **StatusCode**（只读）
  
    
    
获取 HTTP 状态代码。 **HttpStatusCode** 值的字符串的版本。
  
    
    



```cs
public string StatusCode
```

 **SubscriberType**
  
    
    
获取或设置通知发送到的设备的类型。
  
    
    



```cs
public SPPhoneNotificationSubscriberType SubscriberType
```

有关 **SPPhoneNotificationSubscriberType** 的信息，请参阅本文档后面的内容。
  
    
    
 **TimeStamp**（只读）
  
    
    
通知的 UTC 时间。
  
    
    



```cs
public DateTime Timestamp
```


### SPPhoneNotificationSubscriber 类

表示服务器端 SharePoint 应用程序发出的通知的订阅者的类的基类。
  
    
    

```cs
public abstract class SPPhoneNotificationSubscriber
```


#### 方法

通知
  
    
    
向订阅者发送指定通知内容并进行错误检查。
  
    
    



```cs
public SPPhoneNotificationResponse Notify(SPPhoneNotificationContent notificationContent)
```

 **参数**
  
    
    
 _notificationContent_ 是有关触发通知的事件的信息。
  
    
    
此方法不可重写。它包装 **NotifyInternal** 抽象方法并确保在调用 **NotifyInternal** 时进行特定的错误检查。
  
    
    
有关 **SPPhoneNotificationContent** 和 **SPPhoneNotificationResponse** 类的详细信息，请参阅本文档前面的内容。
  
    
    
 **NotifyInternal**
  
    
    
在派生类中重写时，向订阅者发送指定通知内容。
  
    
    



```cs
protected abstract SPPhoneNotificationResponse NotifyInternal(SPPhoneNotificationContent notificationContent);
```

 **参数**
  
    
    
 _notificationContent_ 是有关触发通知的事件的信息。
  
    
    
有关 **SPPhoneNotificationContent** 和 **SPPhoneNotificationResponse** 类的详细信息，请参阅本文档前面的内容。
  
    
    
 **ToString**
  
    
    
作为字符串返回对象的所选属性。
  
    
    



```cs
public override string ToString()
```

默认实现包括 **ParentWeb**、 **ApplicationTag** 和 **DeviceAppInstanceId** 属性。
  
    
    
更新
  
    
    
将（可能已更改的） **SPPhoneNotificationSubscriber** 对象保存到网站的 Subscriber Store。
  
    
    



```cs
public void Update()
```

 **ValidateSubscriberProperties**
  
    
    
在派生类中实现时，验证所选对象属性。
  
    
    



```cs
protected abstract void ValidateSubscriberProperties();
```


#### 属性

 **CustomArgs**
  
    
    
获取或设置表示通知订阅的状态的自定义参数字符串。应用程序逻辑可使用此字符串区分不同种类的通知的通知订阅者。
  
    
    



```cs
public string CustomArgs
```

 **DeviceAppInstanceId**（只读）
  
    
    
获取电话或其他移动设备上应用程序的特定实例的 ID。
  
    
    



```cs
public Guid DeviceAppInstanceId
```

 **LastModifiedTimeStamp**（只读）
  
    
    
获取上次修改订阅者的日期和时间。
  
    
    



```cs
public DateTime LastModifiedTimeStamp
```

 **RegistrationTimeStamp**（只读）
  
    
    
获取订阅者注册通知的日期和时间。
  
    
    



```cs
public DateTime RegistrationTimeStamp
```

 **ServiceToken**
  
    
    
获取或设置通知服务需要的发送通道信息，如通道 URI。
  
    
    



```cs
public string ServiceToken
```

 **SubscriberType**（只读）
  
    
    
获取设备的类型，如 Windows Phone 7。
  
    
    



```cs
public SPPhoneNotificationSubscriberType SubscriberType
```

有关 **SPPhoneNotificationSubscriberType** 类的信息，请参阅本文档后面的内容。
  
    
    
 **User**（只读）
  
    
    
获取注册了通知的用户。
  
    
    



```cs
public SPUser User
```


### SPPhoneNotificationSubscriberCollection 类

通知订阅者的集合。该集合对象采用 **Int32** 索引器。
  
    
    

```cs
public sealed class SPPhoneNotificationSubscriberCollection : SPBaseCollection
```


#### 属性

 **Count**
  
    
    
获取集合中项的数目。
  
    
    



```cs
public override int Count
```


### SPPhoneNotificationSubscriberType 枚举

指定可接收消息的设备的类型。
  
    
    


|**通知**|**设备**|
|:-----|:-----|
|||
|**WP7** <br/> |Windows Phone 7.5  <br/> |
|**Custom** <br/> |Windows Phone 7.5 以外的任何设备  <br/> |
   

### SPPhoneNotificationType 枚举

指定通知的类型。
  
    
    


|||
|:-----|:-----|
|**None** <br/> ||
|**Tile** <br/> ||
|**Toast** <br/> ||
|**Raw** <br/> ||
   

### SPWeb 类

已将以下成员添加到此类中。
  
    
    

#### 方法

 **DoesPhoneNotificationSubscriberExist**
  
    
    
获取一个值，指示当前用户是否为指定应用程序的特定实例的订阅者。
  
    
    



```cs
public bool DoesPhoneNotificationSubscriberExist(Guid deviceAppInstanceId)
```

 **GetPhoneNotificationSubscriber**
  
    
    
从网站的 Subscription Store 通知列表获取指定应用程序的通知订阅者和电话 ID。
  
    
    



```cs
public SPPhoneNotificationSubscriber GetPhoneNotificationSubscriber(Guid deviceAppInstanceId)
```

 **参数**
  
    
    
 _deviceAppInstanceId_ 是特定电话或设备上的应用程序的实例的 ID。
  
    
    
有关 **SPPhoneNotificationSubscriber** 类的信息，请参阅本文档前面的内容。
  
    
    
 **GetPhoneNotificationSubscribers**（重载）
  
    
    
从网站的 Subscription Store 列表获取通知订阅者的集合，可选择对电话应用程序的 ID 进行筛选，还可能对以下各项之一进行筛选：用户或一些自定义参数。
  
    
    



```cs
public SPPhoneNotificationSubscriberCollection GetPhoneNotificationSubscribers(string customArgs)
```


> **注释**
> 客户端对象模型名称为 **GetPhoneNotificationSubscribersByArgs**。 
  
    
    




```cs
public SPPhoneNotificationSubscriberCollection GetPhoneNotificationSubscribers(string user)

```


> **注释**
> 客户端对象模型名称为 **GetPhoneNotificationSubscribersByUser**。 
  
    
    

 **参数**
  
    
    

-  _customArgs_ 是一些启用了通知的应用程序可能使用的附加自定义信息。
    
  
-  _user_ 是注册了通知的用户。
    
  
有关 **SPPhoneNotificationSubscriberCollection** 类的信息，请参阅本文档前面的内容。
  
    
    
 **RegisterPhoneNotificationSubscriber**
  
    
    
在电话上注册电话应用程序以接收通知。
  
    
    



```cs

public SPPhoneNotificationSubscriber RegisterPhoneNotificationSubscriber(SPPhoneNotificationSubscriberType subscriberType, Guid deviceAppInstanceId, string serviceToken)
```

 **参数**
  
    
    

-  _subscriberType_ 表示设备类型，如 Windows Phone 7。
    
  
-  _deviceAppInstanceId_ 是特定电话或设备上的应用程序的实例的 ID。
    
  
-  _serviceToken_ 是向订阅者发送通知的通知服务使用的标记。
    
  
有关 **SPPhoneNotificationSubscriberType** 的信息，请参阅本文档前面的内容。
  
    
    
 **UnregisterPhoneNotificationSubscriber**
  
    
    
在电话上注销电话应用程序阻止接收通知。
  
    
    



```cs
public void UnregisterPhoneNotificationSubscriber(Guid deviceAppInstanceId)
```

 **参数**
  
    
    
 _deviceAppInstanceId_ 是特定电话或设备上的应用程序的实例的 ID。
  
    
    

#### 属性

 **PhoneNotificationSubscribers**（只读）
  
    
    
在网站的 Subscriber Store 中获取所有电话通知订阅者的集合。
  
    
    



```cs
public SPPhoneNotificationSubscriberCollection PhoneNotificationSubscribers
```

有关 **SPPhoneNotificationSubscriberCollection** 类的信息，请参阅本文档前面的内容。
  
    
    

### WP7NotificationTileContent 类

表示瓷砖通知的内容。
  
    
    

```cs
public sealed class WP7NotificationTileContent : SPPhoneNotificationContent
```


#### 构造函数

初始化 WP7NotificationTileContent 类的新实例。
  
    
    

```cs
public WP7NotificationTileContent()
```


#### 方法

 **PreparePayload**
  
    
    
将内容转换为 **Byte** 数组，并通过线路发送到通知服务。
  
    
    



```cs
protected internal override byte[] PreparePayload();
```


#### 属性

 **Count**
  
    
    
获取或设置通知的计数。必须在 -1 到 99 之间（含这两个值）。
  
    
    



```cs
public int Count
```

将属性设置为 -1 将不会更改瓷砖的计数。
  
    
    
 **Title**
  
    
    
获取或设置瓷砖通知的标题。
  
    
    



```cs
public string Title
```

 **BackgroundImagePath**
  
    
    
获取或设置瓷砖的背景图像的路径。
  
    
    



```cs
public string BackgroundImagePath
```

 **BackBackgroundImagePath**
  
    
    
获取或设置翻转瓷砖的背面的背景图像。
  
    
    



```cs
public string BackBackgroundImagePath
```

 **BackContent**
  
    
    
获取或设置翻转瓷砖的背面的内容。
  
    
    



```cs
public string BackContent
```

 **BackTitle**
  
    
    
获取或设置翻转瓷砖的背面上显示的标题。
  
    
    



```cs
public string BackTitle
```

 **TileId**
  
    
    
获取或设置瓷砖的 ID。
  
    
    



```cs
public string TileId
```


### WP7NotificationToastContent 类

表示吐司通知的内容。
  
    
    

```cs
public sealed class WP7NotificationToastContent : SPPhoneNotificationContent
```


#### 构造函数

初始化 WP7NotificationToastContent 类的新实例。
  
    
    

```cs
public WP7NotificationToastContent()
```


#### 方法

 **PreparePayload**
  
    
    
将内容转换为 **Byte** 数组，并通过线路发送到通知服务。
  
    
    



```cs
protected internal override byte[] PreparePayload();
```


#### 属性

 **Message**
  
    
    
获取或设置吐司通知的消息。
  
    
    



```cs
public string Message
```

 **Title**
  
    
    
获取或设置吐司通知的标题。
  
    
    



```cs
public string Title
```

 **Param**
  
    
    
获取或设置用户响应吐司通知时传递给接收应用程序的自定义设置数据。
  
    
    



```cs
public string Param
```

此属性可用于将 URL 或一组名称值对等信息传递给接收应用程序。
  
    
    

### WP7NotificationRawContent 类

表示原生通知的内容。
  
    
    

```cs
public sealed class WP7NotificationRawContent : SPPhoneNotificationContent
```


#### 构造函数

初始化 WP7NotificationRawContent 类的新实例。
  
    
    

```cs
public WP7NotificationRawContent()
```


#### 方法

 **PreparePayload**
  
    
    
将内容转换为字节数组，并通过线路发送到通知服务。
  
    
    



```cs
protected internal override byte[] PreparePayload();
```


#### 属性

 **Message**
  
    
    
获取或设置原生通知的消息。
  
    
    



```cs
public string Message
```


### WP7PhoneNotificationResponse 类

表示向 Windows Phone 7 订阅者发送通知的尝试的结果。
  
    
    

```cs
public WP7PhoneNotificationResponse(SPPhoneNotificationType notificationType, HttpWebResponse response)
```

 **参数**
  
    
    

-  _notificationType_ 是通知的类型，如吐司或瓷砖。
    
  
-  _response_ 是服务器生成的 HTTP 响应对象。
    
  
有关 **SPPhoneNotificationType** 的详细信息，请参阅本文档前面的内容。
  
    
    

#### 属性

 **NotificationStatus**（只读）
  
    
    
获取通知状态，例如，成功或失败。
  
    
    



```cs
public string NotificationStatus
```

 **DeviceConnectionStatus**（只读）
  
    
    
获取通知时设备的状态
  
    
    



```cs
public string DeviceConnectionStatus
```

 **SubscriptionStatus**（只读）
  
    
    
通知时设备的订阅状态。
  
    
    



```cs
public string SubscriptionStatus
```

 **MessageId**（只读）
  
    
    
获取通知中发送的消息的 ID。
  
    
    



```
public string MessageId
```


## 其他资源
<a name="SP15MobileOM_addlresources"> </a>


-  [构建访问 SharePoint 2013 的 Windows Phone 应用程序](build-windows-phone-apps-that-access-sharepoint-2013.md)
    
  
-  [如何：在针对 Windows Phone 的 SharePoint 2013 应用程序中配置和使用推送通知](how-to-configure-and-use-push-notifications-in-sharepoint-2013-apps-for-windows.md)
    
  
-  [集成 SharePoint 2013 中的位置和映射功能](integrating-location-and-map-functionality-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 移动客户端身份验证对象模型概述](overview-of-the-sharepoint-2013-mobile-client-authentication-object-model.md)
    
  

