---
title: 手順 4 アプリケーションのビルドとテストを行う
ms.prod: OFFICE365
ms.assetid: f2feeecb-1b4c-4049-be4e-11d414f13d9f
---


# 手順 4: アプリケーションのビルドとテストを行う

この手順では、アプリケーションのビルドとテストを行います。Visual Studio は、コンソール アプリケーションをビルドし、IDE から実行するいくつかの方法を備えています。それらは次のとおりです。
  
    
    


- デバッグなしで開始 ( **Ctrl + F5 キーを押す**)
    
  
- 開始 ( **F5 キー**)
    
  

## アプリケーションのビルド、実行、デバッグ


### アプリケーションをビルドして実行するには


1. [ **デバッグ**] メニューで [ **デバッグなしで開始**] をクリックするか、 **CTRL + F5 キー**を押します。こうすることで、プログラムの実行が終了した後もコンソール ウィンドウが開いたままになります。 
    
  
2. アプリケーションは、次の出力をコンソールに出力します。
    
    > **メモ**
      > これらの値は、ブック内の値やセッション ID などによって異なります。 

  ```
  
The Credential is: System.Net.SystemNetworkCredential
Total rows in range: 18
Value in range is: 4245.955129
  ```

3. いずれかのキーを押して SampleApplication.exe を閉じます。
    
  

### 「ファイルが見つからない」例外


1. 指定したブックへのパスが正しくないと、「ファイルが見つからない」例外が返されます。 この例外は、次のコードでキャッチされます。
    
  ```cs
  
catch (SoapException e)
{
    Console.WriteLine("SOAP Exception Message: {0}", e.Message);
}
  ```


  ```VB.net
  
Catch e As SoapException
Console.WriteLine("SOAP Exception Message: {0}", e.Message)
End Try
  ```

2. アプリケーションは、次の SOAP 例外の出力をコンソールに出力します。
    
  ```
  
SOAP Exception Message: The file you selected could not be found. Check the spelling of the file name and verify that the location is correct.

  ```


### 「インデックスが範囲外」例外


1. 範囲外の値を取得しようとすると、例外 **System.IndexOutOfRangeException** が返されます。アプリケーションは、次の出力をコンソールに出力します。
    
  ```
  
The Credential is: System.Net.SystemNetworkCredential
The sessionID is : 64.28e58e90-b757-4658-b1c4-890ad68ef6cbRmqR4IINXfkMeOJRG8Iq0Y
27tVk=110.33d3R6fqv7tr2jPyYiPwRu|!@en-US|en-US|+0480#0000-10-00-05T02:00:00:0000
#+0000#0000-04-00-01T02:00:00:0000#-0060
Total rows in range: 18
  ```

2. それから、次のような処理されない例外が返されます。
    
  ```
  
An unhandled exception of type 'System.IndexOutOfRangeException' occurred in SampleApplication.exe
Additional information: Index was outside the bounds of the array.
  ```

3. 上記の処理されない例外は、ここに示すとおり、SOAP 例外の **catch** ブロックの後に例外をキャッチする別の **catch** ブロックを追加すると処理できます。
    
  ```cs
  
catch (Exception e)
{
    Console.WriteLine("Exception Message: {0}", e.Message);
}
  ```


  ```VB.net
  
Catch e As Exception
Console.WriteLine("Exception Message: {0}", e.Message)
End Try
  ```


### F5 キーを使用してアプリケーションを実行するには


1. アプリケーションは、[ **デバッグ**] メニューで [ **開始**] をクリックするか、 **F5** キーを押すと実行できます。プログラムの実行が終了した後もコンソール ウィンドウを開いたままにするには、コードの末尾 ( **catch** ブロックの後) に次のコード行を追加します。
    
  ```cs
  
Console.ReadLine();
  ```


  ```VB.net
  Console.ReadLine()
  ```

2. いずれかのキーを押して SampleApplication.exe を閉じます。
    
  

## 関連項目


#### 概念


  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
#### その他の技術情報


  
    
    
 [ステップ 1: Web サービス クライアント プロジェクトを作成する](step-1-creating-the-web-service-client-project.md)
  
    
    
 [手順 2: Web 参照を追加する](step-2-adding-a-web-reference.md)
  
    
    
 [手順 3: Web サービスへのアクセス](step-3-accessing-the-web-service.md)
  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
  
    
    
 [[方法] スクリプトを使用してブックの場所を信頼する](http://msdn.microsoft.com/library/79ab6ced-7a0c-4275-b852-bb246fc6be57%28Office.15%29.aspx)
