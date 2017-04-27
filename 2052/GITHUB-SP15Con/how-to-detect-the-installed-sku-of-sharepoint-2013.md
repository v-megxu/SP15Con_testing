---
title: 如何：检测已安装的 SharePoint 2013 SKU
ms.prod: SHAREPOINT
ms.assetid: d5d84d6f-6a8e-4ead-9296-7025baf1e154
---


# 如何：检测已安装的 SharePoint 2013 SKU
如果解决方案的行为取决于本地安装的 SharePoint 2013 或 Project Server 2013 SKU，则可使用本文中的代码示例来查找您所需要的 SKU 信息。
## 使用代码检测已安装的 SharePoint 2013 或 Project Server 2013 SKU
<a name="SP15DetectSKU_detect"> </a>

以下代码示例演示如何检索 SharePoint 2013、Microsoft Project Server 2013 和其他 Office Server 产品的已安装 SKU 的注册表项，以及如何使用存储这些产品的所有已知 SKU 的名称和项的哈希表匹配 SKU。控制台输出将显示已安装 SKU 的名称。
  
    
    

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


## 其他资源
<a name="bk_SP15DetectSKUaddresources"> </a>


-  [SharePoint 2013 开发概述](sharepoint-2013-development-overview.md)
    
  
-  [SharePoint 2013 中面向开发人员的新增功能](what’s-new-for-developers-in-sharepoint-2013.md)
    
  
-  [SharePoint 开发人员博客](http://blogs.msdn.com/b/sharepointdev/)
    
  
-  [SharePoint Stack Exchange](http://sharepoint.stackexchange.com/)
    
  

