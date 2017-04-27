---
title: [方法] SharePoint 2013 でサーバー オブジェクト モデルを使用して、ユーザー プロファイルと組織プロファイルを操作する
ms.prod: SHAREPOINT
ms.assetid: 13f16dc3-f652-4fb3-996b-5f2166236d2b
---


# [方法] SharePoint 2013 でサーバー オブジェクト モデルを使用して、ユーザー プロファイルと組織プロファイルを操作する
SharePoint 2013のユーザー プロファイルやユーザー プロファイル プロパティを SharePoint 2013のサーバー オブジェクト モデルを使用してプログラムによって作成、取得、変更する方法を説明します。
## SharePoint 2013のユーザー プロファイルとは

SharePoint 2013において、ユーザー プロファイルは SharePoint ユーザーを表します。ユーザー プロファイル プロパティは、そのユーザーに関する情報、またプロパティそのものに関する関する情報を表します。プロパティの例としては、ユーザーのアカウント名や電子メール アドレス、プロパティのデータ型などがあります。サーバー オブジェクト モデルを使用すると、ユーザー プロファイル、プロファイルのサブタイプ、プロファイルのプロパティをプログラムによって作成、取得、変更できます。
  
    
    

> **メモ**
> ユーザー プロファイルを操作するための一般的なプログラミング作業と、そうした作業の実行に使用する API の詳細については、「 [SharePoint 2013 のユーザー プロファイルの操作](work-with-user-profiles-in-sharepoint-2013.md)」を参照してください。 
  
    
    


## SharePoint 2013のサーバー オブジェクト モデルを使用してユーザー プロファイルを操作できる開発環境をセットアップするための前提条件
<a name="bkmk_Prereqs"> </a>

サーバー オブジェクト モデルを使用してユーザー プロファイルやユーザー プロファイル プロパティを操作するコンソール アプリケーションを作成するには、以下のものが必要です。
  
    
    

- SharePoint Server 2013 と、現在のユーザー用に作成されたプロファイル。
    
  
- Visual Studio 2012。
    
  
- ユーザー プロファイル オブジェクトを作成、取得、変更するための権限 (プロファイルを作成および変更するには、[ **Modify User Profiles**] 権限が必要です)。
    
  

## SharePoint 2013のサーバー オブジェクト モデルを使用してユーザー プロファイルを操作するコンソール アプリケーションを作成する
<a name="bkmk_CreateConsoleApp"> </a>


1. Visual Studio を開き、[ **ファイル**]、[ **[新規**]、[ **プロジェクト**] を選択します。
    
  
2. [ **新しいプロジェクト**] ダイアログ ボックスで、上部のドロップダウン リストから [ **.NET Framework 4.5**] を選択します。
    
  
3. [ **テンプレート**] リストで [ **Windows**] を選択し、さらに [ **コンソール アプリケーション**] を選択します。
    
  
4. プロジェクトの名前を UserProfilesSSOM に設定して、[ **OK**] ボタンをクリックします。
    
    > **メモ**
      > プロジェクトの [ **ビルド**] プロパティで [ **32 ビットを優先**] 設定が選択されていないことを確認します。 
5. 以下のアセンブリへの参照を追加します。
    
  - Microsoft.Office.Server
    
  
  - Microsoft.Office.Server.UserProfiles
    
  
  - Microsoft.SharePoint
    
  
  - System.Web
    
  
6. **Program** クラスの内容を、以下のシナリオのいずれかのコード例に置き換えます。
    
  -  [ユーザー プロファイルを作成する](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_CreateUP)
    
  
  -  [ユーザー プロファイル プロパティを作成する](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_CreateUPProp)
    
  
  -  [ユーザー プロファイルを取得および変更する](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_GetChangeUP)
    
  
  -  [ユーザー プロファイル プロパティの属性を取得および変更する](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_GetChangePropAttributes)
    
  
  -  [ユーザー プロパティの値を取得および変更する](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md#bkmk_GetChangePropValues)
    
  
7. コンソール アプリケーションをテストするには、メニュー バーの [ **デバッグ**] を選択し、[ **デバッグ開始**] をクリックします。変更した内容は、[ **プロファイル サービスの管理**] ページから、サーバー全体の管理のユーザー プロファイル サービス アプリケーションで確認できます。
    
  

## コード例: SharePoint 2013のサーバー オブジェクト モデルを使用してユーザー プロファイルを作成する
<a name="bkmk_CreateUP"> </a>

SharePoint 2013において、ユーザー プロファイルは SharePoint ユーザーを表します。プロファイルのタイプおよびサブタイプは、プロファイルを従業員や顧客のようなグループに分類する際に役立ちます。プロファイルのタイプとサブタイプは、共通のプロファイル プロパティを設定したり、属性をサブタイプのレベルで設定したりするために使用されます。SharePoint Server には、既定のユーザー プロファイル サブタイプが用意されています。
  
    
    
次のコード例は、既定のユーザー プロファイル サブタイプに関連付けられた  [UserProfile](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.aspx) オブジェクトを作成します。ユーザー プロファイル プロパティの一部は、Active Directory ドメイン サービス など、ユーザー アカウントを含むディレクトリからインポートされた情報に基づいて自動的に設定されます。カスタム サブタイプを作成するコード例については、 [ProfileSubtype](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtype.aspx) を参照してください。
  
    
    

> **メモ**
> コードを実行する前に、domain\\\\username およびservername のプレースホルダー値を変更してください。
  
    
    




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


## コード例: SharePoint 2013 サーバー オブジェクト モデルを使用してユーザー プロファイル プロパティを作成する
<a name="bkmk_CreateUPProp"> </a>

ユーザー プロファイル プロパティは、ユーザーに関する個人または組織の情報を記述します。カスタム プロファイル プロパティを作成して、SharePoint プロファイル プロパティの既定のセットに追加することができます。
  
    
    
プロファイル プロパティとその属性は、リンクされた一連のオブジェクト ( [CoreProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.aspx) オブジェクト、 [ProfileTypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.aspx) オブジェクト、 [ProfileSubtypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.aspx) オブジェクト) によって表されます。
  
    
    
以下のコード例は、URL データ型を持つ  [CoreProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.aspx) を作成しています (また任意で、複数値の文字列データ型を持つ [CoreProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.aspx) を作成しています)。さらに、状態、プライバシー、およびプロパティのその他の設定を定義する [ProfileTypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.aspx) および [ProfileTypeProperty](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.aspx) を作成しています。 [ProfileSubtypeProperty.DefaultPrivacy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.DefaultPrivacy.aspx) プロパティは、プロパティおよびその他の個人用サイトのコンテンツの表示/非表示を制御します。プロファイル プロパティ値として可能なデータ型の完全な一覧については、 [PropertyDataType](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyDataType.aspx) を参照してください。
  
    
    

> **メモ**
> コードを実行する前に、servername プレースホルダー値を変更してください。
  
    
    




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


## コード例: SharePoint 2013のサーバー オブジェクト モデルを使用してユーザー プロファイルを取得および変更する
<a name="bkmk_GetChangeUP"> </a>

次のコード例は、コンテキスト内のすべてのユーザー プロファイルを取得し、ユーザーの  [DisplayName](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.DisplayName.aspx) プロパティの値を変更します。ほとんどのプロファイル プロパティには [UserProfile.Item](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.UserProfile.Item.aspx) アクセサーを使用してアクセスします。
  
    
    

> **メモ**
> コードを実行する前に、domain\\\\username およびservername のプレースホルダー値を変更してください。
  
    
    


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


## コード例: SharePoint 2013 サーバー オブジェクト モデルを使用してユーザー プロファイル プロパティの属性を取得および変更する
<a name="bkmk_GetChangePropAttributes"> </a>

以下のコード例は、特定のユーザー プロパティとその属性を表すプロパティのセットを取得し、その後、 [CoreProperty.DisplayName](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.CoreProperty.DisplayName.aspx) 属性、 [ProfileTypeProperty.IsVisibleOnViewer](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileTypeProperty.IsVisibleOnViewer.aspx) 属性、および [ProfileSubtypeProperty.PrivacyPolicy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.PrivacyPolicy.aspx) 属性を変更しています。これらの変更はプロパティのセットにグローバルに適用されます。 [ProfileSubtypeProperty.PrivacyPolicy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.PrivacyPolicy.aspx) はユーザーがそのプロパティの値を入力する必要があるかどうかを指定しています。 [PrivacyPolicy](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.ProfileSubtypeProperty.PrivacyPolicy.aspx) はユーザー プロファイル プロパティにのみ適用されます。
  
    
    

> **メモ**
> コードを実行する前に、servername プレースホルダー値を変更してください。
  
    
    


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


## コード例: SharePoint 2013 サーバー オブジェクト モデルを使用してユーザー プロパティの値を変更および取得する
<a name="bkmk_GetChangePropValues"> </a>

以下のコード例は、すべての **UserProfile** 型プロパティを取得し、特定のユーザーのプロパティ値を取得しています。その後、単一値の [PictureUrl](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyConstants.PictureUrl.aspx) プロパティ、および複数値の [PastProjects](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyConstants.PastProjects.aspx) プロパティを変更しています。プロファイル プロパティ名定数の完全な一覧については、 [PropertyConstants](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.PropertyConstants.aspx) を参照してください。
  
    
    

> **メモ**
> コードを実行する前に、domain\\\\username、http://servername/docLib/pic.jpg、および servername のプレースホルダー値を変更してください。
  
    
    


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


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 のユーザー プロファイルの操作](work-with-user-profiles-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してユーザー プロファイル プロパティを取得する](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [SharePoint 2013 で JavaScript オブジェクトモデルを使用して、ユーザー プロファイル プロパティを取得する方法](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md)
    
  
-  [Microsoft.Office.Server.UserProfiles](https://msdn.microsoft.com/library/Microsoft.Office.Server.UserProfiles.aspx)
    
  

