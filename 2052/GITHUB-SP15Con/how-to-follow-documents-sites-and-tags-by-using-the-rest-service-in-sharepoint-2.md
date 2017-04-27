---
title: 如何：在 SharePoint 2013 中使用 REST 服务关注文档、网站和标签
ms.prod: SHAREPOINT
ms.assetid: 989a5873-49f9-49e4-8d0f-439dde891cc2
---


# 如何：在 SharePoint 2013 中使用 REST 服务关注文档、网站和标签
创建使用 REST 服务来关注内容（文档、网站、标签）并获取关注的内容的 SharePoint 承载的应用程序。
## 我该如何使用 SharePoint Server 2013 REST 服务来关注内容？
<a name="bk_intro"> </a>

SharePoint Server 2013 用户可以关注文档、网站和标签来获得有关自己的新闻源中项目的更新，并快速打开关注的文档和网站。您可以使用应用程序或解决方案中的 SharePoint Server 2013 REST API 开始以当前用户的身份关注内容、停止关注内容并获取关注的内容。
  
    
    
以下 REST 资源是用于"关注内容"任务的主要 API：
  
    
    

- **SocialRestFollowingManager** 提供了用于管理用户的已关注好友列表的方法。
    
  
- **SocialActor** 表示服务器响应客户端请求时返回的文档、网站或标记。
    
  
- **SocialActorInfo** 指定客户端对服务器的请求中的文档、网站或标记。
    
  
- **SocialActorType** 和 **SocialActorTypes** 指定客户端对服务器的请求中的内容类型。
    
  
若要使用 REST API 执行"关注内容"任务，您需要将 HTTP **GET** 和 HTTP **POST** 请求发送到 REST 服务。用于"关注内容"任务的 REST 端点 URI 以 **SocialRestFollowingManager** 资源 ( `<siteUri>/_api/social.following`) 为起点，以下列资源之一为终点：
  
    
    

- **follow**，用于开始关注某文档、网站或标签
    
  
- **stopfollowing**，用于停止关注某文档、网站或标签
    
  
- **isfollowed**，用于查明用户是否正在关注特定的文档、网站或标签
    
  
- **my/followed**，用于获取关注的文档、网站和标签
    
  
- **my/followedcount**，用于获取关注的文档、网站和标签的数量
    
  

> **注释**
> 也可以将这些端点用于"关注好友"任务，但 **SocialRestFollowingManager** 中提供的 **followers** 和 **suggestions** 资源仅支持关注好友，而不支持关注内容。有关如何使用 **SocialRestFollowingManager** 的详细信息，请参阅 [通过 SharePoint 2013 跟踪内容](follow-content-in-sharepoint-2013.md)和 [通过 SharePoint 2013 跟踪人员](follow-people-in-sharepoint-2013.md)。 
  
    
    


## 使用 SharePoint 2013 REST 服务创建管理关注内容的 SharePoint 承载的应用程序的先决条件
<a name="bkmk_Prereqs"> </a>

本文假定您通过在 Office 365 开发人员网站上使用 Napa来创建 SharePoint 外接程序。如果您使用此开发环境，则已经满足先决条件。
  
    
    

> **注释**
> 转到 [在 Office 365 上设置 SharePoint 加载项的开发环境](http://msdn.microsoft.com/library/b22ce52a-ae9e-4831-9b68-c9210af6dc54%28Office.15%29.aspx)注册 Office 365 开发人员网站，并开始使用Napa。 
  
    
    

如果您未在 Office 365 开发人员网站上使用Napa，则在部署 SharePoint 外接程序以前您需要满足下列先决条件：
  
    
    

- 一个配置为用于应用程序隔离的 SharePoint 2013 开发环境。如果您正在进行远程开发，则服务器必须支持应用程序侧载，或者您必须在"开发人员网站"上安装该应用程序。
    
  
- 已配置的我的网站主机，以及为当前用户创建的个人网站。
    
  
- 带有 Visual Studio 2013 Office 开发人员工具的 Visual Studio 2008 或 Visual Studio 2013。
    
  
- 登录用户的足够权限：
    
  - 开发计算机上的本地管理员权限。
    
  
  - 到安装应用程序的 SharePoint 网站的管理 Web 网站和创建子网站用户权限。默认情况下，这些权限只提供给那些具有完全控制权限级别的用户或网站的所有者。
    
  
  - 您必须以系统帐户以外的人的身份登录。系统帐户没有安装应用程序的权限。
    
  

> **注释**
> 请参阅 [设置 SharePoint 加载项的本地开发环境](http://msdn.microsoft.com/library/b0878c12-27c9-4eea-ae3b-7e79e5a8838d%28Office.15%29.aspx)，获取有关本地设置的指南（包括必要情况下如何禁用环回检查）。 
  
    
    


  
    
    

## 创建 SharePoint 外接程序项目
<a name="bkmk_CreateApp"> </a>


1. 在您的开发人员网站上，打开 Napa，然后选择"添加新项目"。
    
  
2. 选择"SharePoint 相关应用程序"模板，对项目命名，然后选择"创建"按钮。
    
  
3. 为您的应用程序设置权限：
    
1. 选择页面底部的"属性"按钮。
    
  
2. 在"属性"窗口中，选择"权限"。
    
  
3. 在"内容"类别中，为"租户"范围设置 **Write** 权限。
    
  
4. 在"社交"类别中，为"用户配置文件"范围设置 **Read** 权限。
    
  
5. 关闭"属性"窗口。
    
  
4. 展开"脚本"节点，选择 App.js 文件，并使用以下某一个方案中的代码来替换该文件中的内容：
    
  -  [开始关注和停止关注文档](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_FollowDocs)
    
  
  -  [开始关注和停止关注网站](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_FollowSites)
    
  
  -  [开始关注和停止关注标签](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_FollowTags)
    
  
  -  [获取关注的内容](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bkmk_GetFollowed)
    
  
5. 若要运行应用程序，请选择页面底部的"运行项目"按钮。
    
  
6. 在打开的"是否信任"页面上，选择"信任它"按钮。应用程序页面将打开并运行代码。若要调试页面，请选择"F12"键，然后选择"脚本"选项卡上的 App.js。
    
  

## 代码示例：使用 SharePoint 2013 REST 服务开始关注和停止关注文档
<a name="bkmk_FollowDocs"> </a>

以下代码示例展示了 App.js 文件的内容，并显示了如何执行以下操作：
  
    
    

- 从查询字符串中获取应用程序 web URI，并构建  `<siteUri>/_api/social.following` 端点 URI。
    
  
- 构建并发送一个 **POST** 请求到 `isfollowed` 端点，查明当前用户是否已关注特定文档。
    
  
- 构建并发送一个 **POST** 请求到 `follow` 端点，开始关注文档。
    
  
- 构建并发送一个 **POST** 请求到 `stopfollowing` 端点，停止关注文档。
    
  
- 阅读  `isfollowed` 请求和 `follow` 请求的 JSON 响应。（ `stopfollowing` 请求不会在响应中返回任何内容。）请参阅 [示例 JSON 响应](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses)。
    
  
在运行代码之前，您需要上载一个文档，并将 **documentUrl** 变量的占位符值更改为该文档的 URL。
  
    
    



```

// Replace the documentUrl placeholder value before you run the code.
var documentUrl = "https://domain.sharepoint.com/Shared%20Documents/fileName.docx";
var followingManagerEndpoint;

// Get the SPAppWebUrl parameter from the query string and build
// the Following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl) + "/_api/social.following";
    isFollowed();
});

// Check whether the current user is already following the document.
// The request body includes a SocialActorInfo object that represents
// the specified item. 
// The success function reads the response from the REST service and then
// toggles the user's following status by calling the appropriate method.
function isFollowed() {
    $.ajax( {
        url: followingManagerEndpoint + "/isfollowed",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":1,
                "ContentUri":documentUrl,
                "Id":null
            } 
        }),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            if (jsonObject.d.IsFollowed === true ) {
                alert('The user is currently following the document.');
                stopFollowDocument();
            }
            else {
                alert('The user is currently NOT following the document.');
                followDocument();
            }
        },
        error: requestFailed
    });
}

// Make the current user start following a document.
// The request body includes a SocialActorInfo object that represents
// the document to follow.
// The success function reads the response from the REST service.
function followDocument() {
    $.ajax( {
        url: followingManagerEndpoint + "/follow",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":1,
                "ContentUri":documentUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            var statusMessage = {
                0 : 'The user has started following the document. ',
                1 : 'The user is already following the document. ',
                2 : 'An internal limit was reached. ',
                3 : 'An internal error occurred. '
            }
            alert(statusMessage[jsonObject.d.Follow] + 'Status code = ' + jsonObject.d.Follow);
        },
        error: requestFailed
    } );
}

// Make the current user stop following a document.
// The request body includes a SocialActorInfo object that represents
// the document to stop following.
function stopFollowDocument() {
    $.ajax( {
        url: followingManagerEndpoint + "/stopfollowing",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":1,
                "ContentUri":documentUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function () { 
            alert('The user has stopped following the document.');
        },
        error: requestFailed
    } );
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## 代码示例：使用 SharePoint 2013 REST 服务开始关注和停止关注网站
<a name="bkmk_FollowSites"> </a>

以下代码示例展示了 App.js 文件的内容，并显示了如何执行以下操作：
  
    
    

- 从查询字符串中获取应用程序 web URI，并构建  `<siteUri>/_api/social.following` 端点 URI。
    
  
- 构建并发送一个 **POST** 请求到 `isfollowed` 端点，查明当前用户是否已关注特定网站。
    
  
- 构建并发送一个 **POST** 请求到 `follow` 端点，开始关注网站。
    
  
- 构建并发送一个 **POST** 请求到 `stopfollowing` 端点，停止关注网站。
    
  
- 阅读  `isfollowed` 请求和 `follow` 请求的 JSON 响应。（ `stopfollowing` 请求不会在响应中返回任何内容。）请参阅 [示例 JSON 响应](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses)。
    
  
在运行代码之前，您需要更改 **siteUrl** 变量的值，使其与您要关注的网站相匹配。将 **http://server/siteCollection/site** 格式用于网站集中的网站。您可以从该网站的任何页面或库关注网站。如果网站使用了不支持关注的模板（比如"我的网站"主机或个人网站），您会遇到一个 **UnsupportedSite** 错误（错误代码 10）。
  
    
    



```

// Replace the siteUrl placeholder value before you run the code.
var siteUrl = "https://domain.sharepoint.com";
var followingManagerEndpoint;

// Get the SPAppWebUrl parameter from the query string and build
// the Following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl) + "/_api/social.following";
    isFollowed();
});

// Check whether the current user is already following the site.
// The request body includes a SocialActorInfo object that represents
// the specified item. 
// The success function reads the response from the REST service and then
// toggles the user's following status by calling the appropriate method.
function isFollowed() {
    $.ajax( {
        url: followingManagerEndpoint + "/isfollowed",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":2,
                "ContentUri":siteUrl,
                "Id":null
            } 
        }),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            if (jsonObject.d.IsFollowed === true ) {
                alert('The user is currently following the site.');
                stopFollowSite();
            }
            else {
                alert('The user is currently NOT following the site.');
                followSite();
            }
        },
        error: requestFailed
    });
}

// Make the current user start following a site.
// The request body includes a SocialActorInfo object that represents
// the site to follow.
// The success function reads the response from the REST service.
function followSite() {
    $.ajax( {
        url: followingManagerEndpoint + "/follow",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":2,
                "ContentUri":siteUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            var statusMessage = {
                0 : 'The user has started following the site. ',
                1 : 'The user is already following the site. ',
                2 : 'An internal limit was reached. ',
                3 : 'An internal error occurred. '
            }
            alert(statusMessage[jsonObject.d.Follow] + 'Status code = ' + jsonObject.d.Follow);
        },
        error: requestFailed
    } );
}

// Make the current user stop following a site.
// The request body includes a SocialActorInfo object that represents
// the site to stop following.
function stopFollowSite() {
    $.ajax( {
        url: followingManagerEndpoint + "/stopfollowing",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":2,
                "ContentUri":siteUrl,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function () { 
            alert('The user has stopped following the site.');
        },
        error: requestFailed
    } );
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## 代码示例：使用 SharePoint 2013 REST 服务开始关注和停止关注标签
<a name="bkmk_FollowTags"> </a>

以下代码示例展示了 App.js 文件的内容，并显示了如何执行以下操作：
  
    
    

- 从查询字符串中获取应用程序 web URI，并构建  `<siteUri>/_api/social.following` 端点 URI。
    
  
- 构建并发送一个 **POST** 请求到 `isfollowed` 端点，查明当前用户是否已关注特定标签。
    
  
- 构建并发送一个 **POST** 请求到 `follow` 端点，开始关注标签。
    
  
- 构建并发送一个 **POST** 请求到 `stopfollowing` 端点，停止关注标签。
    
  
- 阅读  `isfollowed` 请求和 `follow` 请求的 JSON 响应。（ `stopfollowing` 请求不会在响应中返回任何内容。）有关详细信息，请参阅 [示例 JSON 响应](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses)。
    
  
在运行代码之前，要将 **tagGuid** 变量的占位符值更改为现有标签的 GUID。您用于从 **HashTagsTermSet** 中检索标签的分类 API 没有 REST 界面，所以您必须使用 .NET 客户端对象模型或 JavaScript 对象模型。例如，请参阅 [如何使用 JavaScript 对象模型基于标签名称获取标签 GUID](follow-content-in-sharepoint-2013.md#bk_getTagGuid)。
  
    
    



```

// Replace the tagGuid placeholder value before you run the code.
var tagGuid = "19a4a484-c1dc-4bc5-8c93-bb96245ce928";
var followingManagerEndpoint;

// Get the SPAppWebUrl parameter from the query string and build
// the Following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl) + "/_api/social.following";
    isFollowed();
});

// Check whether the current user is already following the tag.
// The request body includes a SocialActorInfo object that represents
// the specified item. 
// The success function reads the response from the REST service and then
// toggles the user's following status by calling the appropriate method.
function isFollowed() {
    $.ajax( {
        url: followingManagerEndpoint + "/isfollowed",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":3,
                "TagGuid":tagGuid,
                "Id":null
            } 
        }),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            if (jsonObject.d.IsFollowed === true ) {
                alert('The user is currently following the tag.');
                stopFollowTag();
            }
            else {
                alert('The user is currently NOT following the tag.');
                followTag();
            }
        },
        error: requestFailed
    });
}

// Make the current user start following a tag.
// The request body includes a SocialActorInfo object that represents
// the tag to follow.
// The success function reads the response from the REST service.
function followTag() {
    $.ajax( {
        url: followingManagerEndpoint + "/follow",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":3,
                "TagGuid":tagGuid,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function (responseData) { 
            stringData = JSON.stringify(responseData);
            jsonObject = JSON.parse(stringData);
            var statusMessage = {
                0 : 'The user has started following the tag. ',
                1 : 'The user is already following the tag. ',
                2 : 'An internal limit was reached. ',
                3 : 'An internal error occurred. '
            }
            alert(statusMessage[jsonObject.d.Follow] + 'Status code = ' + jsonObject.d.Follow);
        },
        error: requestFailed
    } );
}

// Make the current user stop following a tag.
// The request body includes a SocialActorInfo object that represents
// the tag to stop following.
function stopFollowTag() {
    $.ajax( {
        url: followingManagerEndpoint + "/stopfollowing",
        type: "POST",
        data: JSON.stringify( { 
            "actor": {
                "__metadata": {
                    "type":"SP.Social.SocialActorInfo"
                },
                "ActorType":3,
                "TagGuid":tagGuid,
                "Id":null
            } 
        } ),
        headers: { 
            "accept":"application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest":$("#__REQUESTDIGEST").val()
        },
        success: function () { 
            alert('The user has stopped following the tag.');
        },
        error: requestFailed
    } );
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## 使用 SharePoint 2013 REST 服务获取关注的内容的代码示例。
<a name="bkmk_GetFollowed"> </a>

以下代码示例展示了 App.js 文件的内容，并显示了如何执行以下操作：
  
    
    

- 从查询字符串中获取应用程序 web URI，并构建  `<siteUri>/_api/social.following` 端点 URI。
    
  
- 构建并发送一个 **GET** 请求到 `my/followedcount` 端点，获取当前用户关注的内容的数量。
    
  
- 构建并发送一个 **GET** 请求到 `my/followed` 端点，获取当前用户关注的内容。
    
  
- 读取由请求返回的 JSON 响应。请参阅 [示例 JSON 响应](how-to-follow-documents-sites-and-tags-by-using-the-rest-service-in-sharepoint-2.md#bk_exampleResponses)。
    
  

```

var followingManagerEndpoint;
var followedCount;

// Get the SPAppWebUrl parameter from the query string and build
// the following manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    followingManagerEndpoint = decodeURIComponent(appweburl)+ "/_api/social.following";
    getMyFollowedCount();
} );

// Get the count of content that the current user is following.
// The "types=14" parameter specifies all content types
// (documents = 2 + sites = 4 + tags = 8).
function getMyFollowedCount() {
    $.ajax( {
        url: followingManagerEndpoint + "/my/followedcount(types=14)",
        headers: { 
            "accept": "application/json;odata=verbose"
        },
        success: function (data) { 
            followedCount = data.d.FollowedCount;
            getMyFollowedContent();
        },
        error: requestFailed
    } );
}

// Get the content that the current user is following.
// The "types=14" parameter specifies all content types
// (documents = 2 + sites = 4 + tags = 8).
function getMyFollowedContent() {
    $.ajax( {
        url: followingManagerEndpoint + "/my/followed(types=14)",
        headers: { 
            "accept": "application/json;odata=verbose"
        },
        success: followedContentRetrieved,
        error: requestFailed
    });
}

// Parse the JSON data and iterate through the collection.
function followedContentRetrieved(data) {
    var stringData = JSON.stringify(data);
    var jsonObject = JSON.parse(stringData); 
    var types = {
        1: "document",
        2: "site",
        3: "tag" 
    };
 
    var followedActors = jsonObject.d.Followed.results; 
    var followedList = "You're following " + followedCount + " items:";
    for (var i = 0; i < followedActors.length; i++) {
        var actor = followedActors[i];
        followedList += "<p>The " + types[actor.ActorType] + ": \\"" +
        actor.Name + "\\"</p>";
    } 
    $("#message").html(followedList); 
}

function requestFailed(xhr, ajaxOptions, thrownError) {
    alert('Error:\\n' + xhr.status + '\\n' + thrownError + '\\n' + xhr.responseText);
}
```


## "关注内容"请求的 JSON 响应示例
<a name="bk_exampleResponses"> </a>

默认情况下，REST 服务会返回使用 Atom 协议格式化的响应，但您也可以使用 HTTP **Accept** 头（例如： `"accept":"application/json;odata=verbose"`）请求 JSON 格式。响应数据作为字符串返回，并且您可以使用 **JSON.stringify** 函数和 **JSON.parse** 函数将该字符串转换成一个对象，如前面的代码示例所示。
  
    
    
若要解决由 REST 服务返回的错误，在调试模式下，查看 **responseText** 属性，如前面示例中的 **requestFailed** 回调函数所示。您还可以从网络探查器或 HTTP 调试程序（如 Fiddler）中获取 ULS 服务器日志的相关 ID。
  
    
    

### 对 Follow 端点的示例响应

作为对  `follow` 端点的客户端请求的响应，REST 服务返回一个 **SocialFollowResult** 值，它表示 **Follow** 请求是否成功。
  
    
    
以下响应表示 **AlreadyFollowing** 状态。
  
    
    



```

{"d":{"Follow":1}}
```

表 1 显示 **SocialFollowResult** 状态代码和值。
  
    
    

**表 1. SocialFollowResult 代码和值**

|||
|:-----|:-----|
|0  <br/> |**OK**。当前用户正在关注该角色。  <br/> |
|1  <br/> |**AlreadyFollowing**。当前用户已经关注该角色。  <br/> |
|2  <br/> |**LimitReached**。请求失败，因为达到了内部限制。  <br/> |
|3  <br/> |**InternalError**。由于内部错误导致了请求失败。  <br/> |
   

> **注释**
> REST 服务没有返回对 **StopFollowing** 请求的响应。它返回 `{"d":{"StopFollowing":null}}`。 
  
    
    


### 对 IsFollowed 端点的示例响应

作为对  `isfollowed` 端点的客户端请求的响应，REST 服务返回一个 **bool** 值，它表示当前用户是否正在关注特定的角色。
  
    
    
以下响应指示当前用户没有关注特定的文档、网站和标签。
  
    
    



```
{"d":{"IsFollowed":false}}
```


### 对 My/Followed 端点的示例响应

作为对  `my/followed` 端点的客户端请求的响应，REST 服务返回一个 **SP.Social.SocialActor** 对象数组，它表示当前用户正在关注的文档、网站和标签。
  
    
    
以下响应表示一个已关注的文档、网站和标签。请求指定要包括的内容类型。
  
    
    



```
{"d":{"Followed":{"results":[
  {"__metadata":{"type":"SP.Social.SocialActor"}
    "AccountName":null
    "ActorType":1
    "CanFollow":true
    "ContentUri":"https://domain.sharepoint.com:443/Shared%20Documents/fileName.docx"
    "EmailAddress":null
    "FollowedContentUri":null
    "Id":"2.089f4944a6374a64b52b7af5ba140392.9340a4837688405daa6b83f2b58f973d.
      51bbb5d8e214457ba794669345d23040.98b9fc73d5224265b039586688b15b98"
    "ImageUri":null
    "IsFollowed":true
    "LibraryUri":null
    "Name":"snippets.txt"
    "PersonalSiteUri":null
    "Status":0
    "StatusText":null
    "TagGuid":"00000000-0000-0000-0000-000000000000"
    "Title":null
    "Uri":"https://domain.sharepoint.com:443/Shared%20Documents/fileName.docx"
  }
  {"__metadata":{"type":"SP.Social.SocialActor"}
    "AccountName":null
    "ActorType":2
    "CanFollow":true
    "ContentUri":"https://domain.sharepoint.com:443/"
    "EmailAddress":null
    "FollowedContentUri":null
    "Id":"8.089f4944a6374a64b52b7af5ba140392.9340a4837688405daa6b83f2b58f973d.
      089f4944a6374a64b52b7af5ba140392.98b9fc73d5224265b039586688b15b98"
    "ImageUri":null
    "IsFollowed":true
    "LibraryUri":null
    "Name":"Developer Site"
    "PersonalSiteUri":null
    "Status":0
    "StatusText":null
    "TagGuid":"00000000-0000-0000-0000-000000000000"
    "Title":null
    "Uri":"https://domain.sharepoint.com:443/"
  }
  {"__metadata":{"type":"SP.Social.SocialActor"}
    "AccountName":null
    "ActorType":3
    "CanFollow":true
    "ContentUri":null
    "EmailAddress":null
    "FollowedContentUri":null
    "Id":"16.00000000000000000000000000000000.00000000000000000000000000000000.
      19a4a484c1dc4bc58c93bb96245ce928.98b9fc73d5224265b039586688b15b98"
    "ImageUri":null
    "IsFollowed":true
    "LibraryUri":null
    "Name":"#someTag"
    "PersonalSiteUri":null
    "Status":0
    "StatusText":null
    "TagGuid":"19a4a484-c1dc-4bc5-8c93-bb96245ce928"
    "Title":null
    "Uri":"https://domain-my.sharepoint.com:443/_layouts/15/HashTagProfile.aspx?
      TermID=19a4a484-c1dc-4bc5-8c93-bb96245ce928"
  }
]}}}
```


### 对 My/FollowedCount 端点的示例响应

作为对  `my/followedcount` 端点的客户端请求的响应，REST 服务返回一个 **Int32** 值，它表示当前用户正在关注的指定角色类型的总数量。
  
    
    
以下响应表示已关注文档、网站和/或标签的总数量为 3。请求指定要包括的内容类型。
  
    
    



```

{"d":{"FollowedCount":3}}
```


## 其他资源
<a name="bkmk_AddtionalResources"> </a>


-  [通过 SharePoint 2013 跟踪内容](follow-content-in-sharepoint-2013.md)
    
  
-  [关注好友及 SharePoint 2013 的内容 REST API 引用](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型关注文档和网站](how-to-follow-documents-and-sites-by-using-the-net-client-object-model-in-sharep.md)
    
  

