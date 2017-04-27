---
title: SharePoint 2013 の BDC モデル スキーマの変更点
ms.prod: SHAREPOINT
ms.assetid: 882ea867-9acb-4313-99c9-865a523b72fd
---


# SharePoint 2013 の BDC モデル スキーマの変更点
BDC モデル スキーマの SharePoint 2013の変更内容を確認します。
SharePoint 2013で BDC モデルを作成するスキーマ (BDCMetadata.xsd) の変更点は比較的少数です。ただし、これらの変更は、Business Connectivity Services (BCS)の機能セットの提供物に多大な影響を与えます。
  
    
    

BDCMetadata スキーマの詳細については、「 [SharePoint 2013 BDC モデル スキーマ リファレンス](bdc-model-schema-reference-for-sharepoint-2013.md)」を参照してください。
## BDCMetadata.xsd 内の複合型の要素に対する変更
<a name="bkmk_ChangesToElements"> </a>

次の表は、BDCMetadata スキーマ内の最上位の要素に対して加えられた変更を示しています。
  
    
    

**表 1. 新しい複合型**


|**要素**|**説明**|
|:-----|:-----|
|IndividuallySecurableMetadataObject  <br/> |指定されている **MetadataObject** を、親との関連付けによって保護するのではなく、明示的にセキュリティで保護することが可能であることを示します。 <br/> |
|MetadataObject  <br/> |外部データ ソースへの接続に関する追加のメタデータの格納に使用されます。  <br/> |
   

## BDCMetadata.xsd 内の単純型の要素に対する変更
<a name="bkmk_ChangesToSimpleTypes"> </a>

次の表は、各要素の属性に加えられた変更を示しています。
  
    
    

**表 2. 単純型に対する変更**


|**要素**|**説明**|
|:-----|:-----|
|変更なし  <br/> ||
   

## BDCMetadata.xsd 内の属性に対する変更
<a name="bkmk_ChangesToAttributes"> </a>

次の表は、各要素のセグメントに加えられた変更を示しています。
  
    
    

**表 3. 属性に対する変更**


|**属性**|**親**|**説明**|
|:-----|:-----|:-----|
|変更なし  <br/> |||
   

## その他の技術情報
<a name="bkmk_AdditionalResources"> </a>


-  [SharePoint 2013 の Business Connectivity Services](business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の新機能](what-s-new-in-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services の概要](get-started-with-business-connectivity-services-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 Business Connectivity Services プログラマー リファレンス](business-connectivity-services-programmers-reference-for-sharepoint-2013.md)
    
  
-  [SharePoint 2013 BDC モデル スキーマ リファレンス](bdc-model-schema-reference-for-sharepoint-2013.md)
    
  

