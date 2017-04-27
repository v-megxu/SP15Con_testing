---
title: 方法 SharePoint Server でコンテンツ エンリッチメント Web サービス呼び出しを使用する
ms.prod: SHAREPOINT
ms.assetid: d4e44498-9a3d-4f2f-b5ba-6ebef9971dcb
---


# 方法: SharePoint Server でコンテンツ エンリッチメント Web サービス呼び出しを使用する
SharePoint Server 2013のコンテンツ エンリッチメント Web サービスを実装して、クロールされたアイテムの管理プロパティをインデックス作成前に変更する方法を説明します。
SharePoint 2013 の検索では、開発者がカスタム手順をコンテンツ処理に追加して、クロールされたアイテムの管理プロパティをインデックス作成前に変更できます。このカスタム手順では、処理されるアイテムの管理プロパティを拡張できる外部 Web サービスであるコンテンツ エンリッチメント Web サービスの実装、さらにこの外部 Web サービスを呼び出すためのシステムの構成が必要です。
  
    
    

外部コンテンツ エンリッチメント Web サービスの実装では、 [Microsoft.Office.Server.Search.ContentProcessingEnrichment](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.ContentProcessingEnrichment.aspx) 名前空間の下にあるインターフェイスを利用します。
## コンテンツ エンリッチメント Web サービスで使用する Windows PowerShell コマンドレット
<a name="SP15_PowerShell_Cmdlets_Content_Enrichment"> </a>

コンテンツ処理エンリッチメント機能の構成と有効化には、次の Windows PowerShell コマンドレットを使用します。
  
    
    

-  [Get-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/ja-jp/library/jj219783%28office.15%29.aspx)
    
  
-  [Set-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/ja-jp/library/jj219659%28office.15%29.aspx)
    
  
-  [Remove-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/ja-jp/library/jj219742%28office.15%29.aspx)
    
  
-  [New-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/ja-jp/library/jj219502%28office.15%29.aspx)
    
  
管理者は、これらの Windows PowerShell コマンドレットを使用して、以下のものを構成できます。
  
    
    

- 外部 Web サービスに送信される管理プロパティのカスタム セット。
    
  
- 外部 Web サービスによって返される管理プロパティのカスタム セット。
    
  
- 処理されるすべてのアイテムについて実行する述語を表すトリガー条件。トリガー条件が使用される場合、外部 Web サービスは、トリガーが **true** と評価されたときにのみ、呼び出されます。トリガー条件がまったく使用されない場合は、すべてのアイテムが外部 Web サービスに送信されます。
    
  
- **FailureMode**。Web サービスによって、コンテンツ エンリッチメント手順で処理できないアイテムをエラーとするか、これらのアイテムを一切の変更なしにパススルーできるようにします。アイテムがエラーになった場合、それらのアイテムはインデックス作成が行われず、警告が ULS ログに書き込まれます。
    
  
- **DebugMode**。外部 Web サービスのラピッド プロトタイピングを有効にします。有効にすると、外部 Web サービスは使用可能なすべての管理プロパティを受け取ります。 **DebugMode** では、トリガー条件が無視され、Web サービスによって出力された管理プロパティもすべて無視されます。
    
  
- アイテムの生データをバイナリ形式で送信する **SendRawData** スイッチ。解析されたバージョンのアイテムから取得できる以上のメタデータが必要な場合に役立ちます。
    
  
また、サイズの上限やタイムアウトを指定するためのオプションもあります。構成可能なプロパティの完全な一覧については、「 [コンテンツ エンリッチメント Web サービス呼び出しによるカスタム コンテンツ処理](custom-content-processing-with-the-content-enrichment-web-service-callout.md)」を参照してください。
  
    
    

## SharePoint Server 2013でコンテンツ エンリッチメント Web サービス呼び出しを使用するための前提条件
<a name="SP15ContentEnrich_prereq"> </a>

この方法による手順を完了するためには、開発環境に以下のものがインストールされている必要があります。
  
    
    

- SharePoint 2013 の検索
    
  
- Visual Studio 2010、または類似の .NET Framework 互換開発ツール
    
  
- SharePoint Server 2013 インストールに対する管理者特権
    
  
- サービスを IIS と共にホストできるサーバー
    
  
また、IIS でサイトを作成してそのサイトにサービスを展開する方法も把握しておく必要があります。
  
    
    

## コンテンツ エンリッチメント サービス プロジェクトをセットアップする
<a name="SP15ContentEnrich_setup"> </a>

この手順では、サービス実装プロジェクトを作成し、このプロジェクトに必須の参照情報を追加します。
  
    
    

### コンテンツ エンリッチメント サービスのプロジェクトを作成するには


1. Visual Studio のメニュー バーで、[ **ファイル**]、[ **新規作成**]、[ **プロジェクト**] の順に選択します。
    
  
2. [ **プロジェクトの種類**] の Visual C# で、[ **WCF**] を選択します。
    
  
3. [ **テンプレート**] で、[ **WCF サービス アプリケーション**] を選択します。[ **名前**] フィールドに「 **ContentProcessingEnrichmentService**」と入力し、[ **OK**] をクリックします。
    
  
4. 自動生成された **Service1** クラスと **Service1** インターフェイスを削除します。
    
  

### コンテンツ エンリッチメント サービス プロジェクトに参照情報を追加するには


1. [ **プロジェクト**] メニューの [ **参照の追加**] を選択します。
    
  
2. [ **参照**] を選択し、<インストール パス>\\Microsoft Office Servers\\15.0\\Search\\Applications\\External の下にある SharePoint インストール フォルダーで **Microsoft.Office.Server.Search.ContentProcessingEnrichment** アセンブリを探します。
    
    > **メモ**
      > 開発用でないコンピューターに SharePoint がインストールされている場合は、このアセンブリを開発用のコンピューターにコピーし、そこからこのアセンブリを参照します。 

## コンテンツ エンリッチメント サービスを作成する
<a name="SP15ContentEnrich_createservice"> </a>

コンテンツ処理エンリッチメント サービスでは、 [Microsoft.Office.Server.Search.ContentProcessingEnrichment](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.ContentProcessingEnrichment.aspx) 名前空間の **IContentProcessingEnrichmentService** インターフェイスを実装する必要があります。このセクションのコード例は、このインターフェイスの基本的な実装です。
  
    
    
この実装では、外部 Web サービスから受け取ったアイテムごとに、 **Author** と **Filename** という 2 つの管理プロパティが必要です。 **Author** は **String** オブジェクトの一覧であり、 **Filename** は **String** オブジェクトです。
  
    
    
 **IContentProcessingEnrichmentService** の実装では、生のバイナリ データをディスク上の一時的な場所 ( **Filename** で指定されたファイル名) に書き込みます。その後、新しい名前が作成者の一覧に追加され、コンテンツ処理コンポーネントに返されます。
  
    
    

### コンテンツ エンリッチメント サービスのクラス ファイルを作成するには


1. [ **プロジェクト**] メニューの [ **新しい項目の追加**] をクリックします。
    
  
2. [ **インストールされているテンプレート**] の [ **Visual C#**] で、[ **Web**]、[ **WCF サービス**] の順に選択します。
    
  
3. 「 **ContentProcessingEnrichmentService.svc**」を入力し、[ **追加**] を選択します。
    
  
4. 作成された **IContentProcessingEnrichmentService.cs** インターフェイスを削除します。
    
  

### ContentProcessingEnrichmentService クラスの既定のコードを変更するには


1. クラスの冒頭で、既存の **using** ディレクティブを以下の **using** ディレクティブで置き換えます。
    
  ```cs
  
using System;
using System.Collections.Generic;
using System.IO;
using Microsoft.Office.Server.Search.ContentProcessingEnrichment;
using Microsoft.Office.Server.Search.ContentProcessingEnrichment.PropertyTypes;

  ```

2. **DoWork** メソッドを削除します。
    
  

### IContentProcessingEnrichmentService インターフェイス メソッドを実装するには


1. クラス内部に次のコードを追加して、必須の定数とメンバーを定義します。
    
  ```cs
  
// Defines the name of the managed property 'Filename'.
private const string FileNameProperty = "Filename";

// Defines the name of the managed property 'Author'
private const string AuthorProperty = "Author";

// Defines the temporary directory where binary data will be stored.
private const string TempDirectory = @"C:\\Temp";

// Defines the error code for managed properties with an unexpected type.
private const int UnexpectedType = 1;

// Defines the error code for encountering unexpected exceptions.
private const int UnexpectedError = 2;

private readonly ProcessedItem processedItemHolder = new ProcessedItem
{ 
   ItemProperties = new List<AbstractProperty>()
};
  ```

2. 次のコードを **ProcessItem** メソッドとして追加します。
    
  ```cs
  
public ProcessedItem ProcessItem(Item item)
{
   processedItemHolder.ErrorCode = 0;
   processedItemHolder.ItemProperties.Clear();
   try
   {
      // Iterate over each property received and locate the two properties we
      // configured the system to send.
      foreach (var property in item.ItemProperties)
      {
         // Check if this is the author property.
         if (property.Name.Equals(AuthorProperty, StringComparison.Ordinal))
         {
            var author = property as Property<List<string>>;
            if (author == null)
            {
               // The author property was not of the expected type.
               // Update the error code and return. 
                  processedItemHolder.ErrorCode = UnexpectedType;
                  return processedItemHolder;
            }
               // Adding a new author to the list so it will become searchable.      
                  author.Value.Add("ExampleService");
                  processedItemHolder.ItemProperties.Add(author);
         }
         else if (property.Name.Equals(FileNameProperty, StringComparison.Ordinal))
         {
            var filename = property as Property<string>;
            if (filename == null)
            {
               // The file name property was not of the expected type.
               // Update error code and return.
                  processedItemHolder.ErrorCode = UnexpectedType;
                  return processedItemHolder;
            }
            if (!string.IsNullOrEmpty(filename.Value))
            {
               var fullFilePath = string.Join(char.ToString(Path.DirectorySeparatorChar), TempDirectory, filename.Value);
               if (item.RawData != null)
               {   
                  var outputFile = File.Create(fullFilePath);
                  using (var writer = new BinaryWriter(outputFile))
                  {
                     writer.Write(item.RawData);
                  }
               }
            }
         }
      }
   }
   catch (Exception)
   { 
      processedItemHolder.ErrorCode = UnexpectedError;
   } return processedItemHolder;
}
  ```

3. 最大 8 MB のメッセージを受け入れるように **web.config** を変更し、十分に大きな値になるように **readerQuotas** を構成します。
    
  
4. **<system.serviceModel>** 内部に次のコードを追加します。
    
  ```XML
  
<bindings>
   <basicHttpBinding>
   <!-- The service will accept a maximum blob of 8 MB. -->
      <binding maxReceivedMessageSize = "8388608">
         <readerQuotas maxDepth="32"
          maxStringContentLength="2147483647"
          maxArrayLength="2147483647"   
          maxBytesPerRead="2147483647"   
          maxNameTableCharCount="2147483647" />  
             <security mode="None" />
      </binding>
   </basicHttpBinding>
</bindings>
  ```

プロジェクトをビルドして IIS サイトに展開します。
  
    
    

## SharePoint Server 2013を構成する
<a name="SP15ContentEnrich_configure"> </a>

SharePoint 管理シェルを開き、以下に示す Windows PowerShell コマンドレットのシーケンスを入力します。
  
    
    

```

$ssa = Get-SPEnterpriseSearchServiceApplication
$config = New-SPEnterpriseSearchContentEnrichmentConfiguration
$config.Endpoint = http://Site_URL/ContentEnrichmentService.svc
$config.InputProperties = "Author", "Filename"
$config.OutputProperties = "Author"
$config.SendRawData = $True
$config.MaxRawDataSize = 8192
Set-SPEnterpriseSearchContentEnrichmentConfiguration -SearchApplication
$ssa -ContentEnrichmentConfiguration $config
```

この Windows PowerShell コマンドレットのシーケンスは、 [New-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/ja-jp/library/jj219502%28office.15%29.aspx) コマンドレットを使用して構成オブジェクトを初めて作成する場合に役立ちます。その後、この構成オブジェクトはサービス実装を指し示します。ベスト プラクティスとして、Site_URL には `http://localhost:808` を使用します。
  
    
    
管理プロパティである **Author** と **Filename** は、処理されるすべてのアイテムについてサービスに送信されます。また、Web サービス クライアントには、このサービスによって 1 つの管理プロパティ、 **Author** が出力されることが伝えられています。また、管理プロパティに加え、Web サービス クライアントも、データのサイズに対する制限付きでアイテムの生データを送信するように構成されています。さらに、 [Set-SPEnterpriseSearchContentEnrichmentConfiguration](http://technet.microsoft.com/ja-jp/library/jj219659%28office.15%29.aspx)コマンドレットは、構成全体を格納するために使用されています。このコマンドから制御が返ると、構成はアクティブになり、クロールされたコンポーネントは次のクロール処理でこの構成を使用します。
  
    
    
以上の処理が終了した後、サイトのフル クロールを開始できます。サービスが正常に動作していれば、サイトをホストしているサーバー上の一時フォルダーを監視して、ディスクに書き込まれたドキュメントを確認できます。
  
    
    
この構成は、後で次の Windows PowerShell コマンドレットを使用して削除できます。
  
    
    



```

Remove-SPEnterpriseSearchContentEnrichmentConfiguration -SearchApplication $ssa
```


## その他の技術情報
<a name="SP15ContentEnrich_addresources"> </a>


-  [SharePoint 2013 でクロールを開始、一時停止、再開、または停止する](http://technet.microsoft.com/ja-jp/library/jj219814%28office.15%29.aspx)
    
  
-  [SharePoint 2013 で検索を構成する](configure-search-in-sharepoint-2013.md)
    
  
-  [コンテンツ エンリッチメント Web サービス呼び出しによるカスタム コンテンツ処理](custom-content-processing-with-the-content-enrichment-web-service-callout.md)
    
  

