---
title: チュートリアル マネージ コード UDF を開発する
ms.prod: SHAREPOINT
ms.assetid: e6a00833-0606-4a7d-91c3-b89a6e340348
---


# チュートリアル: マネージ コード UDF を開発する

このチュートリアルでは、Microsoft Visual C# を使用して Excel Services のユーザー定義関数 (UDF) を開発するプロセスについて説明します。
  
    
    

このチュートリアルでは、以下の方法について説明します。
- Microsoft Visual Studio 2005年クラス ライブラリのプロジェクト テンプレートを使用してプロジェクトを作成する
    
  
- Microsoft.Office.Excel.Server.Udf.dll への参照を追加する
    
  
- Excel Services で使用するための UDF を作成する
    
  
- セルからカスタム関数を呼び出すブックを作成する
    
  
- Excel Services で UDF のテストと実行を行う
    
  

## 前提条件

このチュートリアルを完了するには、以下が必要です。 
  
    
    

- Microsoft SharePoint Server 2010. 
    
    > **メモ**
      > サーバー上に必要なすべてを用意する最も簡単な方法は、基本的なスタンドアロンのインストールを実行することです。さらに、信頼できる場所を追加する必要があります。 
- Excel
    
  
- Visual Studio またはこれに類似した Microsoft.NET Framework 互換の開発ツール
    
  
- UDF アセンブリを実行できるようにすること
    
  
- ブックを格納するための、信頼できる SharePoint ドキュメント ライブラリ、および **AllowUdfs** の値を「 **true**」にすることで、ブックが UDF を呼び出せるようにすること 
    
  
- 信頼できる SharePoint ドキュメント ライブラリに格納された UDF を呼び出すブックのサンプル 
    
  
- ブックを表示する許可、およびブックを SharePoint ドキュメント ライブラリに発行する許可 
    
    > **メモ**
      > 許可の設定について、詳細は Windows SharePoint Services 3.0 のドキュメントを参照してください。 
- Excel を使用したブックの作成
    
  
- ブックを .xlsx または .xlsb ファイルで保存すること
    
    > **メモ**
      > 場所の信頼方法、UDF を有効にする方法、 **AllowUdfs** フラグの設定方法について、詳細は「 [ステップ 3: UDF を展開して有効にする](step-3-deploying-and-enabling-udfs.md)」を参照してください。 

## 関連項目


#### タスク


  
    
    
 [ステップ 1: プロジェクトを作成し、UDF への参照を追加する](step-1-creating-a-project-and-adding-a-udf-reference.md)
  
    
    
 [ステップ 2: マネージ コード UDF を作成する](step-2-creating-a-managed-code-udf.md)
  
    
    
 [ステップ 3: UDF を展開して有効にする](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [手順 4: セルから UDF のテストと呼び出しを行う](step-4-testing-and-calling-udfs-from-cells.md)
  
    
    
 [方法: Web サービスを呼び出す UDF の作成](how-to-create-a-udf-that-calls-a-web-service.md)
#### 概念


  
    
    
 [Excel Services UDF の理解](understanding-excel-services-udfs.md)
#### その他の技術情報


  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
