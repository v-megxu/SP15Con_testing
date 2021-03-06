---
title: SharePoint 2013 でページをプレビューしているときのエラーと警告を解決する方法
ms.prod: SHAREPOINT
ms.assetid: 03f72f65-b22b-4304-be92-f44ce0619372
---


# SharePoint 2013 でページをプレビューしているときのエラーと警告を解決する方法
HTML ファイルを SharePoint 2013 マスター ページに変換した後、または、ページ レイアウトを作成した後、そのページをブラウザーでプレビューできます。しかし、サーバー側プレビューでページが表示できない問題を解決しなければ、マスター ページまたはページ レイアウトをプレビューできない場合があります。
## プレビュー エラー解決の概要
<a name="Introduction"> </a>

HTML ファイルを SharePoint 2013 マスター ページに変換した後、または、ページ レイアウトを作成した後、そのページをブラウザーでプレビューできます。HTML マスター ページまたはページ レイアウトを編集および保存したら、プレビューを最新の情報に更新して、SharePoint 2013 でどのようにページが表示されるかをはっきり見ることができます。
  
    
    
デザイン マネージャーのプレビューはリアルタイムのサーバー側プレビューなので、ナビゲーション コントロール、検索型 Web パーツなど、ページ上のスニペットやコントロールはすべてライブ データを使用します。また、マスター ページやページ レイアウトをプレビューする場合、そのファイルだけの全体プレビューを選択するか、または、サイト内の特定のページがそのマスター ページやページ レイアウトでどのように表示されるかをプレビューするかを選択できます。サーバー側プレビューは、HTML エディターでのデザイン時のプレビューを補う非常に有用なツールです。詳細については、「 [方法: SharePoint 2013 デザイン マネージャーでプレビュー ページを変更する](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)」を参照してください。
  
    
    
しかし、サーバー側プレビューでページが表示できない問題を解決しなければ、マスター ページまたはページ レイアウトをプレビューできない場合があります。サーバー側プレビューが動作していない場合、マスター ページまたはページ レイアウトは、サイトに適用された後も動作しないということになります。デザイン マネージャーで、マスター ページを変換するか、ページ レイアウトを作成するかした後、ファイル名または変換ステータスをクリックして、そのファイルをプレビューできます。プレビュー ページのページ上部にある通知領域に、エラーまたは警告が表示されます。
  
    
    
発生する可能性のあるプレビュー エラーと警告、およびその解決方法に関するヘルプをここに紹介します。
  
    
    

## HTML ファイルでは <form> タグを使えない
<a name="FormTags"> </a>


### メッセージ

 **マスター ページに 1 つ以上の HTML <FORM> タグが含まれています。マスター ページが機能するようにするには、このタグを削除します (タグの内容は残しておいてもかまいません)。**
  
    
    

### 解決策

ASP.NET がポストバックできるように、SharePoint 2013 ページはすでに **<form>** タグで括られています (具体的には、SharePoint 2013.master ページには、関連付けられたコンテンツ ページを表示するときの、実際の **<form>** タグを作成する **<SharePoint:SharePointForm>** タグが含まれます)。そのため、マスター ページまたはページ レイアウトに **<form>** タグを含めると、最終的にページを表示するときに、入れ子になった **<form>** タグが存在することになります。これは HTML では無効です。HTML エディターで **<form>** タグをすべて削除し、ページを保存してから、プレビューを更新してください。
  
    
    
ページ レイアウトに HTML **<form>** タグを入れる場合、次のコードを HTML ページ レイアウトに追加することによって、 **PlaceHolderUtilityContent** という ID のコンテンツ プレースホルダーの中にフォームを置く必要があります。
  
    
    



```HTML

<!--CS: Start Create Snippets From Custom ASP.NET Markup Snippet-->
<!--SPM:<SharePoint:AjaxDelta id="DeltaPlaceHolderUtilityContent" runat="server">-->
<!--SPM:<asp:ContentPlaceHolder id="PlaceHolderUtilityContent" runat="server" />-->
<!--SPM:</SharePoint:AjaxDelta>-->
<!--CE: End Create Snippets From Custom ASP.NET Markup Snippet-->
```

スニペット ギャラリーからページに HTML フォーム Web パーツまたは InfoPath フォーム Web パーツを追加することもできます。詳細については、「 [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md)」を参照してください。
  
    
    

## HTML ファイルは XML に準拠している必要がある
<a name="XMLCompliant"> </a>


### メッセージ

 **SharePoint には XML に準拠した HTML ファイルが必要です。ファイルが XML に準拠していません。タグのプロパティの引用符が抜けている、終了タグがない、プロパティが無効であるなどの理由が考えられます。{エラーの種類, エラーの場所}。エラーの発生時刻: {時刻}**
  
    
    

### 解決策

HTML ファイルを対応する ASP.NET ファイルに変換するには、HTML ファイルが XML に準拠している必要があります。このエラーでは、HTML ファイルの中で XML に準拠していないマークアップを特定します。HTML ファイルの XML 検証を実行し、HTML エディターで問題の箇所を修正して、ファイルを保存してから、プレビューを更新してください。
  
    
    

> **メモ**
> この要件は HTML 5 標準よりも優先されます。たとえば、HTML 5 では小文字で doctype を指定できますが、XML の場合、doctype は大文字である必要があります。 
  
    
    


  
    
    

## 問題のあるマークアップが HTML ファイルにある
<a name="ProblematicMarkup"> </a>


### メッセージ

 **このファイルを解析できませんでした。最も可能性の高い原因は、SharePoint のスニペットの形式が正しくないことです。次の位置にあるマークアップが問題を引き起こしています。このマークアップを手動で編集して修正するか、スニペット ギャラリーにある新しいスニペットに置き換えてください。{エラーの種類, エラーの位置}。エラーの発生時刻: {時刻}**
  
    
    

### 解決策

HTML ファイル内の SharePoint スニペットに問題があると、このエラーが表示されます。このエラーを修正するには、エラーを引き起こした変更をすべて元に戻します。あるいは、問題のスニペットを、スニペット ギャラリーから、または、そのスニペットが動作している別のマスター ページやページ レイアウト ファイルから、新しいものに置き換えます。HTML エディターでスニペットの修正または置き換えを行った後、ページを保存してからプレビューを更新します。
  
    
    

## ページ レイアウト用のマスター ページが変更された
<a name="PageLayoutChanged"> </a>


### メッセージ

 **このページ レイアウトのマスター ページが変更されたため、サイトに表示される内容に一致しなくなった可能性があります。ここをクリックすると、マスター ページ領域に相当するページ レイアウトのセクションが更新されます。**
  
    
    

### 解決策

ページ レイアウトが所定のマスター ページと連動するには、この 2 つが同じコンテンツ プレースホルダーのセットを持つ必要があります。特定のマスター ページに基づいてページ レイアウトを作成した後、その HTML マスター ページを編集すると、このメッセージが表示されます。マスター ページに対する変更によってコンテンツ プレースホルダーの追加や削除が起きなかったとわかっていても、ページ レイアウトに影響を及ぼす可能性のあるマスター ページの変更をプレビューできるように、必ずページ レイアウトのコンテンツ領域を更新する必要があります。
  
    
    

## プレビューをリセットする
<a name="ResetPreview"> </a>


### メッセージ

 **マスター ページ (ページ レイアウト) に警告またはエラーはありません。元の状態にするには、プレビューをリセットします。**
  
    
    

### 説明

このメッセージは、変換プロセスの動作にエラーまたは問題がなかったことを確認しているだけです。ただし、ページをプレビューすると、その特定のページから移動する場合や、プレビューになんらかの変更を行う場合があります。この場合、いつでもメッセージ領域で [ **プレビューをリセット**] をクリックできます。そうするとプレビューが更新され、作業中の特定のマスター ページまたはページ レイアウト、および左上隅の [ **プレビュー ページの変更**] オプションで選択した任意のページが使用されるようになります。
  
    
    

## プレビュー ページを変更する
<a name="ChangePreviewPage"> </a>


### メッセージ

 **現在、まったく表示する内容のないマスター ページ (ページ レイアウト) をプレビューしています。上のメニューでプレビューするページを変更できます。**
  
    
    

### 説明

マスター ページまたはページ レイアウトのプレビューに SharePoint 2013 の有効なページを使用していない場合、このメッセージが表示されます。たとえば、ページ レイアウトをプレビューしている場合、左上隅で [ **プレビュー ページの変更**] をクリックしてから、そのページ レイアウトでプレビューする特定のコンテンツ ページを選択できます。このようにして、ページ フィールドでは実際のページ コンテンツでページ レイアウトをプレビューできます。プレビューで **ContentPlaceHolderMain** またはページ フィールドの位置だけを表示する場合、いつでも [ **プレビュー ページの変更**] を使用して、全体のプレビューに切り替えられます。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 のサイト デザインの開発](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [方法: SharePoint 2013 デザイン マネージャーでプレビュー ページを変更する](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [SharePoint 2013 デザイン マネージャー スニペット](sharepoint-2013-design-manager-snippets.md)
    
  

