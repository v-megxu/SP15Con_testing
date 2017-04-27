---
title: ステップ 1 プロジェクトを作成し、UDF への参照を追加する
ms.prod: SHAREPOINT
ms.assetid: 4c6f1279-28df-45af-8488-42a6573d526d
---


# ステップ 1: プロジェクトを作成し、UDF への参照を追加する

この手順では、プロジェクトを作成し、Microsoft.Office.Excel.Server.Udf.dll への参照を追加します。 
  
    
    


## プロジェクトの作成

以下のプロジェクトでは、Microsoft Visual Studio 2005 を使用します。
  
    
    

> **メモ**
> Visual Studio 統合開発環境 (IDE) で使用している設定に応じて、プロジェクトを作成するプロセスが若干異なることがあります。 
  
    
    


### プロジェクトを作成するには


1. Visual Studio を開始します。
    
  
2. [ **ファイル**] メニューの [ **新規**] をポイントし、[ **プロジェクト**] をクリックします。[ **新しいプロジェクト**] ダイアログ ボックスが表示されます。 
    
  
3. [ **プロジェクトの種類**] ウィンドウで、[ **Visual C# プロジェクト**] を選択します。
    
  
4. [ **テンプレート**] ウィンドウで、[ **クラス ライブラリ**] をクリックします。
    
  
5. [ **名前**] ボックスに、「 **SampleUdf**」と入力します。
    
  
6. [ **場所**] ボックスに、プロジェクトの保存先のパスを入力するか、[ **参照**] をクリックしてフォルダーまでナビゲートします。
    
  
7. [ **OK**] をクリックします。新しいプロジェクトが [ **ソリューション エクスプローラー**] に表示されます。また。既定で Class1.cs という名前の付いたファイルがプロジェクトに追加されます。
    
  
8. Class1.cs ファイルには次のコードが表示されます。
    
  ```cs
  
using System;
using System.Collections.Generic;
using System.Text;

namespace SampleUdf
{
    public class Class1
    {
    }
}
  ```


  ```VB.net
  
Imports System
Imports System.Collections.Generic
Imports System.Text

Namespace SampleUdf
Public Class Class1
End Class
End Namespace
  ```


## 参照の追加

以下の手順は、Microsoft.Office.Excel.Server.Udf.dll を見つけ、それに対する参照を追加する方法を示しています。 
  
    
    

### 参照を追加するには


1. [ **プロジェクト**] メニューの [ **参照の追加**] をクリックします。
    
  
2. [ **参照の追加**] ダイアログ ボックスの [ **.NET**] タブで、[ **Excel Services UDF Framework**] を選択します。
    
    > **メモ**
      > [ **ソリューション エクスプローラー**] から [ **参照の追加**] ダイアログ ボックスを開く別の方法として、[ **参照**] を右クリックして [ **参照の追加**] を選択することもできます。 
3. [ **OK**] をクリックします。
    
    > **メモ**
      > 上記の手順では、Microsoft SharePoint Server 2010 がインストールされたコンピューター上でプロジェクトを作成していることを想定しています。SharePoint Server 2010 がインストールされたコンピューターでは、Microsoft.Office.Excel.Server.Udf.dll のコピーは以下の場所にあります。 > [drive:]\\Program Files\\Common Files\\Microsoft Shared\\web server extensions\\14\\ISAPI 

## 関連項目


#### タスク


  
    
    
 [ステップ 2: マネージ コード UDF を作成する](step-2-creating-a-managed-code-udf.md)
  
    
    
 [ステップ 3: UDF を展開して有効にする](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [手順 4: セルから UDF のテストと呼び出しを行う](step-4-testing-and-calling-udfs-from-cells.md)
  
    
    
 [方法: Web サービスを呼び出す UDF の作成](how-to-create-a-udf-that-calls-a-web-service.md)
#### 概念


  
    
    
 [チュートリアル: マネージ コード UDF を開発する](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [Excel Services UDF の理解](understanding-excel-services-udfs.md)
