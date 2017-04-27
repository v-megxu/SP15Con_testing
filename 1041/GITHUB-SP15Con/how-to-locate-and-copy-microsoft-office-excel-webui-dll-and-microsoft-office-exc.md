---
title: 方法 Microsoft.Office.Excel.WebUI.dll および Microsoft.Office.Excel.WebUI.Internal.dll を検索してコピーする
keywords: how to,howdoi,howto,WebUI DLL
f1_keywords:
- how to,howdoi,howto,WebUI DLL
ms.prod: OFFICE365
ms.assetid: 09ad5d5e-1678-45e4-8159-23ef56f84215
---


# 方法: Microsoft.Office.Excel.WebUI.dll および Microsoft.Office.Excel.WebUI.Internal.dll を検索してコピーする

プログラムを使用して Excel Web Access Web パーツを SharePoint ページに追加し、プログラムを使用して Excel Web Access Web パーツに変更を加える場合は、必要な SharePoint DLL への参照を追加する必要があります。たとえば、次のような DLL です。 
  
    
    


- Microsoft.Office.Excel.WebUI.dll
    
  
- Microsoft.Office.Excel.WebUI.Internal.dll
    
  
- Microsoft.SharePoint.dll
    
  

Microsoft SharePoint Server 2010 を実行しているコンピューター上では、Microsoft.Office.Excel.WebUI.dll および Microsoft.Office.Excel.WebUI.Internal.dll のコピーがグローバル アセンブリ キャッシュ内に見つかります。Microsoft Visual Studio の [ **参照の追加**] ダイアログ ボックスを使用して Microsoft.Office.Excel.WebUI.dll への参照を追加するには、その前にまず Microsoft.Office.Excel.WebUI.dll および Microsoft.Office.Excel.WebUI.Internal.dll をグローバル アセンブリ キャッシュからフォルダーにコピーする必要があります。その後、[ **参照の追加**] ダイアログ ボックスの [ **参照**] タブを使用して、Microsoft.Office.Excel.WebUI.dll および Microsoft.Office.Excel.WebUI.Internal.dll のコピーを入れたフォルダーを参照できます。
  
    
    

この後に記載する手順は、以下の操作を実行するための手順です。 
- Microsoft.Office.Excel.WebUI.dll を検索する。 
    
  
- Microsoft.Office.Excel.WebUI.dll をグローバル アセンブリ キャッシュから任意のフォルダーにコピーする。
    
  

> **メモ**
> 同じ手順を繰り返して、Microsoft.Office.Excel.WebUI.Internal.dll をグローバル アセンブリ キャッシュからフォルダーにコピーしてください。 
  
    
    


### Microsoft.Office.Excel.WebUI.dll を検索するには


1. コマンド プロンプト コンソールを開始するために、[ **スタート**] をクリックし、[ **ファイル名を指定して実行**] をクリックします。 
    
  
2. [ **名前**] フィールドのテキスト ボックスに「cmd」と入力します。 
    
    コマンド プロンプト コンソールが表示されます。
    
  
3. **cd** コマンドを使用して "C:\\Windows\\assembly" ディレクトリに移動します。
    
    > **メモ**
      > ご使用のコンピューターのディレクトリ構造は、この例と少し異なることがあります。この例では、Windows Server 2008 がインストールされているコンピューターを使用しています。 

  ```
  
cd C:\\Windows\\assembly
  ```

4. **dir** コマンドを使用して、"C:\\Windows\\assembly" ディレクトリの内容を表示します。
    
  ```
  C:\\Windows\\assembly>dir
  ```


    次のような内容が表示されます。
    


  ```
  Volume in drive C has no label.
 
 Directory of C:\\Windows\\assembly

02/20/2010  09:22 AM    <DIR>          GAC
02/20/2010  09:39 AM    <DIR>          GAC_32
02/20/2010  09:32 AM    <DIR>          GAC_64
02/22/2010  05:05 PM    <DIR>          GAC_MSIL
02/22/2010  05:35 PM    <DIR>          NativeImages_v2.0.50727_32
02/22/2010  04:33 PM    <DIR>          NativeImages_v2.0.50727_64
02/20/2010  10:34 AM    <DIR>          NativeImages_v4.0.30219_32
02/20/2010  10:35 AM    <DIR>          NativeImages_v4.0.30219_64
02/22/2010  05:04 PM    <DIR>          temp
02/22/2010  05:05 PM    <DIR>          tmp
               0 File(s)              0 bytes
              10 Dir(s)  104,032,665,600 bytes free
  ```

5. 再び **cd** コマンドを使用してディレクトリを変更し、gac_msil ディレクトリに移動します。
    
  ```
  
C:\\Windows\\assembly>cd gac_msil
  ```

6. **dir** コマンドを使用して、"C:\\Windows\\assembly\\GAC_MSIL" ディレクトリの内容を表示します。
    
  ```
  C:\\Windows\\assembly\\GAC_MSIL>dir
  ```


    次のような内容が表示されます。
    


  ```
  Volume in drive C has no label.
Directory of C:\\Windows\\assembly\\GAC_MSIL
...
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.Server.Udf
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.Server.WebServices

02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.WebUI
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.WebUI.Internal
...
02/20/2010  07:57 AM    <DIR>          Microsoft.SharePoint
...
0 File(s)              0 bytes
             739 Dir(s)  100,594,409,472 bytes free
  ```

7. これで Microsoft.Office.Excel.WebUI.dll および Microsoft.Office.Excel.WebUI.Internal.dll の場所がわかったので、任意のフォルダーにコピーできます。
    
  

### Microsoft.Office.Excel.WebUI.dll をコピーするには


1. 再び **cd** コマンドを使用して、ディレクトリ "Microsoft.Office.Excel.WebUI" に移動します。
    
  ```
  
C:\\Windows\\assembly\\GAC_MSIL>cd Microsoft.Office.Excel.WebUI 
  ```

2. **dir** コマンドを使用して、内容を表示します。
    
  ```
  C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI>dir
  ```


    次のような内容が表示されます。
    


  ```
  Volume in drive C has no label.
Directory of C:\\Windows\\assembly\\GAC_MSIL\Microsoft.Office.Excel.WebUI

02/20/2010  07:57 AM    <DIR>          .
02/20/2010  07:57 AM    <DIR>          ..
02/20/2010  07:57 AM    <DIR>          14.0.0.0__71e9bce111e9429c
               0 File(s)              0 bytes
               3 Dir(s)  104,006,115,328 bytes free
  ```

3. もう一度 **cd** コマンドを使用して、ディレクトリを変更します。
    
  ```
  
C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI>cd 14.0.0.0__71e9bce111e9429c
  ```

4. **copy** コマンドを使用して、Microsoft.Office.Excel.WebUI.dll を任意のフォルダーにコピーします。
    
    下の例では、Microsoft.Office.Excel.WebUI.dll を "C:\\WebUIAssembly" にコピーしています。ここで、"C:\\WebUIAssembly" は、あらかじめ作成しておいたフォルダーです。
    


  ```
  C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI\\14.0.0.0__71e9bce111e9429c>copy Microsoft.Office.Excel.WebUI.dll c:\\WebUIAssembly
        1 file(s) copied.
  ```


## 例

次の例は、コマンド プロンプトを使用して Microsoft.Office.Excel.WebUI.dll を検索し、フォルダーにコピーした結果を示しています。
  
    
    

```

C:\\Windows\\assembly>dir
Volume in drive C has no label.
Directory of C:\\Windows\\assembly

02/20/2010  09:22 AM    <DIR>          GAC
02/20/2010  09:39 AM    <DIR>          GAC_32
02/20/2010  09:32 AM    <DIR>          GAC_64
02/22/2010  05:05 PM    <DIR>          GAC_MSIL
02/22/2010  05:35 PM    <DIR>          NativeImages_v2.0.50727_32
02/22/2010  04:33 PM    <DIR>          NativeImages_v2.0.50727_64
02/20/2010  10:34 AM    <DIR>          NativeImages_v4.0.30219_32
02/20/2010  10:35 AM    <DIR>          NativeImages_v4.0.30219_64
02/22/2010  05:04 PM    <DIR>          temp
02/22/2010  05:05 PM    <DIR>          tmp
               0 File(s)              0 bytes
              10 Dir(s)  104,032,665,600 bytes free
C:\\Windows\\assembly>cd gac_msil

C:\\Windows\\assembly\\GAC_MSIL>dir
 Volume in drive C has no label.
 Directory of C:\\Windows\\assembly\GAC_MSIL
...
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.Server.Udf
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.Server.WebServices

02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.WebUI
02/20/2010  07:57 AM    <DIR>          Microsoft.Office.Excel.WebUI.Internal
...

C:\\Windows\\assembly\\GAC_MSIL>cd Microsoft.Office.Excel.WebUI

C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI>dir
 Volume in drive C has no label.
Directory of C:\\Windows\\assembly\\GAC_MSIL\Microsoft.Office.Excel.WebUI

02/20/2010  07:57 AM    <DIR>          .
02/20/2010  07:57 AM    <DIR>          ..
02/20/2010  07:57 AM    <DIR>          14.0.0.0__71e9bce111e9429c
               0 File(s)              0 bytes
               3 Dir(s)  104,006,115,328 bytes free

C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI>cd 14.0.0.0__71e9bce111e9429c

C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI\\14.0.0.0__71e9bce111e9429c>copy Microsoft.Office.Excel.WebUI.dll c:\\WebUIAssembly
        1 file(s) copied.

C:\\Windows\\assembly\\GAC_MSIL\\Microsoft.Office.Excel.WebUI\\14.0.0.0__71e9bce111e9429c>
```


## 関連項目


#### タスク


  
    
    
 [プログラムを使用して Excel Web Access の Web パーツをページに追加する方法](how-to-programmatically-add-an-excel-web-access-web-part-to-a-page.md)
  
    
    
 [方法: 場所を信頼する](how-to-trust-a-location.md)
#### 概念


  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
  
    
    
 [Excel Services の既知の問題およびヒント](excel-services-known-issues-and-tips.md)
