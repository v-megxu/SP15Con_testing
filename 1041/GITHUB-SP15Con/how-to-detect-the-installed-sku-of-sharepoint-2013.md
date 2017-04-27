---
title: 方法 SharePoint 2013 のインストール済み SKU を検出する
ms.prod: SHAREPOINT
ms.assetid: d5d84d6f-6a8e-4ead-9296-7025baf1e154
---


# 方法: SharePoint 2013 のインストール済み SKU を検出する
使用中のソリューションの動作が SharePoint 2013 または Project Server 2013 のローカルにインストールされた SKU に依存している場合は、この記事のコード例を使用して必要な SKU 情報を見つけてください。
## SharePoint 2013または Project Server 2013のインストール済み SKU をコードを使って検出する
<a name="SP15DetectSKU_detect"> </a>

次のコード例は、SharePoint 2013、Microsoft Project Server 2013、およびその他の Office サーバー製品のインストール済み SKU のレジストリ キーを取得する方法、およびこれらの製品の既知の SKU の名前とキーがすべて格納されたハッシュ テーブルと SKU を照合する方法を示しています。コンソールの出力には、インストール済み SKU の名前が表示されます。
  
    
    

```cs

using System;
using System.Collections;
using Microsoft.Win32;


namespace GetInstalledSharePointSku
{
    class Program
    {
        internal static Hashtable _products;

        public static Hashtable SharePointProducts
        {
            get 
            {
                if (_products == null)
                {
                    _products = new Hashtable();

                    _products.Add("35466B1A-B17B-4DFB-A703-F74E2A1F5F5E", "Project Server 2013");
                    _products.Add("BC7BAF08-4D97-462C-8411-341052402E71", " Project Server 2013 Preview");

                    _products.Add("C5D855EE-F32B-4A1C-97A8-F0A28CE02F9C", "SharePoint Server 2013");
                    _products.Add("CBF97833-C73A-4BAF-9ED3-D47B3CFF51BE", "SharePoint Server 2013 Preview");
                    _products.Add("B7D84C2B-0754-49E4-B7BE-7EE321DCE0A9", "SharePoint Server 2013 Enterprise");
                    _products.Add("298A586A-E3C1-42F0-AFE0-4BCFDC2E7CD0", "SharePoint Server 2013 Enterprise Preview");

                    _products.Add("D6B57A0D-AE69-4A3E-B031-1F993EE52EDC ", "Microsoft Office Online");
                    _products.Add("9FF54EBC-8C12-47D7-854F-3865D4BE8118", "SharePoint Foundation 2013");
                }
                
                return _products;
            }
        }

        private const String SharePointProductsRegistryPath = @"SOFTWARE\\Microsoft\\Shared Tools\\Web Server Extensions\\15.0\\WSS\\InstalledProducts\\";

        static void Main(string[] args)
        {
            try
            {
                //Open the registry key in read-only mode.
                using (RegistryKey key = Registry.LocalMachine.OpenSubKey(SharePointProductsRegistryPath, false))
                {
                    //Get all of the installed product code/SKUId pairs.
                    foreach (String value in key.GetValueNames())
                    {
                        try
                        {
                            //Get the SKUId and see whether it is a known product.
                            String SKUId = key.GetValue(value) as String;

                            if (SharePointProducts[SKUId] != null)
                            {
                                Console.WriteLine("Product Installed: {0}", SharePointProducts[SKUId]);
                            }
                            else
                            {
                                Console.WriteLine("Unknown Product: {0}", SKUId);
                            }
                        }
                        catch (Exception e)
                        {
                            Console.WriteLine("Could not read key exception was {0}", e.Message);
                        }
                    }
                }
            }
            catch (Exception e)
            {
                Console.WriteLine("Could not open key exception was {0}", e.Message);
            }
            Console.Read();
        }
    }
}
```


## その他の技術情報
<a name="bk_SP15DetectSKUaddresources"> </a>


-  [SharePoint 2013 開発の概要](sharepoint-2013-development-overview.md)
    
  
-  [SharePoint 2013 の開発者のための新機能](what’s-new-for-developers-in-sharepoint-2013.md)
    
  
-  [SharePoint 開発者チーム ブログ](http://blogs.msdn.com/b/sharepointdev/)
    
  
-  [SharePoint Stack Exchange](http://sharepoint.stackexchange.com/)
    
  

