---
title: Web ページからの Excel 対話型ビューの削除
ms.prod: SHAREPOINT
ms.assetid: 407b3aa3-7286-462b-905f-811a3b7f3f1c
---


# Web ページからの Excel 対話型ビューの削除

Excel 対話型ビュー機能は使用できなくなりました。Web ページに Excel 対話式ビューが挿入されている場合は、Web ページの HTML から、 `<script>` タグと、ボタン用のプレースホルダー `<a>` タグを削除することにより、このビューを削除できます。
  
    
    

 `<script>` タグを削除するには、以下の HTML を検索して削除します。


```HTML

<script src="http://r.office.microsoft.com/r/rlidExcelButton?v=1&amp;amp;kip=1" type="text/javascript"></script>
```

プレースホルダー  `<a>` タグを削除するには、HTML で <table> 要素の直前にある <a> タグを見つけます。<a> タグはカスタマイズ可能なので、HTML を解析してこの文字列の最初の部分を探し、ボタンのインスタンスをすべて見つけます。


```HTML
<a href="#" name="MicrosoftExcelButton" data-xl-tableTitle="" data-xl-buttonStyle="Standard" data-xl-fileName="Book1" data-xl-attribution="" ></a>
```


## 回避策

代替策として、 [Excel を Web ページに埋め込む](https://support.office.com/en-au/article/Share-it-Embed-an-Excel-workbook-on-your-blog-804e1845-5662-487e-9b38-f96307144081?ui=en-US&amp;rs=en-AU&amp;ad=AU)ことをお勧めします。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 の Excel Services](excel-services-in-sharepoint-2013.md)
    
  
-  [Excel ブックをブログに埋め込む](https://support.office.com/en-au/article/Share-it-Embed-an-Excel-workbook-on-your-blog-804e1845-5662-487e-9b38-f96307144081?ui=en-US&amp;rs=en-AU&amp;ad=AU)
    
  

