---
title: Инструкции. Получение свойств профиля пользователя с помощью объектной модели JavaScript в SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: c6e1ca38-134f-428a-8d21-b8b2615b161b
---


# Инструкции. Получение свойств профиля пользователя с помощью объектной модели JavaScript в SharePoint 2013
Узнайте, как получать свойства пользователей и их профилей программным способом с помощью объектной модели SharePoint 2013 JavaScript.
## Что такое свойства пользователей и их профилей в SharePoint 2013?
<a name="bkmk_WhatIs"> </a>

Свойства пользователей и их профилей предоставляют сведения о пользователях SharePoint, например отображаемое имя, адрес электронной почты, должность, а также другие рабочие и личные сведения. В клиентских интерфейсах API доступ к этим свойствам можно получить с помощью объекта  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) и его свойства [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx). Свойство  [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) содержит все свойства профиля пользователя, но объект [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) содержит часто используемые свойства (например, [accountName](http://msdn.microsoft.com/library/ad1551bf-dad8-d54e-880a-8a4388fad44e%28Office.15%29.aspx),  [displayName](http://msdn.microsoft.com/library/ffc35ed6-5f3e-c86d-6931-97ff9d825a8b%28Office.15%29.aspx) и [email](http://msdn.microsoft.com/library/74302f73-aaf6-920b-0605-812b0dbf4568%28Office.15%29.aspx)), к которым легче получить доступ.
  
    
    
Объект  [PeopleManager](http://msdn.microsoft.com/library/985fd2df-0e31-6ece-b846-ba2ccb156d00%28Office.15%29.aspx) включает следующие методы, которые можно использовать для получения свойств пользователей и их профилей с помощью объектной модели JavaScript:
  
    
    

- Методы  [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx) и [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx) возвращают объект [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx).
    
  
- Методы  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx) и [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx) возвращают значения свойств профиля пользователя, которые можно указать.
    
  
Свойства профиля пользователя из клиентских интерфейсов API доступны только для чтения (за исключением изображения профиля, которое можно изменить с помощью метода  [PeopleManager.setMyProfilePicture](http://msdn.microsoft.com/library/a4f8d745-f211-e750-4fd0-047091804683%28Office.15%29.aspx)). Чтобы изменить другие свойства профиля пользователя, необходимо использовать серверную объектную модель. Дополнительные сведения о работе с профилями пользователей см. в статье  [Работа с профилями пользователей в SharePoint 2013](work-with-user-profiles-in-sharepoint-2013.md).
  
    
    

> **Примечание**
> Клиентский объект  [UserProfile](http://msdn.microsoft.com/library/f8c4a219-fbaa-2e50-1bd5-fdc80051b33d%28Office.15%29.aspx) содержит не все свойства пользователей, доступные в серверной версии. Тем не менее, в клиентской версии предусмотрены методы для создания личного сайта для текущего пользователя. Чтобы получить его, используйте метод [ProfileLoader.getUserProfile](http://msdn.microsoft.com/library/8e30e811-5da1-b6d0-a8b5-befea9b22496%28Office.15%29.aspx). 
  
    
    


## Необходимые условия для настройки среды разработки для получения свойств пользователя с помощью объектной модели SharePoint 2013 JavaScript
<a name="bk_Prereqs"> </a>

Чтобы создать страницу приложения, которая использует объектную модель JavaScript для получения свойств пользователей, вам потребуются:
  
    
    

- SharePoint Server 2013 с профилями для текущего пользователя и целевого пользователя;
    
  
- Visual Studio 2012
    
  
- Инструменты разработчика Office для Visual Studio 2013
    
  
- разрешения уровня **Полный доступ** для подключения к приложению-службе профиля текущего пользователя.
    
  

## Создание страницы приложения в Visual Studio 2012
<a name="bk_CreateAppPage"> </a>


1. На сервере под управлением SharePoint Server 2013 откройте Visual Studio и выберите команды **Файл**, **Создать**, **Проект**.
    
  
2. В верхней части диалогового окна **Новый проект** выберите **.NET Framework 4.5** в раскрывающемся списке.
    
  
3. В списке **Шаблоны** разверните узел **Office/SharePoint**, выберите категорию **Решения SharePoint**, а затем  шаблон **Проект SharePoint 2013**.
    
  
4. Назовите проект UserProfilesJSOM и нажмите кнопку **ОК**.
    
  
5. В диалоговом окне **Мастер настройки SharePoint** введите URL-адрес целевого сайта SharePoint, выберите **Развернуть как решение фермы** и нажмите кнопку **Готово**.
    
  
6. В **диспетчере решений** откройте контекстное меню для проектаUserProfilesJSOM и добавьте сопоставленную папку Layouts для SharePoint.
    
  
7. В папке **Layouts** откройте контекстное меню папкиUserProfilesJSOM и добавьте новую страницу приложения SharePoint под названиемUserProfiles.aspx.
    
    > **Примечание**
      > Примеры кода в этой статье задают пользовательский код в разметке страницы, но не используют файла класса программной части, который Visual Studio создает для страницы. 
8. Откройте контекстное меню для страницы UserProfiles.aspx и выберите пункт **Назначить запускаемым элементом**.
    
  
9. В разметке страницы UserProfiles.aspx вставьте приведенный ниже код в теги Main **asp:Content**. Этот код создает элемент управления **span**, который отображает результаты запроса, элементы управления **SharePoint:ScriptLink**, которые ссылаются на файлы библиотеки классов JavaScript в SharePoint, и теги **script** для пользовательской логики.
    
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

10. Чтобы добавить логику для получения свойств профиля пользователя, замените комментарий между тегами **script** примером кода из одного из следующих сценариев:
    
  -  [Получение свойств профиля пользователя из объекта PersonProperties и его свойства userProfileProperties](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_examplePersonPropsObj)
    
  
  -  [Получение набора свойств профиля пользователя с помощью метода getUserProfilePropertiesFor](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_exampleGetUPMethod)
    
  
11. Чтобы протестировать страницу приложения, в панели меню выберите команды **Отладка**, **Начать отладку**. Если вам будет предложено изменить файл web.config, нажмите кнопку **ОК**.
    
  

## Пример кода. Получение свойств профиля пользователя из объекта PersonProperties и его свойства userProfileProperties в объектной модели SharePoint 2013 JavaScript
<a name="bk_examplePersonPropsObj"> </a>

В приведенном ниже примере кода показано, как получить свойства профиля целевого пользователя с помощью запроса к объекту  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) и его свойству [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx). Он показывает, как:
  
    
    

- получить объект  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx), который представляет целевого пользователя, с помощью метода  [getPropertiesFor](http://msdn.microsoft.com/library/097464db-2630-4c7a-fd0c-0f333680b5a4%28Office.15%29.aspx). Чтобы получить объект  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx) для текущего пользователя, используйте метод [getMyProperties](http://msdn.microsoft.com/library/be001abc-a431-8d48-8e6f-161251aa19ac%28Office.15%29.aspx);
    
  
- получить свойство непосредственно из объекта  [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx). Этот пример получает свойство  [displayName](http://msdn.microsoft.com/library/ffc35ed6-5f3e-c86d-6931-97ff9d825a8b%28Office.15%29.aspx);
    
  
- получить свойство из свойства  [userProfileProperties](http://msdn.microsoft.com/library/56516666-7425-4993-222f-f745cf266e89%28Office.15%29.aspx) объекта [PersonProperties](http://msdn.microsoft.com/library/0274d97f-b697-f436-2aaf-f5bcf9b70df8%28Office.15%29.aspx). Этот пример получает свойство **Department**.
    
  

> **Примечание**
> Вставьте приведенный ниже код между тегами **script**, добавленными в файл UserProfiles.aspx в разделе  [Создание страницы приложения](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_CreateAppPage). Прежде чем запускать код, замените значение  `domainName\\\\userName`. В этом примере кода не используется файл класса программной части. 
  
    
    


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


## Пример кода. Получение набора свойств профиля пользователя с помощью метода getUserProfilePropertiesFor в объектной модели SharePoint 2013 JavaScript
<a name="bk_exampleGetUPMethod"> </a>

Приведенный ниже пример кода получает значения указанного набора свойств профиля целевого пользователя с помощью метод  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx). Он показывает, как:
  
    
    

- создать объект  [UserProfilePropertiesForUser](http://msdn.microsoft.com/library/97bc94ec-62c8-dc38-d204-c5ad9ee8faee%28Office.15%29.aspx), который задает целевого пользователя и получаемые свойства профиля. Этот пример получает свойства **PreferredName** и **Department**;
    
  
- получить значения указанных свойств с помощью метода  [getUserProfilePropertiesFor](http://msdn.microsoft.com/library/8674e96f-d320-4a50-1580-9a4568842ee5%28Office.15%29.aspx), передав их в объект  [UserProfilePropertiesForUser](http://msdn.microsoft.com/library/97bc94ec-62c8-dc38-d204-c5ad9ee8faee%28Office.15%29.aspx). Чтобы получить значение только одного свойства профиля пользователя, используйте метод  [getUserProfilePropertyFor](http://msdn.microsoft.com/library/da048bfa-54c6-8216-e8ef-09bd84f68d8d%28Office.15%29.aspx);
    
  
- получить значения из возвращенного массива значений свойств.
    
  

> **Примечание**
> Вставьте приведенный ниже код между тегами **script**, добавленными в файл UserProfiles.aspx в разделе  [Создание страницы приложения](how-to-retrieve-user-profile-properties-by-using-the-javascript-object-model-in.md#bk_CreateAppPage). Прежде чем запускать код, замените значение  `domainName\\\\userName`. В этом примере кода не используется файл класса программной части. 
  
    
    


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


## Дополнительные ресурсы
<a name="bk_addresources"> </a>


-  [Работа с профилями пользователей в SharePoint 2013](work-with-user-profiles-in-sharepoint-2013.md)
    
  
-  [Как: получение свойств профиля пользователя с помощью клиентской объектной модели .NET в SharePoint 2013](how-to-retrieve-user-profile-properties-by-using-the-net-client-object-model-in.md)
    
  
-  [Инструкции. Работа с профилями пользователей и организации с использованием объектной модели сервера в SharePoint 2013](how-to-work-with-user-profiles-and-organization-profiles-by-using-the-server-obj.md)
    
  
-  [SP.UserProfiles Пространства имен (sp.userprofiles)](http://msdn.microsoft.com/library/8c1fcceb-cd9a-b25c-32f4-1cfb0578278c%28Office.15%29.aspx)
    
  

