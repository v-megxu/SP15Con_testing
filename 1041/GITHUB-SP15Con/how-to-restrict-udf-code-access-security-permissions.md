---
title: 方法 UDF コード アクセス セキュリティのアクセス許可を制限する
keywords: cas,how to,howdoi,howto,UDF list
f1_keywords:
- cas,how to,howdoi,howto,UDF list
ms.prod: OFFICE365
ms.assetid: 4f022e0d-1fe3-4fab-b41f-82a0d628f77c
---


# 方法: UDF コード アクセス セキュリティのアクセス許可を制限する

特定のユーザー定義関数 (UDF) アセンブリを完全信頼で実行しないようにするには、そのアセンブリに対するコード アクセスのセキュリティ アクセス許可を明示的に制限する必要があります。コード グループを構成し、アクセス許可を制限するには, .NET Framework 2.0 構成ツールを使用します。 
  
    
    

たとえば、複数のメソッドを含む UDF アセンブリに関するシナリオを考えてみましょう。1 つの UDF メソッドはカスタム計算を実行し、同じアセンブリに含まれるもう 1 つの UDF メソッドは Web サービスを呼び出して株価を取得します。ユーザーは最初のメソッド (計算) を呼び出す Excel ブックのみを使用するため、このアセンブリからの Web アクセスを無効にしてセキュリティを高めることにします。 
UDF アセンブリは、サーバー上のフォルダー C:\\UdfAssemblies\\CalcAndWebAccessUdf.dll にインストールしました。アセンブリは Microsoft SharePoint Server 2010 と同じコンピューター上にあるため、Excel Calculation Services によって UDF アセンブリが読み込まれるとき、それは MyComputer ゾーンに読み込まれます。既定で、MyComputer ゾーンは完全信頼されます。したがって、読み込まれた UDF アセンブリには完全信頼のアクセス許可が付与されます。 
  
    
    

UDF アセンブリをロックダウンして Web アクセスをできないようにするには、以下の手順を実行して、付与されているアクセス許可セットを明示的に制限する必要があります。
1. 新しい URL ベースのコード グループをマシン レベルの My_Computer_Zone の下に作成します。コード グループのスコープをその特定のアセンブリに設定し、カスタム アクセス許可セットを作成します。
    
  
2. カスタム コード グループのプロパティを、そのカスタム コード グループに関連付けられたアクセス許可セットからのアクセス許可のみをポリシー レベルが持つという構成にします。同じコンピューター上に存在する UDF アセンブリを Excel Calculation Services が読み込むとき、アセンブリは MyComputer ゾーンに読み込まれます。したがって、既定では、UDF アセンブリには完全信頼が付与されます。カスタム アクセス許可セットと完全信頼アクセス許可セットの論理積をとると、結果は完全信頼になります。そうではなく、カスタム コード グループに関連付けられたアクセス許可セットからのアクセス許可のみをポリシーに設定するには、[ **このポリシー レベルはこのコード グループに関連するアクセス許可セットからのアクセス許可のみを持つ**] プロパティを有効にする必要があります。
    
  
コード グループを構成する方法の詳細については、MSDN の以下の資料を参照してください。
-  [.NET Framework 構成ツールを使用してコード グループを構成する](http://msdn.microsoft.com/library/default.asp?url=/library/ja-jp/cpguide/html/cpconUsingNETConfigurationToolToWorkWithCodeGroups.asp?frame=true) (http://msdn.microsoft.com/library/default.asp?url=/library/ja-jp/cpguide/html/cpconUsingNETConfigurationToolToWorkWithCodeGroups.asp?frame=true)
    
  
-  [コード アクセス セキュリティの実践](http://msdn.microsoft.com/library/default.asp?url=/library/ja-jp/dnnetsec/html/thcmch08.asp) (http://msdn.microsoft.com/library/default.asp?url=/library/ja-jp/dnnetsec/html/thcmch08.asp)
    
  

### 新しいコード グループを作成するには


1. [ **スタート**] をクリックし、[ **すべてのプログラム**]、[ **管理ツール**] とポイントしてから、[ **Microsoft .NET Framework 2.0 Configuration**] をクリックします。 
    
    これにより、[ **.NET 2.0 Framework Configuration**] ツールが開始されます。
    
  
2. 左側のウィンドウで、[ **マイ コンピューター**] ノードを展開し、[ **ランタイム セキュリティ ポリシー**] ノードを展開します。
    
  
3. [ **マシン**] ノードを展開します。
    
  
4. [ **コード グループ**] ノードを展開します。
    
  
5. [ **All_Code**] ノードを展開します。
    
  
6. [ **My_Computer_Zone**] ノードを展開します。[ **My_Computer_Zone**] を右クリックしてから、[ **新規**] を選択します。[ **新しいコード グループの識別**] ダイアログ ボックスが表示されます。
    
  
7. [ **新しいコード グループを作成する**] を選択します。
    
  
8. [ **名前**] フィールドに、新しいコード グループの名前を入力します。例: RestrictWebAccessUdf。
    
  
9. [ **次へ**] をクリックします。
    
  
10. コード グループのスコープを特定の UDF アセンブリに限定するために、[ **このコード グループの条件の種類を選択します**] から [ **URL**] を選択します。 
    
    これにより、[ **URL**] フィールドが表示されます。
    
  
11. [ **URL**] フィールドに、Web へのアクセスを制限する UDF アセンブリへのパスを入力します。例: C:\\UdfAssemblies\\CalcAndWebAccessUdf.dll。
    
  
12. [ **次へ**] をクリックします。
    
  
13. [ **新しいアクセス許可セットの作成**] を選択し、[ **次へ**] をクリックします。
    
  
14. [ **名前**] フィールドに、アクセス許可セットの名前を入力します。例: AssemblyExecutionCustomPermissionSet。
    
  
15. [ **次へ**] をクリックします。
    
  
16. UDF アセンブリに "アセンブリ実行" アクセス許可を付与するために、[ **アセンブリへのアクセス許可**] の一覧から [ **セキュリティ**] を選択した後、[ **追加**] をクリックします。 
    
    これにより、[ **アクセス許可の設定**] ダイアログ ボックスが表示されます。
    
  
17. [ **アセンブリに以下のセキュリティ アクセスを許可**] を選択します。
    
  
18. [ **アセンブリを有効にする**] を選択します。
    
  
19. [ **OK**] をクリックしてから [ **次へ**] をクリックします。
    
  
20. [ **完了**] をクリックします。 
    
    [ **My_Computer_Zone**] ノードの下に新しいカスタム コード グループが表示されるはずです (この例では、 **RestrictWebAccessUdf**)。
    
  

### アクセス許可セットが実行されるかどうかを確認するには


1. [ **My_Computer_Zone**] ノードの下で、新しいカスタム コード グループ (この例では、 **RestrictWebAccessUdf**) を右クリックして、[ **プロパティ**] を選択します。 
    
  
2. [ **全般**] タブで、[ **このポリシーレベルはこのコード グループに関連するアクセス許可セットからのアクセス許可のみを持つ**] チェック ボックスを選択します。
    
  
3. [ **適用**] をクリックしてから、[ **OK**] をクリックします。
    
    > **メモ**
      > UDF メソッドが Web サービス呼び出しを実行できなかったために例外を throw した場合は、その UDF を呼び出した Excel 数式に [ **#VALUE!**] エラーが表示されます。 

    > **メモ**
      >  テストのために UDF アセンブリに対する Web アクセスを有効にする場合は、カスタム アクセス許可セットに適切なアクセス許可を追加する必要があります。そのためには、「新しいコード グループを作成するには」の手順のステップ 11 で [ **Web アクセス**] を選択します。 

## 関連項目


#### タスク


  
    
    
 [方法: Web サービスを呼び出す UDF の作成](how-to-create-a-udf-that-calls-a-web-service.md)
  
    
    
 [UDF を有効にする方法](how-to-enable-udfs.md)
  
    
    
 [UDF から外部データ ソースにアクセスする方法](how-to-access-an-external-data-source-from-a-udf.md)
  
    
    
 [SharePoint Foundation のソリューションを使用して UDF を配置する方法](how-to-deploy-udfs-using-sharepoint-foundation-solutions.md)
#### 概念


  
    
    
 [チュートリアル: マネージ コード UDF を開発する](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [Excel Services UDF に関するよく寄せられる質問](frequently-asked-questions-about-excel-services-udfs.md)
  
    
    
 [Excel Services UDF の理解](understanding-excel-services-udfs.md)
