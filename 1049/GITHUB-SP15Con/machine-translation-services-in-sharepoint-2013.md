---
title: Службы машинного перевода в SharePoint 2013
ms.prod: SHAREPOINT
ms.assetid: 15a81428-da94-40b8-8ed4-6a12f05661e2
---


# Службы машинного перевода в SharePoint 2013
Сведения о Служба машинного перевода, новом приложении службы в SharePoint 2013, выполняющем автоматический машинный перевод для файлов и сайтов.
## Обзор Служба машинного перевода
<a name="TranslationSvc_Overview"> </a>


> **Примечание**
> Применение машинного перевода позволит пользователям отправлять содержимое корпорации Майкрософт для перевода. Майкрософт может применять отправленное пользователями содержимое для улучшения качества перевода. Если вы используете службу машинного перевода в своем приложении, вы несете ответственность за то, чтобы уведомить пользователей, что это приложение позволяет отправлять содержимое корпорации Майкрософт для перевода и что Майкрософт может применять отправленное пользователями содержимое для улучшения качества перевода. Дополнительные сведения см. в статье Политика переводчиков Майкрософт. 
  
    
    

Служба машинного перевода  новое приложение службы в SharePoint 2013 для автоматического машинного перевода текста в файлах и на сайтах. Когда Служба машинного перевода обрабатывает запрос на перевод, этот запрос пересылается в  [Microsoft Translator](http://www.microsoft.com/en-us/translator/), облачную службу машинного перевода. Она и выполняет фактический перевод. На базе этой службы основаны функции перевода также в Microsoft Office, Lync, Yammer и Bing.
  
    
    
Приложение Служба машинного перевода обрабатывает запросы на перевод асинхронно и синхронно. Асинхронные запросы на перевод обрабатываются при выполнении задания таймера для перевода. Интервал по умолчанию, заданный для такого задания, составляет 15 минут. Вы можете настроить его в Центре администрирования или с помощью Windows PowerShell. Кроме того, можно задать немедленное выполнение таймера с помощью такой команды:
  
    
    



```

$tj = get-sptimerjob "Sharepoint Translation Services"
$tj.Runnow()
```

Синхронные запросы на перевод обрабатываются по мере их отправки.
  
    
    

### Компоненты, общие с Word Automation Services
<a name="TranslationSvc_SharedWAS"> </a>

У архитектур Служба машинного перевода и Microsoft Word Automation Services есть некоторые общие компоненты. Дополнительные сведения об архитектуре Word Automation Services см. в статье  [Архитектура Word Automation Services](http://msdn.microsoft.com/library/567bf68d-46bb-4ee8-981d-186549b9e5b8%28Office.15%29.aspx).
  
    
    
Объектная модель Служба машинного перевода создана наподобие объектной модели Word Automation Services. Следовательно, если вы знакомы с программированием с использованием Word Automation Services, вы найдете сходства с программированием согласно объектной модели Служба машинного перевода.
  
    
    

## Использование серверной объектной модели Служба машинного перевода
<a name="TranslationSvc_ServerOM"> </a>

Приложения, использующие серверную объектную модель, должны работать непосредственно на сервере с SharePoint 2013. Сведения о том, как создавать приложения, которые можно разместить удаленно, см. в разделе  [Использование клиентской объектной модели Служба машинного перевода](#TranslationSvc_UsingCSOM) этой статьи. Серверная объектная модель Служба машинного перевода находится в пространстве имен **Microsoft.Office.TranslationServices** в Microsoft.Office.TranslationServices.dll.
  
    
    
Используя серверную объектную модель, вы можете отправлять запросы в приложение Служба машинного перевода асинхронно или синхронно (для срочного перевода). У приложения Служба машинного перевода есть две рабочие очереди для хранения запросов на перевод: асинхронная и синхронная. Запросы в синхронной очереди обрабатываются как запросы с более высоким приоритетом, то есть перевод выполняется ранее, чем по запросам в асинхронной очереди. Запросы передаются в одну из этих очередей на основании класса, который вы укажете.
  
    
    

  
    
    
![Связанные фрагменты кода и примеры приложений](images/mod_icon_links_samples.png)
  
    
    
Пример кода, демонстрирующий использование серверной объектной модели в консольном приложении, приведен в статье  [SharePoint 2013: доступ к службе машинного перевода с помощью серверной объектной модели](http://code.msdn.microsoft.com/SharePoint-2013-Access-86639c3d).
  
    
    

### Асинхронный перевод с помощью серверной объектной модели

Класс **TranslationJob** определяет набор элементов, которые необходимо перевести. Это может быть один или все файлы в папке либо библиотеке документов. Задания на перевод, которые отправляются таким образом, хранятся в базе данных переводов. Всякий раз, когда выполняется задание таймера для перевода, несколько заданий из базы данных переводов добавляются в асинхронную очередь для перевода. Интервал по умолчанию для такого задания таймера составляет 15 минут.
  
    
    
Приведенный ниже код показывает, как выполнять асинхронный перевод для одного файла.
  
    
    



```cs

SPServiceContext sc = SPServiceContext.GetContext(new SPSite(site));
TranslationJob job = new TranslationJob(sc, CultureInfo.GetCultureInfo(culture)); 
job.AddFile(input, output);
job.Start(); 

```

Приведенный ниже код показывает, как выполнять асинхронный перевод для всех файлов в папке.
  
    
    



```VB.net

SPServiceContext sc = SPServiceContext.GetContext(new SPSite(site));
TranslationJob job = new TranslationJob(sc, CultureInfo.GetCultureInfo(culture));
using (SPSite siteIn = new SPSite(inputFolder))
{
    using (SPWeb webIn = siteIn.OpenWeb())
    {
        using (SPWeb webOut = siteOut.OpenWeb())
        {
            SPFolder folderIn = webIn.GetFolder(inputFolder);
            SPFolder folderOut = webOut.GetFolder(outputFolder);                    
            job.AddFolder(folderIn, folderOut, true);
            job.Start();
        }
    }
}
```

Приведенный ниже код показывает, как выполнять асинхронный перевод для всех файлов в библиотеке документов.
  
    
    



```cs

SPServiceContext sc = SPServiceContext.GetContext(new SPSite(site));
TranslationJob job = new TranslationJob(sc, CultureInfo.GetCultureInfo(culture));
using (SPSite siteIn = new SPSite(inputList))
{
    using (SPWeb webIn = siteIn.OpenWeb())
    {
        using (SPSite siteOut = new SPSite(outputList))
        {
            using (SPWeb webOut = siteOut.OpenWeb())
            {
                SPDocumentLibrary listIn = (SPDocumentLibrary)webIn.GetList(inputList);
                SPDocumentLibrary listOut = (SPDocumentLibrary)webOut.GetList(outputList);
                job.AddLibrary(listIn, listOut);
                job.Start();
            }
        }
    }
}
```


### Синхронный перевод с помощью серверной объектной модели

Чтобы запросить срочный перевод для файлов и потоков, можно указать класс **SyncTranslator**. Запросы на перевод, которые выполняются с использованием этого класса, не передаются так же, как и запросы с использованием класса **TranslationJob**. Они немедленно добавляются в синхронную очередь для обработки. Класс **TranslationItemInfo** содержит сведения об отдельном элементе, перевод которого выполняется с помощью Служба машинного перевода. Метод **SyncTranslator.Translate** возвращает экземпляр этого класса в заданиях синхронного перевода.
  
    
    
Приведенный ниже код показывает, как выполнять синхронный перевод для одного файла.
  
    
    



```cs

SPServiceContext sc = SPServiceContext.GetContext(new SPSite(site));
SyncTranslator job = new SyncTranslator(sc, CultureInfo.GetCultureInfo(jobCulture));
TranslationItemInfo itemInfo = job.Translate(input, output);

```

Приведенный ниже код показывает, как выполнять синхронный перевод для потока.
  
    
    



```cs

SPServiceContext sc = SPServiceContext.GetContext(new SPSite(site));
SyncTranslator job = new SyncTranslator(sc, CultureInfo.GetCultureInfo(jobCulture));
FileStream inputStream = new FileStream(input, FileMode.Open);
FileStream outputStream = new FileStream(output, FileMode.Create);     
TranslationItemInfo itemInfo = job.Translate(inputStream, outputStream, fileFormat);
inputStream.Close();
outputStream.Flush();
outputStream.Close();

```

Приведенный ниже код показывает, как выполнять синхронный перевод для последовательности байтов.
  
    
    



```cs

SPServiceContext sc = SPServiceContext.GetContext(new SPSite(site));
SyncTranslator job = new SyncTranslator(sc, CultureInfo.GetCultureInfo(jobCulture));
Byte[] inputByte;
Byte[] outputByte;
inputByte = File.ReadAllBytes(input);
outputByte = null;
TranslationItemInfo itemInfo = job.Translate(inputByte, out outputByte, fileFormat);
FileStream outputStream = File.Open(output, FileMode.Create);
MemoryStream memoryStream = new MemoryStream(outputByte);
memoryStream.WriteTo(outputStream);
outputStream.Flush();
outputStream.Close();

```


### Разрешения
<a name="TranslationSvc_Permissions"> </a>

Если пользователь, для которого выполняется задание перевода, может получить доступ к файлу, который нужно перевести, и расположению соответствующих выходных данных, пользователь отменяет проверку безопасности, и выполняется перевод.
  
    
    

## Использование клиентской объектной модели Служба машинного перевода
<a name="TranslationSvc_UsingCSOM"> </a>

Служба машинного перевода также включает клиентскую объектную модель (CSOM), обеспечивающую доступ к API Служба машинного перевода для разработки с использованием локальной среды, мобильного устройства или Интернета. Клиентские приложения с помощью CSOM могут получать доступ к содержимому и функциональности на стороне сервера. CSOM реализует большинство возможностей перевода на стороне сервера, но между CSOM и серверной объектной моделью есть отличия. Асинхронный перевод поддерживается как для отдельных файлов, так и для файлов в библиотеке документов или папке. Синхронный перевод поддерживается только для файлов (не для потоков).
  
    
    
CSOM Служба машинного перевода включает управляемую CSOM .NET, а также объектные модели Microsoft Silverlight и JavaScript. Она создана на основе CSOM SharePoint 2013. Следовательно, код на стороне клиента сначала получает доступ к CSOM SharePoint 2013, а затем уже к CSOM Служба машинного перевода.
  
    
    
Дополнительные сведения о CSOM SharePoint см. в статье  [Клиентская объектная модель SharePoint 2010](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx). Дополнительные сведения об объекте **ClientContext**, представляющем собой точку входа в CSOM, см. в статье  [Контекст клиента как центральный объект](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx).
  
    
    
Таблица 1 показывает эквивалентные объекты, которые интерфейсы API CSOM предоставляют для объектов сервера Служба машинного перевода.
  
    
    

**Таблица 1. Интерфейсы API серверной объектной модели и их эквиваленты CSOM**


|**Сервер**|**Silverlight и управляемые модели .NET**|**JavaScript**|
|:-----|:-----|:-----|
|Microsoft.Office.TranslationServices.TranslationJob  <br/> |Microsoft.Office.TranslationServices.Client.TranslationJob  <br/> |SP.Translation.TranslationJob  <br/> |
|Microsoft.Office.TranslationServices.TranslationJobInfo  <br/> |Microsoft.Office.TranslationServices.Client.TranslationJobInfo  <br/> |SP.Translation.TranslationJobInfo  <br/> |
|Microsoft.Office.TranslationServices.TranslationItemInfo  <br/> |Microsoft.Office.TranslationServices.Client.TranslationItemInfo  <br/> |SP.Translation.TranslationItemInfo  <br/> |
|Microsoft.Office.TranslationServices.TranslationJobStatus  <br/> |Microsoft.Office.TranslationServices.Client.TranslationJobStatus  <br/> |SP.Translation.TranslationJobStatus  <br/> |
|Microsoft.Office.TranslationServices.SyncTranslator  <br/> |Microsoft.Office.TranslationServices.Client.SyncTranslator  <br/> |SP.Translation.SyncTranslator  <br/> |
   

### CSOM Silverlight и управляемые CSOM .NET для Служба машинного перевода
<a name="TranslationSvc_ManagedCSOM"> </a>

Для управляемых CSOM .NET получите экземпляр **ClientContext** (расположенный в пространстве имен **Microsoft.SharePoint.Client** из Microsoft.SharePoint.Client.dll). Затем воспользуйтесь объектной моделью в пространстве имен **Microsoft.Office.TranslationServices.Client** из Microsoft.Office.TranslationServices.Client.dll.
  
    
    

  
    
    
![Связанные фрагменты кода и примеры приложений](images/mod_icon_links_samples.png)
  
    
    
Пример кода, показывающий, как использовать управляемую CSOM .NET, приведен в статье  [SharePoint 2013: доступ к службе машинного перевода с помощью клиентской объектной модели](http://code.msdn.microsoft.com/SharePoint-2013-Perform-a-8e53b06a).
  
    
    
Для CSOM Silverlight получите экземпляр **ClientContext** (расположенный в пространстве имен **Microsoft.SharePoint.Client** из Microsoft.SharePoint.Client.Silverlight.dll). Затем воспользуйтесь объектной моделью в пространстве имен **Microsoft.Office.TranslationServices.Client** из Microsoft.Office.TranslationServices.Silverlight.dll.
  
    
    

  
    
    
![Связанные фрагменты кода и примеры приложений](images/mod_icon_links_samples.png)
  
    
    
Пример кода, показывающий, как использовать CSOM Silverlight, см. в статье  [SharePoint 2013: доступ к службе машинного перевода из приложения Silverlight](http://code.msdn.microsoft.com/SharePoint-2013-Access-cdaff6b2).
  
    
    
Чтобы выполнить асинхронный перевод для отдельного файла:
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
string culture  = "cultureID";
string name = "translationJobName";
string  inputFile =  "http://serverName/path/inputFileName";
string outputFile = "http://serverName/path/outputFileName";
TranslationJob job = new TranslationJob(clientContext , culture);
job.AddFile(inputFile , outputFile);
job.Name = name;
job.Start();
clientContext.Load(job);
clientContext.ExecuteQuery();
//To retrieve the translation job ID.
string jobID = job.JobId;
```

Чтобы выполнить асинхронный перевод для папки:
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
string culture = "cultureID";
string name = "translationJobName";
string inputFolder = clientContext.Web.GetFolderByServerRelativeUrl("inFolderPath");
string outputFolder = clientContext.Web.GetFolderByServerRelativeUrl("outFolderPath");  
TranslationJob job = new TranslationJob(clientContext , culture);
job.AddFolder(inputFolder, outputFolder, true);
job.Name = name;
job.Start();            
clientContext.Load(job);
clientContext.ExecuteQuery();
//To retrieve the translation job ID.
string jobID = job.JobId;
```

Чтобы выполнить асинхронный перевод для библиотеки:
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
string culture = "cultureID";
string name = "translationJobName";
string inputLibrary = clientContext.Web.Lists.GetByTitle("inputLibraryName");
string outputLibrary = clientContext.Web.Lists.GetByTitle("outputLibraryName");
TranslationJob job = new TranslationJob(clientContext , culture);
job.AddFolder(inputLibrary , outputLibrary , true);
job.Name = name;
job.Start();            
clientContext.Load(job);
clientContext.ExecuteQuery();
//To retrieve the translation job ID.
string jobID = job.JobId;
```

Чтобы выполнить синхронный перевод для отдельного файла:
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
string culture = "cultureID"
string inputFile = "http://serverName/path/inputFileName";
string outputFile = "http://serverName/path/outputFileName";
SyncTranslator job = new SyncTranslator(clientContext , culture);
job.OutputSaveBehavior = SaveBehavior.AlwaysOverwrite;
ClientResult<TranslationItemInfo> cr = job.Translate(inputFile, outputFile );
clientContext.ExecuteQuery(); 
//To retrieve additional information about the translation job.
string errorCode = clientContext.Value.ErrorCode;
string errorMessage = clientContext.Value.ErrorMessage;
string translateID = clientContext.Value.TranslationId;
string succeedResult  = clientContext.Value.Succeeded;
string failResult  = clientContext.Value.Failed;
string cancelStatus = clientContext.Value.Canceled;
string inProgressStatus = clientContext.Value.InProgress;
string notStartedStatus = clientContext.Value.NotStarted;
```

Чтобы получить все языки, которые Служба машинного перевода поддерживает:
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
IEnumerable<string> supportedLanguages = TranslationJob.EnumerateSupportedLanguages(clientContext);
clientContext.ExecuteQuery();
foreach (string item in supportedLanguages)
{
    Console.Write(item + ", ");
}
```

Чтобы проверить, поддерживается ли конкретный язык:
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
clientResult<bool> isSupported;
isSupported = TranslationJob.IsLanguageSupported(clientContext, "language");
clientContext.ExecuteQuery();
```

Чтобы получить все расширения файлов, которые Служба машинного перевода поддерживает:
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
IEnumerable<string> fileExt = TranslationJob.EnumerateSupportedFileExtensions(clientContext);
clientContext.ExecuteQuery();
foreach (string item in fileExt)
{
    Console.Write(item + ", ");
}
```

Чтобы проверить, поддерживается ли конкретное расширение файла:
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
clientResult<bool> isSupported;
isSupported = TranslationJob.IsFileExtensionSupported(clientContext, "fileExtension");
clientContext.ExecuteQuery();

```

Чтобы проверить ограничение на размер файлов для конкретного расширения файла:
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
clientResult<int> maxSize;
maxSize = TranslationJob.GetMaximumFileSize(clientContext, "fileExtension");
clientContext.ExecuteQuery();
```


### CSOM JavaScript для Служба машинного перевода
<a name="TranslationSvc_JavaScriptCSOM"> </a>

Для CSOM JavaScript получите экземпляр **SP.ClientContext**, а затем воспользуйтесь объектной моделью в файле SP.Translation.js.
  
    
    

  
    
    
![Связанные фрагменты кода и примеры приложений](images/mod_icon_links_samples.png)
  
    
    
Пример кода, показывающий, как использовать CSOM JavaScript, см. в статье  [SharePoint 2013: доступ к службе машинного перевода с помощью JavaScript](http://code.msdn.microsoft.com/SharePoint-2013-Accessing-647f6dd9).
  
    
    
Чтобы выполнить асинхронный перевод для отдельного файла:
  
    
    



```

var asyncJob;
var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
asyncJob = SP.Translation.TranslationJob.newObject(clientContext, "cultureID");
asyncJob.set_outputSaveBehavior(SP.Translation.SaveBehavior.alwaysOverwrite);
asyncJob.addFile("inputFilePath", "outputFilePath");
asyncJob.set_name("translationJobName");
asyncJob.start();
clientContext.load(asyncJob);
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededASync),Function.createDelegate(this, this.onQueryFailed));
```

Чтобы выполнить асинхронный перевод для папки:
  
    
    



```

var asyncJob;
var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
asyncJob = SP.Translation.TranslationJob.newObject(clientContext, "cultureID");
asyncJob.set_outputSaveBehavior(SP.Translation.SaveBehavior.alwaysOverwrite);
var inputFolder = clientContext.get_web().getFolderByServerRelativeUrl("inputFilePath");
var outputFolder = clientContext.get_web().getFolderByServerRelativeUrl("outputFilePath");
asyncJob.addFolder(inputFolder, outputFolder, true);
asyncJob.set_name("translationJobName");
asyncJob.start();
clientContext.load(asyncJob);
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededASync),Function.createDelegate(this, this.onQueryFailed));
```

Чтобы выполнить асинхронный перевод для библиотеки:
  
    
    



```

var asyncJob;
var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
asyncJob = SP.Translation.TranslationJob.newObject(clientContext, "cultureID");
asyncJob.set_outputSaveBehavior(SP.Translation.SaveBehavior.alwaysOverwrite);
var inputLibrary= clientContext.get_web().get_lists().getByTitle("inputFilePath");
var outputLibrary= clientContext.get_web().get_lists().getByTitle("outputFilePath");
asyncJob.addLibrary(inputLibrary, outputLibrary);
asyncJob.set_name("translationJobName");
asyncJob.start();
clientContext.load(asyncJob);
clientContext.executeQueryAsync(Function.createDelegate(this,this.onQuerySucceededASync),Function.createDelegate(this, this.onQueryFailed));
```

Чтобы выполнить синхронный перевод для отдельного файла:
  
    
    



```

var result;
var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var job = SP.Translation.SyncTranslator.newObject(clientContext, "cultureID");
job.set_outputSaveBehavior(SP.Translation.SaveBehavior.alwaysOverwrite);
result = job.translate("inputFilePath", "outputFilePath");
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededSync),
Function.createDelegate(this, this.onQueryFailed));
```

Чтобы получить все языки, которые Служба машинного перевода поддерживает:
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.enumerateSupportedLanguages(clientContext);
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededListAllLang),Function.createDelegate(this, this.onQueryFailed));
```

Чтобы проверить, поддерживается ли конкретный язык:
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.isLanguageSupported(clientContext," language");
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededTestLang),Function.createDelegate(this, this.onQueryFailed));
```

Чтобы получить все расширения файлов, которые Служба машинного перевода поддерживает:
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.enumerateSupportedFileExtensions(clientContext);
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededListAllFileExt),Function.createDelegate(this, this.onQueryFailed));
```

Чтобы проверить, поддерживается ли конкретное расширение файла:
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.isFileExtensionSupported(clientContext," fileExtension");
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededTestFileExt),Function.createDelegate(this, this.onQueryFailed));
```


## Служба REST для Служба машинного перевода
<a name="TranslationSvc_REST"> </a>

SharePoint 2013 включает службу REST (Representational State Transfer), позволяющую удаленно управлять приложением Служба машинного перевода с помощью любой технологии, которая поддерживает веб-запросы REST. Общие сведения о REST в SharePoint 2013 см. в статье  [Программирование с использованием службы SharePoint 2013 REST](use-odata-query-operations-in-sharepoint-rest-requests.md).
  
    
    

### REST API для асинхронного перевода

REST API для выполнения асинхронного перевода: 
  
    
    
 `http://serverName/_api/TranslationJob('language')`.
  
    
    
Чтобы выполнить асинхронный перевод для одного файла:
  
    
    
 `http://serverName/_api/TranslationJob('language')/TranslateFile(inputFile='/path/intput file', outputFile='/path/output file')`
  
    
    
Чтобы выполнить асинхронный перевод для папки:
  
    
    
 `http://serverName/_api/TranslationJob('language')/TranslateFolder(inputFolder='/path/in', outputFolder='/path/out')`.
  
    
    
Чтобы выполнить асинхронный перевод для библиотеки:
  
    
    
 `http://serverName/_api/TranslationJob('language')/TranslateLibrary(inputLibrary='/LibraryName', outputLibrary='/LibraryName'')`.
  
    
    

### REST API для синхронного перевода

Служба REST для Служба машинного перевода поддерживает синхронный перевод только для файлов. Соответствующий API: 
  
    
    
 `http://serverName/_api/SyncTranslator('language')/Translate(outputFile='/path/output file', inputFile='/path/input file')`.
  
    
    

### Дополнительные REST API для Служба машинного перевода

Служба REST для Служба машинного перевода включает дополнительные интерфейсы API, с помощью которых можно получить сведения о возможностях приложения Служба машинного перевода и состоянии задания перевода.
  
    
    
Чтобы получить все языки, которые Служба машинного перевода поддерживает: 
  
    
    
 `http://serverName/_api/TranslationJob.EnumerateSupportedLanguages`.
  
    
    
Чтобы проверить, поддерживается ли конкретный язык:
  
    
    
 `http://serverName/_api/TranslationJob.IsLanguageSupported('language')`.
  
    
    
Чтобы получить все расширения файла, которые Служба машинного перевода поддерживает:
  
    
    
 `http://serverName/_api/TranslationJob.EnumerateSupportedFileEXtensions`.
  
    
    
Чтобы проверить, поддерживается ли конкретное расширение файла:
  
    
    
 `http://serverName/_api/TranslationJob.IsFileExtensionSupported('extension')`.
  
    
    
Чтобы проверить ограничение на размер файлов для конкретного расширения файла:
  
    
    
 `http://serverName/_api/TranslationJob.GetMaximumFileSize('extension')`.
  
    
    
Чтобы получить список всех заданий асинхронного перевода:
  
    
    
 `http://serverName/_api/TranslationJobStatus.GetAllJobs`.
  
    
    
Чтобы получить список всех активных заданий асинхронного перевода:
  
    
    
 `http://serverName/_api/TranslationJobStatus.GetAllActiveJobs`.
  
    
    
Чтобы получить сведения из документа, касающиеся конкретного задания асинхронного перевода:
  
    
    
 `http://serverName/_api/TranslationJobStatus('jobid')/GetAllItems`.
  
    
    
Чтобы отменить задание асинхронного перевода:
  
    
    
 `http://serverName/_api/TranslationJob.CancelJob('jobid')`.
  
    
    

## Требования для документов Microsoft Word
<a name="TranslationSvc_REST"> </a>

Служба машинного перевода SharePoint переводит документы Microsoft Word с языка абзаца. Например, если абзац написан на испанском языке, но для него выбран английский язык, служба перевода не переведет его на английский, потому что этот язык для него уже выбран.
  
    
    

### Чтобы выбрать язык абзаца, сделайте следующее:


1. Выделите абзац.
    
  
2.  Перейдите на вкладку ленты "Рецензирование".
    
  
3.  Откройте раскрывающееся меню "Язык" и выберите "Язык проверки правописания".
    
  

## Дополнительные ресурсы
<a name="TranslationSvc_AR"> </a>


-  [Службы приложений Office 2013 и SharePoint 2013](office-2013-and-sharepoint-2013-application-services.md)
    
  

