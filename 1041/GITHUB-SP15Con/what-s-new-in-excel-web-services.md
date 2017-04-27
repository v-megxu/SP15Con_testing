---
title: Excel Web Services の新機能
ms.prod: OFFICE365
ms.assetid: cb342e94-0308-4608-b027-b73ebe8107b0
---


# Excel Web Services の新機能

このトピックでは、Excel Web Services に追加された新しい型とメンバーを挙げます。
  
    
    


## Excel Web Services の強化

Excel Web Services は、Microsoft SharePoint Server 2010 で拡張され強化されました。SharePoint Server 2010 で、プログラムでブックの編集と保存を行えます。加えて、Excel Web Services は、SharePoint Server 2010 の編集セッションでブックを開くことをサポートするようになりました。このシナリオでは、他のユーザーがブックを共同作成するのと同時に、コードを使用してそのブックを編集することができます。
  
    
    
Excel Web Services API および新しいメソッドの詳細、および列挙体、型に関する詳細な解説については、「 **Microsoft.Office.Excel.Server.WebServices**」を参照してください。
  
    
    

### 新しいメソッド

以下に、Excel Web Services に追加された新しいメソッドをアルファベット順で示します。 
  
    
    

- **GetChartImageUrl** ブックにあるグラフやピボットグラフのイメージ ファイルの URL 値を取得します。
    
  
- **GetPublishedItemNames** ブックにある発行済みアイテムのリストを取得します。
    
  
- **GetSheetNames** ブックにあるすべてのシート名のリストを取得します。
    
  
- **OpenWorkbookForEditing** ブックを編集用に開きます。
    
  
- **SaveWorkbook** ブックを元の形式 (.xlsx, .xlsb, .xlsm) で保存します。
    
  
- **SaveWorkbookCopy** ブックを異なるファイル名で保存したり、異なる SharePoint ドキュメント ライブラリに保存します。
    
  
- **SetCalculationOptions** ブックの計算モード設定を変更します。
    
  
- **SetParameters** 1 つの Web サービスの呼び出しで複数の発行済みパラメーターを設定します。
    
  
上記に加えて、
  
    
    

- 値の設定メソッドを使用して数式を設定できるようになりました。
    
  
- SharePoint Server 2010 の Excel Web Services ではダイナミック レンジがサポートされます。
    
  

### 新しい列挙体

以下に、Excel Web Services に追加された新しい列挙体をアルファベット順で示します。
  
    
    

- **ItemType** 返されるアイテムの型を示します。
    
  
- **SheetType** 返されるシートの型を示します。
    
  
- **SheetVisibility** 返されるシートが表示可能かどうかを示します。
    
  
- **SaveOptions** ロックが解除された既存のファイルを上書きするかどうかを指定します。
    
  
- **WorkbookCalculation** ブックの計算モード設定を定義します。
    
  

### 新しい型

以下に、Excel Web Services に追加された新しい型をアルファベット順で示します。
  
    
    

- **ParameterInfo** パラメーターの名前と値を取得または設定します。
    
  
- **SheetInfo** ブック内のシートに関する情報が含まれています。
    
  
- **Size** グラフ イメージの縦横の長さを定義します。
    
  
- **WorkbookItem** ブック内の名前付きアイテムを表します。
    
  

## 関連項目


#### その他の技術情報


  
    
    
 [チュートリアル: Excel Web Services を使用してカスタム アプリケーションを開発する](walkthrough-developing-a-custom-application-using-excel-web-services.md)
