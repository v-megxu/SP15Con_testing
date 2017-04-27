---
title: 如何：了解通过使用 SharePoint 2013 中的 REST 服务读取和写入好友动态订阅源
ms.prod: SHAREPOINT
ms.assetid: 1da8d484-3666-42c3-8a8f-8b3ef93e96e9
---


# 如何：了解通过使用 SharePoint 2013 中的 REST 服务读取和写入好友动态订阅源
创建一个 SharePoint 承载的应用程序，以便使用 REST 服务发布文章和获取当前用户的个人订阅源。
## 使用 SharePoint 2013 REST 服务创建可发布文章和获取好友动态订阅源的 SharePoint 托管的 SharePoint 外接程序的先决条件
<a name="bkmk_Prereqs"> </a>

本文假定您通过在 Office 365 开发人员网站上使用 Napa来创建 SharePoint 外接程序。如果您使用此开发环境，则已经满足先决条件。
  
    
    

> **注释**
> 转到 [在 Office 365 上设置 SharePoint 加载项的开发环境](http://msdn.microsoft.com/library/b22ce52a-ae9e-4831-9b68-c9210af6dc54%28Office.15%29.aspx)来了解如何注册开发人员网站并开始使用 Napa。 
  
    
    

如果您没有在开发人员网站上使用 Napa，则需要：
  
    
    

- SharePoint Server 2013，其中已配置了"我的网站"，并且为当前用户创建了个人网站
    
  
- Visual Studio 2008 和Visual Studio 2013 Office 开发人员工具
    
  
- 对登录用户的 User Profile Service 应用程序的"完全控制"访问权限
    
  

> **注释**
> 有关如何设置符合您的需求的开发环境的指南，请参阅 [开始构建 Office 和 SharePoint 相关应用程序](http://msdn.microsoft.com/library/187f8c8c-1b15-471c-80b5-69a40e67deea%28Office.15%29.aspx)。 
  
    
    


## 了解有关使用 SharePoint 2013 好友动态订阅源的核心概念
<a name="bkmk_CoreConcepts"> </a>

您在本文中创建的 SharePoint 承载的应用程序使用 JavaScript 创建 HTTP 请求并将其发送到代表性状态传输 (REST) 终结点。这些请求可发布文章并获取当前用户的个人订阅源。表 1 包含指向相关文章的链接，这些文章介绍您在开始使用好友动态订阅源之前应了解的一般概念。
  
    
    

**表 1. 关于使用 SharePoint 2013 好友动态订阅源的核心概念**


|**文章标题**|**说明**|
|:-----|:-----|
| [SharePoint 外接程序](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx) <br/> |了解 SharePoint 外接程序以及构建它们的基础概念。  <br/> |
| [使用 SharePoint 2013 中的社交功能开始进行开发](get-started-developing-with-social-features-in-sharepoint-2013.md) <br/> |了解如何开始对 好友动态订阅源和微博帖子进行编程、关注他人和内容（文档、网站和标签），以及使用用户配置文件。  <br/> |
| [使用 SharePoint 2013 中的社交源](work-with-social-feeds-in-sharepoint-2013.md) <br/> |了解使用好友动态订阅源的常见编程任务和用于执行这些任务的 API。  <br/> |
   

## 创建 SharePoint 外接程序项目
<a name="bkmk_CreateApp"> </a>


1. 在您的开发人员网站上，打开 Napa，然后选择"添加新项目"。
    
  
2. 选择"SharePoint 相关应用程序"模板，将项目命名为 SocialFeedREST，然后选择"创建"按钮。
    
  
3. 指定您的应用程序所需的权限：
    
1. 选择页面底部的"属性"按钮。 
    
  
2. 在"属性"窗口中，选择"权限"。
    
  
3. 在"内容"类别中，为"租户"范围设置 **Write** 权限。
    
  
4. 在"社交"类别中，为"用户配置文件"范围设置 **Read** 权限。
    
  
5. 关闭"属性"窗口。
    
  
4. 展开"脚本"节点，选择 App.js 文件，然后删除该文件的内容。
    
  

## 使用 SharePoint 2013 REST 服务向好友动态订阅源发布内容
<a name="bkmk_PubPost"> </a>


1. 在 App.js 文件中，为 **SocialFeedManager** 终结点的 URL 声明一个全局变量。
    
  ```
  
var feedManagerEndpoint;
  ```

2. 添加下面的代码，以便从查询字符串中获取 **SPAppWebUrl** 参数，并使用它构建 **SocialFeedManager** 终结点。
    
  ```
  $(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    feedManagerEndpoint = decodeURIComponent(appweburl) + "/_api/social.feed";
    postToMyFeed();
});
  ```

3. 添加下面的代码，以便为  `/my/Feed/Post` 终结点创建 HTTP **POST** 请求，定义帖子的创建数据并发布该帖子。
    
    该请求发送请求正文中的 **SocialRestPostCreationData** 资源。 **SocialRestPostCreationData** 包含文章的目标位置（在本例中为 `null`，用以指定当前用户的根帖子），以及定义帖子属性的 **SocialPostCreationData** 复杂类型。
    


  ```
  
function postToMyFeed() {
    $.ajax( {
        url: feedManagerEndpoint + "/my/Feed/Post",
        type: "POST",
        data: JSON.stringify( { 
            'restCreationData':{
                '__metadata':{ 
                    'type':'SP.Social.SocialRestPostCreationData'
                },
                'ID':null, 
                'creationData':{ 
                    '__metadata':{ 
                        'type':'SP.Social.SocialPostCreationData'
                    },
                'ContentText':'This post was published using REST.',
                'UpdateStatusText':false
                } 
            } 
        }),
        headers: { 
            "accept": "application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest": $("#__REQUESTDIGEST").val()
        },
        success: getMyFeed,
        error: function (xhr, ajaxOptions, thrownError) { 
            alert("POST error:\\n" + xhr.status + "\\n" + thrownError);
        }
    });
}

  ```


## 使用 SharePoint 2013 REST 服务检索当前用户的好友动态订阅源
<a name="bkmk_GetFeed"> </a>

添加下面的代码，以便使用  `/my/Feed` 终结点获取当前用户的 **Personal** 订阅源类型。 **accept** 标头请求服务器在其响应中返回订阅源的 JavaScript 对象表示法 (JSON) 表示形式。
  
    
    

```

function getMyFeed() {
    $.ajax( {
        url: feedManagerEndpoint + "/my/Feed",
        headers: { 
            "accept": "application/json;odata=verbose"
        },
        success: feedRetrieved,
        error: function (xhr, ajaxOptions, thrownError) { 
            alert("GET error:\\n" + xhr.status + "\\n" + thrownError);
        }
    });    
}

```


## 使用 SharePoint 2013 REST 服务循环访问好友动态订阅源并读取其内容
<a name="bkmk_ReadFeed"> </a>

添加下面的代码，以便使用 **JSON.stringify** 和 **JSON.parse** 函数准备返回的数据，然后循环访问订阅源并获取线索的所有者和根帖子的相应文本。
  
    
    

```

function feedRetrieved(data) {
    var stringData = JSON.stringify(data);
    var jsonObject = JSON.parse(stringData); 
 
    var feed = jsonObject.d.SocialFeed.Threads; 
    var threads = feed.results;
    var feedContent = "";
    for (var i = 0; i < threads.length; i++) {
        var thread = threads[i];
        var participants = thread.Actors;
        var owner = participants.results[thread.OwnerIndex].Name;
        feedContent += '<p>' + owner + 
            ' said "' + thread.RootPost.Text + '"</p>';
    }  
    $("#message").html(feedContent); 
}
```


## 在开发人员网站上运行 SharePoint 相关应用程序
<a name="bkmk_ReadFeed"> </a>


1. 若要运行应用程序，请选择页面底部的"运行项目"按钮。 
    
  
2. 在打开的"是否信任"页面上，选择"信任它"按钮。该应用程序页面将打开并显示所有者的姓名以及订阅源中每个根帖子的相应文本。
    
  

  
    
    

## 代码示例：使用 SharePoint 2013 REST 服务发布文章和获取当前用户的订阅源
<a name="bkmk_PubPosts1"> </a>

下面是有关 App.js 文件的完整代码示例。该示例发布一篇文章并获取作为 JSON 对象返回的当前用户的个人订阅源。然后，该示例循环访问该订阅源。
  
    
    

```

var feedManagerEndpoint;

// Get the SPAppWebUrl parameter from the query string and build
// the feed manager endpoint.
$(document).ready(function () {
    var appweburl;
    var params = document.URL.split("?")[1].split("&amp;");
    for (var i = 0; i < params.length; i = i + 1) {
        var param = params[i].split("=");
        if (param[0] === "SPAppWebUrl") appweburl = param[1];
    }
    feedManagerEndpoint = decodeURIComponent(appweburl)+ "/_api/social.feed";
    postToMyFeed();
});

// Publish a post to the current user's feed by using the 
// "<app web URL>/_api/social.feed/my/Feed/Post" endpoint.
function postToMyFeed() {
    $.ajax( {
        url: feedManagerEndpoint + "/my/Feed/Post",
        type: "POST",
        data: JSON.stringify( { 
            'restCreationData':{
                '__metadata':{ 
                    'type':'SP.Social.SocialRestPostCreationData'
                },
                'ID':null, 
                'creationData':{ 
                    '__metadata':{ 
                        'type':'SP.Social.SocialPostCreationData'
                    },
                'ContentText':'This post was published using REST.',
                'UpdateStatusText':false
                } 
            } 
        }),
        headers: { 
            "accept": "application/json;odata=verbose",
            "content-type":"application/json;odata=verbose",
            "X-RequestDigest": $("#__REQUESTDIGEST").val()
        },
        success: getMyFeed,
        error: function (xhr, ajaxOptions, thrownError) { 
            alert("POST error:\\n" + xhr.status + "\\n" + thrownError);
        }
    });
}

// Get the current user's feed by using the 
// "<app web URL>/_api/social.feed/my/Feed" endpoint.
function getMyFeed() {
    $.ajax( {
        url: feedManagerEndpoint + "/my/Feed",
        headers: { 
            "accept": "application/json;odata=verbose"
        },
        success: feedRetrieved,
        error: function (xhr, ajaxOptions, thrownError) { 
            alert("GET error:\\n" + xhr.status + "\\n" + thrownError);
        }
    });    
}

// Parse the JSON data and iterate through the feed.
function feedRetrieved(data) {
    var stringData = JSON.stringify(data);
    var jsonObject = JSON.parse(stringData); 
 
    var feed = jsonObject.d.SocialFeed.Threads; 
    var threads = feed.results;
    var feedContent = "";
    for (var i = 0; i < threads.length; i++) {
        var thread = threads[i];
        var participants = thread.Actors;
        var owner = participants.results[thread.OwnerIndex].Name;
        feedContent += '<p>' + owner + 
            ' said "' + thread.RootPost.Text + '"</p>';
    }  
    $("#message").html(feedContent); 
}
```


## 后续步骤
<a name="bkmk_PubPosts1"> </a>

请参阅 [SharePoint 2013 的好友动态订阅源 REST API 引用](social-feed-rest-api-reference-for-sharepoint-2013.md)和 [关注好友及 SharePoint 2013 的内容 REST API 引用](following-people-and-content-rest-api-reference-for-sharepoint-2013.md)了解可以用于访问社交功能的其他 REST 端点。
  
    
    

## 其他资源
<a name="bk_addResources"> </a>


-  [SharePoint 2013 的好友动态订阅源 REST API 引用](social-feed-rest-api-reference-for-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 中的社交功能开始进行开发](get-started-developing-with-social-features-in-sharepoint-2013.md)
    
  
-  [使用 SharePoint 2013 中的社交源](work-with-social-feeds-in-sharepoint-2013.md)
    
  

