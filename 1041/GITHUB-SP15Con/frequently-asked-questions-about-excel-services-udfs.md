---
title: Excel Services UDF に関するよく寄せられる質問
keywords: faqs
f1_keywords:
- faqs
ms.prod: SHAREPOINT
ms.assetid: 3d94d040-eecf-4f8e-a316-6d1cca95e7eb
---


# Excel Services UDF に関するよく寄せられる質問

ここでは、Excel Services のユーザー定義関数 (UDF) に関してよく寄せられる質問をいくつか取り上げます。 
  
    
    


## マネージ コード UDF の作成


### サポートされる UDF のクラスはどのようなものですか?

UDF アセンブリ内の UDF クラスは public でなければなりません。sealed にすることができます。abstract、internal、private にすることはできません。パラメーターのない public コンストラクターを持っている必要があります。パラメーターのない public コンストラクターを自動的に生成する言語 (たとえば、C#) では、コンストラクターをまったくコーディングしなくても構いません。
  
    
    

### サポートされる UDF メソッドはどのようなものですか?

UDF アセンブリ内の UDF メソッドは、public でなければなりません。UDF メソッドは、スレッド セーフでなければなりません。
  
    
    
UDF メソッドは、以下のものを持つことはできません。 
  
    
    

- **ref** または **out** パラメーター
    
  
- **retval** 属性
    
  
- **Optional** 引数
    
  
- サポートされないデータ型
    
  
さらに、UDF メソッドは、サポートされる戻り値の型を持つ必要があります。サポートされるデータ型のリストについては、このトピックの「データ型」セクションを参照してください。
  
    
    

### UDF アセンブリから Web サービスを呼び出すことはできますか?

はい、できます。たとえば、次の UDF サンプルコードを参照してください。また、「 [方法: Web サービスを呼び出す UDF の作成](how-to-create-a-udf-that-calls-a-web-service.md)」も参照してください。
  
    
    

```cs

using System;
using System.Collections.Generic;
using System.Text;
using Microsoft.Office.Excel.Server.Udf;
using UdfWS.dk.iter.webservices;

namespace UdfWS
{
    [UdfClass]
    public class MyUdfClass
    {
        // Instantiate the Web service. The Web service used is at   
        // http://webservices.iter.dk/calculator.asmx
        Calculator calc = new Calculator();

        [UdfMethod]
        public int MyFunction()
        {
            int i;
            i = (i + 88) * 2;
            return i;
        }

        [UdfMethod(IsVolatile = true)]
        public double MyDouble(double d)
        {
            return d * 9;
        }

        [UdfMethod]
        public int AddMe(int a, int b)
        {
            int c;
            // Call the Web service Add method
            c = calc.Add(a, b);
            return c;
        }        
    }
}
```


```VB.net

Imports System
Imports System.Collections.Generic
Imports System.Text
Imports Microsoft.Office.Excel.Server.Udf
Imports UdfWS.dk.iter.webservices

Namespace UdfWS
    <UdfClass> _
    Public Class MyUdfClass
        ' Instantiate the Web service. The Web service used is at   
        ' http://webservices.iter.dk/calculator.asmx
        Private calc As New Calculator()

        <UdfMethod> _
        Public Function MyFunction() As Integer
            Dim i As Integer
            i = (i + 88) * 2
            Return i
        End Function

        <UdfMethod(IsVolatile := True)> _
        Public Function MyDouble(ByVal d As Double) As Double
            Return d * 9
        End Function

        <UdfMethod> _
        Public Function AddMe(ByVal a As Integer, ByVal b As Integer) As Integer
            Dim c As Integer
            ' Call the Web service Add method
            c = calc.Add(a, b)
            Return c
        End Function
    End Class
End Namespace
```


## データ型


### UDF パラメーターとして使用できるデータ型はどのようなものですか?

サポートされるデータ型は、以下のとおりです。
  
    
    

- 数値型: Double、Single、Int32、UInt32、Int16、UInt16、Byte、Sbyte
    
  
- String
    
  
- Boolean
    
  
- オブジェクト配列: 1 次元または 2 次元配列、すなわち、object [] および object [,]
    
  
- DateTime 
    
  

### サポートされている戻り値の型はどのようなものですか?

サポートされる戻り値の型は、以下のとおりです。
  
    
    

- 数値型: Double、Single、Int32、UInt32、Int16、UInt16、Byte、Sbyte
    
  
- String
    
  
- Boolean
    
  
- オブジェクト配列: 1 次元または 2 次元配列、すなわち、object []、object [,]、int[]、および int[,]
    
  
- DateTime 
    
  
- Object
    
  

## XLL


### XLL はサポートされていますか?

直接的にはサポートされていません。Excel Services は、マネージ コード UDF のみを読み込み、呼び出します。しかし、XLL を呼び出すマネージ コード ラッパーをコーディングし、XLL をマネージ コード ラッパー アセンブリと一緒にサーバーに展開することができます。
  
    
    

## 関連項目


#### タスク


  
    
    
 [方法: Web サービスを呼び出す UDF の作成](how-to-create-a-udf-that-calls-a-web-service.md)
  
    
    
 [方法: 場所を信頼する](how-to-trust-a-location.md)
  
    
    
 [例外をキャッチする方法](how-to-catch-exceptions.md)
#### 概念


  
    
    
 [Excel Services UDF の理解](understanding-excel-services-udfs.md)
  
    
    
 [チュートリアル: マネージ コード UDF を開発する](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [Excel Services のアーキテクチャ](excel-services-architecture.md)
  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
  
    
    
 [Excel Services の既知の問題およびヒント](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services のベスト プラクティス](excel-services-best-practices.md)
