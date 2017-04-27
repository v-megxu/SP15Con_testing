---
title: SOAP API にアクセスする
keywords: soap
f1_keywords:
- soap
ms.prod: OFFICE365
ms.assetid: 36e8e3d5-83ac-4bd3-b556-1af132add3eb
---


# SOAP API にアクセスする

Excel Web Services は、HTTP 上の簡易オブジェクト アクセス プロトコル (SOAP) を使用し、クライアント プログラムと Excel Services の間の接続インターフェイスとして機能します。Web サービスは、メソッドと、Excel Web Services の完全な機能へのアクセスに使用できる複合型オブジェクトのセットで構成されています。サービスを呼び出すには、Excel Web Services の WSDL (Web Services Description Language) を参照する必要があります。
  
    
    


## WSDL を参照する

Web サービスを正常に呼び出すには、サービスへのアクセス方法、サービスがサポートする操作、サービスが想定するパラメータ、およびサービスが返すものを知っておく必要があります。WSDL は、これらの情報をコンピュータでの表示および処理が可能な XML ドキュメントで提供します。
  
    
    
Excel Web Services エンドポイントの WSDL には、 `ExcelServices.asmx?wsdl` を使用してアクセスします。WSDL は、Microsoft .NET Framework SDK などの SOAP および Web サービスをサポートする開発キットによって使用できます。
  
    
    
以下の例は、Excel Web Services の WSDL ファイルへの URL の書式を示しています。
  
    
    
 `http://<server>/<customsite>/_vti_bin/excelservice.asmx?WSDL`
  
    
    
カスタム サイトがない場合は、一時的に以下の URL を使用できます。
  
    
    
 `http://<server>/_vti_bin/excelservice.asmx?WSDL`
  
    
    
カスタム サイトを作成して、URL 書式でカスタム サイトが含まれる URL を使用することをお勧めします。
  
    
    
次の表では、URL の各要素を説明します。
  
    
    


|****URL element****|****Description****|
|:-----|:-----|
| _server_ <br/> |Microsoft SharePoint Server 2010 が展開されているサーバーの名前。  <br/> |
| _customsite_ <br/> |サーバー管理者が作成する SharePoint Server 2010 のカスタム サイト。  <br/> |
| _<endpointname>.asmx_ <br/> |Web サービス エンドポイントの名前。Excel Web Services の場合は、 `ExcelService.asmx` です。 <br/> |
   
WSDL 書式の詳細については、http://www.w3.org/TR/wsdl にある W3C (World Wide Web Consortium) WSDL の仕様を参照してください。
  
    
    

## 関連項目


#### その他の技術情報


  
    
    
 [ステップ 1: Web サービス クライアント プロジェクトを作成する](step-1-creating-the-web-service-client-project.md)
  
    
    
 [手順 2: Web 参照を追加する](step-2-adding-a-web-reference.md)
  
    
    
 [手順 3: Web サービスへのアクセス](step-3-accessing-the-web-service.md)
  
    
    
 [手順 4: アプリケーションのビルドとテストを行う](step-4-building-and-testing-the-application.md)
  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
