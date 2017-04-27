---
title: SharePoint 2013 の機械翻訳サービス
ms.prod: SHAREPOINT
ms.assetid: 15a81428-da94-40b8-8ed4-6a12f05661e2
---


# SharePoint 2013 の機械翻訳サービス
Machine Translation Service について説明します。これは、SharePoint 2013 に含まれる新しいサービス アプリケーションであり、ファイルおよびサイトを自動で機械翻訳する機能を提供します。
## Machine Translation Service の概要
<a name="TranslationSvc_Overview"> </a>


> **メモ**
> 機械翻訳を使用すると、ユーザーは翻訳のためにコンテンツを Microsoft に送信できます。Microsoft では、翻訳の品質を向上させるため、ユーザーから送信されたコンテンツを使用することがあります。アプリケーションで Machine Translation Service を使用する場合、このアプリケーションが、ユーザーが翻訳のためにコンテンツを Microsoft に送信することを許可し、Microsoft では翻訳の品質を向上させるためユーザーから送信されたコンテンツを使用する可能性があることをユーザーに知らせる必要があります。詳細については、「Microsoft Translator のプライバシー」を参照してください。 
  
    
    

Machine Translation Service は、SharePoint 2013 に含まれる新しいサービス アプリケーションであり、ファイルおよびサイトを自動で機械翻訳する機能を提供します。Machine Translation Service アプリケーションは、翻訳要求を処理する場合、その要求を  [Microsoft Translator](http://www.microsoft.com/en-us/translator/) クラウドのホスト型機械翻訳サービスに転送します。転送先のサービスが実際に翻訳処理を実行します。このクラウド サービスはまた、Microsoft Office、Lync、Yammer、および Bing の翻訳機能を強化します。
  
    
    
Machine Translation Service アプリケーションは翻訳要求を非同期的または同期的に処理します。非同期的な翻訳要求は、翻訳タイマー ジョブが実行されるときに処理されます。翻訳タイマー ジョブの既定の間隔は 15 分です。この設定はサーバーの全体管理で、または Windows PowerShell を使用することによって管理できます。さらに、以下のコマンドを使用してタイマーを即時に実行するように設定することもできます。
  
    
    



```

$tj = get-sptimerjob "Sharepoint Translation Services"
$tj.Runnow()
```

同期的な翻訳要求は、要求が送信されるとすぐに処理されます。
  
    
    

### Word Automation Services との共有コンポーネント
<a name="TranslationSvc_SharedWAS"> </a>

Machine Translation Service アーキテクチャは、いくつかのコンポーネントを Microsoft Word Automation Services アーキテクチャと共有しています。Word Automation Services アーキテクチャについての詳細は、 [Word Automation Services アーキテクチャ](http://msdn.microsoft.com/library/567bf68d-46bb-4ee8-981d-186549b9e5b8%28Office.15%29.aspx)を参照してください。
  
    
    
Machine Translation Service オブジェクト モデルは、Word Automation Services オブジェクト モデルに従ってモデル化されています。このため、Word Automation Services でのプログラミングに慣れている場合は、Machine Translation Service オブジェクト モデルでのプログラミングがそれに似ていることに気付くでしょう。
  
    
    

## Machine Translation Service のサーバー オブジェクト モデルの使用
<a name="TranslationSvc_ServerOM"> </a>

サーバー オブジェクト モデルを使用するアプリケーションは、SharePoint 2013 を実行するサーバー上で直接実行される必要があります。リモートにホストできるアプリケーションの作成についての詳細は、後述の「 [Machine Translation Service のクライアント オブジェクト モデルの使用](#TranslationSvc_UsingCSOM)」を参照してください。Machine Translation Service サーバー オブジェクト モデルは **Microsoft.Office.TranslationServices** 名前空間にあり、これは Microsoft.Office.TranslationServices.dll にあります。
  
    
    
サーバー オブジェクト モデルを使用する場合、翻訳の要求は、Machine Translation Service アプリケーションに対して非同期的にも同期的 (即時の翻訳) にも発行できます。Machine Translation Service アプリケーションは翻訳要求を保存する作業キューとして、非同期キューと同期キューの 2 つを備えています。同期キュー内の要求は、より優先度が高いものとして扱われ、非同期キュー内の要求よりも先に翻訳されます。要求は、使用したクラスに基づいてこれらのキューのいずれかに送られます。
  
    
    

  
    
    
![関連するコード スニペットおよびサンプル アプリ](images/mod_icon_links_samples.png)
  
    
    
コンソール アプリケーションからサーバー オブジェクト モデルを使用する方法を説明するサンプル コードについては、 [SharePoint 2013: サーバー オブジェクト モデルを使用して機械翻訳サービスにアクセスする](http://code.msdn.microsoft.com/SharePoint-2013-Access-86639c3d)を参照してください。
  
    
    

### サーバー オブジェクト モデルを使用した非同期的翻訳

 **TranslationJob** クラスは、翻訳されるアイテムの集合を定義します。これは、単一のファイルにすることも、フォルダーやドキュメント ライブラリ内のすべてのファイルにすることもできます。この方法で発行された翻訳ジョブは、翻訳データベースに保管されます。翻訳タイマー ジョブが実行されるたびに、翻訳データベースからいくつかのジョブが取り出され、翻訳対象として非同期キューに追加されます。翻訳タイマー ジョブの既定の間隔は 15 分です。
  
    
    
以下のコードは、1 つのファイルを非同期で翻訳する方法を示しています。
  
    
    



```cs

SPServiceContext sc = SPServiceContext.GetContext(new SPSite(site));
TranslationJob job = new TranslationJob(sc, CultureInfo.GetCultureInfo(culture)); 
job.AddFile(input, output);
job.Start(); 

```

以下のコードは、1 つのフォルダー内のすべてのファイルを非同期で翻訳する方法を示しています。
  
    
    



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

以下のコードは、1 つのドキュメント ライブラリ内のすべてのファイルを非同期で翻訳する方法を示しています。
  
    
    



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


### サーバー オブジェクト モデルを使用した同期的翻訳

 **SyncTranslator** クラスを使用してファイルまたはストリームについて即時の翻訳を要求できます。このクラスを使用して行われた翻訳要求は、 **TranslationJob** クラスを使用して行われた要求とは別の方法で処理が進みます。これは、処理対象として即時に同期キューに追加されます。 **TranslationItemInfo** クラスは、Machine Translation Service によって翻訳された 1 つのアイテムについての詳細を格納します。 **SyncTranslator.Translate** メソッドは、同期的翻訳ジョブにおいてこのクラスのインスタンスを戻します。
  
    
    
以下のコードは、1 つのファイルを同期的に翻訳する方法を示しています。
  
    
    



```cs

SPServiceContext sc = SPServiceContext.GetContext(new SPSite(site));
SyncTranslator job = new SyncTranslator(sc, CultureInfo.GetCultureInfo(jobCulture));
TranslationItemInfo itemInfo = job.Translate(input, output);

```

以下のコードは、ストリームを同期的に翻訳する方法を示しています。
  
    
    



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

以下のコードは、バイト シーケンスを同期的に翻訳する方法を示しています。
  
    
    



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


### 権限
<a name="TranslationSvc_Permissions"> </a>

翻訳要求を実行しているユーザーが、翻訳対象のファイルにアクセスできる場合、かつファイルの出力場所にアクセスできる場合、そのユーザーはセキュリティ チェックに合格し、ファイルが翻訳されます。
  
    
    

## Machine Translation Service のクライアント オブジェクト モデルの使用
<a name="TranslationSvc_UsingCSOM"> </a>

Machine Translation Service には、オンライン、オンプレミス、およびモバイル開発用の Machine Translation Service API へのアクセスを可能にするクライアント オブジェクト モデル (CSOM) が含まれています。 クライアント アプリケーションは CSOM を使用してサーバーのコンテンツおよび機能にアクセスします。CSOM は、サーバーの翻訳機能のほとんどを実装していますが、CSOM とサーバー側オブジェクト モデルは完全に同一ではありません。非同期的翻訳は、個別のファイル、またはドキュメント ライブラリやフォルダー内の複数のファイルについてサポートされます。同期的翻訳は、ファイルについてはサポートされますが、ファイル ストリームについてはサポートされません。
  
    
    
Machine Translation Service CSOM は, .NET マネージ クライアント側オブジェクト モデルと、Microsoft Silverlight および JavaScript オブジェクト モデルを含んでおり、SharePoint 2013 CSOM に基づいて構築されています。このため、クライアント コードは最初に SharePoint 2013 CSOM にアクセスし、その後で Machine Translation Service CSOM にアクセスします。 
  
    
    
SharePoint CSOM についての詳細は、 [SharePoint 2010 クライアント オブジェクト モデル](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx)を参照してください。CSOM へのエントリ ポイントである **ClientContext** オブジェクトについての詳細は、 [中心的オブジェクトであるクライアント コンテキスト](http://msdn.microsoft.com/library/6299f0df-ab4c-40e6-b709-ec80271c99b3%28Office.15%29.aspx)を参照してください。
  
    
    
表 1 は、Machine Translation Service サーバー オブジェクトと、それに対応する CSOM API が提供するオブジェクトを示しています。 
  
    
    

**表 1. サーバー オブジェクト モデル API と対応する CSOM API**


|**サーバー**|**.NET マネージおよび Silverlight**|**JavaScript**|
|:-----|:-----|:-----|
|Microsoft.Office.TranslationServices.TranslationJob  <br/> |Microsoft.Office.TranslationServices.Client.TranslationJob  <br/> |SP.Translation.TranslationJob  <br/> |
|Microsoft.Office.TranslationServices.TranslationJobInfo  <br/> |Microsoft.Office.TranslationServices.Client.TranslationJobInfo  <br/> |SP.Translation.TranslationJobInfo  <br/> |
|Microsoft.Office.TranslationServices.TranslationItemInfo  <br/> |Microsoft.Office.TranslationServices.Client.TranslationItemInfo  <br/> |SP.Translation.TranslationItemInfo  <br/> |
|Microsoft.Office.TranslationServices.TranslationJobStatus  <br/> |Microsoft.Office.TranslationServices.Client.TranslationJobStatus  <br/> |SP.Translation.TranslationJobStatus  <br/> |
|Microsoft.Office.TranslationServices.SyncTranslator  <br/> |Microsoft.Office.TranslationServices.Client.SyncTranslator  <br/> |SP.Translation.SyncTranslator  <br/> |
   

### Machine Translation Service .NET マネージ CSOM と Silverlight CSOM
<a name="TranslationSvc_ManagedCSOM"> </a>

.NET マネージ CSOM の場合は、 **ClientContext** インスタンス (Microsoft.SharePoint.Client.dll の **Microsoft.SharePoint.Client** 名前空間にある) を取得します。そして、Microsoft.Office.TranslationServices.Client.dll の **Microsoft.Office.TranslationServices.Client** 名前空間の中のオブジェクト モデルを使用します。
  
    
    

  
    
    
![関連するコード スニペットおよびサンプル アプリ](images/mod_icon_links_samples.png)
  
    
    
.NET マネージ CSOM の使用方法を説明するサンプル コードについては、 [SharePoint 2013: クライアント オブジェクト モデルを使用して機械翻訳サービスにアクセスする](http://code.msdn.microsoft.com/SharePoint-2013-Perform-a-8e53b06a)を参照してください。
  
    
    
Silverlight CSOM の場合は、 **ClientContext** インスタンス (Microsoft.SharePoint.Client.Silverlight.dll の **Microsoft.SharePoint.Client** 名前空間にある) を取得します。そして、Microsoft.Office.TranslationServices.Silverlight.dll の **Microsoft.Office.TranslationServices.Client** 名前空間の中のオブジェクト モデルを使用します。
  
    
    

  
    
    
![関連するコード スニペットおよびサンプル アプリ](images/mod_icon_links_samples.png)
  
    
    
Silverlight CSOM の使用方法を説明するサンプル コードについては、 [SharePoint 2013: Silverlight アプリケーションから機械翻訳サービスにアクセスする](http://code.msdn.microsoft.com/SharePoint-2013-Access-cdaff6b2)を参照してください。
  
    
    
1 つのファイルを非同期的に翻訳するには次のようにします。
  
    
    



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

1 つのフォルダーを非同期的に翻訳するには次のようにします。
  
    
    



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

1 つのライブラリを非同期的に翻訳するには次のようにします。
  
    
    



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

1 つのファイルを同期的に翻訳するには次のようにします。
  
    
    



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

Machine Translation Service によってサポートされているすべての言語を取得するには次のようにします。
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
IEnumerable<string> supportedLanguages = TranslationJob.EnumerateSupportedLanguages(clientContext);
clientContext.ExecuteQuery();
foreach (string item in supportedLanguages)
{
    Console.Write(item + ", ");
}
```

特定の言語がサポートされているかどうかを確認するには次のようにします。
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
clientResult<bool> isSupported;
isSupported = TranslationJob.IsLanguageSupported(clientContext, "language");
clientContext.ExecuteQuery();
```

Machine Translation Service によってサポートされているすべてのファイル名拡張子を取得するには次のようにします。
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
IEnumerable<string> fileExt = TranslationJob.EnumerateSupportedFileExtensions(clientContext);
clientContext.ExecuteQuery();
foreach (string item in fileExt)
{
    Console.Write(item + ", ");
}
```

特定のファイル名拡張子がサポートされているかどうかを確認するには次のようにします。
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
clientResult<bool> isSupported;
isSupported = TranslationJob.IsFileExtensionSupported(clientContext, "fileExtension");
clientContext.ExecuteQuery();

```

特定のファイル名拡張子についてファイル サイズの制限を確認するには次のようにします。
  
    
    



```cs

ClientContext clientContext = new ClientContext("http://serverName/sites/siteCollectionPath");
clientResult<int> maxSize;
maxSize = TranslationJob.GetMaximumFileSize(clientContext, "fileExtension");
clientContext.ExecuteQuery();
```


### Machine Translation Service の JavaScript CSOM
<a name="TranslationSvc_JavaScriptCSOM"> </a>

JavaScript CSOM の場合は、 **SP.ClientContext** インスタンスを取得し、SP.Translation.js ファイル内のオブジェクト モデルを使用します。
  
    
    

  
    
    
![関連するコード スニペットおよびサンプル アプリ](images/mod_icon_links_samples.png)
  
    
    
JavaScript CSOM の使用方法を説明するサンプル コードについては、 [SharePoint 2013: JavaScript を使用して機械翻訳サービスにアクセスする](http://code.msdn.microsoft.com/SharePoint-2013-Accessing-647f6dd9)を参照してください。
  
    
    
1 つのファイルを非同期的に翻訳するには次のようにします。
  
    
    



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

1 つのフォルダーを非同期的に翻訳するには次のようにします。
  
    
    



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

1 つのライブラリを非同期的に翻訳するには次のようにします。
  
    
    



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

1 つのファイルを同期的に翻訳するには次のようにします。
  
    
    



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

Machine Translation Service によってサポートされているすべての言語を取得するには次のようにします。
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.enumerateSupportedLanguages(clientContext);
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededListAllLang),Function.createDelegate(this, this.onQueryFailed));
```

特定の言語がサポートされているかどうかを確認するには次のようにします。
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.isLanguageSupported(clientContext," language");
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededTestLang),Function.createDelegate(this, this.onQueryFailed));
```

Machine Translation Service によってサポートされているすべてのファイル名拡張子を取得するには次のようにします。
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.enumerateSupportedFileExtensions(clientContext);
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededListAllFileExt),Function.createDelegate(this, this.onQueryFailed));
```

特定のファイル名拡張子がサポートされているかどうかを確認するには次のようにします。
  
    
    



```

var clientContext = new SP.ClientContext("serverRelativeUrl");
var contextSite = clientContext.get_site();
var result= SP.Translation.TranslationJob.isFileExtensionSupported(clientContext," fileExtension");
clientContext.executeQueryAsync(Function.createDelegate(this, this.onQuerySucceededTestFileExt),Function.createDelegate(this, this.onQueryFailed));
```


## Machine Translation Service の REST サービス
<a name="TranslationSvc_REST"> </a>

SharePoint 2013 には REST (Representational State Transfer) サービスが含まれています。これにより、REST 要求をサポートする任意のテクノロジを使用してリモートで Machine Translation Service アプリケーションとやり取りすることができます。SharePoint 2013 の REST に関する全般的な情報については、 [SharePoint 2013 REST サービスを使用したプログラミング](use-odata-query-operations-in-sharepoint-rest-requests.md) を参照してください。
  
    
    

### 非同期的な翻訳用の REST API

翻訳を非同期的に実行する REST API は次のとおりです。
  
    
    
 `http://serverName/_api/TranslationJob('language')`
  
    
    
1 つのファイルを非同期的に翻訳するには次のようにします。
  
    
    
 `http://serverName/_api/TranslationJob('language')/TranslateFile(inputFile='/path/intput file', outputFile='/path/output file')`
  
    
    
1 つのフォルダーを非同期的翻訳するには次のようにします。
  
    
    
 `http://serverName/_api/TranslationJob('language')/TranslateFolder(inputFolder='/path/in', outputFolder='/path/out')`
  
    
    
1 つのライブラリを非同期的翻訳するには次のようにします。 
  
    
    
 `http://serverName/_api/TranslationJob('language')/TranslateLibrary(inputLibrary='/LibraryName', outputLibrary='/LibraryName'')`
  
    
    

### 同期的な翻訳用の REST API

Machine Translation Service REST サービスはファイルについてのみ同期的な翻訳をサポートします。このための API は次のとおりです。
  
    
    
 `http://serverName/_api/SyncTranslator('language')/Translate(outputFile='/path/output file', inputFile='/path/input file')`
  
    
    

### その他の Machine Translation Service REST API

Machine Translation Service REST サービスには、この他に、Machine Translation Service アプリケーションの機能および翻訳ジョブのステータスに関する情報を取得するために使用できる API も含まれています。
  
    
    
Machine Translation Service によってサポートされるすべての言語を取得するには次のようにします。
  
    
    
 `http://serverName/_api/TranslationJob.EnumerateSupportedLanguages`
  
    
    
特定の言語がサポートされているかどうかを確認するには次のようにします。
  
    
    
 `http://serverName/_api/TranslationJob.IsLanguageSupported('language')`
  
    
    
Machine Translation Service によってサポートされているすべてのファイル名拡張子を取得するには次のようにします。
  
    
    
 `http://serverName/_api/TranslationJob.EnumerateSupportedFileEXtensions`
  
    
    
特定のファイル名拡張子がサポートされているかどうかを確認するには次のようにします。
  
    
    
 `http://serverName/_api/TranslationJob.IsFileExtensionSupported('extension')`
  
    
    
特定のファイル名拡張子についてファイル サイズの制限を確認するには次のようにします。
  
    
    
 `http://serverName/_api/TranslationJob.GetMaximumFileSize('extension')`
  
    
    
非同期翻訳ジョブすべてを含むリストを取得するには次のようにします。
  
    
    
 `http://serverName/_api/TranslationJobStatus.GetAllJobs`
  
    
    
アクティブな非同期翻訳ジョブすべてを含むリストを取得するには次のようにします。
  
    
    
 `http://serverName/_api/TranslationJobStatus.GetAllActiveJobs`
  
    
    
特定の非同期翻訳ジョブのドキュメント情報を取得するには次のようにします。
  
    
    
 `http://serverName/_api/TranslationJobStatus('jobid')/GetAllItems`
  
    
    
非同期翻訳ジョブを取り消すには次のようにします。
  
    
    
 `http://serverName/_api/TranslationJob.CancelJob('jobid')`
  
    
    

## その他の技術情報
<a name="TranslationSvc_AR"> </a>


-  [Office 2013 および SharePoint 2013 のアプリケーション サービス](office-2013-and-sharepoint-2013-application-services.md)
    
  

