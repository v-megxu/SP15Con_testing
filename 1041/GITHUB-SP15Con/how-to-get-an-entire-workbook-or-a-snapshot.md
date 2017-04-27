---
title: 方法 ブック全体またはスナップショットの取得
keywords: how to,howdoi,howto
f1_keywords:
- how to,howdoi,howto
ms.prod: SHAREPOINT
ms.assetid: 39115503-8352-4589-87f4-cfa9c07260b6
---


# 方法: ブック全体またはスナップショットの取得

この例では、Excel Web Services を使用してブック全体を取得する方法、ファイル全体のスナップショットを取得する方法、ファイル内の表示可能なシートまたはオブジェクトのスナップショットだけを取得する方法を紹介します。ブックやスナップショットの取得は、最新のブックのコピーを取得し、それを特定の場所に保存し、それを他のユーザーに送信するなどの操作を行う場合に便利です。
  
    
    

スナップショットは、Excel Calculation Services によって生成されるブックであり、Excel Services セッションにおけるブックの現在の状態を表しています。ある種類のスナップショット ("発行されたアイテムのスナップショット" と呼ばれる) には、作成者がファイルをサーバーに保存するときに表示可能として選択した Excel ファイルの一部分だけが含まれます。スナップショットには、元のファイルのレイアウトとフォーマットのほか、Excel Calculation Services によって計算された最新の値が含まれていますが、Excel の数式や外部データ接続は含まれていません。Excel Services はサーバー上で Excel ファイルを開き、データ ソースを最新表示し、すべての Excel 数式を計算します。ユーザーまたはアプリケーションがスナップショットを要求すると、Excel Services がスナップショットを生成し、Web サービス API を通じてスナップショットを送り返します。
サーバー上の実際のファイルにアクセスする権限のないユーザーであっても、サーバーに既に保存されているブックのスナップショットであれば取得できます。
  
    
    

Web サービスの **GetWorkbook** メソッドを使用すると、ブック全体、またはスナップショットのうちの 1 種類を取得できます。たとえば、次に示すコードは、Excel ブック全体のスナップショットを返します。このコードでは、 **GetWorkbook** メソッドの 2 番目の引数に **WorkbookType.FullSnapshot** 列挙を使用しています。


```cs

byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullSnapshot, out status);
```




```VB.net
Dim workbook() As Byte = xlService.GetWorkbook(sessionId, WorkbookType.FullSnapshot, status)
```

 **GetWorkbook** メソッドは、このセッションで読み込まれたのと同じ Excel ファイル形式でバイト配列を返します。Excel ブックの作成者がブックを Excel からサーバーに保存するときに表示可能として選択した項目のスナップショットを取得するには、次の例のように、 **WorkbookType.PublishedItemsSnapshot** 列挙を使用します。


```cs
byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.PublishedItemsSnapshot, out status);
```




```VB.net
Dim workbook() As Byte = xlService.GetWorkbook(sessionId, WorkbookType.FullSnapshot, status)
```

現在のセッションの状態でブック全体のスナップショットを取得するには、 **WorkbookType.FullWorkbook** 列挙を使用します。


```cs
byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullWorkbook, out status);
```




```VB.net
Dim workbook() As Byte = xlService.GetWorkbook(sessionId, WorkbookType.FullWorkbook, status)
```

 **WorkbookType.FullWorkbook** オプションは、ユーザーがファイルを開くアクセス権を持っている場合にのみ機能します。ユーザーのアクセス権が表示のみの場合は、呼び出しが失敗します。場合によっては、コードが **GetWorkbook** 呼び出しの結果を保存しなければならないことがあります。ブックを保存する方法については、「 [[方法] ブックを保存する](http://msdn.microsoft.com/library/feb74f7a-2d8f-4672-911b-de85f8852aea%28Office.15%29.aspx)」の例を参照してください。 **GetWorkbook** メソッドと **WorkbookType** 列挙の詳細については、Excel Web Services のリファレンス ドキュメントを参照してください。
## 例

次に示すプログラム (コンソール アプリケーション) は、1 つのコマンド ライン引数 (サーバー上のブックへのパス) を受け取ります。プログラムでは、Web サービスを呼び出してサーバー上のブックを開き、スナップショットを取得します。その後、その内容が標準出力に書き込まれるため、その内容を新しいスナップショット ファイルにリダイレクトできます。 
  
    
    

```cs

using System;
using System.IO;
using System.Text;
using System.Web.Services.Protocols;
// TODO: Change the using GetSnapshot.myServer02 statement 
// to point to the Web service you are referencing.
using GetSnapshot.myServer02;

namespace GetSnapshot
{
    class ExcelServicesSnapshot
    {
        static void Main(string[] args)
        {
            try
            {
                if (args.Length < 1)
                {
                    Console.Error.WriteLine("Command line arguments should be: GetSnapshot [workbook_path] > [snapshot_filename]");
                    return;
                }
                // Instantiate the Web service and 
                // create a status array object.
                ExcelService xlService = new ExcelService();
                Status[] status;
                
                xlService.Timeout = 600000;
                // Set credentials for requests.
                // Use the current user's logon credentials.
                xlService.Credentials =   
                    System.Net.CredentialCache.DefaultCredentials;
                 
                // Open the workbook, then call GetWorkbook 
                // and close the session.
                string sessionId = xlService.OpenWorkbook(args[0], "en-US", "en-US", out status);
                byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.PublishedItemsSnapshot, out status);
                // byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullWorkbook, out status);
                // byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullSnapshot, out status);

                // Close the workbook. This also closes the session.
                status = xlService.CloseWorkbook(sessionId);

                // Write the resulting Excel file to stdout 
                // as a binary stream.
                BinaryWriter binaryWriter = new BinaryWriter(Console.OpenStandardOutput());
                binaryWriter.Write(workbook);
                binaryWriter.Close();
            }

            catch (SoapException e)
            {
                Console.WriteLine("SOAP Exception Message: {0}", e.Message);
            }

            catch (Exception e)
            {
                Console.WriteLine("Exception Message: {0}", e.Message);
            }   
        } 
    }
}
```


```VB.net

Imports System
Imports System.IO
Imports System.Text
Imports System.Web.Services.Protocols
' TODO: Change the using GetSnapshot.myServer02 statement 
' to point to the Web service you are referencing.
Imports GetSnapshot.myServer02

Namespace GetSnapshot
    Friend Class ExcelServicesSnapshot
        Shared Sub Main(ByVal args() As String)
            Try
                If args.Length < 1 Then
                    Console.Error.WriteLine("Command line arguments should be: GetSnapshot [workbook_path] > [snapshot_filename]")
                    Return
                End If
                ' Instantiate the Web service and 
                ' create a status array object.
                Dim xlService As New ExcelService()
                Dim status() As Status

                xlService.Timeout = 600000
                ' Set credentials for requests.
                ' Use the current user's logon credentials.
                xlService.Credentials = System.Net.CredentialCache.DefaultCredentials

                ' Open the workbook, then call GetWorkbook 
                ' and close the session.
                Dim sessionId As String = xlService.OpenWorkbook(args(0), "en-US", "en-US", status)
                Dim workbook() As Byte = xlService.GetWorkbook(sessionId, WorkbookType.PublishedItemsSnapshot, status)
                ' byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullWorkbook, out status);
                ' byte[] workbook = xlService.GetWorkbook(sessionId, WorkbookType.FullSnapshot, out status);

                ' Close the workbook. This also closes the session.
                status = xlService.CloseWorkbook(sessionId)

                ' Write the resulting Excel file to stdout 
                ' as a binary stream.
                Dim binaryWriter As New BinaryWriter(Console.OpenStandardOutput())
                binaryWriter.Write(workbook)
                binaryWriter.Close()

            Catch e As SoapException
                Console.WriteLine("SOAP Exception Message: {0}", e.Message)

            Catch e As Exception
                Console.WriteLine("Exception Message: {0}", e.Message)
            End Try
        End Sub
    End Class
End Namespace
```

GetSnapshot アプリケーションを実行するには、次のコマンド ラインおよび引数を使用します。 
  
    
    



```

GetSnapshot.exe [workbook_path] > [snapshot_filename]
```

以下に例を示します。 
  
    
    



```
C:\\>GetSnapshot.exe http://myServer02/reports/reports/OriginalWorkbook.xlsx > SnapshotCopy.xlsx
```

上記のコマンド ライン例を使用した場合、GetSnapshot ツールは新しいファイルを "C:\\" ディレクトリに置きます。
  
    
    

> **メモ**
> スナップショットの取得元のブックは、信頼できる場所になければなりません。 
  
    
    


## 堅牢なプログラミング

アクセス許可のある Excel Web Services サイトへの Web 参照を必ず追加してください。 `using GetSnapshot.myServer02;` ステートメントを、参照先の Web サービス サイトを指すように変更します。
  
    
    

## 関連項目


#### タスク


  
    
    
 [方法: 場所を信頼する](how-to-trust-a-location.md)
#### 概念


  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
#### その他の技術情報


  
    
    
 [ステップ 1: Web サービス クライアント プロジェクトを作成する](step-1-creating-the-web-service-client-project.md)
  
    
    
 [手順 2: Web 参照を追加する](step-2-adding-a-web-reference.md)
  
    
    
 [手順 3: Web サービスへのアクセス](step-3-accessing-the-web-service.md)
  
    
    
 [手順 4: アプリケーションのビルドとテストを行う](step-4-building-and-testing-the-application.md)
  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
