---
title: 手順 2 コンテンツ エディターと Excel Services Web パーツを追加する
ms.prod: SHAREPOINT
ms.assetid: c9c66843-fd77-4a0d-a512-d936d15d4429
---


# 手順 2: コンテンツ エディターと Excel Services Web パーツを追加する

ECMAScript (JavaScript, JScript) テキスト ファイルを作成し、信頼できる場所に保存したところで、次の手順では、Web パーツ ページを作成してから、コンテンツ エディター Web パーツと Excel Services Web パーツをページに追加します。 
  
    
    

次に、ページに追加した Excel Services Web パーツを使用してブックを表示します。 
### コンテンツ エディター Web パーツと Excel Services Web パーツを追加するには


1. 新しい Web パーツ ページを作成します。 
    
  
2. 作成した Web パーツ ページにコンテンツ エディター Web パーツを追加します。
    
  
3.  [手順 1: ECMAScript テキスト ファイルを作成する](step-1-creating-a-ecmascript-text-file.md) で作成したテキスト ファイルの URL をコンテンツ エディター Web パーツに付与します。これを行うには、 [手順 1: ECMAScript テキスト ファイルを作成する](step-1-creating-a-ecmascript-text-file.md) で信頼できるドキュメント ライブラリにアップロードしたテキスト ファイルの URL を追加します。
    
    例: 
    
     `http://` _myserver_ `/Docs/Documents/JSOM_FeedToContentEditor.txt`
    
  
4. Excel Services Web パーツをページに追加します。
    
  

### ECMAScript のサンプルを実行するには


1. 信頼できるドキュメント ライブラリにブックをアップロードします。[ **共有 Web パーツの変更**] メニューを使用して、Excel Services Web パーツの作業ウィンドウを表示します。[ **ブックの表示**] セクションの [ **ブック**] フィールドに、Excel Services Web パーツが読み込みと表示を行うブックの URL を入力します。以下に例を示します。 
    
     `http://` _myserver_ `/Docs/Documents/WorkbookToDisplay.xlsx`
    
  
2. 異なるセルをクリックして、コンテンツ エディターの **div** に追加されるセルの値を確認してみます。
    
  

