---
title: Excel Services の ECMAScript の概要
ms.prod: SHAREPOINT
ms.assetid: f8c1be86-df19-44c3-a3bc-c0da2b80df10
---


# Excel Services の ECMAScript の概要

Microsoft SharePoint Server 2010 において、Excel Services に ECMAScript (JavaScript, JScript) のサポートが追加されました。JavaScript では、Excel Services を使った新しい一連のソリューションを利用できます。 
  
    
    

Excel Services の JavaScript オブジェクト モデルにより、開発者はページ上の Excel Web Access の Web パーツ コントロールの自動化、カスタマイズ、操作ができるようになります。JavaScript オブジェクト モデルを使用すると、ページにある 1 つ以上の Excel Web Access の Web パーツ コントロールで操作するマッシュアップおよびその他の統合ソリューションをビルドできます。また、ブックおよび関連するコードにさらに機能を追加できるようになります。
JavaScript オブジェクト モデルを使用すると、Excel Web Access の Web パーツに対するユーザーの操作を検出して対応するとともに、プログラムを使用して 1 つまたは複数の Excel Web Access Web パーツを操作できます。
  
    
    


## ECMAScript オブジェクト モデルの使用

JavaScript オブジェクト モデルを Excel Services で使用するには、Excel Web Access の Web パーツを含むページ上に JavaScript コードを挿入します。これを行うには、コンテンツ エディター Web パーツを使用するか, .aspx ページを直接編集することで、Web パーツ ページにコードを追加します。
  
    
    
Excel Services の JavaScript オブジェクト モデルを使用すると、開発者は以下ができるようになります。 
  
    
    

- 範囲、表、ピボットテーブル、グラフ、およびシートなどのブック内のアイテムにアクセスする
    
  
- 範囲または名前付き範囲によって、セルに値を設定し、セルから値を取得する
    
  
- ユーザーがアクティブな選択やアクティブ セルを変更したとき、またはユーザーがセルの編集を開始したときにイベントを発生させる
    
  
- 異なる領域にスクロールし、表示するシートまたは名前付きアイテムを切り替える 
    
  
詳細は、次のリンクを参照してください。
  
    
    

- Excel Services の JavaScript オブジェクト モデルについて、詳細は  [Ewa](http://msdn.microsoft.com/library/6fe73191-3213-b986-1ad6-2c3b918a2241%28Office.15%29.aspx) 名前空間のリファレンス ドキュメントを参照してください。
    
  
- コンテンツ エディター Web パーツを使用して Excel Services の JavaScript オブジェクト モデルを操作する方法の例については、「 [チュートリアル: コンテンツ エディターと Web パーツを使用した開発](walkthrough-developing-using-the-content-editor-web-part.md)」を参照してください。
    
  

## ECMAScript .js ファイルの場所

JavaScript オブジェクト モデルの縮小処理された .js ファイルは、%ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\TEMPLATE\\LAYOUTS ディレクトリにインストールされています。ファイル名は "EwaMoss.js" です。
  
    
    
 .aspx ページまたは .js ファイルでの JavaScript オブジェクト モデルの使用方法に関する基本情報は、「 [ECMAScript を使用するアプリケーション ページをセットアップする](http://msdn.microsoft.com/library/48582a0b-f787-4868-8298-958717ec8ff8%28Office.15%29.aspx)」を参照してください。
  
    
    

