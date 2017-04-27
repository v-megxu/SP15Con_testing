---
title: [方法] SharePoint 2013 で、Web およびファーム レベルで Bing Maps キーを設定する
ms.prod: SHAREPOINT
ms.assetid: 507ed9de-c349-44b5-b182-e838795dd862
---


# [方法] SharePoint 2013 で、Web およびファーム レベルで Bing Maps キーを設定する

  
    
    
![方法トピック](images/mod_icon_howto.png)
  
    
    

  
    
    

  
    
    
SharePoint 2013 クライアント オブジェクト モデルと Windows PowerShell を使用してプログラムにより Web およびファーム レベルで Bing Maps キーを設定し、SharePoint リストの Bing Maps 機能および場所ベースの Web アプリとモバイル アプリを有効にする方法を説明します。

  
    
    


## Bing Maps キーを設定する場合の前提条件
<a name="SP15Bing_prereq"> </a>

この例で示す手順を実行するには、次の前提条件を満たす必要があります。
  
    
    

- 管理権限付きの SharePoint 2013。
    
  
- 「 [Bing Maps アカウント センター](https://www.bingmapsportal.com/)」から入手できる有効な Bing Maps キー。
    
    > **重要**
      > Bing Maps キーを使用する場合に適用される使用条件に準拠、Bing Maps サービスに渡されるデータに関してアプリケーションのユーザーに必要なデータ開示を行う責任は、このキーを設定するユーザーにあります。 

## コード サンプル: ファームまたは Web レベルでの Bing Maps キーの設定
<a name="SP15Setbing_farm"> </a>

Bing Maps キーは、ファームまたは Web レベルで設定できます。ファーム レベルで Bing Maps キーを設定するには、サーバーでの管理者権限が必要です。この権限があれば、SharePoint 2013 管理シェルを使用することによってキーを追加できます。Web レベルで Bing Maps キーを設定するには、SharePoint クライアント オブジェクト モデルを使用するコンソール アプリケーションを作成します。
  
    
    

> **ヒント**
> Web レベルで設定された Bing Maps キーは、ファーム レベルで設定された Bing Maps キーより優先順位が高くなります。 
  
    
    


### Windows PowerShell を使用してファーム レベルで Bing Maps キーを設定するには


1. SharePoint サーバーに管理者としてログオンし、SharePoint 2013 管理シェルを開きます。
    
  
2. 次のコマンドを実行します。 
    
     `Set-SPBingMapsKey -BingKey "<Enter a valid Bing Maps key>"`
    
    これで、Bing Maps キーが SharePoint Server 2013 のファーム レベルで設定されます。 
    
    > **メモ**
      > Windows PowerShell を使用する場合、Bing Maps キーはファーム レベルでのみ設定できます。Bing Maps キーを Web レベルで設定する場合は、次のセクションに示すようにプログラムによってキーを設定できます。 

### クライアント オブジェクト モデルを使用して Bing Maps キーをファームまたは Web レベルで設定するには


1. Visual Studio を起動します。
    
  
2. メニュー バーで、[ **ファイル**]、[ **新しいプロジェクト**] を選択します。[ **新しいプロジェクト**] ダイアログ ボックスが開きます。
    
  
3. [ **新しいプロジェクト**] ダイアログ ボックスの [ **インストールされたテンプレート**] ボックスで [ **C#**] を選択して、[ **コンソール アプリケーション**] テンプレートを選択します。
    
  
4. プロジェクトに名前を付け、[ **OK**] ボタンをクリックします。
    
  
5. Visual Studio がプロジェクトを作成します。参照を次のアセンブリに追加し、[ **OK**] を選択します。
    
  - Microsoft.SharePoint.Client.dll
    
  
  - Microsoft.SharePoint.Client.Runtime.dll
    
  
6. 既定の .cs ファイルに、次のようにして **using** ディレクティブを追加します。
    
     `using Microsoft.SharePoint.Client;`
    
  
7. .cs ファイルの Main メソッドに次のコードを追加します。
    
  ```cs
  
class Program
    {
        static void Main(string[] args)
        {
            SetBingMapsKey();
            Console.WriteLine("Bing Maps set successfully");
        }
     static private void SetBingMapsKey()
        {

            ClientContext context = new ClientContext("<Site Url>");
            Web web = context.Web;
            web.AllProperties["BING_MAPS_KEY"] = "<Valid Bing Maps Key>"
            web.Update();
            context.ExecuteQuery();
        }    
    }

  ```

8. <Site Url> と  _<Valid Bing Maps Key>_ を有効な値で置き換えます。
    
  
9. [プロジェクトのプロパティ] でターゲット フレームワークを [.NET Framework 4.0] として設定し、サンプル コードを実行します。
    
  
10. これで、キーが Web レベルで設定されます。 
    
  

## 次の手順
<a name="SP15Bing_nextsteps"> </a>

SharePoint 2013 での場所およびマップ機能の使用法の詳細については、以下を参照してください。
  
    
    

-  [[方法] SharePoint 2013 で地理位置情報列をプログラムでリストに追加する](how-to-add-a-geolocation-column-to-a-list-programmatically-in-sharepoint-2013.md)
    
  
-  [方法: クライアント側レンダリングを使用して地理位置情報フィールド型を拡張する](how-to-extend-the-geolocation-field-type-using-client-side-rendering.md)
    
  

