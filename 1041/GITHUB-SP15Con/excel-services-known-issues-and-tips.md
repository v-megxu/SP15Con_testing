---
title: Excel Services の既知の問題およびヒント
ms.prod: SHAREPOINT
ms.assetid: b4a41437-4f00-4f88-8510-627fa0252004
---


# Excel Services の既知の問題およびヒント

以下は、Excel Services を操作する際の既知の問題およびヒントです。
  
    
    


## Excel Web Services


### WSDL の場所の表示

Excel Web Services の Web サービス記述言語 (WSDL) ページは、サーバー上で URL  `http://<server>/<customsite>/_vti_bin/excelservice.asmx?WSDL` に移動すると表示できます。
  
    
    
カスタム サイトがない場合、次の URL を使用すると WSDL を表示できます。:
  
    
    
 `http://<server>/_vti_bin/excelservice.asmx?WSDL`
  
    
    
詳細は、「 [SOAP API にアクセスする](accessing-the-soap-api.md)」を参照してください。
  
    
    

### Excel Web Services および名前空間の理解

Excel Web Services と名前空間を次に示します。
  
    
    

- すべての API メソッドを含む 1 つの Web サービス オブジェクト: **ExcelService**
    
  
- スキーマの名前空間:  `http://schemas.microsoft.com/office/excel/server/webservices`
    
  
- Web サービス ページの名前: ExcelService.asmx
    
  

### ローカルまたは Web サービスへのリンク

特定のシナリオでは、SOAP over HTTP を介して Web サービスとして呼び出すのではなく、直接 Microsoft.Office.Excel.Server.WebServices.dll にリンクして、ローカル アセンブリのようにアクセスする必要があります。 
  
    
    
直接リンクを使用する場合について、詳細およびガイドラインは「 [SOAP 呼び出しのループバックおよび直接リンク](loop-back-soap-calls-and-direct-linking.md)」を参照してください。
  
    
    

### 無効な文字の理解

XML 応答で無効の文字がブックのセルに含まれていると、 **GetCell** メソッドと **GetRange** メソッドの呼び出しは失敗します。
  
    
    
たとえば、セルに 16 進値 0x1、0x2 ... 0x8 を持つ文字が含まれる場合、ASP.NET パーサーは、XML 応答に書き込まれる文字の値が無効であるという例外をスローします。
  
    
    
 **System.InvalidOperationException: クライアントは 'text/html; charset=utf-8' の応答のコンテンツ タイプを見つけましが、'text/html' が必要です。要求が失敗しました。エラー メッセージ:<html> <head> <title>' ' (16 進数値 0x01) は無効な文字です。</title>**
  
    
    
この動作は想定されています。XML の仕様の定義では、有効な XML 応答で許可される文字について、16 進数の値 0x1、0x2 ... 0x8 は無効な XML 文字であると規定されています。
  
    
    
 **Char ::= #x9 | #xA | #xD | [#x20-#xD7FF] | [#xE000-#xFFFD] | [#x10000-#x10FFFF] /* any Unicode character, excluding the surrogate blocks, FFFE, and FFFF. */**
  
    
    
詳細は、「 [W3C 拡張マークアップ言語 (XML) の仕様](http://www.w3.org/TR/REC-xml)」(http://www.w3.org/TR/REC-xml#NT-Char) を参照してください。 
  
    
    

### ブックの保存

たとえば、Excel Web Services を使用して範囲に値を設定するなどしてブックに対して変更を行う場合、ブックに対する変更は、その特定のセッションにのみ保持されます。変更は保存されたり、元のブックに保存されることはありません。現在のブックのセッションが終了 (例えば、 **CloseWorkbook** メソッドを呼び出したり、セッションがタイムアウトしたりして) すると、行われた変更は失われます。
  
    
    
ブックへの変更を保存する場合は、 **GetWorkbook** メソッドを使用してから、保存先のファイル ストアの API を使用してブックを保存します。詳細は、「 [方法: ブック全体またはスナップショットの取得](how-to-get-an-entire-workbook-or-a-snapshot.md)」および「 [[方法] ブックを保存する](http://msdn.microsoft.com/library/feb74f7a-2d8f-4672-911b-de85f8852aea%28Office.15%29.aspx)」を参照してください。
  
    
    

### Excel Web Services プロキシ クラスの Url プロパティの理解

開こうとするブックの場所のために Excel Web Services プロキシの **Url** プロパティを使用しないでください。Visual Studio が生成する Web サービス プロキシ クラスの **Url** プロパティには、クライアントが要求する XML Web サービスのベース URL を取得または設定します。Excel Web Services の場合、通常は次のようになります。
  
    
    
 `http://<server name>/_vti_bin/ExcelService.asmx`
  
    
    
ブックの場所を指定するには、次のコード例に示すとおり、 **Url** プロパティではなく **OpenWorkbook** メソッドを使用します。
  
    
    



```

//Instantiate the web service and make a status array object.
ExcelService xlservice = new ExcelService();
string sheetName = "Sheet1";         

//Set the path to the workbook to open.
//TODO: Change the path to the workbook
 //to point to a workbook you have access to.
//The workbook must be in a trusted location.
string targetWorkbookPath = 
   "http://myserver02/example/Shared%20Documents/Book1.xlsx";

//Set credentials for requests.
xlservice.Credentials = System.Net.CredentialCache.DefaultCredentials;

//Call the open workbook, and point to the trusted   
//location of the workbook to open.
string sessionId = xlservice.OpenWorkbook(targetWorkbookPath, "en-US", 
    "en-US", out outStatus);
                
```

詳細は、「 [WebClientProtocol.Url プロパティ](http://go.microsoft.com/fwlink/?LinkId=64908)」(http://msdn.microsoft.com/library/default.asp?url=/library/ja-jp/cpref/html/frlrfSystemWebServicesProtocolsWebClientProtocolClassUrlTopic.asp) を参照してください。
  
    
    

## セキュリティの理解


### ブックのアクセス許可の使用

ブックのアクセス許可については、次の点に注意してください。
  
    
    

- Excel Web Services は、Microsoft SharePoint Foundation 承認スキームを使用して、SharePoint Foundation サイト (つまり、Excel Web Services が配置されている Web サイト) においてリモートで API を呼び出す (つまり、Web サービスを呼び出す) 権利が呼び出し元にあるかどうかを確認します。呼び出し元に「リモートで API を使用する」権利がない場合、Excel Web Services は「HTTP 401 (権限がない)」エラーを返し、ログにイベント「API authorization failed」を記録します。Excel Web Services は、SOAP の呼び出しとして発信された呼び出しにのみ承認チェックを実行します。Microsoft.Office.Excel.Server.WebServices.dll にローカルにリンクしているアプリケーションからの呼び出しはリモート呼び出しとは見なされません。したがって、これらの呼び出しには承認チェックを行いません。ただし、Microsoft.Office.Excel.Server.WebServices.dll にローカルでリンクするアプリケーション自体が SOAP サービスで、サービスの SOAP 呼び出しを処理する場合、(Microsoft.Office.Excel.Server.WebServices.dll にアプリケーションが直接リンクしているにもかかわらず) Excel Web Services への呼び出しは SOAP の呼び出しとみなされます。このシナリオでは、Excel Web Services は承認チェックを行います。
    
  
- ブック全体を取得 (たとえば、引数  `WorkbookType.FullWorkbook` を使用して **GetWorkbook** メソッドを呼び出すことにより) するには、ブックに対する「開く」許可またはファイル共有の「読み取り」許可が呼び出し元に必要です。
    
  
- **GetApiVersion** メソッドの呼び出しには、許可は不要です。
    
  
- 残りの Excel Web Services メソッドについては、資格情報に加えて、呼び出し元にはブックに対する「表示」許可 (SharePoint Foundation 内) または「読み取り」許可 (ファイル共有内) が必要です。
    
  

### 信頼できる場所

Excel Services で開くブックは、信頼できる場所に配置する必要があります。信頼できる場所に配置されていない場合、ブックを開く Excel Web Services の呼び出しは失敗します。
  
    
    
場所の信頼方法について、詳細は「 [方法: 場所を信頼する](how-to-trust-a-location.md)」および「 [[方法] スクリプトを使用してブックの場所を信頼する](http://msdn.microsoft.com/library/79ab6ced-7a0c-4275-b852-bb246fc6be57%28Office.15%29.aspx)」を参照してください。
  
    
    

## Visual Studio


### Microsoft Visual Studio のプロキシの動作

Microsoft Visual Studio は、Excel Web Services を呼び出すクライアント プロジェクトのプロキシ クラスを作成する場合、次のように動作します。 
  
    
    
メソッドに戻り値がなく、1 つ以上の **out** 引数がある場合、最初の **out** 引数は移動して戻り値になります。つまり、プロキシ クラスのメソッドでは、メソッド シグネチャの引数 **out** が 1 つ少なくなります。しかし、シグネチャには、最初の **out** 引数だったものと型と内容が同じの戻り値が含まれます。
  
    
    
影響を受ける Excel Web Services メソッドは次のとおりです。
  
    
    

- **Calculate**
    
  
- **CalculateA1**
    
  
- **CalculateWorkbook**
    
  
- **CancelRequest**
    
  
- **CloseWorkbook**
    
  
- **GetSessionInformation**
    
  
- **Refresh**
    
  
- **SetCell**
    
  
- **SetCellA1**
    
  
- **SetRange**
    
  
- **SetRangeA1**
    
  

## Excel Services ユーザー定義関数


### グローバル アセンブリ キャッシュが最初にチェックされ、その後ローカル フォルダーがチェックされる

Microsoft .NET Framework の設計上、グローバル アセンブリ キャッシュ内のアセンブリは、ローカル フォルダー内の同じアセンブリの代わりに読み込まれます。共通言語ランタイムは、ローカル フォルダーを検索するより前に、グローバル アセンブリ キャッシュでアセンブリを探します。
  
    
    
このため、アセンブリがグローバル アセンブリ キャッシュにインストールされていて、UDF リストにあるが無効になっている (または UDF リストから削除されている) 場合、かつ同一のアセンブリがローカル フォルダーにインストールされていて有効になっている場合、ローカル フォルダー内のアセンブリではなくグローバル アセンブリ キャッシュ内のアセンブリが読み込まれて使用されます。
  
    
    
これは、アセンブリのバージョンが変更されるアップグレード シナリオには影響を与えません。つまり、アセンブリは同一ではないということです。
  
    
    

## 全般


### Sharedstring.xml 内の文字列の順序は維持されない

Excel Services は、ブックの共有文字列テーブル (Microsoft Office Excel XML 形式 ファイル内の Sharedstrings.xml 部分) の元の文字列の順序を維持しません。たとえば、次の手順を実行する場合を考えます。
  
    
    

1. Excel でファイルを開きます。 
    
  
2. ファイルを .xlsx ファイル形式で保存します。 
    
  
3. ファイルを、信頼できる場所であるドキュメント ライブラリにアップロードします。
    
  
4. Excel Web Access でドキュメント ライブラリ内のファイルを開きます。
    
  
5. [ **Excel で開く**] をクリックします。
    
  
6. ファイルを .xlsx ファイル形式で保存します。
    
  
手順 2 で作成した Sharedstrings.xml ファイルを 手順 6 で作成したものと比較すると、Sharedstrings.xml 部分の順序が異なる場合があることが分かります。
  
    
    
共有文字列テーブルの順序が固定であることが前提のアプリケーションは記述しないほうがよいでしょう。たとえば、共有文字列テーブルを既存のローカライズされた翻訳テーブルに置き換えることはできません。共有文字列テーブルの新しい順序に合わせて調整する必要があります。
  
    
    

## 関連項目


#### タスク


  
    
    
 [方法: 場所を信頼する](how-to-trust-a-location.md)
#### 概念


  
    
    
 [Excel Services のベスト プラクティス](excel-services-best-practices.md)
  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
  
    
    
 [Excel Services のアーキテクチャ](excel-services-architecture.md)
  
    
    
 [サポートされる機能とサポートされない機能](supported-and-unsupported-features.md)
  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
  
    
    
 [Excel Services ブログ、フォーラム、リソース](excel-services-blogs-forums-and-resources.md)
