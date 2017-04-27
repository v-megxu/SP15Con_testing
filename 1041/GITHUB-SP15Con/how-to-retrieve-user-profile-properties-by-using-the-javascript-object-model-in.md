---
title: SharePoint 2013 で JavaScript オブジェクトモデルを使用して、ユーザー プロファイル プロパティを取得する方法
ms.prod: SHAREPOINT
ms.assetid: c6e1ca38-134f-428a-8d21-b8b2615b161b
---


# SharePoint 2013 で JavaScript オブジェクトモデルを使用して、ユーザー プロファイル プロパティを取得する方法
SharePoint 2013 JavaScript オブジェクト モデルを使用して、プログラムによるユーザー プロパティとユーザー プロファイル プロパティを取得する方法について説明します。
## SharePoint 2013 のユーザー プロパティとユーザー プロファイル プロパティとは
<a name="bkmk_WhatIs"> </a>

ユーザー プロパティとユーザー プロファイル プロパティは、表示名、電子メール、肩書き、その他のビジネス情報や個人情報など、SharePoint ユーザーに関する情報を提供します。クライアント側の API では、 [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) オブジェクトとその [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) プロパティから、これらのプロパティにアクセスします。 [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) プロパティにはすべてのユーザー プロファイル プロパティが含まれていますが、 [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) オブジェクトには一般的に使われるプロパティ ( [accountName](http://msdn.microsoft.com/library/ad1551bf-dad8-d54e-880a-8a4388fad44e%28Office.15%29.aspx)、 [displayName](http://msdn.microsoft.com/library/ffc35ed6-5f3e-c86d-6931-97ff9d825a8b%28Office.15%29.aspx)、 [email](http://msdn.microsoft.com/library/74302f73-aaf6-920b-0605-812b0dbf4568%28Office.15%29.aspx) など) が含まれていて、より簡単にアクセスできます。
  
    
    
 [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) オブジェクトには、JavaScript オブジェクト モデルを使用してユーザー プロパティとユーザー プロファイル プロパティの取得に使用できる、次のメソッドが含まれています。
  
    
    

-  [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) メソッドと [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) メソッドは、 [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) オブジェクトを返します。
    
  
-  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) メソッドと [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) メソッドは、指定したユーザー プロファイル プロパティの値を返します。
    
  
クライアント UPI からのユーザー プロファイル プロパティは読み取り専用です (プロファイルのイメージは除きます。これは  [PeopleManager.setMyProfilePicture](http://msdn.microsoft.com/library/a4f8d745-f211-e750-4fd0-047091804683%28Office.15%29.aspx) メソッドを使用することで変更できます)。他のユーザー プロファイル プロパティを変更するには、サーバー オブジェクト モデルを使用する必要があります。ユーザー プロファイルの操作の詳細については、「 [SharePoint 2013 のユーザー プロファイルの操作](work-with-user-profiles-in-sharepoint-2013.md)」を参照してください。
  
    
    

> **メモ**
> クライアント側の  [UserProfile](http://msdn.microsoft.com/library/f8c4a219-fbaa-2e50-1bd5-fdc80051b33d%28Office.15%29.aspx) オブジェクトには、サーバー側のバージョンにあるユーザー プロパティのすべては含まれていません。ただし、クライアント側バージョンは、現在のユーザーの個人サイトを作成するメソッドを提供します。それを取得するには、 [ProfileLoader.getUserProfile](http://msdn.microsoft.com/library/8e30e811-5da1-b6d0-a8b5-befea9b22496%28Office.15%29.aspx) メソッドを使用します。
  
    
    


## SharePoint 2013 JavaScript オブジェクト モデルを使用してユーザー プロパティを取得するための開発環境をセットアップするための前提条件
<a name="bk_Prereqs"> </a>

JavaScript オブジェクト モデルを使用するアプリケーション ページを作成してユーザー プロパティを取得するには、以下のものが必要です。
  
    
    

- 現在のユーザーとターゲット ユーザーに対して作成されたプロファイルがある SharePoint Server 2013
    
  
- Visual Studio 2012
    
  
- Office Developer Tools for Visual Studio 2013
    
  
- 現在のユーザーのユーザー プロファイル サービス アプリケーションにアクセスするための **フル コントロール**接続権限
    
  

## Visual Studio 2012 でのアプリケーション ページの作成
<a name="bk_CreateAppPage"> </a>


1. SharePoint Server 2013 を実行しているサーバーで Visual Studio を開き、[ **ファイル**]、[ **新規作成**]、[ **プロジェクト**] の順に選択します。
    
  
2. [ **新しいプロジェクト**] ダイアログ ボックスで、ダイアログ ボックスの上にあるドロップダウン リストから [ **.NET Framework 4.5**] を選択します。
    
  
3. [ **テンプレート**] リストで、[ **Office/SharePoint**] を展開し、[ **SharePoint ソリューション**] カテゴリを選択し、[ **SharePoint 2013 プロジェクト**] テンプレートを選択します。
    
  
4. プロジェクトに「UserProfilesJSOM」という名前を付け、[ **OK**] ボタンを選択します。
    
  
5. [ **SharePoint カスタマイズ ウィザード**] ダイアログ ボックスに、ターゲットの SharePoint サイトの URL を入力し、[ **ファーム ソリューションとして配置する**]、[ **完了**] ボタンの順に選択します。
    
  
6. [ **ソリューション エクスプローラー**] で 「UserProfilesJSOM」プロジェクトのショートカット メニューを開き、SharePoint「レイアウト」マップ フォルダーを追加します。
    
  
7. [ **レイアウト**] フォルダーで「UserProfilesJSOM」フォルダーのショートカット メニューを開き、「UserProfiles.aspx」という名前の新しい SharePoint アプリケーション ページを追加します。
    
    > **メモ**
      > この記事のコード例は、ページ マークアップでカスタム コードを定義していますが、ページ用に Visual Studio が生成する分離コード クラス ファイルは使用しません。 
8. UserProfiles.aspx ページのショートカット メニューを開き、[ **スタートアップ アイテムとして設定**] を選択します。
    
  
9. UserProfiles.aspx ページのマークアップでは、"Main"の **asp:Content** タグ内に次のコードを貼り付けます。このコードは、クエリ結果を表示する **span** コントロール、SharePoint JavaScript クラス ライブラリ ファイルを参照する **SharePoint:ScriptLink** コントロール、カスタム ロジックを含めるための **script** タグを追加します。
    
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

10. ユーザー プロファイル プロパティを取得するロジックを追加するには、 **script** タグに囲まれたコメントを次のシナリオのいずれかのコード例と置き換えます。
    
  -  [PersonProperties オブジェクトとその userProfileProperties プロパティからユーザー プロファイル プロパティを取得する](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_examplePersonPropsObj)
    
  
  -  [getUserProfilePropertiesFor メソッドを使用して、一連のユーザー プロファイル プロパティを取得する](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_exampleGetUPMethod)
    
  
11. アプリケーション ページをテストするには、メニューバーで [ **デバッグ**]、[ **デバッグ開始**] の順に選択します。web.config ファイルを変更するように求められた場合は、[ **OK**] ボタンをクリックします。
    
  

## コード例: SharePoint 2013 JavaScript オブジェクト モデルで、PersonProperties オブジェクトとその userProfileProperties プロパティからユーザー プロファイル プロパティを取得する
<a name="bk_examplePersonPropsObj"> </a>

次のコード例は、 [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) オブジェクトとその [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) プロパティをクエリすることで、ターゲット ユーザーのユーザー プロファイル プロパティを取得する方法を示しています。この例では以下の方法を示します。
  
    
    

-  [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) メソッドを使用して、ターゲット ユーザーを表す [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) オブジェクトを取得します (現在のユーザーの [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) オブジェクトを取得するには、 [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) メソッドを使用します。)
    
  
-  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) オブジェクトから直接プロパティを取得します。この例では、 [displayName](http://msdn.microsoft.com/library/ffc35ed6-5f3e-c86d-6931-97ff9d825a8b%28Office.15%29.aspx) プロパティを取得します。
    
  
-  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx)オブジェクトの  [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) プロパティからプロパティを取得します。この例では、 **Department** プロパティを取得します。
    
  

> **メモ**
>  [アプリケーション ページの作成](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_CreateAppPage)手順で UserProfiles.aspx ファイルに追加した **script** タグ間に、次のコードを貼り付けます。コードを実行する前に、 `domainName\\\\userName` プレースホルダーの値を置き換えます (このコード例では、分離コード クラス ファイルは使用しません)。
  
    
    


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


## コード例: SharePoint 2013 JavaScript オブジェクト モデルの GetUserProfilePropertiesFor メソッドを使用して一連のユーザー プロファイル プロパティを取得する
<a name="bk_exampleGetUPMethod"> </a>

次のコード例では、 [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) メソッドを使用して、ターゲット ユーザーの指定された一連のユーザー プロファイル プロパティの値を取得します。この例では、以下の方法を示します。
  
    
    

- 取得するターゲット ユーザーとユーザー プロファイル プロパティを指定する [UserProfilePropertiesForUser](http://msdn.microsoft.com/library/97bc94ec-62c8-dc38-d204-c5ad9ee8faee%28Office.15%29.aspx) オブジェクトを作成します。この例では、 **PreferredName** プロパティと **Department** プロパティを取得します。
    
  
-  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) メソッドを使用し、 [UserProfilePropertiesForUser](http://msdn.microsoft.com/library/97bc94ec-62c8-dc38-d204-c5ad9ee8faee%28Office.15%29.aspx) オブジェクトで渡すことで、指定されたプロパティの値を取得します (1 つのユーザー プロファイル プロパティの値だけを取得するには、 [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) メソッドを使用します)。
    
  
- 返されたプロパティ値の配列から値を取得します。
    
  

> **メモ**
>  [アプリケーション ページの作成](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_CreateAppPage)手順で UserProfiles.aspx ファイルに追加した **script** タグ間に次のコードを貼り付けます。コードを実行する前に、 `domainName\\\\userName` プレースホルダーの値を置き換えてください (このコード例では、分離コード クラス ファイルは使用しません)。
  
    
    


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


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 のユーザー プロファイルの操作](work-with-user-profiles-in-sharepoint-2013.md)
    
  
-  [[方法] SharePoint 2013 の .NET クライアント オブジェクト モデルを使用してユーザー プロファイル プロパティを取得する](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [[方法] SharePoint 2013 でサーバー オブジェクト モデルを使用して、ユーザー プロファイルと組織プロファイルを操作する](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)
    
  
-  [SP へユーザーの名前空間 (sp.userprofiles)](http://msdn.microsoft.com/library/8c1fcceb-cd9a-b25c-32f4-1cfb0578278c%28Office.15%29.aspx)
    
  

