---
title: 手順 2 Web 参照を追加する
ms.prod: SHAREPOINT
ms.assetid: e9175863-ddb4-4750-847d-d53cb59b33cb
---


# 手順 2: Web 参照を追加する

Web サービスの探索は、クライアントが Web サービスを検索し、サービスの説明を取得するプロセスです。Visual Studio における Web サービスの探索プロセスは、あらかじめ定義されたアルゴリズムに従って Web サイトを照会することなどです。プロセスの目的は、サービスの説明、つまり Web サービス記述言語 (WSDL) を使用する XML ドキュメントを検索することです。
  
    
    

サービスの説明では、どのようなサービスが利用できるか、およびそれらのサービスの操作方法について説明しています。 サービスの説明がなければ、プログラムによって Web サービスを操作することはできません。
アプリケーションは、Web サービスと通信して実行時に場所を指定する手段を持つ必要があります。これを行うには、Web サービスとインターフェイスし、Web サービスのローカル表現を提供するプロキシ クラスを生成することで、Web サービス用のプロジェクトに Web 参照を追加します。詳細は、Microsoft Visual Studio 2005 ドキュメントの「Web 参照および XML Web サービス プロキシの生成」を参照してください。
  
    
    


## Web 参照を追加するには


1. [ **プロジェクト**] メニューの [ **Web 参照の追加**] をクリックします。
    
  
2. [ **Web 参照の追加**] ダイアログ ボックスの [ **URL**] ボックスに、 `http://<server>/<customsite>/_vti_bin/excelservice.asmx` または `http://<server>/_vti_bin/excelservice.asmx` といった Excel Web Services のサービスの説明を取得する URL を入力します。続いて、[ **検索**] をクリックして Web サービスに関する情報を取得します。
    
    > **メモ**
      > または、[ **参照**] を右クリックして [ **Web 参照の追加**] を選択しても、[ **ソリューション エクスプローラー**] ウィンドウ内の [ **Web 参照の追加**] を開くことができます。 
3. [ **Web 参照名**] ボックスで、Web 参照の名前を「ExcelWebService」に変更します。
    
  
4. [ **参照の追加**] をクリックして、対象の Web サービスの Web 参照を追加します。 
    
  
5. Visual Studio は、サービスの説明をダウンロードし、プロキシ クラスを生成して、アプリケーションと Excel Web Services との間をインターフェイスします。 
    
  
6. 詳細は、「 [SOAP API にアクセスする](accessing-the-soap-api.md)」を参照してください。
    
  

## 関連項目


#### 概念


  
    
    
 [SOAP 呼び出しのループバックおよび直接リンク](loop-back-soap-calls-and-direct-linking.md)
#### その他の技術情報


  
    
    
 [ステップ 1: Web サービス クライアント プロジェクトを作成する](step-1-creating-the-web-service-client-project.md)
  
    
    
 [手順 3: Web サービスへのアクセス](step-3-accessing-the-web-service.md)
  
    
    
 [手順 4: アプリケーションのビルドとテストを行う](step-4-building-and-testing-the-application.md)
  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
