---
title: 关于 Excel Services UDF 的常见问题
keywords: faqs
f1_keywords:
- faqs
ms.prod: OFFICE365
ms.assetid: 3d94d040-eecf-4f8e-a316-6d1cca95e7eb
---


# 关于 Excel Services UDF 的常见问题

下面是关于 Excel Services 用户定义函数 (UDF) 的一些常见问题。 
  
    
    


## 创建托管代码 UDF


### 什么是受支持的 UDF 类？

UDF 程序集中的 UDF 类必须为公开状态。它可以密封，不能为抽象、内部或私有状态。它必须具有无参数的公开构建器。对于自动生成无参数公开构建器的语言（例如 C#），您可能根本没有构建器。
  
    
    

### 什么是受支持的 UDF 方法？

UDF 程序集中的 UDF 方法必须为公开状态。UDF 方法必须为线程安全。
  
    
    
UDF 方法不能具有： 
  
    
    

- **ref** 或 **out** 参数
    
  
- **retval** 属性
    
  
- **Optional** 参数
    
  
- 不受支持的数据类型
    
  
UDF 方法还必须具有受支持的返回类型。有关受支持的数据类型的列表，请参阅本主题的"数据类型"部分。
  
    
    

### 能否从 UDF 程序集调用 Web 服务？

可以。有关示例，请参阅以下 UDF 示例代码。另请参见 [如何：创建调用 Web 服务的 UDF](how-to-create-a-udf-that-calls-a-web-service.md)。
  
    
    

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


## 数据类型


### 可用作 UDF 参数的数据类型有哪些？

受支持的数据类型如下：
  
    
    

- 数值类型：Double、Single、Int32、UInt32、Int16、UInt16、Byte、Sbyte
    
  
- String
    
  
- Boolean
    
  
- 对象数组：一维或两维数组，即 object [] 和 object [,]
    
  
- DateTime
    
  

### 受支持的返回值类型有哪些？

受支持的返回值类型如下：
  
    
    

- 数值类型：Double、Single、Int32、UInt32、Int16、UInt16、Byte、Sbyte
    
  
- String
    
  
- Boolean
    
  
- 对象数组：一维或两维数组，即 object []、object [,]、int[] 和 int[,])
    
  
- DateTime
    
  
- Object
    
  

## XLL


### XLL 是否受支持？

不直接支持。Excel Services 将仅加载和调用托管代码 UDF。但是，您可以编写托管代码包装，以调用 XLL 并将其与托管代码包装程序集一起部署到服务器中。
  
    
    

## 另请参阅


#### 任务


  
    
    
 [如何：创建调用 Web 服务的 UDF](how-to-create-a-udf-that-calls-a-web-service.md)
  
    
    
 [如何：信任位置](how-to-trust-a-location.md)
  
    
    
 [如何：捕获异常](how-to-catch-exceptions.md)
#### 概念


  
    
    
 [了解 Excel Services UDF](understanding-excel-services-udfs.md)
  
    
    
 [演练：开发托管代码 UDF](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [Excel Services 体系结构](excel-services-architecture.md)
  
    
    
 [Excel Services 警告](excel-services-alerts.md)
  
    
    
 [Excel Services 已知问题和提示](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services 最佳实践](excel-services-best-practices.md)
