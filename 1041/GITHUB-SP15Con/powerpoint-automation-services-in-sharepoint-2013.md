---
title: SharePoint 2013 の PowerPoint Automation Services
ms.prod: SHAREPOINT
ms.assetid: 168c7dc0-fbdc-41a2-84db-65d211d3d673
---


# SharePoint 2013 の PowerPoint Automation Services
Microsoft PowerPoint Automation Services を使用して、サーバー側でプレゼンテーションをさまざまなファイル形式に変換する方法について説明します。 

  
    
    

 * **Applies to:*** *Microsoft SharePoint Server 2013*  | *Microsoft PowerPoint Automation Services* 
## 概要
<a name="PAS_Intro"> </a>

大企業および中小企業の多くは Microsoft SharePoint Server ライブラリを Microsoft PowerPoint プレゼンテーションのリポジトリとして使用します。これらの企業では、プレゼンテーションの保存、配布、更新に対して独自のニーズがあります。Microsoft PowerPoint Automation Services は Microsoft SharePoint Server 2013 の新機能で、企業のプレゼンテーションの管理に役立ちます。これは共有サービスであり、これを使用して、サーバー側でプレゼンテーションを他の形式に無人で変換できます。これは最初からサーバーで動作するように設計されており、信頼性の高い予測可能な方法で多くのプレゼンテーション ファイルを処理できます。
  
    
    
PowerPoint Automation Services を使用して PowerPoint バイナリ ファイル形式 (.ppt) および PowerPoint Open XML ファイル形式 (.pptx) から他の形式に変換できます。たとえば、PowerPoint 97-2003 ファイルのバッチを Open XML のプレゼンテーション ファイルにアップグレードが必要な場合があります。また、[ **編集**] メニューでカスタム アクションを作成して、ユーザーがオン デマンドでプレゼンテーションの PDF 版を作成できるようにする場合もあります。
  
    
    

> **メモ**
> PowerPoint Automation Services は、SharePoint 2013 の機能を利用し、またその機能の 1 つとなっています。PowerPoint Automation Services を使用するには、SharePoint Server 2013 をインストールしておく必要があります。サーバー ファームで SharePoint Server 2013 を使用する場合、PowerPoint Automation Services を明示的に有効にする必要があります。 
  
    
    


## PowerPoint Automation Services のシナリオ
<a name="PAS_Scenarios"> </a>

次のシナリオでは、PowerPoint Automation Services を使用してサーバー上でプレゼンテーションを自動処理する方法をいくつか説明します。
  
    
    

- ある大企業は、すべての年間収益のプレゼンテーションを企業のイントラネット サイト上の単一のドキュメント ライブラリに保存しています。このライブラリには、長年にわたって蓄積された多くのプレゼンテーションが含まれています。IT 部門では、PowerPoint 97-2003 のバイナリ ファイル形式 (.ppt) のプレゼンテーション ファイルをすべて Open XML のプレゼンテーション ファイル形式に (.pptx) アップグレードすることを望んでいます。変換を行う開発者は、ライブラリ内の各ファイルに対して反復処理を行い、ファイルが .ppt 形式であることを確認し、各 .ppt ファイルを .pptx ファイル形式に変換するソリューションをサーバーに展開することを決定します。
    
  
- 地域の営業部は、各顧客に対してカスタム サービスの見積もりを提供します。各営業担当者は、対面またはオンラインの会議で顧客に見積もりを伝えます。会議後、営業担当者はこの見積もりのコピーを PDF 形式で顧客に提供します。この部署ではベンダーを雇い、エクストラネットのドキュメント ライブラリに保存された PowerPoint ファイルの [ **編集**] メニューにカスタムの verb を作成します。verb がクリックされると、サーバーは PowerPoint ファイルを同じライブラリ内で PDF に変換するプログラムを実行します。
    
  

### サポートされる変換元のプレゼンテーション形式

プレゼンテーションの変換元の形式として、次の形式がサポートされます。
  
    
    

- Open XML ファイル形式のプレゼンテーション形式 (.pptx)
    
  
- PowerPoint 97-2003 プレゼンテーション (.ppt)
    
  

### サポートされる変換先のドキュメント形式

サポートされる変換先のドキュメント形式には、サポートされる変換元のドキュメント形式のすべてと次の形式が含まれます。
  
    
    

- .pptx (Open XML ファイル形式のプレゼンテーション形式)
    
  
- .pdf
    
  
- .xps (Open XML Paper Specification)
    
  
- .jpg
    
  
- .png (Portable Network Graphics 形式)
    
  

### PowerPoint Automation Services の制限事項

PowerPoint Automation Services には、ドキュメントの印刷機能が組み込まれていません。ただし、PowerPoint プレゼンテーション ファイル (.ppt および .pptx) を PDF または XPS に変換して、プリンターにスプールすることは簡単にできます。
  
    
    

## PowerPoint Automation Services の API
<a name="PAS_APIs"> </a>

PowerPoint Automation Services を使用するには、そのプログラミング インターフェイスを使用して SharePoint Server 2013 サーバーに変換要求を送信します。各変換要求に対して、変換するファイルと変換ジョブの出力形式を指定します。一部の変換要求では、コメント、非表示のスライド、ドキュメント プロパティなどの変換するコンテンツのタイプを指定できます。
  
    
    
PowerPoint Automation Services は、変換要求の送受信に非同期パターン メソッドを使用します。したがって、変換要求が送信された後に実行を継続するコードを記述できます。変換要求の完了後にユーザーに通知を示す必要がある場合には、操作が完了したときに実行するコールバック メソッドを参照するデリゲートを指定できます。 
  
    
    

> **メモ**
> 非同期デザイン パターンの操作方法の詳細については、「 [非同期プログラミング モデル (APM)](http://msdn.microsoft.com/ja-jp/library/ms228963.aspx)」を参照してください。 
  
    
    

以下のセクションでは、変換要求の送受信に必要なクラスの制限されたリストを取り上げます。これらのクラスはすべて、 **Microsoft.Office.Server.PowerPoint.Conversion** 名前空間に含まれます。
  
    
    

### Request 基本クラス

 **Request** クラスは **Microsoft.Office.Server.PowerPoint.Conversion** 名前空間の中で最も基本的なクラスです。他のすべてのrequest タイプ ( **PresentationRequest**、 **PictureRequest**、 **PdfRequest**、および **XpsRequest**) はこのクラスを継承します。 
  
    
    

**表 1. Request 基本クラス メンバー**


|**メンバー名**|**説明**|
|:-----|:-----|
|**BeginConvert(Microsoft.SharePoint.SPServiceContext, System.AsyncCallback, System.Object)** メソッド <br/> |変換操作を開始します。最初のパラメーター  _serviceContext_ は、変換されるファイルがある SharePoint サイトのコンテキストを指定します。操作が完了したら、 _callback_ パラメーターを使用して実行するメソッドを参照するデリゲートを指定します。呼び出しているコードからコールバック メソッドに追加の情報を渡す必要がある場合には、 _state_ パラメーターを使用します。 <br/>  [IAsyncResult](https://msdn.microsoft.com/library/System.IAsyncResult.aspx) オブジェクトを返します。 <br/> |
|**EndConvert(IAsyncResult)** メソッド <br/> |変換操作を終了します。 _result_ パラメーターは、対応する **BeginConvert** 変換要求が返す結果の [IAsyncResult](https://msdn.microsoft.com/library/System.IAsyncResult.aspx) オブジェクトを期待します。 **EndConvert** が呼び出されたときに要求が完了していない場合、呼び出し側のスレッドは、変換操作が完了するまでブロックされます。 <br/> 値は返されません。  <br/> |
   

### PresentationRequest クラス

 **Request** クラスから継承する **PresentationRequest** クラス。PowerPoint 97-2003 ファイル (.ppt) または Open XML ファイル形式のプレゼンテーション (.pptx) を別のプレゼンテーション ファイル形式に変換します。先に述べた最初のシナリオでは、このクラスを使用してドキュメント ライブラリ内の古いプレゼンテーション ファイルを Open XML ファイル形式のプレゼンテーション形式に変換します。
  
    
    
 **PresentationRequest** クラスのコンストラクター メソッドには、必要なパラメーターが 3 つあります。
  
    
    

-  _input_:  [Stream](https://msdn.microsoft.com/library/System.IO.Stream.aspx) オブジェクトとして変換するファイルを取得。
    
  
-  _extension_: 変換されるファイルのファイル拡張子を指定する文字列。
    
  
-  _output_: 出力を保存する場所を指定する  [SPFileStream](http://msdn.microsoft.com/ja-jp/library/microsoft.sharepoint.spfilestream%28office.12%29.aspx) オブジェクト。
    
  
 **PresentationRequest** クラスには、 _settings_ パラメーターを追加するコンストラクター メソッドの単一のオーバーロードがあります。 _settings_ パラメーターは **PresentationSettings** オブジェクトを引数として受け付けます。
  
    
    

> **ヒント**
> 出力  [Stream](https://msdn.microsoft.com/library/System.IO.Stream.aspx) オブジェクトを [SPFile](http://msdn.microsoft.com/ja-jp/library/microsoft.sharepoint.spfile%28office.12%29.aspx) オブジェクトに変換しなおす場合には、結果のファイルに付けられる拡張子が目的のファイル タイプ (.ppt または .pptx) の拡張子と一致していることを確認してください。
  
    
    


### PdfRequest クラス

 **PdfRequest** クラスも **Request** クラスから継承し、PowerPoint 97-2003 ファイル (.ppt) または Open XML ファイル形式のプレゼンテーション (.pptx) を .pdf ファイルに変換します。先に述べた 2 つ目のシナリオでは、このクラスを使用してプレゼンテーションを PDF ファイルに変換します。
  
    
    
 **PresentationRequest** クラスと同様に、 **PdfRequest** クラス用のコンストラクター メソッドにも 3 つの必要なパラメーター ( _input_、 _extension_、および  _output_) があります。
  
    
    
 **PdfRequest** クラスにも、 _settings_ パラメーターを追加するコンストラクター メソッドの単一のオーバーロードがあります。 _settings_ パラメーターは **FixedFormatSettings** オブジェクトを引数として受け付けます。
  
    
    

> **ヒント**
> 出力  [Stream](https://msdn.microsoft.com/library/System.IO.Stream.aspx) オブジェクトを [SPFile](http://msdn.microsoft.com/ja-jp/library/microsoft.sharepoint.spfile%28office.12%29.aspx) オブジェクトに変換しなおす場合には、結果のファイルに付けられる拡張子が目的のファイル タイプ (.pdf) の拡張子と一致していることを確認してください。
  
    
    


### PictureRequest クラス

 **PictureRequest** クラスも **Request** クラスから継承し、PowerPoint 97-2003 ファイル (.ppt) または Open XML ファイル形式のプレゼンテーション (.pptx) を .jpg または .png のいずれかの形式の画像ファイルのコレクションに変換します。
  
    
    
 **PictureRequest** クラスのコンストラクター メソッドにも、必要なパラメーターが 4 つあります。 _input_、 _extension_、および  _output_ パラメーターは **PresentationRequest** クラス コンストラクターのパラメーターと同様です。 **PictureRequest** クラスのコンストラクター メソッドにも必要な _format_ パラメーターがあり、これは **PictureFormat** 列挙型の定数である必要があります。
  
    
    
 **PictureRequest** クラスでは、そのコンストラクター メソッドに対するオーバーロードはありません。
  
    
    

> **ヒント**
> **PictureRequest** クラスは、画像ファイルのパッケージを含むストリームを返します。出力 [Stream](https://msdn.microsoft.com/library/System.IO.Stream.aspx) オブジェクトを [SPFile](http://msdn.microsoft.com/ja-jp/library/microsoft.sharepoint.spfile%28office.12%29.aspx) オブジェクトに変換しなおす場合には、結果のファイルに付けられる拡張子が .zipであることを確認してください。
  
    
    


## PowerPoint Automation Services アプリケーションの構築
<a name="PAS_Build"> </a>

PowerPoint Automation Services を使用するコードの作成方法を示す最も簡単な方法は、コンソール アプリケーションを構築することです。 コンソール アプリケーションは、クライアント コンピューター上ではなく SharePoint Server 上で構築し、実行する必要があります。変換要求を開始するコードは、変換要求コードが Web パーツ、ワークフロー、またはイベント ハンドラーに組み込まれていても同様です。次の手順では、コンソール アプリケーションから PowerPoint Automation Services を使用することで、Web パーツ、イベント ハンドラー、またはワークフローの複雑性を追加することなく API を使用する方法について説明します。
  
    
    

> **メモ**
> PowerPoint Automation Services は SharePoint Server 2013 のサービスであるため、SharePoint Server 上で直接実行されるアプリケーション内でのみ使用できます。アプリケーションは、ファーム ソリューション として構築する必要があります。PowerPoint Automation Services は セキュリティで保護されたソリューション から使用できません。 
  
    
    


### アプリケーションを構築するには


1. Microsoft Visual Studio 2012 を起動します。
    
  
2. [ **ファイル**] メニューの [ **新規作成**] をポイントし、[ **プロジェクト**] を選択します。 
    
  
3. [ **新しいプロジェクト**] ダイアログ ボックスの [ **インストール済み**] で [ **テンプレート**] を展開し、[ **Visual C#**] を展開して [ **Windows**] を選択します。
    
  
4. プロジェクト テンプレートの一覧で、[ **コンソール アプリケーション**] を選択します。
    
  
5. Visual Studio 内のプロジェクトが .NET Framework 4 を対象としていることを確認します。
    
    > **メモ**
      > 以前のバージョンの SharePoint Server では, .NET Framework 3.5 を対象にする必要がありました。今度の Microsoft.SharePoint ライブラリは, .NET Framework 4 のアセンブリを参照します。プロジェクトが .NET Framework 4 Client Profile ではなく、完全な .NET Framework 4 を対象としていることも確認します。 
6. [ **名前**] ボックスに、たとえば、 PAS_Sampleなどのプロジェクトに使用する名前を入力します。
    
  
7. [ **場所**] ボックスに、プロジェクトを保存する場所を入力します。
    
  
8. [ **OK**] をクリックして、ソリューションを作成します。
    
  
9. 既定で、Visual Studio 2012 は x86 CPU を対象とするプロジェクトを作成しますが、SharePoint Server アプリケーションを構築するには、すべての CPU を対象とする必要があります。
    
    Microsoft Visual C# アプリケーションを構築する場合、 **ソリューション エクスプローラー**で、プロジェクトを右クリックし、[ **プロパティ**] をクリックします。
    
  - プロジェクトの [ **プロパティ**] ウィンドウで、[ **ビルド**] をクリックします。
    
  
  - [ **構成**] の一覧をポイントし、[ **すべての構成**] を選択します。
    
  
  - [ **プラットフォーム ターゲット**] の一覧をポイントし、[ **Any CPU**] を選択します。
    
  

    
    
    Microsoft Visual Basic .NET Framework アプリケーションを構築する場合、[ **プロパティ**] ウィンドウで [ **コンパイル**] をクリックします。
    
  - [ **詳細コンパイル オプション**] をクリックします。
    
  
  - [ **構成**] の一覧をポイントし、[ **すべての構成**] を選択します。
    
  
  - [ **プラットフォーム ターゲット**] の一覧をポイントし、[ **Any CPU**] をクリックします。
    
  

    
    
  
10. [ **プロジェクト**] メニューの [ **参照の追加**] をクリックし、[ **参照の追加**] ダイアログ ボックスを開きます。 
    
  
11. [ **アセンブリ**] を展開し、次の操作を行います。 
    
  - [ **フレームワーク**] を展開し、System.Web への参照を追加します。
    
  
  - [ **拡張子**] を展開し、Microsoft.SharePoint への参照を追加します。
    
  
12. また、[ **参照の追加**] ダイアログ ボックスで [ **参照**] を選択し、Microsoft.Office.Server.PowerPoint.dll (既定の場所は C:\\Windows\\Microsoft.NET\\assembly\\GAC_MSIL\\Microsoft.Office.Server.PowerPoint\\v4.0_15.0.0.0__71e9bce111e9429c) の場所に移動し、アセンブリを選択してから [ **追加**] を選択します。 
    
  
以下の C# および Visual Basic の例では、SharePoint サイトの共有ドキュメント フォルダーの PowerPoint 97-2003 ファイル (.ppt) を同じフォルダー内の PowerPoint Open XML ファイル (.pptx) に変換する、シンプルな PowerPoint Automation Services アプリケーションを示しています。
  
    
    



```cs

using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using System.Text;
using System.Web;
using Microsoft.SharePoint;
using Microsoft.Office.Server.PowerPoint.Conversion;

namespace PAS_Sample
{
    class Program
    {
        static void Main(string[] args)
        {
            try
            {
                string siteURL = "http://localhost";
                using (SPSite site = new SPSite(siteURL))
                {
                    using (SPWeb web = site.OpenWeb())
                    {
                        Console.WriteLine("Begin conversion");

                        // Get a reference to the "Shared Documents" library 
                        // and the presentation file to be converted.
                        SPFolder docs = web.Folders[siteURL + 
                            "/Shared Documents"];
                        SPFile file = docs.Files[siteURL + 
                            "/Shared Documents/Pres1.ppt"];

                        // Convert the file to a stream and create an
                        // SPFileStream object for the conversion output.
                        Stream fStream = file.OpenBinaryStream();
                        SPFileStream stream = new SPFileStream(web, 0x1000);

                        // Create the presentation conversion request.
                        PresentationRequest request = new PresentationRequest(
                            fStream,
                            ".ppt",
                            stream);

                        // Send the request synchronously, passing
                        // in a 'null' value for the callback parameter, 
                        // and capturing the response in the result object.
                        IAsyncResult result = request.BeginConvert(
                            SPServiceContext.GetContext(site),
                            null,
                            null);

                        // Use the EndConvert method to get the result. 
                        request.EndConvert(result);

                        // Add the converted file to the document library.
                        SPFile newFile = docs.Files.Add(
                            "newPres1.pptx", 
                            stream, 
                            true);
                        Console.WriteLine("Output: {0}", newFile.Url);

                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine("Error: " + ex.Message);
            }
            finally
            {
                Console.WriteLine("Complete");
                Console.ReadKey();
            }
        }
    }
}
```




```VB.net

Imports System
Imports System.Collections.Generic
Imports System.IO
Imports System.Linq
Imports System.Text
Imports System.Web
Imports Microsoft.SharePoint
Imports Microsoft.Office.Server.PowerPoint.Conversion

Namespace PAS_Sample
    Class Program
        Private Shared Sub Main(args As String())
            Try
                Dim siteURL As String = "http://localhost"
                Using site As New SPSite(siteURL)
                    Using web As SPWeb = site.OpenWeb()
                        Console.WriteLine("Begin conversion")

                        ' Get a reference to the "Shared Documents" library 
                        ' and the presentation file to be converted.
                        Dim docs As SPFolder = web.Folders(siteURL + _
                            "/Shared Documents")
                        Dim file As SPFile = docs.Files(siteURL + _
                            "/Shared Documents/Pres1.ppt")

                        ' Convert the file to a stream and create an
                        ' SPFileStream object for the conversion output.
                        Dim fStream As Stream = file.OpenBinaryStream()
                        Dim stream As New SPFileStream(web, &amp;H1000)

                        ' Create the presentation conversion request.
                        Dim request As New PresentationRequest(fStream, _
                            ".ppt", 
                            stream)

                        ' Send the request synchronously, passing
                        ' in a Nothing value for the callback parameter, 
                        ' and capturing the response in the result object.
                        Dim result As IAsyncResult = request.BeginConvert(_
                            SPServiceContext.GetContext(site), _
                            Nothing, _
                            Nothing)

                        ' Use the EndConvert method to get the result. 
                        request.EndConvert(result)

                        ' Add the converted file to the document library.
                        Dim newFile As SPFile = docs.Files.Add(_
                            "newPres1.pptx", _
                            stream, _
                            True)

                        Console.WriteLine("Output: {0}", newFile.Url)
                    End Using
                End Using
            Catch ex As Exception
                Console.WriteLine("Error: " + ex.Message)
            Finally
                Console.WriteLine("Complete")
                Console.ReadKey()
            End Try
        End Sub
    End Class
End Namespace

```


### 例をビルドして実行するには


1. PowerPoint ドキュメント ( Pres1.ppt ) を SharePoint サイトの共有ドキュメント フォルダーに追加します。
    
  
2. 例をビルドして実行します。
    
  
3. 変換プロセスの実行を 1 分待機した後、SharePoint サイトの共有ドキュメント フォルダーに移動し、ページを更新します。ドキュメント ライブラリに新しい PowerPoint ドキュメントである Pres1.pptx が含まれています。
    
  
SharePoint Server 2013 上の PowerPoint Automation Services は、プレゼンテーション ファイルを管理する高度な機能を企業に提供します。この高パフォーマンスのソリューションによって、スケーラブルな、サーバー側のプレゼンテーションの操作と生成をバッチで、または要求時に実行できるようになります。 
  
    
    

> **メモ**
>  この例を実行する前に、PowerPoint Automation Services が SharePoint サーバーの全体管理コンソールで有効になっていることを確認してください。>  PowerPoint Automation Services が有効になっていることを確認するには、次の操作を行います。>  サーバーの全体管理コンソールの [ **システム設定**] で、[ **サーバーのサービスの管理**] を選択し、[ **PowerPoint Conversion Service**] が [ **Started**] に設定されていることを確認します。 >  また、サーバーの全体管理コンソールの [ **アプリケーション構成の管理**] で [ **サービス アプリケーションの管理**] を選択し、[ **PowerPoint Conversion Service Application**] および [ **PowerPoint Conversion Service Application Proxy**] が [Started] に設定されていることを確認します。 
  
    
    


## まとめ
<a name="PAS_Conclusion"> </a>

SharePoint Server 2013 上の PowerPoint Automation Services は、プレゼンテーション ファイルを管理する高度な機能を企業に提供します。この高パフォーマンスのソリューションによって、スケーラブルな、サーバー側のプレゼンテーションの操作と生成をバッチで、または要求時に実行できるようになります。 
  
    
    

## その他の技術情報
<a name="PAS_Additional"> </a>


-  [SharePoint 2010 Word Automation Services での開発](http://msdn.microsoft.com/ja-jp/library/ff742315.aspx)
    
  
-  [PowerPoint デベロッパー ポータル](http://msdn.microsoft.com/ja-jp/office/aa905465)
    
  
-  [SharePoint デベロッパー センター](http://msdn.microsoft.com/ja-jp/sharepoint/default.aspx)
    
  

