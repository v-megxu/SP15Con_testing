---
title: SharePoint 2013 での検索設定のエクスポートとインポート
ms.prod: SHAREPOINT
ms.assetid: d00679a3-ffa2-4281-ad8b-70fc2c4a14e2
---


# SharePoint 2013 での検索設定のエクスポートとインポート
カスタマイズされた検索設定のエクスポートとインポートの方法を示すコード例を取得します。これらの設定には、カスタマイズされたすべてのクエリ ルール、検索先、結果タイプ、ランク付けモデル、サイトの検索設定などがあります。SharePoint は、 [Microsoft.Office.Server.Search.Portability](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Portability.aspx) 名前空間を介して、この機能を公開します。また、カスタマイズした検索設定を検索サービス アプリケーション (SSA) からエクスポートしたり、サイト コレクションやサイトに設定をインポートすることもできます。 
> **メモ**
> カスタマイズした検索設定を SSA にインポートしたり、既定の検索構成をエクスポートすることはできません。 
  
    
    


## 検索設定のエクスポート
<a name="SP15_exporting_search_configuration"> </a>

次のコードは、 [SearchConfigurationPortability](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Portability.SearchConfigurationPortability.aspx) を使用して、サイトの検索設定をエクスポートする方法を示しています。このコードでは、サンプル サイト _http://yoursite/sites/publishing1_ を使用します。このサイトを実際に使用するサイトに置き換えてください。 _fileName_ は、検索設定を保存するファイルです。 _owner_ は、検索設定を取得する [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) のレベルです。
  
    
    

```

private static void Export(string fileName)
{
    SPSite site = new SPSite("http://yoursite/sites/publishing1");
    SearchConfigurationPortability conf = new SearchConfigurationPortability(site);
    SearchObjectOwner owner = new SearchObjectOwner(SearchObjectLevel.SPWeb, site.OpenWeb());
    var buff = conf.ExportSearchConfiguration(owner);
    File.WriteAllText(fileName, buff);
    site.Close();
}
```


## 検索設定のインポート
<a name="SP15_importing_search_configuration"> </a>

次のコードは、 [SearchConfigurationPortability](https://msdn.microsoft.com/library/Microsoft.Office.Server.Search.Portability.SearchConfigurationPortability.aspx) を使用して、ファイルから検索設定をインポートし、特定のサイト _http://yoursite/sites/publishing1_ の検索設定を置き換える方法を示しています。 _fileName_ は、検索設定を保存するファイルです。 _owner_ は、検索設定を取得する [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) のレベルです。
  
    
    

```cs

private static void Import(string fileName)
{
    SPSite site = new SPSite("http://yoursite/sites/publishing1");
    SearchConfigurationPortability conf = new SearchConfigurationPortability(site);
    SearchObjectOwner owner = new SearchObjectOwner(SearchObjectLevel.SPWeb, site.OpenWeb());
    conf.ImportSearchConfiguration(owner, File.ReadAllText(fileName));
    site.Close();
}

```


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 の検索](search-in-sharepoint-2013.md)
    
  
-  [Sharepoint Server 2013 で検索構成のカスタマイズした設定をエクスポートおよびインポートする](http://technet.microsoft.com/ja-jp/library/jj871675.aspx)
    
  

  
    
    

