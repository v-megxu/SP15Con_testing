---
title: Excel Services UDF の理解
ms.prod: OFFICE365
ms.assetid: a1567278-fac4-4b3b-a814-56f2376c1217
---


# Excel Services UDF の理解

ユーザー定義関数 (UDF) は、Excel の計算とデータのインポート機能を拡張するカスタム関数です。開発者は、以下を提供するカスタム計算パッケージを作成します。
  
    
    


- Excel に組み込まれていない関数
    
  
- 組み込み機能のカスタム実装
    
  
- 古いまたはサポートされていないデータ ソースのカスタム データ フィード、およびアプリケーション固有のデータ フロー
    
  

ブックを作成するユーザーは、組み込みの関数を呼び出すのと同じように、たとえば「=MyUdf(A1*3.42)」などの数式を介して、セルから UDF を呼び出すことができます。
  
    
    

Excel Services UDF は、マネージ コードで記述され、Microsoft SharePoint Server 2010 に配置されるカスタム関数を呼び出すため、セル内で数式を使用する機能を提供します。UDF は次の目的に作成できます。
- カスタムの数学関数を呼び出す
    
  
- カスタム データ ソースからデータを取得してワークシートに入力する
    
  
- UDF から Web サービスを呼び出す
    
  

## マネージ コード UDF を作成する

Excel Services マネージ コード UDF を作成する簡単な方法は、Microsoft Visual Studio 2005 クラス ライブラリ テンプレートを使用することです。マネージ コード UDF プロジェクト内で、Microsoft.Office.Excel.Server.Udf.dll という Excel Services UDF ダイナミック リンク ライブラリ (DLL) を参照する必要があります。 
  
    
    
Microsoft.Office.Excel.Server.Udf.dll は、Microsoft.NET Framework 2.0 を使用してコンパイルされました。Visual Studio 2003 を使用してマネージ コード UDF を作成する場合は、 Microsoft.Office.Excel.Server.Udf.dll を参照できなくなります。古いバージョンの .NET Framework で作成されたアセンブリで .NET Framework 2.0 によって作成されたアセンブリを参照することはできません。
  
    
    

### 必須の属性

Excel Services UDF クラスとしてクラス内のカスタム関数を使用するには、UDF クラスを **Microsoft.Office.Excel.Server.Udf.UdfClass** 属性でマークする必要があります。UDF アセンブリにおいてこの属性でマークされていないクラスはすべて、Excel Calculation Services によって無視されます。これらは Excel Services UDF クラスとしてみなされないためです。
  
    
    
Excel Services UDF メソッドとしてクラス内のカスタム関数を使用するには、UDF メソッドを **Microsoft.Office.Excel.Server.Udf.UdfMethod** 属性でマークする必要があります。UDF アセンブリにおいてこの属性でマークされていないメソッドはすべて無視されます。これらは Excel Services UDF メソッドしてみなされないためです。
  
    
    
 **Microsoft.Office.Excel.Server.Udf.UdfMethod**属性には **IsVolatile** プロパティがあります。 **IsVolatile** プロパティを使用すると、UDF メソッドを volatile または nonvolatile に指定できます。 **IsVolatile** プロパティはブール値 (Boolean) をとります。既定値は **false** で、特定の UDF メソッドが不揮発であることを意味します。
  
    
    

### Microsoft.Office.Excel.Server.Udf.dll の場所

SharePoint Server 2010 がインストールされているコンピューターの次の場所に、Microsoft.Office.Excel.Server.Udf.dll のコピーがあります。
  
    
    
 `[drive:]\\Program Files\\Common Files\\Microsoft Shared\\web server extensions\\14\\ISAPI`
  
    
    

## 配置とセキュリティ


### 配置場所の種類

UDF アセンブリは、ローカル ディレクトリ、グローバル アセンブリ キャッシュ、またはネットワーク共有に置くことができます。 ファームのシナリオでは、ローカル ディレクトリのパスはファーム全体で同じである必要があります。
  
    
    

### UDF アセンブリの識別

UDF アセンブリの ID は、呼び出す Excel Calculation Services のアセンブリの完全なパスまたは厳密な名前を使用すると公開できます。 
  
    
    
たとえば、以下を使用できます。
  
    
    

- C:\\UDFs\\MySampleUdf.dll 
    
  
- \\\\MyNetworkServer\\UDFs\\MySampleUdf.dll
    
  
- CompanyName.Hierarchichal.MyUdfNamespace.MyUdfClassName.dll, Version=1.1.0.0, Culture=en, PublicKeyToken=e8123117d7ba9ae38
    
  

### UDF アセンブリの有効化

UDF アセンブリは、既定では無効です。 
  
    
    
Excel Services の信頼できる場所のそれぞれには **AllowUdfs** フラグがあります。
  
    
    

> **メモ**
> **AllowUdfs** フラグは、[Excel Services: 信頼できるファイル保存場所] ページにある [ **User-defined functions allowed**] オプションで示されます。[信頼できるファイル保存場所] ページにナビゲートする方法について知るには、「 [ステップ 3: UDF を展開して有効にする](step-3-deploying-and-enabling-udfs.md)」を参照してください。 
  
    
    

 **AllowUdfs** の既定値は **false** です。特定の信頼できる場所で **AllowUdfs** の値を **false** に設定すると、その信頼された場所にあるブックは UDF の呼び出しが許可されません。
  
    
    
特定の信頼できる場所からの UDF の呼び出しを許可するには、 **AllowUdfs** の値を **true** に設定します。
  
    
    
この信頼できる場所に UDF の呼び出しがあるブックでセッションが開始したときに **AllowUdfs** の値が **false** である場合、UDF の呼び出しは失敗します。セッションが開始した後に **AllowUdfs** の値を **true** に変更しても、UDF の呼び出しは失敗します。これは、 **AllowUdfs** フラグの変更は、構成データベースが更新された後、次回のセッションで有効になるためです。
  
    
    

### UDF アセンブリの実行を許可する

管理者は、UDF アセンブリを実行する場合、すべての UDF アセンブリを登録してから、信頼できる場所で **AllowUdfs** フラグを **true** に設定して、ブックが UDF を呼び出せるようにします。
  
    
    

### UDF アセンブリの再読み込み

UDF アセンブリを再読み込みするには、 **iisreset** を実行するか、Excel Calculation Services アプリケーション ドメインを再起動します。
  
    
    

> **注意**
> IIS をリセットすると、現在のセッションはすべて終了します。 > 詳細は、「 [UDF を有効にする方法](how-to-enable-udfs.md)」を参照してください。 
  
    
    

詳細は、「 [メモリからアプリケーションをアンロードする](http://go.microsoft.com/fwlink/?LinkId=65706)」(http://msdn.microsoft.com/library/default.asp?url=/library/ja-jp/csvr2002/htm/cs_mmc_administering_myhj.asp) を参照してください。
  
    
    

### UDF アセンブリの既定コード アクセス セキュリティのアクセス許可

既定では、UDF アセンブリを完全信頼で実行します。 
  
    
    

### UDF アセンブリ用のコード アクセス セキュリティのアクセス許可を制限する

特定の UDF アセンブリを完全信頼で実行しないようにするには、その UDF アセンブリに対するコード アクセス セキュリティのアクセス許可を明示的に制限する必要があります。コード グループを構成し、アクセス許可を制限するには, .NET Framework 2.0 構成ツールを使用します。 
  
    
    
開発者は、コード内で **RequestMinimum** メソッドおよび **RequestOptional** メソッドを使用して、UDF アセンブリが必要以上のアクセス許可を得ないようにすることもできます。
  
    
    
コード グループの構成、および **RequestMinimum** メソッドと **RequestOptional** メソッドについて、詳細は MSDN の以下の記事を参照してください。
  
    
    

-  [.NET Framework 構成ツールを使用してコード グループを構成する](http://msdn.microsoft.com/library/default.asp?url=/library/ja-jp/cpguide/html/cpconUsingNETConfigurationToolToWorkWithCodeGroups.asp?frame=true) (http://msdn.microsoft.com/library/default.asp?url=/library/ja-jp/cpguide/html/cpconUsingNETConfigurationToolToWorkWithCodeGroups.asp?frame=true)
    
  
-  [コード アクセス セキュリティの実践](http://go.microsoft.com/fwlink/?LinkId=65465) (http://msdn.microsoft.com/library/default.asp?url=/library/ja-jp/dnnetsec/html/thcmch08.asp)
    
  

## 関連項目


#### タスク


  
    
    
 [方法: Web サービスを呼び出す UDF の作成](how-to-create-a-udf-that-calls-a-web-service.md)
  
    
    
 [方法: 場所を信頼する](how-to-trust-a-location.md)
  
    
    
 [例外をキャッチする方法](how-to-catch-exceptions.md)
  
    
    
 [UDF を有効にする方法](how-to-enable-udfs.md)
#### 概念


  
    
    
 [チュートリアル: マネージ コード UDF を開発する](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [Excel Services UDF に関するよく寄せられる質問](frequently-asked-questions-about-excel-services-udfs.md)
  
    
    
 [Excel Services のアーキテクチャ](excel-services-architecture.md)
  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
  
    
    
 [Excel Services の既知の問題およびヒント](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services のベスト プラクティス](excel-services-best-practices.md)
