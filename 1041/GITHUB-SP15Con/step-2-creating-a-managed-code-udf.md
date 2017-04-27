---
title: ステップ 2 マネージ コード UDF を作成する
keywords: soap
f1_keywords:
- soap
ms.prod: OFFICE365
ms.assetid: 3c9edf82-ee2d-41f0-9d66-e88e8dc0cc69
---


# ステップ 2: マネージ コード UDF を作成する

プロジェクトに Microsoft.Office.Excel.Server.Udf.dll への参照を追加したら、次のステップは、カスタム関数を作成し、それらの関数に Excel Services のユーザー定義関数 (UDF) 属性でマークを付けることです。 
  
    
    

UDF クラスは **Microsoft.Office.Excel.Server.Udf.UdfClass** 属性でマークを付け、UDF メソッドは **Microsoft.Office.Excel.Server.Udf.UdfMethod** 属性でマークを付ける必要があります。
UDF アセンブリ内で **Microsoft.Office.Excel.Server.Udf.UdfMethod** 属性によるマークが付いていないメソッドは、UDF メソッドとは見なされないため、無視されます。
  
    
    

 **Microsoft.Office.Excel.Server.Udf.UdfMethod** 属性には、 **IsVolatile** プロパティがあります。 **IsVolatile** プロパティを使用して、UDF メソッドが自動再計算か非自動再計算かを指定します。 **IsVolatile** プロパティはブール値をとります。既定値は **false** で、特定の UDF メソッドが非自動再計算であることを意味します。
## UDF を作成する


### ディレクティブを追加するには


- 使用する型は ** Microsoft.Office.Excel.Server.Udf** 名前空間で定義されています。Class1.cs ファイルの先頭に **using** (または **Imports**) ディレクティブを追加すると、名前空間に含まれる型を完全に修飾せずに **Microsoft.Office.Excel.Server.Udf** の型を使用できるようになります。
    
    このディレクティブを追加するには、Class1.cs ファイルのコードの先頭にある  `using System.Text:` の後に、次のコードを追加します。
    


  ```cs
  
using Microsoft.Office.Excel.Server.Udf; 
  ```




  ```VB.net
  Imports Microsoft.Office.Excel.Server.Udf
  ```


### UDF クラスとメソッドにマークを付けるには


1.  `Class1` に UDF クラスとしてマークを付けるために、 `public class Class1` のすぐ上に次のような属性を追加します。
    
  ```cs
  [UdfClass]
  ```


  ```VB.net
  <UdfClass>_
  ```

2. 引数として数値 ( **double** 型) をとる関数を作成し、この関数では数値に 9 を掛けます。この関数は UDF メソッドで、非自動計算です。 `Class1` に次のようなコードを追加します。
    
  ```cs
  [UdfMethod]
public double MyDouble(double d)
{
    return d * 9;
}
  ```


  ```VB.net
  
<UdfMethod> _
Public Function MyDouble(ByVal d As Double) As Double
    Return d * 9
End Function
  ```


    > **メモ**
      > **IsVolatile** プロパティの既定値は **false** であるため、特定の UDF メソッドは非自動計算です。したがって、非自動計算の UDF メソッドは `[UdfMethod]` とマークを付ければ十分です。 `[UdfMethod(IsVolatile = false)]` としてマークを付ける必要はありません。
3. **System.DateTime.Today** プロパティを使用して現在の日付を返す、別の関数を作成します。この関数は自動計算の UDF メソッドです。 `Class1` に次のようなコードを追加します。
    
  ```cs
  
[UdfMethod(IsVolatile = true)]
public DateTime ReturnDateTimeToday()
{
    return (DateTime.Today);
}      
  ```


  ```VB.net
  
<UdfMethod(IsVolatile := True)> _
Public Function ReturnDateTimeToday() As Date
    Return (Date.Today)
End Function
  ```


### プロジェクトをビルドするには


1. [ **ビルド**] メニューで、[ **ソリューションのビルド**] をクリックします。
    
  
2. プロジェクトを保存したディレクトリに、SampleUdf.dll アセンブリが見つかるはずです。 
    
  

### 完全なコード

次のコード サンプルは、ここまでの手順で作成した Class1.cs サンプル ファイルの完全なコードです。
  
    
    

```cs

using System;
using System.Collections.Generic;
using System.Text;
using Microsoft.Office.Excel.Server.Udf;

namespace SampleUdf
{
    [UdfClass]
    public class Class1
    {
        [UdfMethod]
        public double MyDouble(double d)
        {
            return d * 9;
        }  

        [UdfMethod(IsVolatile = true)]
        public DateTime ReturnDateTimeToday()
        {
            return (DateTime.Today);
        }
    }
}
```


```VB.net

Imports System
Imports System.Collections.Generic
Imports System.Text
Imports Microsoft.Office.Excel.Server.Udf

Namespace SampleUdf
    <UdfClass> _
    Public Class Class1
        <UdfMethod> _
        Public Function MyDouble(ByVal d As Double) As Double
            Return d * 9
        End Function

        <UdfMethod(IsVolatile := True)> _
        Public Function ReturnDateTimeToday() As Date
            Return (Date.Today)
        End Function
    End Class
End Namespace
```


## 関連項目


#### タスク


  
    
    
 [ステップ 1: プロジェクトを作成し、UDF への参照を追加する](step-1-creating-a-project-and-adding-a-udf-reference.md)
  
    
    
 [ステップ 3: UDF を展開して有効にする](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [手順 4: セルから UDF のテストと呼び出しを行う](step-4-testing-and-calling-udfs-from-cells.md)
  
    
    
 [方法: Web サービスを呼び出す UDF の作成](how-to-create-a-udf-that-calls-a-web-service.md)
#### 概念


  
    
    
 [チュートリアル: マネージ コード UDF を開発する](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [Excel Services UDF の理解](understanding-excel-services-udfs.md)
