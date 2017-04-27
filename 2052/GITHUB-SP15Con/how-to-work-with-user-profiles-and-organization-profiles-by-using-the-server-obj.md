---
title: 如何：通过使用 SharePoint 2013 中的服务器对象模型来处理用户配置文件和组织配置文件
ms.prod: SHAREPOINT
ms.assetid: 13f16dc3-f652-4fb3-996b-5f2166236d2b
---


# 如何：通过使用 SharePoint 2013 中的服务器对象模型来处理用户配置文件和组织配置文件
了解如何使用 SharePoint 2013 服务器对象模型以编程方式创建、检索和更改 SharePoint 2013 用户配置文件和用户配置文件属性。
## 什么是 SharePoint 2013 中的用户配置文件？

在 SharePoint 2013 中，用户配置文件表示 SharePoint 用户。用户配置文件属性表示有关用户以及属性本身的信息。例如，属性包括用户的帐户名或电子邮件地址以及属性的数据类型。您可以使用服务器对象模型以编程方式创建、检索和更改用户配置文件、配置文件子类型和配置文件属性。
  
    
    

> **注释**
> 有关使用用户配置文件的常见编程任务和用于执行这些任务的 API 的详细信息，请参阅 [在 SharePoint 2013 中使用用户配置文件](work-with-user-profiles-in-sharepoint-2013.md)。 
  
    
    


## 设置通过 SharePoint 2013 服务器对象模型使用用户配置文件的开发环境的先决条件
<a name="bkmk_Prereqs"> </a>

若要创建一个通过服务器对象模型使用用户配置文件和用户配置文件属性的控制台应用程序，您将需要：
  
    
    

- 具有为当前用户创建的配置文件的 SharePoint Server 2013。
    
  
- Visual Studio 2008。
    
  
- 创建、检索和更改用户配置文件对象的权限。（创建和修改配置文件需要"修改用户配置文件"权限。）
    
  

## 创建一个通过 SharePoint 2013 服务器对象模型使用用户配置文件的控制台应用程序
<a name="bkmk_CreateConsoleApp"> </a>


1. 打开 Visual Studio 并选择"文件"、"新建"、"项目"。
    
  
2. 在"新建项目"对话框中，从对话框的顶部下拉列表中选择".NET Framework 4.5"。
    
  
3. 在"模板"列表中，选择"窗口"，然后选择"控制台应用程序"。
    
  
4. 将项目命名为 UserProfilesSSOM，然后选择"确定"按钮。
    
    > **注释**
      > 请确保未在项目的"生成"属性中选择"首选 32 位"设置。 
5. 将引用添加到以下程序集：
    
  - Microsoft.Office.Server
    
  
  - Microsoft.Office.Server.UserProfiles
    
  
  - Microsoft.SharePoint
    
  
  - System.Web
    
  
6. 将 **Program** 类的内容替换为以下其中一个方案的代码示例：
    
  -  [创建用户配置文件](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_CreateUP)
    
  
  -  [创建用户配置文件属性](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_CreateUPProp)
    
  
  -  [检索和更改用户配置文件](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_GetChangeUP)
    
  
  -  [检索和更改用户配置文件属性 (Property) 的属性 (Attribute)](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_GetChangePropAttributes)
    
  
  -  [检索和更改用户属性的值](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_GetChangePropValues)
    
  
7. 要测试控制台应用程序，请在菜单栏上，依次选择"调试"和"开始调试"。可以在管理中心的 User Profile Service 应用程序的"管理配置文件服务"页中查看您的更改。
    
  

## 代码示例：使用 SharePoint 2013 服务器对象模型创建用户配置文件
<a name="bkmk_CreateUP"> </a>

在 SharePoint 2013 中，用户配置文件表示 SharePoint 用户。配置文件类型和子类型有助于将配置文件划分到各个组中，例如员工或客户。配置文件类型和子类型用于在子类型级别设置常见配置文件属性 (Property) 和属性 (Attribute)。SharePoint Server 包括默认用户配置文件子类型。
  
    
    
以下代码示例创建一个与默认用户配置文件子类型关联的  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) 对象。一些用户配置文件属性中将自动填入从包含用户帐户的目录（例如 Active Directory 域服务）导入的信息。有关创建自定义子类型的代码示例，请参阅 [ProfileSubtype](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtype.aspx) 。
  
    
    

> **注释**
> 在运行代码之前，请更改 domain\\\\username 和servername 占位符值。
  
    
    




```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.Office.Server;
using Microsoft.Office.Server.UserProfiles;
using Microsoft.SharePoint;
using System.Web;
namespace UserProfilesSSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace "domain\\\\username" and "servername" with actual values.
            string newAccountName = "domain\\\\username";
            using (SPSite site = new SPSite("http://servername"))
            {
                SPServiceContext serviceContext = SPServiceContext.GetContext(site);
                try
                {

                    // Create a user profile that uses the default user profile
                    // subtype.
                    UserProfileManager userProfileMgr = new UserProfileManager(serviceContext);
                    UserProfile userProfile = userProfileMgr.CreateUserProfile(newAccountName);

                    Console.WriteLine("A profile was created for " + userProfile.DisplayName);
                    Console.Read();
                }

                catch (System.Exception e)
                {
                    Console.WriteLine(e.GetType().ToString() + ": " + e.Message);
                    Console.Read();
                }
            }
        }
    }
}
```


## 代码示例：使用 SharePoint 2013 服务器对象模型创建用户配置文件属性
<a name="bkmk_CreateUPProp"> </a>

用户配置文件属性描述了有关用户的个人和组织信息。您可以创建自定义配置文件属性并将其添加到默认的 SharePoint 配置文件属性集。
  
    
    
配置文件属性及其属性由一组已链接的对象表示：一个  [CoreProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.aspx) 对象，一个 [ProfileTypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.aspx) 对象和一个 [ProfileSubtypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.aspx) 对象。
  
    
    
以下代码示例创建一个具有 URL 数据类型的  [CoreProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.aspx) 或一个（可选）具有多值字符串数据类型的 [CoreProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.aspx) 。此外，它创建一个 [ProfileTypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.aspx) 和一个 [ProfileTypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.aspx) （定义了该属性的可用性、隐私性和其他属性）。 [ProfileSubtypeProperty.DefaultPrivacy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.DefaultPrivacy.aspx) 属性控制属性和其他"我的网站"内容的可见性。有关配置文件属性值的可能数据类型的完整列表，请参阅 [PropertyDataType](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyDataType.aspx) 。
  
    
    

> **注释**
> 在运行代码之前，请更改 servername 占位符值。
  
    
    




```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.Office.Server;
using Microsoft.Office.Server.Administration;
using Microsoft.Office.Server.UserProfiles;
using Microsoft.SharePoint;
using System.Web;
namespace UserProfilesSSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace "servername" with an actual value.
            using (SPSite site = new SPSite("http://servername"))
            {
                SPServiceContext serviceContext = SPServiceContext.GetContext(site);
                try
                {
                    ProfilePropertyManager profilePropMgr = new UserProfileConfigManager(serviceContext).ProfilePropertyManager;
                    CorePropertyManager corePropMgr = profilePropMgr.GetCoreProperties();

                    // Create a URL property.
                    CoreProperty coreProp = corePropMgr.Create(false);
                    coreProp.Name = "AppsWebsite";
                    coreProp.DisplayName = "Apps site";
                    coreProp.Type = PropertyDataType.URL;
                    coreProp.Length = 100;
                    corePropMgr.Add(coreProp);

                    //// Create a multivalue property.
                    //// To create this property, comment out the previous
                    //// block of code and uncomment this block of code.
                    //CoreProperty coreProp = corePropMgr.Create(false);
                    //coreProp.Name = "PublishedAppsList";
                    //coreProp.DisplayName = "Published apps";
                    //coreProp.Type = PropertyDataType.StringMultiValue;
                    //coreProp.IsMultivalued = true;
                    //coreProp.Length = 100;
                    //corePropMgr.Add(coreProp);

                    // Create a profile type property and make the core property 
                    // visible in the Details section page.
                    ProfileTypePropertyManager typePropMgr = profilePropMgr.GetProfileTypeProperties(ProfileType.User);
                    ProfileTypeProperty typeProp = typePropMgr.Create(coreProp);
                    typeProp.IsVisibleOnViewer = true;
                    typePropMgr.Add(typeProp);

                    // Create a profile subtype property.
                    ProfileSubtypeManager subtypeMgr = ProfileSubtypeManager.Get(serviceContext);
                    ProfileSubtype subtype = subtypeMgr.GetProfileSubtype(ProfileSubtypeManager.GetDefaultProfileName(ProfileType.User));
                    ProfileSubtypePropertyManager subtypePropMgr = profilePropMgr.GetProfileSubtypeProperties(subtype.Name);
                    ProfileSubtypeProperty subtypeProp = subtypePropMgr.Create(typeProp);
                    subtypeProp.IsUserEditable = true;
                    subtypeProp.DefaultPrivacy = Privacy.Public;
                    subtypeProp.UserOverridePrivacy = true;
                    subtypePropMgr.Add(subtypeProp);

                    Console.WriteLine("The properties were created.");
                    Console.Read();
                }

                catch (System.Exception e)
                {
                    Console.WriteLine(e.GetType().ToString() + ": " + e.Message);
                    Console.Read();
                }
            }
        }
    }
}
```


## 代码示例：使用 SharePoint 2013 服务器对象模型检索和更改用户配置文件
<a name="bkmk_GetChangeUP"> </a>

以下代码示例检索上下文中的所有用户配置文件，并更改用户的  [DisplayName](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.DisplayName.aspx) 属性的值。可使用 [UserProfile.Item](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.Item.aspx) 访问器访问大多数配置文件属性。
  
    
    

> **注释**
> 在运行代码之前，请更改 domain\\\\username 和servername 占位符值。
  
    
    


```cs

using System;
using System.Collections;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.Office.Server;
using Microsoft.Office.Server.UserProfiles;
using Microsoft.SharePoint;
using System.Web;
namespace UserProfilesSSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace "domain\\\\username" and "servername" with actual values.
            string targetAccountName = "domain\\\\username";
            using (SPSite site = new SPSite("http://servername"))
            {
                SPServiceContext serviceContext = SPServiceContext.GetContext(site);
                try
                {

                    // Retrieve and iterate through all of the user profiles in this context.
                    Console.WriteLine("Retrieving user profiles:");
                    UserProfileManager userProfileMgr = new UserProfileManager(serviceContext);
                    IEnumerator userProfiles = userProfileMgr.GetEnumerator();
                    while (userProfiles.MoveNext())
                    {
                        UserProfile userProfile = (UserProfile)userProfiles.Current;
                        Console.WriteLine(userProfile.AccountName);
                    }

                    // Retrieve a specific user profile. Change the value of a user profile property
                    // and save (commit) the change on the server.
                    UserProfile user = userProfileMgr.GetUserProfile(targetAccountName);
                    Console.WriteLine("\\nRetrieving user profile for " + user.DisplayName + ".");
                    user.DisplayName = "Pat";
                    user.Commit();
                    Console.WriteLine("\\nThe user\\'s display name has been changed.");
                    Console.Read();
                }

                catch (System.Exception e)
                {
                    Console.WriteLine(e.GetType().ToString() + ": " + e.Message);
                    Console.Read();
                }
            }
        }
    }
}
```


## 代码示例：使用 SharePoint 2013 服务器对象模型检索和更改用户配置文件属性 (Property) 的属性 (Attribute)
<a name="bkmk_GetChangePropAttributes"> </a>

以下代码示例检索一组表示特定用户属性 (Property) 及其属性 (Attribute) 的属性 (Property)，然后它将更改  [CoreProperty.DisplayName](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.DisplayName.aspx) 属性、 [ProfileTypeProperty.IsVisibleOnViewer](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.IsVisibleOnViewer.aspx) 属性和 [ProfileSubtypeProperty.PrivacyPolicy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.PrivacyPolicy.aspx) 属性。这些更改全局适用于属性集。 [ProfileSubtypeProperty.PrivacyPolicy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.PrivacyPolicy.aspx) 指定用户是否需要为属性提供值。 [PrivacyPolicy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.PrivacyPolicy.aspx) 仅适用于用户配置文件属性。
  
    
    

> **注释**
> 在运行代码之前，请更改 servername 占位符值。
  
    
    


```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.Office.Server;
using Microsoft.Office.Server.UserProfiles;
using Microsoft.SharePoint;
using System.Web;
namespace UserProfilesSSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace "servername" with an actual value.
            using (SPSite site = new SPSite("http://servername"))
            {
                SPServiceContext serviceContext = SPServiceContext.GetContext(site);
                try
                {
                    ProfilePropertyManager profilePropMgr = new UserProfileConfigManager(serviceContext).ProfilePropertyManager;
                    ProfileSubtypePropertyManager subtypePropMgr = profilePropMgr.GetProfileSubtypeProperties("UserProfile");

                    // Retrieve a specific property set (a profile subtype property and
                    // its associated core and profile type properties).
                    // Changing these properties affects all instances of this property set.
                    ProfileSubtypeProperty subtypeProp = subtypePropMgr.GetPropertyByName(PropertyConstants.Title);
                    CoreProperty coreProp = subtypeProp.CoreProperty;
                    ProfileTypeProperty typeProp = subtypeProp.TypeProperty;

                    Console.WriteLine("Property name: " + coreProp.DisplayName);
                    Console.WriteLine("IsVisibleOnViewer = " + typeProp.IsVisibleOnViewer);
                    Console.WriteLine("PrivacyPolicy = " + subtypeProp.PrivacyPolicy);
                    Console.WriteLine("Press Enter to change the values.");
                    Console.Read();

                    // Change attributes on the properties and save (commit) the changes
                    // on the server.
                    coreProp.DisplayName = "Position";
                    coreProp.Commit();
                    typeProp.IsVisibleOnViewer = true;
                    typeProp.Commit();
                    subtypeProp.PrivacyPolicy = PrivacyPolicy.OptOut;
                    subtypeProp.Commit();
                    Console.WriteLine("The property attributes have been changed.");
                    Console.Read();
                }

                catch (System.Exception e)
                {
                    Console.WriteLine(e.GetType().ToString() + ": " + e.Message);
                    Console.Read();
                }
            }
        }
    }
}
```


## 代码示例：使用 SharePoint 2013 服务器对象模型检索和更改用户属性的值
<a name="bkmk_GetChangePropValues"> </a>

以下代码示例检索所有 **UserProfile** 类型属性并检索特定用户的属性值。然后，它会更改单值 [PictureUrl](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyConstants.PictureUrl.aspx) 属性和多值 [PastProjects](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyConstants.PastProjects.aspx) 属性。有关配置文件属性名称常量的完整列表，请参阅 [PropertyConstants](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyConstants.aspx) 。
  
    
    

> **注释**
> 在运行代码之前，请更改 domain\\\\username、http://servername/docLib/pic.jpg 和servername 占位符值。
  
    
    


```cs

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.Office.Server;
using Microsoft.Office.Server.UserProfiles;
using Microsoft.SharePoint;
using System.Web;
namespace UserProfilesSSOM
{
    class Program
    {
        static void Main(string[] args)
        {

            // Replace "domain\\\\username," "http://servername/docLib/pic.jpg," and "servername" with actual values.
            string accountName = "domain\\\\username";
            string newPictureUrl = "http://servername/docLib/pic.jpg";
            using (SPSite site = new SPSite("http://servername"))
            {
                SPServiceContext serviceContext = SPServiceContext.GetContext(site);

                try
                {
                    UserProfileManager userProfileMgr = new UserProfileManager(serviceContext);
                    ProfilePropertyManager profilePropMgr = new UserProfileConfigManager(serviceContext).ProfilePropertyManager;
                   
                    // Retrieve all properties for the "UserProfile" profile subtype,
                    // and retrieve the property values for a specific user.
                    ProfileSubtypePropertyManager subtypePropMgr = profilePropMgr.GetProfileSubtypeProperties("UserProfile");
                    UserProfile userProfile = userProfileMgr.GetUserProfile(accountName);
                    IEnumerator<ProfileSubtypeProperty> userProfileSubtypeProperties = subtypePropMgr.GetEnumerator();
                    while (userProfileSubtypeProperties.MoveNext())
                    {
                        string propName = userProfileSubtypeProperties.Current.Name;
                        ProfileValueCollectionBase values = userProfile.GetProfileValueCollection(propName);
                        if (values.Count > 0)
                        {

                            // Handle multivalue properties.
                            foreach (var value in values)
                            {
                                Console.WriteLine(propName + ": " + value.ToString());
                            }
                        }
                        else
                        {
                            Console.WriteLine(propName + ": ");
                        }
                    }
                    Console.WriteLine("Press Enter to change the values.");
                    Console.Read();

                    // Change the value of a single-value user property.
                    userProfile[PropertyConstants.PictureUrl].Value = newPictureUrl;

                    // Add a value to a multivalue user property.
                    userProfile[PropertyConstants.PastProjects].Add((object)"Team Feed App");
                    userProfile[PropertyConstants.PastProjects].Add((object)"Social Ratings View Web Part");

                    // Save the changes to the server.
                    userProfile.Commit();
                    Console.WriteLine("The property values for the user have been changed.");
                    Console.Read();
                }

                catch (System.Exception e)
                {
                    Console.WriteLine(e.GetType().ToString() + ": " + e.Message);
                    Console.Read();
                }
            }
        }
    }
}
```


## 其他资源
<a name="bk_addresources"> </a>


-  [在 SharePoint 2013 中使用用户配置文件](work-with-user-profiles-in-sharepoint-2013.md)
    
  
-  [如何：使用 SharePoint 2013 中的 .NET 客户端对象模型检索用户配置文件属性](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [如何：在 SharePoint 2013 中使用 JavaScript 对象模型检索用户配置文件属性](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md)
    
  
-  [Microsoft.Office.Server.UserProfiles](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.aspx)
    
  

