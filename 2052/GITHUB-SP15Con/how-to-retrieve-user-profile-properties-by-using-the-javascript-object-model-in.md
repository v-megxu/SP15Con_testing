---
title: 如何：在 SharePoint 2013 中使用 JavaScript 对象模型检索用户配置文件属性
ms.prod: SHAREPOINT
ms.assetid: c6e1ca38-134f-428a-8d21-b8b2615b161b
---


# 如何：在 SharePoint 2013 中使用 JavaScript 对象模型检索用户配置文件属性
了解如何通过 SharePoint 2013 JavaScript 对象模型以编程模式检索用户属性和用户配置文件属性。
## 什么是 SharePoint 2013 中的用户属性和用户配置文件属性？
<a name="bkmk_WhatIs"> </a>

用户属性和用户配置文件属性提供有关 SharePoint 用户的信息，如显示名称、电子邮件、职位及其他业务和个人信息。在客户端 API 中，您可以从  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) 对象及其 [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) 属性访问这些属性。 [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) 属性包含所有用户配置文件属性，但 [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) 对象包含更容易访问的常用属性（例如， [accountName](http://msdn.microsoft.com/library/ad1551bf-dad8-d54e-880a-8a4388fad44e%28Office.15%29.aspx)、 [displayName](http://msdn.microsoft.com/library/ffc35ed6-5f3e-c86d-6931-97ff9d825a8b%28Office.15%29.aspx) 和 [email](http://msdn.microsoft.com/library/74302f73-aaf6-920b-0605-812b0dbf4568%28Office.15%29.aspx)）。
  
    
    
 [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) 对象包含以下方法，您可以使用这些方法来通过 JavaScript 对象模型检索用户属性和用户配置文件属性：
  
    
    

-  [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) 方法和 [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) 方法返回 [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) 对象。
    
  
-  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) 方法和 [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) 方法返回您指定的用户配置文件属性值。
    
  
来自客户端 API 的用户配置文件属性是只读的（配置文件图片除外，您可以使用  [PeopleManager.setMyProfilePicture](http://msdn.microsoft.com/library/a4f8d745-f211-e750-4fd0-047091804683%28Office.15%29.aspx) 方法对该图片进行更改）。如果您希望更改其他用户配置文件属性，则必须使用服务器对象模型。有关使用用户配置文件的详细信息，请参阅 [在 SharePoint 2013 中使用用户配置文件](work-with-user-profiles-in-sharepoint-2013.md)。
  
    
    

> **注释**
> 与服务器端版本不同，客户端  [UserProfile](http://msdn.microsoft.com/library/f8c4a219-fbaa-2e50-1bd5-fdc80051b33d%28Office.15%29.aspx) 对象不包含所有的用户属性。但是，客户端版本确实提供了为当前用户创建个人网站的方法。若要检索它，请使用 [ProfileLoader.getUserProfile](http://msdn.microsoft.com/library/8e30e811-5da1-b6d0-a8b5-befea9b22496%28Office.15%29.aspx) 方法。
  
    
    


## 设置开发环境以使用 SharePoint 2013 JavaScript 对象模型检索用户属性的必备组件
<a name="bk_Prereqs"> </a>

若要创建使用 JavaScript 对象模型检索用户属性的应用程序页，您将需要：
  
    
    

- 为当前用户和目标用户创建有配置文件的 SharePoint Server 2013
    
  
- Visual Studio 2008
    
  
- Visual Studio 2013 Office 开发人员工具
    
  
- 访问当前用户的 User Profile Service 应用程序的"完全控制"连接权限
    
  

## 在 Visual Studio 2008 中创建应用程序页
<a name="bk_CreateAppPage"> </a>


1. 在运行 SharePoint Server 2013 的服务器上，打开 Visual Studio 并选择"文件"、"新建"和"项目"。
    
  
2. 在"新建项目"对话框中，从对话框的顶部下拉列表中选择".NET Framework 4.5"。
    
  
3. 在"模版"列表中，展开"Office/SharePoint"，选择"SharePoint 解决方案"类别，然后选择"SharePoint 2013 项目"模板。
    
  
4. 将项目命名为 UserProfilesJSOM，然后选择"确定"按钮。
    
  
5. 在"SharePoint 自定义向导"对话框中，输入目标 SharePoint 网站的 URL，选择"部署为场解决方案"，然后选择"完成"按钮。
    
  
6. 在"解决方案资源管理器"中，打开 UserProfilesJSOM 项目的快捷菜单，然后添加"SharePoint 的'Layouts'映射文件夹"。
    
  
7. 在"Layouts"文件夹中，打开 UserProfilesJSOM 文件夹的快捷菜单，然后添加一个名为UserProfiles.aspx 的新 SharePoint 应用程序页。
    
    > **注释**
      > 本文的代码示例定义了页面标记中的自定义代码，但是没有使用 Visual Studio 为该页面创建的代码隐藏类文件。 
8. 打开 UserProfiles.aspx 页的快捷菜单，然后选择"设置为启动项。
    
  
9. 在 UserProfiles.aspx 页的标记中，将以下代码粘贴到"主" **asp:Content** 标记中。该代码会添加显示查询结果的 **span** 控件、引用 SharePoint JavaScript 类库文件的 **SharePoint:ScriptLink** 控件，以及 **script** 标记，以包含您的自定义逻辑。
    
  ```HTML
  
<span id="results"></span><br />
<SharePoint:ScriptLink ID="ScriptLink1" name="SP.js" runat="server"
    ondemand="false" localizable="false" loadafterui="true" />
<SharePoint:ScriptLink ID="ScriptLink2" name="SP.UserProfiles.js" runat="server"
    ondemand="false" localizable="false" loadafterui="true" />
<script type="text/javascript">

    // Replace this comment with the code for your scenario.

</script>

  ```

10. 若要添加逻辑以检索用户配置文件属性，请将 **script** 标记之间的注释替换为以下某一方案中的代码示例：
    
  -  [从 PersonProperties 对象及其 userProfileProperties 属性检索用户配置文件属性](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_examplePersonPropsObj)
    
  
  -  [通过使用 getUserProfilePropertiesFor 方法检索用户配置文件属性集](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_exampleGetUPMethod)
    
  
11. 若要测试应用程序页，请在菜单栏上选择"调试"和"启动调试"。如果系统提示您修改 web.config 文件，请选择"确定"按钮。
    
  

## 代码示例：在 SharePoint 2013 JavaScript 对象模型中从 PersonProperties 对象及其 userProfileProperties 属性检索用户配置文件属性
<a name="bk_examplePersonPropsObj"> </a>

以下代码示例演示了如何通过查询  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) 对象及其 [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) 属性获取目标用户的用户配置文件属性。它演示了如何执行以下操作：
  
    
    

- 通过使用  [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) 方法获取代表目标用户的 [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) 对象。（若要获取当前用户的 [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) 对象，请使用 [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) 方法。）
    
  
- 直接从  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) 对象获取一种属性。该示例获取 [displayName](http://msdn.microsoft.com/library/ffc35ed6-5f3e-c86d-6931-97ff9d825a8b%28Office.15%29.aspx) 属性。
    
  
- 从  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) 对象的 [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) 属性获取一种属性。该示例获取 **Department** 属性。
    
  

> **注释**
> 粘贴您在 [创建应用程序页](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_CreateAppPage)过程中添加到 UserProfiles.aspx 文件的 **script** 标记间的以下代码。在运行代码之前，请先替换 `domainName\\\\userName` 占位符值。（此代码示例未使用代码隐藏类文件。）
  
    
    


```

var personProperties;

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(getUserProperties, 'SP.UserProfiles.js');

function getUserProperties() {

    // Replace the placeholder value with the target user's credentials.
    var targetUser = "domainName\\\\userName";

    // Get the current client context and PeopleManager instance.
    var clientContext = new SP.ClientContext.get_current();
    var peopleManager = new SP.UserProfiles.PeopleManager(clientContext);

    // Get user properties for the target user.
    // To get the PersonProperties object for the current user, use the
    // getMyProperties method.
    personProperties = peopleManager.getPropertiesFor(targetUser);

    // Load the PersonProperties object and send the request.
    clientContext.load(personProperties);
    clientContext.executeQueryAsync(onRequestSuccess, onRequestFail);
}

// This function runs if the executeQueryAsync call succeeds.
function onRequestSuccess() {

    // Get a property directly from the PersonProperties object.
    var messageText = " \\"DisplayName\\" property is "
        + personProperties.get_displayName();

    // Get a property from the UserProfileProperties property.
    messageText += "<br />\\"Department\\" property is "
        + personProperties.get_userProfileProperties()['Department'];
    $get("results").innerHTML = messageText;
}

// This function runs if the executeQueryAsync call fails.
function onRequestFail(sender, args) {
    $get("results").innerHTML = "Error: " + args.get_message();
}
```


## 代码示例：在 SharePoint 2013 JavaScript 对象模型中通过使用 getUserProfilePropertiesFor 方法检索用户配置文件属性集
<a name="bk_exampleGetUPMethod"> </a>

以下代码示例通过使用  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) 方法检索目标用户指定用户配置文件属性集的值。它演示了如何执行以下操作：
  
    
    

- 创建指定目标用户和要检索的用户配置文件属性的  [UserProfilePropertiesForUser](http://msdn.microsoft.com/library/97bc94ec-62c8-dc38-d204-c5ad9ee8faee%28Office.15%29.aspx) 对象。该示例获取 **PreferredName** 属性和 **Department** 属性。
    
  
- 通过使用  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) 方法并传入 [UserProfilePropertiesForUser](http://msdn.microsoft.com/library/97bc94ec-62c8-dc38-d204-c5ad9ee8faee%28Office.15%29.aspx) 对象获取指定属性的值。（若要仅检索一个用户配置文件属性的值，请使用 [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) 方法。）
    
  
- 从返回的属性值数组获取值。
    
  

> **注释**
> 粘贴您在 [创建应用程序页](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_CreateAppPage)过程中添加到 UserProfiles.aspx 文件的 **script** 标记间的以下代码。在运行代码之前，请先替换 `domainName\\\\userName` 占位符值。（此代码示例未使用代码隐藏类文件。）
  
    
    


```

var userProfileProperties;

// Ensure that the SP.UserProfiles.js file is loaded before the custom code runs.
SP.SOD.executeOrDelayUntilScriptLoaded(getUserProperties, 'SP.UserProfiles.js');

function getUserProperties() {

    // Replace the placeholder value with the target user's credentials.
    var targetUser = "domainName\\\\userName";

    // Get the current client context and PeopleManager instance.
    var clientContext = new SP.ClientContext.get_current();
    var peopleManager = new SP.UserProfiles.PeopleManager(clientContext);

    // Specify the properties to retrieve and target user for the 
    // UserProfilePropertiesForUser object.
    var profilePropertyNames = ["PreferredName", "Department"];
    var userProfilePropertiesForUser = 
        new SP.UserProfiles.UserProfilePropertiesForUser(
            clientContext,
            targetUser,
            profilePropertyNames);

    // Get user profile properties for the target user.
    // To get the value for only one user profile property, use the
    // getUserProfilePropertyFor method.
    userProfileProperties = peopleManager.getUserProfilePropertiesFor(
        userProfilePropertiesForUser);

    // Load the UserProfilePropertiesForUser object and send the request.
    clientContext.load(userProfilePropertiesForUser);
    clientContext.executeQueryAsync(onRequestSuccess, onRequestFail);
}

// This function runs if the executeQueryAsync call succeeds.
function onRequestSuccess() {
    var messageText = "\\"PreferredName\\" property is " 
        + userProfileProperties[0];
    messageText += "<br />\\"Department\\" property is " 
        + userProfileProperties[1];
    $get("results").innerHTML = messageText;
}

// This function runs if the executeQueryAsync call fails.
function onRequestFail(sender, args) {
    $get("results").innerHTML = "Error: " + args.get_message();
}
```


## 其他资源
<a name="bk_addresources"> </a>


-  [在 SharePoint 2013 中使用用户配置文件](work-with-user-profiles-in-sharepoint-2013.md)
    
  
-  [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型检索用户配置文件属性](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [如何：通过使用 SharePoint 2013 中的服务器对象模型来处理用户配置文件和组织配置文件](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)
    
  
-  [SP.UserProfiles namespace (sp.userprofiles)](http://msdn.microsoft.com/library/8c1fcceb-cd9a-b25c-32f4-1cfb0578278c%28Office.15%29.aspx)
    
  

