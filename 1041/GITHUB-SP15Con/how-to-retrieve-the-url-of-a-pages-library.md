---
title: ページ ライブラリの URL を取得する方法
ms.prod: SHAREPOINT
ms.assetid: d9922e4b-4948-4c4a-a8ca-1623168143a3
---


# ページ ライブラリの URL を取得する方法
現在のコンテキストと異なるサイト コレクションの発行 Web 用ページ リストの URL を取得する方法について説明します。
## ページ リストの URL の取得に関する中心概念
<a name="SP15_Core_Concepts_URL_MP"> </a>

発行サイトのカスタム アプリケーションを開発していると、 [PublishingWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.PublishingWeb.aspx) オブジェクト モデルが、現在のコンテキストとは異なるサイト コレクションの発行 Web のページ リスト用の URL を取得する方法を公開していないことがあります。 **PublishingWeb** クラスは、アクティブ化された発行機能を持つインスタンス用に [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) クラスをラップしますが、そのクラスは現在のコンテキスト外の **SPWeb** オブジェクトをインスタンス化するためのものではありません。
  
    
    
別の Web アプリケーション用のページ リストの URL を取得する必要がある場合、 [Properties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.Properties.aspx) プロパティをクエリできます。 [PublishingWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.PublishingWeb.aspx) オブジェクトは発行サイトの [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) オブジェクトであるため、 [Properties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.Properties.aspx) プロパティをクエリし、そのコンテンツをコンソール アプリケーションに書き込むことができます。 `Key = vti_pageslistname, Value = {the URL to the Pages library}` のエントリがコンソールに返される場合、 *{the URL to the Pages library}*  は URL を一覧するページです。
  
    
    

**表 1. ページ ライブラリの URL の取得に関する中心概念**


|**記事のタイトル**|**説明**|
|:-----|:-----|
|ページ ライブラリ  <br/> |発行サイトのコンテンツ ページすべてを含むドキュメント ライブラリー。  <br/> |
| [SPWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.aspx) <br/> |SharePoint Foundation Web サイトを表します。  <br/> |
| [Properties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.Properties.aspx) <br/> |現在の Web サイトのメタデータで  [SPPropertyBag](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPPropertyBag.aspx) オブジェクトを取得します。 <br/> |
| [SPPropertyBag](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPPropertyBag.aspx) <br/> |カスタム プロパティ設定を含む任意のキーと値のペアを保存します。  <br/> |
| [PublishingWeb](https://msdn.microsoft.com/library/Microsoft.SharePoint.Publishing.PublishingWeb.aspx) <br/> |発行をサポートする **SPWeb** のインスタンスに発行機能を提供します。 <br/> |
   

## 現在のコンテキストと異なるサイト コレクションの発行 Web 用のページ リストの URL を取得
<a name="SP15_Code_URL_Pages_List"> </a>

この例のコンソール アプリケーションは  [Properties](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPWeb.Properties.aspx) プロパティにアクセスし、コレクション間を反復処理し、それぞれのキー/値のペアをコンソールに書き込みます。
  
    
    

### ページ リストに URL の SPWeb.Properties プロパティをクエリするには


1. コンソール アプリケーションを書き込みます。
    
  
2. 出力をコンソールに表示します。
    
  

## 例: ページ リストに対する URL の SPWeb.Properties プロパティのクエリを実行
<a name="SP15_Example_SPWeb_Properties"> </a>

アプリケーションは  [SPPropertyBag](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPPropertyBag.aspx) オブジェクトをクエリし、辞書エントリ間を反復処理し、それらのエントリをコンソールに書き込みます。
  
    
    

```cs

using System;
using System.Collections;
using Microsoft.SharePoint;
using Microsoft.SharePoint.Utilities;

namespace Test
{
    class Program
    {
        static void Main(string[] args)
        {
            using (SPSite site = new SPSite("http://localhost"))
            {
                using (SPWeb web = site.OpenWeb())
                {
                    SPPropertyBag props = web.Properties;
                    foreach (DictionaryEntry de in props)
                    {
                        Console.WriteLine("Key = {0}, Value = {1}", de.Key, de.Value);
                    }
                }
            }
            Console.ReadLine();
        }
    }
}

```

このアプリケーションによるコンソールへの出力は Web サイトによって異なりますが、次のようになる場合があります。
  
    
    



```

Key = vti_associatemembergroup, Value = 5
Key = vti_extenderversion, Value = 14.0.0.4016
Key = vti_associatevisitorgroup, Value = 4
Key = vti_associategroups, Value = 5;4;3
Key = vti_createdassociategroups, Value = 3;4;5
Key = vti_siteusagetotalbandwidth, Value = 547
Key = vti_siteusagetotalvisits, Value = 9
Key = vti_associateownergroup, Value = 3
Key = vti_defaultlanguage, Value = en-us
Key = vti_pageslistname, Value = {the URL to the Pages list}
```


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint サイトの構築](build-sites-for-sharepoint.md)
    
  

