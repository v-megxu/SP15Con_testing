---
title: SharePoint 2013 中的机器翻译服务
ms.prod: SHAREPOINT
ms.assetid: 15a81428-da94-40b8-8ed4-6a12f05661e2
---


# SharePoint 2013 中的机器翻译服务
了解机器翻译服务，它是 SharePoint 2013 中的一个新的服务应用程序，提供了文件和网站的自动机器翻译。
## 机器翻译服务概述
<a name="TranslationSvc_Overview"> </a>


> **注释**
> 使用机器翻译将允许用户将内容发给 Microsoft 进行翻译。Microsoft 可能会使用用户发给我们的内容以改进翻译质量。如果您在应用程序中使用机器翻译服务，您有责任通知用户，此应用程序允许用户将内容发给 Microsoft 进行翻译，并且 Microsoft 可能会使用用户发给我们的内容以改进翻译质量。请参阅 Microsoft Translator 隐私策略，以获取详细信息。 
  
    
    

机器翻译服务是 SharePoint 2013 中的一个新的服务应用程序，它提供了文件和网站的自动机器翻译。当机器翻译服务应用程序处理翻译请求时，它会将请求转发给在其中执行实际翻译工作的云承载的  [Microsoft 翻译程序](http://www.microsoft.com/en-us/translator/)。此基于云的服务还实现了 Microsoft Office、Lync、Yammer 和 Bing 翻译功能。
  
    
    
机器翻译服务应用程序将异步和同步处理翻译请求。在执行翻译计时器作业时，将处理异步翻译请求。翻译计时器作业的默认间隔为 15 分钟；您可以在管理中心中或使用 Windows PowerShell 管理该设置。您还可以使用以下命令将计时器设置为立即执行：
  
    
    



```

$tj = get-sptimerjob "Sharepoint Translation Services"
$tj.Runnow()
```

同步翻译请求一旦提交就会立即得到处理。
  
    
    

### 使用 Word Automation Services 共享组件
<a name="TranslationSvc_SharedWAS"> </a>

机器翻译服务体系结构从 Microsoft Word Automation Services 体系结构共享多个组件。有关 Word Automation Services 体系结构的详细信息，请参阅  [Word Automation Services 体系结构](http://msdn.microsoft.com/library/567bf68d-46bb-4ee8-981d-186549b9e5b8%28Office.15%29.aspx)。
  
    
    
在为 Word Automation Services 对象模型建模后，为机器翻译服务对象模型建模，因此，如果您熟悉 Word Automation Services 编程，则将与对机器翻译服务对象模型进行的编程的相似处。
  
    
    

## 使用机器翻译服务服务器对象模型
<a name="TranslationSvc_ServerOM"> </a>

使用服务器对象模型的应用程序必须在运行 SharePoint 2013 的服务器上直接运行。有关创建可远程承载的应用程序的信息，请参阅本主题后面的 [使用机器翻译服务客户端对象模型](#TranslationSvc_UsingCSOM)。机器翻译服务服务器对象模型驻留在位于 Microsoft.Office.TranslationServices.dll 中的 **Microsoft.Office.TranslationServices** 命名空间中。
  
    
    
通过使用服务器对象模型，您可以同步或异步方式提交对机器翻译服务应用程序的请求（针对即时翻译）。机器翻译服务应用程序具有两个用于存储翻译请求的工作队列：异步队列和同步队列。同步队列中的请求将被视为具有更高的优先级，将先翻译该请求，然后再翻译异步队列中的请求。根据您使用的类，将请求传送到这些队列之一。
  
    
    

  
    
    
![相关代码段和示例应用程序](images/mod_icon_links_samples.png)
  
    
    
有关演示如何从控制台应用程序使用服务器对象模型的示例代码，请参阅  [SharePoint 2013：使用服务器对象模型访问机器翻译服务](http://code.msdn.microsoft.com/SharePoint-2013-Access-86639c3d)。
  
    
    

### 使用服务器对象模型的异步翻译

 **TranslationJob** 类定义了一组要翻译的项目。它可以是单个文件或文件夹/文档库中的每个文件。以此方式提交的翻译作业将存储在翻译数据库中。每次运行翻译计时器作业时，它会从翻译数据库中提取一些作业并将其添加到要翻译的异步队列中。翻译计时器作业的默认间隔为 15 分钟。
  
    
    
以下代码演示如何异步翻译单个文件。
  
    
    



```cs

SPServiceContext sc = SPServiceContext.GetContext(new SPSite(site));
TranslationJob job = new TranslationJob(sc, CultureInfo.GetCultureInfo(culture)); 
job.AddFile(input, output);
job.Start(); 

```

以下代码演示如何异步翻译文件夹中的每个文件。
  
    
    



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

以下代码演示如何异步翻译文档库中的每个文件。
  
    
    



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


### 使用服务器对象模型的同步翻译

使用 **SyncTranslator** 类可请求文件和流的即时翻译。使用此类发起的翻译请求的传送方式与使用 **TranslationJob** 类发起的请求的传送方式不同。它们将立即添加到要处理的同步队列中。 **TranslationItemInfo** 类包含由机器翻译服务翻译的单个项目的详细信息。 **SyncTranslator.Translate** 方法在同步翻译作业中返回此类的实例。
  
    
    
以下代码演示如何同步翻译单个文件。
  
    
    



```cs

SPServiceContext sc = SPServiceContext.GetContext(new SPSite(site));
SyncTranslator job = new SyncTranslator(sc, CultureInfo.GetCultureInfo(jobCulture));
TranslationItemInfo itemInfo = job.Translate(input, output);

```

以下代码演示如何同步翻译流。
  
    
    



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

以下代码演示如何同步翻译一系列字节。
  
    
    



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


### 权限
<a name="TranslationSvc_Permissions"> </a>

如果为其运行翻译请求的用户可以访问要翻译的文件以及文件的输出位置，则该用户可跳过安全检查，并且文件将被翻译。
  
    
    

## 使用机器翻译服务客户端对象模型
<a name="TranslationSvc_UsingCSOM"> </a>

机器翻译服务还包括一个客户端对象模型 (CSOM)，可通过该模型访问机器翻译服务 API 以进行联机、本地和移动开发。客户端应用程序可使用 CSOM 访问服务器内容和功能。CSOM 将实现服务器的大多数翻译功能，但 CSOM 和服务器端对象模型没有一对一奇偶校验。支持对单个文件和文档库或文件夹中的文件进行异步翻译。支持文件的同步翻译，但不支持文件流的同步翻译。
  
    
    
机器翻译服务 CSOM 包括一个 .NET 托管客户端对象模型以及 Microsoft Silverlight 和 JavaScript 对象模型。它是基于 SharePoint 2013 CSOM 构建的。因此，客户端代码先访问 SharePoint 2013 CSOM，然后访问机器翻译服务 CSOM。 
  
    
    
有关 SharePoint CSOM 的详细信息，请参阅  [SharePoint 2010 客户端对象模型](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx)。有关作为 CSOM 的入口点的 **ClientContext** 对象的详细信息，请参阅 [作为中心对象的客户端上下文](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx)。
  
    
    
表 1 显示了 CSOM API 为机器翻译服务服务器对象提供的等效对象。 
  
    
    

**表 1. 服务器对象模型 API 及其 CSOM 等效项**


|**服务器**|**.NET 托管和 Silverlight**|**JavaScript**|
|:-----|:-----|:-----|
|Microsoft.Office.TranslationServices.TranslationJob  <br/> |Microsoft.Office.TranslationServices.Client.TranslationJob  <br/> |SP.Translation.TranslationJob  <br/> |
|Microsoft.Office.TranslationServices.TranslationJobInfo  <br/> |Microsoft.Office.TranslationServices.Client.TranslationJobInfo  <br/> |SP.Translation.TranslationJobInfo  <br/> |
|Microsoft.Office.TranslationServices.TranslationItemInfo  <br/> |Microsoft.Office.TranslationServices.Client.TranslationItemInfo  <br/> |SP.Translation.TranslationItemInfo  <br/> |
|Microsoft.Office.TranslationServices.TranslationJobStatus  <br/> |Microsoft.Office.TranslationServices.Client.TranslationJobStatus  <br/> |SP.Translation.TranslationJobStatus  <br/> |
|Microsoft.Office.TranslationServices.SyncTranslator  <br/> |Microsoft.Office.TranslationServices.Client.SyncTranslator  <br/> |SP.Translation.SyncTranslator  <br/> |
   

### 机器翻译服务 .NET 托管 CSOM 和 Silverlight CSOM
<a name="TranslationSvc_ManagedCSOM"> </a>

对于 .NET 托管 CSOM，获取 **ClientContext** 实例（位于 Microsoft.SharePoint.Client.dll 中的 **Microsoft.SharePoint.Client** 命名空间中）。然后使用 Microsoft.Office.TranslationServices.Client.dll 中的 **Microsoft.Office.TranslationServices.Client** 命名空间中的对象模型。
  
    
    

  
    
    
![相关代码段和示例应用程序](images/mod_icon_links_samples.png)
  
    
    
有关演示如何使用 .NET 托管 CSOM 的示例代码，请参阅  [SharePoint 2013：使用客户端对象模型访问机器翻译服务](http://code.msdn.microsoft.com/SharePoint-2013-Perform-a-8e53b06a)。
  
    
    
对于 Silverlight CSOM，获取 **ClientContext** 实例（位于 Microsoft.SharePoint.Client.Silverlight.dll 中的 **Microsoft.SharePoint.Client** 命名空间中）。然后使用 Microsoft.Office.TranslationServices.Silverlight.dll 中的 **Microsoft.Office.TranslationServices.Client** 命名空间中的对象模型。
  
    
    

  
    
    
![相关代码段和示例应用程序](images/mod_icon_links_samples.png)
  
    
    
有关演示如何使用 Silverlight CSOM 的示例代码，请参阅  [SharePoint 2013：从 Silverlight 应用程序访问机器翻译服务](http://code.msdn.microsoft.com/SharePoint-2013-Access-cdaff6b2)。
  
    
    
异步翻译单个文件：
  
    
    



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

异步翻译文件夹：
  
    
    



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

异步翻译库：
  
    
    



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

同步翻译单个文件：
  
    
    



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

检索机器翻译服务支持的所有语言：
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
IEnumerable<string> supportedLanguages = TranslationJob.EnumerateSupportedLanguages(clientContext);
clientContext.ExecuteQuery();
foreach (string item in supportedLanguages)
{
    Console.Write(item + ", ");
}
```

检查是否支持某种特定语言：
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
clientResult<bool> isSupported;
isSupported = TranslationJob.IsLanguageSupported(clientContext, "language");
clientContext.ExecuteQuery();
```

检索机器翻译服务支持的所有文件扩展名：
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
IEnumerable<string> fileExt = TranslationJob.EnumerateSupportedFileExtensions(clientContext);
clientContext.ExecuteQuery();
foreach (string item in fileExt)
{
    Console.Write(item + ", ");
}
```

检查是否支持某个特定的文件扩展名：
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
clientResult<bool> isSupported;
isSupported = TranslationJob.IsFileExtensionSupported(clientContext, "fileExtension");
clientContext.ExecuteQuery();

```

检查特定文件扩展名的文件大小限制：
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
clientResult<int> maxSize;
maxSize = TranslationJob.GetMaximumFileSize(clientContext, "fileExtension");
clientContext.ExecuteQuery();
```


### 机器翻译服务 JavaScript CSOM
<a name="TranslationSvc_JavaScriptCSOM"> </a>

对于 JavaScript CSOM，获取 **SP.ClientContext** 实例，然后使用 SP.Translation.js 文件中的对象模型。
  
    
    

  
    
    
![相关代码段和示例应用程序](images/mod_icon_links_samples.png)
  
    
    
有关演示如何使用 JavaScript CSOM 的示例代码，请参阅  [SharePoint 2013：使用 JavaScript 访问机器翻译服务](http://code.msdn.microsoft.com/SharePoint-2013-Accessing-647f6dd9)。
  
    
    
异步翻译单个文件：
  
    
    



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

异步翻译文件夹：
  
    
    



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

异步翻译库：
  
    
    



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

同步翻译单个文件：
  
    
    



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

检索机器翻译服务支持的所有语言：
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.enumerateSupportedLanguages(clientContext);
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededListAllLang),Function.createDelegate(this, this.onQueryFailed));
```

检查是否支持某种特定语言：
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.isLanguageSupported(clientContext," language");
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededTestLang),Function.createDelegate(this, this.onQueryFailed));
```

检索机器翻译服务支持的所有文件扩展名：
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.enumerateSupportedFileExtensions(clientContext);
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededListAllFileExt),Function.createDelegate(this, this.onQueryFailed));
```

检查是否支持某个特定文件扩展名：
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.isFileExtensionSupported(clientContext," fileExtension");
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededTestFileExt),Function.createDelegate(this, this.onQueryFailed));
```


## 机器翻译服务 REST 服务
<a name="TranslationSvc_REST"> </a>

SharePoint 2013 包含代表性状态传输 (REST) 服务，该服务使您能够使用支持 REST Web 请求的任何技术以远程方式与机器翻译服务应用程序进行交互。有关 SharePoint 2013 中的 REST 的一般信息，请参阅 [使用 SharePoint 2013 REST 服务进行编程](use-odata-query-operations-in-sharepoint-rest-requests.md)。
  
    
    

### 异步翻译 REST API

以下是用于执行异步翻译的 REST API：
  
    
    
 `http://serverName/_api/TranslationJob('language')`
  
    
    
异步翻译单个文件：
  
    
    
 `http://serverName/_api/TranslationJob('language')/TranslateFile(inputFile='/path/intput file', outputFile='/path/output file')`
  
    
    
异步翻译文件夹：
  
    
    
 `http://serverName/_api/TranslationJob('language')/TranslateFolder(inputFolder='/path/in', outputFolder='/path/out')`
  
    
    
异步翻译库：
  
    
    
 `http://serverName/_api/TranslationJob('language')/TranslateLibrary(inputLibrary='/LibraryName', outputLibrary='/LibraryName'')`
  
    
    

### 同步翻译 REST API

机器翻译服务 REST 服务仅支持文件的同步翻译。以下是用于执行此操作的 API：
  
    
    
 `http://serverName/_api/SyncTranslator('language')/Translate(outputFile='/path/output file', inputFile='/path/input file')`
  
    
    

### 附加的 机器翻译服务 REST API

机器翻译服务 REST 服务包括可用于检索有关机器翻译服务应用程序功能和翻译作业状态的信息的附加 API。
  
    
    
检索机器翻译服务支持的所有语言：
  
    
    
 `http://serverName/_api/TranslationJob.EnumerateSupportedLanguages`
  
    
    
检查是否支持某种特定语言：
  
    
    
 `http://serverName/_api/TranslationJob.IsLanguageSupported('language')`
  
    
    
检索机器翻译服务支持的所有文件扩展名：
  
    
    
 `http://serverName/_api/TranslationJob.EnumerateSupportedFileEXtensions`
  
    
    
检查是否支持某个特定文件扩展名：
  
    
    
 `http://serverName/_api/TranslationJob.IsFileExtensionSupported('extension')`
  
    
    
检查特定文件扩展名的文件大小限制：
  
    
    
 `http://serverName/_api/TranslationJob.GetMaximumFileSize('extension')`
  
    
    
检索所有异步翻译作业的列表：
  
    
    
 `http://serverName/_api/TranslationJobStatus.GetAllJobs`
  
    
    
检索所有活动异步翻译作业的列表：
  
    
    
 `http://serverName/_api/TranslationJobStatus.GetAllActiveJobs`
  
    
    
检索特定异步翻译作业的文档信息：
  
    
    
 `http://serverName/_api/TranslationJobStatus('jobid')/GetAllItems`
  
    
    
取消异步翻译作业：
  
    
    
 `http://serverName/_api/TranslationJob.CancelJob('jobid')`
  
    
    

## 其他资源
<a name="TranslationSvc_AR"> </a>


-  [Office 2013 和 SharePoint 2013 应用程序服务](office-2013-and-sharepoint-2013-application-services.md)
    
  

