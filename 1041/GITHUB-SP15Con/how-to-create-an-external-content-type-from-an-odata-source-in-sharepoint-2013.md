---
title: [方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する
ms.prod: SHAREPOINT
ms.assetid: bc60ea49-c44e-4531-af62-06b8cf77d35d
---


# [方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する
Visual Studio 2012を使用して公開済みの OData ソースを見つけ、Business Connectivity Services (BCS) で再利用可能な外部コンテンツ タイプを SharePoint 2013で作成する方法について説明します。
## OData ベースの外部コンテンツ タイプを作成するための前提条件
<a name="bkmk_Prerequisites"> </a>

Open Data プロトコル (OData) ソースから外部コンテンツ タイプを作成するには、次のものが必要です。
  
    
    

- SharePoint 2013のインスタンス
    
  
- Visual Studio 2012
    
  
- Office Developer Tools for Visual Studio 2012
    
  
- インターネットで使用可能な公開された OData サービス
    
  
SharePoint 開発環境を設定する方法については、「 [SharePoint 2013 の一般的な開発環境の設定](set-up-a-general-development-environment-for-sharepoint-2013.md)」を参照してください。
  
    
    

> **メモ**
> SharePoint Designer 2013 を使用して、OData ソースから BDC モデルを自動生成することはできません。代わりに、Visual Studio 2012 を使用できます。 
  
    
    


### OData 外部コンテンツ タイプの操作の中心概念

以下の記事は、SharePoint 2013における OData および Odata コネクタの背景情報について説明しています。
  
    
    

**表 1. OData 外部コンテンツ タイプの中心概念**


|**記事のタイトル**|**説明**|
|:-----|:-----|
| [SharePoint 2013 の Business Connectivity Services で OData ソースを使用する](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md) <br/> |OData ソースに基づいた外部コンテンツ タイプの作成を開始し、そのデータを SharePoint または Office コンポーネントで使用する方法について説明します。  <br/> |
| [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md) <br/> |BCS 外部コンテンツ タイプ、および SharePoint 2013で作成を開始するための前提条件について説明します。  <br/> |
   

## OData ベースの外部コンテンツ タイプの作成
<a name="bkmk_CreatingODataECT"> </a>

以下の手順は、Visual Studio 2012を使用して OData ソース ベースの外部コンテンツ タイプを作成する方法を示しています。
  
    
    

### 新しい SharePoint アドインを作成するには


1. Visual Studio 2012で、[ **SharePoint 2013 テンプレート**] ノードの下にある、新しい **App for SharePoint 2013** プロジェクトを作成します。
    
  
2. プロジェクトに名前を付けて、[ **OK**] をクリックします。
    
  
3. SharePoint 設定を指定するには、アプリケーションの名前、およびデバッグする SharePoint 2013 サーバーの URL を入力します。
    
  
4. [ **完了**] をクリックします。
    
  
プロジェクトを作成したら、OData ソース用の新しい自動生成ツールを使用して、OData ソース用の BDC モデルをアプリケーションに追加します。
  
    
    

### 新しい BDC モデルを作成するには


1. **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、[ **追加**]、[ **Content types for External Data source (外部データ ソースのコンテンツ タイプ)**] を選択します。
    
    これにより、選択したデータ ソースを見つけ、BDC モデルを作成するのに役立つウィザードが起動します。
    
  
2. ウィザードの最初のページは、データ サービスの URL を収集するために使用します。[ **OData ソースの指定**] ページでは、接続先の OData サービスの URL を入力します。URL は、 `http://services.odata.org/Northwind/Northwind.svc/` のようになります。
    
    > **メモ**
      >  [Open Data Protocol の Web サイト](http://www.odata.org/ecosystem#liveservices)に記載されている作成者の一覧で利用可能な、Northwind サービスが表示されます。 
3. OData ソースの名前を選択して、[ **次へ**] をクリックします。
    
  
4. OData サービスにより公開されているデータ エンティティの一覧が表示されます。1 つまたは複数のエンティティを選択して、[ **完了**] をクリックします。
    
  

### エンティティの構造を表示するには


- Visual Studio によって External Content Types という名前の新しいフォルダーが作成されています。そのフォルダーの中に、新しいデータ ソースの名前が付いたサブフォルダーがあります。これをさらに展開すると、選択したエンティティを表す項目が表示されます。エンティティとその型を示すグラフィックスの一覧を表示するには、表示する **ect** ファイルを開きます。
    
    XML エディターで ect ファイルを開くことにより、エンティティの XML を表示することもできます。
    
  

## OData ソースに対するストリーム アクセサーの使用
<a name="bkmk_UseStreamAccessor"> </a>

次のコードを使用すると、OData コネクタが使用できるデータ ストリームにアクセスできます。
  
    
    

```cs

/*Invoke  Stream Accessor Method */
        internal void ExecuteStreamAccessorMethod(IEntityInstance entityInstance, string streamAccessorName)
        {
            this.Log.Comment("ExecuteStreamAccessorMethod enter");
            this.Log.Comment("streamAccesor method" + streamAccessorName);
            IStreamableField isf = entityInstance.GetStreamableField(streamAccessorName);
            Stream resStream = isf.GetData();
            using (BinaryReader reader = new BinaryReader(resStream))
            {
                using (FileStream fs = File.Create(@"C:\\" + entityInstance.GetIdentity().GetIdentifierValues()[0] + ".jpg"))
                {
                    int bytesRead = 0;
                    do
                    {
                        int nrBytes = 80 * 1000 * 1000;
                        byte[] streamData = new byte[nrBytes];
                        bytesRead = reader.Read(streamData, 0, nrBytes);
                        this.Log.Comment("Total Bytes Read - " + bytesRead);
                        if (bytesRead > 0)
                        {
                            fs.Write(streamData, 0, bytesRead);
                        }
                    } while (bytesRead > 0);
                }
            }
            isf.Dispose();
            this.Log.Comment("ExecuteStreamAccessorMethod Exit" );
        }
```


## 次の手順
<a name="bkmk_Next"> </a>

外部コンテンツ タイプを構築した後は、組み込みオブジェクト (外部リスト、Business Data Web パーツ、またはカスタム コード) を使用することにより、外部コンテンツ タイプを使用して SharePoint 内でデータを表すことができます。
  
    
    
詳細については、「 [[方法] SharePoint 2013 で OData データ ソースを使用して外部リストを作成する](how-to-create-an-external-list-using-an-odata-data-source-in-sharepoint-2013.md)」を参照してください。
  
    
    

## その他の技術情報
<a name="bkmk_Addres"> </a>


-  [SharePoint 2013 の Business Connectivity Services で OData ソースを使用する](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の外部コンテンツ タイプ](external-content-types-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の新機能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  

