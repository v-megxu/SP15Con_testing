---
title: Excel Services REST API でサポートされていない機能
ms.prod: OFFICE365
ms.assetid: 4139901f-255b-4556-b8c8-3d986a07c587
---


# Excel Services REST API でサポートされていない機能

最初のバージョンの Excel Services REST API は、一部の Excel 機能をサポートしていません。 
  
    
    


> **メモ**
> Excel Services REST API は、SharePoint 2013 および SharePoint 2016 オンプレミスに適用されます。Office 365 Education、Business、および Enterprise の各アカウントには、  [Microsoft Graph](http://graph.microsoft.io/ja-jp/docs/api-reference/v1.0/resources/excel
) エンドポイントの一部である Excel REST API を使用します。
  
    
    


Excel Services REST API で現在はサポートされていない、または動作しない主な機能は次のとおりです。
  
    
    


- **浮動グラフはサポートされていません。** 範囲にグラフが含まれている場合、その範囲を REST を通して要求すると、範囲だけが取得されます。
    
  
- **スパークラインと、アイコンによる条件付き書式** は、現在サポートされていません。
    
  
- **EWA と完全には一致しません。** REST が生成する HTML は、Excel Web Access が生成する HTML と非常に近いものです。しかし、Excel Services の REST API は、Excel Web Access がアクセスできるカスケード スタイル シート (CSS) 要素の一部にアクセスできません。Excel Services の REST API は HTML フラグメントを返します。HTML だけですべてを定義する "自己完結型" にする必要があります。
    
  
- **テーブル内に区別はありません。** セルやデータが列見出しか、合計データか、一般データかを判別するための Atom としてテーブルが要求された場合であっても、テーブル内では何も区別されません。つまり、セルやデータが列見出しか、合計データか、一般データかを示す違いは何もありません。テーブル全体のすべてのテーブル セルが、どれも同等に取り扱われます。
    
  
- **URL のサイズに制限があります。** URL のサイズには約 2000 文字という制限があります。したがって、ブックのパラメーター数が多いと、その一部を設定できないことがあります。このことは特に、深いフォルダー構造の中にブックが配置されている場合に問題になります。
    
  
- **特別な文字。** "?" や "#" などの文字はサポートされていません。特別な文字を含むシート名を正しく参照するための基本的な指針は、特別な文字を含むシートを指す数式を参照するときには "Excel クライアントが見るものを見る" こと、そしてその例に従うことです。
    
  

