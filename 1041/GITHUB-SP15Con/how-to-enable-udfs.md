---
title: UDF を有効にする方法
keywords: how to,howdoi,howto,UDF list
f1_keywords:
- how to,howdoi,howto,UDF list
ms.prod: SHAREPOINT
ms.assetid: 8c1af2eb-bb22-45e1-82de-a2b4b53d7a26
---


# UDF を有効にする方法

共有サービス プロバイダー (SSP) にある Excel Services の信頼できる場所のそれぞれに、 **AllowUdfs** フラグがあります。
  
    
    


> **メモ**
> **AllowUdfs** フラグは、[Excel Services: 信頼できるファイル保存場所] ページにある [ **許可されたユーザー定義関数**] オプションによって示されます。 
  
    
    


 **AllowUdfs** の既定値は **false** です。特定の信頼できる場所で **AllowUdfs** の値を **false** に設定すると、その信頼された場所にあるブックは UDF の呼び出しを許可されません。
  
    
    

特定の信頼できる場所からの UDF の呼び出しを許可するには、 **AllowUdfs** の値を **true** に設定します。この信頼できる場所にある UDF の呼び出しを持つブックでセッションを開始したときに **AllowUdfs** の値が **false** である場合、UDF の呼び出しは失敗します。セッションの開始後に **AllowUdfs** の値を **true** に変更しても、UDF の呼び出しは失敗します。これは、 **AllowUdfs** フラグの変更は、構成データベースが更新された後、次回のセッションで有効になるためです。これを回避するには、たとえば Excel Web Access で [ **ブックの再読み込み**] を選択するなどして、セッションを再起動します。
> **注意**
> 代わりに Microsoft インターネット インフォメーション サービス (IIS) をリセットする場合、現在のセッションがすべて終了します。 
  
    
    


## UDF の有効化

次の手順を実行するには、Microsoft SharePoint Server 2010 がインストールされたコンピューターが必要です。
  
    
    

### UDF を有効にするには


1. [ **スタート**] メニューで [ **すべてのプログラム**] をクリックします。 
    
  
2. [ **Microsoft Office Server**] をポイントしてから、[ **SharePoint サーバーの全体管理**] をクリックします。 
    
  
3. クイック起動で、共有サービス プロバイダー (SSP) のリンク (例: 「SharedServices1」) をクリックして、特定の SSP の共有サービス ホーム ページを表示します。
    
  
4. [ **Excel Services の設定**] の下で、[ **ユーザー定義関数**] をクリックします。 
    
  
5. [Excel Services ユーザー定義関数] ページで、[ **ユーザー定義関数の追加**] をクリックして、[Excel Services ユーザー定義関数アセンブリの追加] ページを開きます。
    
  
6. [ **アセンブリ**] ボックスで、UDF アセンブリのパス (例: C:\\MyUdfFolder\\MyUdf.dll) を入力します。
    
  
7. [ **アセンブリの場所**] で、[ **ローカル ファイル**] をクリックします。
    
    > **メモ**
      > Excel Services の今後のリリースでは、[ **ローカル ファイル**] オプションは [ **ファイル パス**] に置き換えられます。[ **ファイル パス**] が表示されたら、代わりにそれを選択してください。 
8. [ **アセンブリの有効化**] の下で、[ **アセンブリが使用可能**] チェック ボックスが既定で選択されているはずです。
    
  
9. [ **OK**] をクリックします。
    
  

## UDF 呼び出しの許可


### ブックからの UDF の呼び出しを許可するには、


1. [Excel Services 信頼できるファイル保存場所の追加] ページ (新しい信頼できるファイルの場所を追加する場合) または [Excel Services 信頼できるファイル保存場所の編集] ページ (既存の信頼できる場所を編集する場合) を開きます。 
    
    > **メモ**
      > 場所の信頼について、詳細は「 [方法: 場所を信頼する](how-to-trust-a-location.md)」を参照してください。 
2. [ **ユーザー定義関数の許可**] の下で、[ **ユーザー定義関数が使用可能**] を選択すると、この信頼できる場所に格納されたブックから UDF を呼び出せるようになります。
    
  
3. [ **OK**] をクリックします。
    
  

## 関連項目


#### タスク


  
    
    
 [ステップ 3: UDF を展開して有効にする](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [方法: Web サービスを呼び出す UDF の作成](how-to-create-a-udf-that-calls-a-web-service.md)
  
    
    
 [方法: 場所を信頼する](how-to-trust-a-location.md)
#### 概念


  
    
    
 [チュートリアル: マネージ コード UDF を開発する](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [Excel Services UDF に関するよく寄せられる質問](frequently-asked-questions-about-excel-services-udfs.md)
  
    
    
 [Excel Services UDF の理解](understanding-excel-services-udfs.md)
  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
  
    
    
 [Excel Services の既知の問題およびヒント](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services のベスト プラクティス](excel-services-best-practices.md)
