---
title: プログラムを使用したアクセスに備えてサーバーに保存する方法
keywords: how to,howdoi,howto
f1_keywords:
- how to,howdoi,howto
ms.prod: OFFICE365
ms.assetid: 80b34a29-3d40-4d11-9ba1-b4886ffcfd42
---


# プログラムを使用したアクセスに備えてサーバーに保存する方法

次の使用例は、プログラムを使用してアクセスできるように Excel ブックをサーバーに保存する方法を示しています。手順は次のとおりです。
  
    
    


1. 名前付き範囲を持つブックを作成します。
    
  
2. SharePoint ライブラリの信頼できる場所にブックを保存します。 
    
    > **メモ**
      > 既に SharePoint ドキュメント ライブラリが作成され、信頼できる場所となっていることが前提です。詳細は、「 [方法: 場所を信頼する](how-to-trust-a-location.md)」を参照してください。 
3. プログラムにより、ワークシートの値、名前付き範囲、セル値を Excel Web Services の **SetCellA1** メソッドを使用して指定します。値は、引数、つまり _args [1]_ および _args [2]_ として渡されます。
    
  ```cs
  
status = xlServices.SetCellA1(sessionId, String.Empty, args[1], args[2]);
  ```


  ```VB.net
  status = xlServices.SetCellA1(sessionId, String.Empty, args(1), args(2))
  ```


 _args [1]_ および _args [2]_ の値は、Web フォームを使用して指定するか、コマンド ラインから指定することができます。
  
    
    




```
GetSnapshot.exe http://MyServer002/MyTrustedDocumentLibrary/TestMyParam.xlsx MyParam28 > MySnapshot.xlsx 
```

この例では、 _args [1]_ は 「 **MyParam**」、 **args [2]** は「 _28_」、作成したアプリケーションの名前は「 _GetSnapshot.exe_」です。サンプル プログラムを見つけるには、「 [方法: ブック全体またはスナップショットの取得](how-to-get-an-entire-workbook-or-a-snapshot.md)」を参照してください。
### 名前付き範囲を作成するには


1. Excel を起動します。
    
  
2. **Sheet1** の名前を「MyParamSheet」に変更します。
    
  
3. セル B2 に「20」と入力します。
    
  
4. セル B3 に「=2+B2」と入力します。
    
  
5. セル B3 を太字にします。
    
  
6. セル B2 を次の名前付き範囲にします。 
    
1. リボンで、[ **数式**] タブをクリックしてから、セル B2 をクリックして選択します。
    
  
2. [ **定義された名前**] グループで [ **名前の定義**] をクリックします。
    
  
3. [ **新しい名前**] ダイアログ ボックスの [ **名前**] テキスト ボックスに、「MyParam」と入力します。
    
  
7. ブックをローカル ドライブ上のお好みの場所に保存します。ブックの名前は「TestMyParam.xlsx」とします。 
    
  

### SharePoint ライブラリに保存するには


1. [ **ファイル**] メニューで、[ **保存と送信**]、[ **SharePoint に保存**] の順にクリックします。 
    
  
2. [ **SharePoint に保存**] ダイアログ ボックスで、[ **発行オプション**] をクリックします。
    
  
3. [ **発行オプション**] ダイアログ ボックスの [ **表示**] タブで、[ **ブック全体**] が選択されていることを確認します。
    
  
4. [ **パラメーター**] をクリックします。 
    
  
5. [ **追加**] をクリックします。
    
  
6. [ **パラメーターの追加**] リストに [ **MyParam**] が表示されます。[ **MyParam**] チェック ボックスをクリックします。
    
  
7. [ **OK**] をクリックします。[ **パラメーター**] リストに [ **MyParam**] が表示されるようになります。
    
  
8. [ **OK**] をクリックします。
    
  
9. [ **SharePoint に保存**] ダイアログ ボックスで [ **名前を付けて保存**] をクリックします。
    
  
10. [ **名前を付けて保存**] ダイアログ ボックスで、 [ **ブラウザーで Excel で開く**] チェック ボックスのチェックを外します。
    
  
11. [ **ファイル名**] ボックスで、このブックを格納する信頼できる SharePoint ドキュメント ライブラリのパスを入力します (例: http:// _MyServer002_/MyDocumentLibrary/TestParam.xlsx)。
    
  
12. [ **保存**] をクリックします。
    
  

### プログラムで値を指定するには


1. Excel Web Services の **SetCellA1** メソッドのシグネチャを以下に示します。
    
  ```cs
  public void SetCellA1 (
string sessionId,
string sheetName,
string rangeName,
Object cellValue,
Out Status[] status
)
  ```


  ```VB.net
  
Public Sub SetCellA1(ByVal sessionId As String,
              ByVal sheetName As String, 
             ByVal rangeName As String, 
             ByVal cellValue As Object, 
             Out ByVal status() As Status)
End Sub
  ```


    **SetCellA1** メソッドに、次のようにワークシートの値、名前付き範囲、セル値を設定します。
    


  ```cs
  
// Set a value into a cell.
status = xlSrv.SetCellA1(sessionId, String.Empty, args[1], args[2]);

  ```

2. 上記のコードで、 
    
  -  _args [1]_ は名前付き範囲の名前です。この例では「 **MyParam**」です。
    
  
  -  _args [2]_ はセルに設定する値です。値が設定されるセルは、 **MyParam** という _args [1]_ 内の名前付き範囲です。
    
  
3. コマンド ラインを使用する場合は、次のように引数を渡します。
    
     `GetSnapshot.exe http://` _MyServer002_ `/` _MyTrustedDocumentLibrary_ `/TestMyParam.xlsx MyParam 28 > MySnapshot.xlsx`
    
  
4. ブックのスナップショットを作成すると、次のように表示されます。 
    
  - セル B2 ( **MyParam** という名前範囲が付いている) には、「 **28**」という、プログラムを介して取り込んだ値が入ります。
    
  
  - セル B3 には、新しい値が計算されて「 **30**」が入ります。
    
  
  - セル B3 に元の数式である "=2+B2" は表示されません。
    
  
  - セル B3 のフォント書式 (太字) は保持されます。
    
  

> **メモ**
> スナップショットについて、詳細は「 [方法: ブック全体またはスナップショットの取得](how-to-get-an-entire-workbook-or-a-snapshot.md)」を参照してください。 **SetCellA1** メソッドについて、詳細は Excel Web Services のリファレンス ドキュメントを参照してください。Web サービスの名前空間は [Microsoft.Office.Excel.Server.WebServices](https://msdn.microsoft.com/library/Microsoft.Office.Excel.Server.WebServices.aspx) です。
  
    
    


## 関連項目


#### タスク


  
    
    
 [方法: Excel クライアントからサーバーへの保存](how-to-save-from-excel-client-to-the-server.md)
#### 参照先


  
    
    
 [Microsoft.Office.Excel.Server.WebServices](https://msdn.microsoft.com/library/Microsoft.Office.Excel.Server.WebServices.aspx)
#### 概念


  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
  
    
    
 [SOAP 呼び出しのループバックおよび直接リンク](loop-back-soap-calls-and-direct-linking.md)
  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
#### その他の技術情報


  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
