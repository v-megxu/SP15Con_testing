---
title: 步骤 2：创建托管代码 UDF
keywords: soap
f1_keywords:
- soap
ms.prod: SHAREPOINT
ms.assetid: 3c9edf82-ee2d-41f0-9d66-e88e8dc0cc69
---


# 步骤 2：创建托管代码 UDF

在项目中添加对 Microsoft.Office.Excel.Server.Udf.dll 的引用后，下一步是创建一些自定义函数，并使用 Excel Services 用户定义函数 (UDF) 属性进行标记。 
  
    
    

您必须使用 **Microsoft.Office.Excel.Server.Udf.UdfClass** 属性标记 UDF 类，使用 **Microsoft.Office.Excel.Server.Udf.UdfMethod** 属性标记 UDF 方法。
UDF 程序集中任何未使用 **Microsoft.Office.Excel.Server.Udf.UdfMethod** 属性进行标记的方法将被忽略，因为它们被视为 UDF 方法。
  
    
    

 **Microsoft.Office.Excel.Server.Udf.UdfMethod** 属性具有 **IsVolatile** 特性。您可使用 **IsVolatile** 特性将 UDF 方法指定为易失性和或非易失性。 **IsVolatile** 特性使用布尔值。默认值为 **false**，这表示特定 UDF 方法为非易失性。 
## 创建 UDF


### 添加指令


- 要使用的类型在 ** Microsoft.Office.Excel.Server.Udf** 命名空间中定义。在 Class1.cs 文件开头添加 **using**（或 **Imports**）指令，即可使用 **Microsoft.Office.Excel.Server.Udf** 中的类型，而无需完全符合命名空间中的类型。
    
    要添加该指令，请将以下代码添加到 Class1.cs 文件中代码的开头，在  `using System.Text:` 之后
    


  ```cs
  
using Microsoft.Office.Excel.Server.Udf; 
  ```




  ```VB.net
  Imports Microsoft.Office.Excel.Server.Udf
  ```


### 标记 UDF 类和方法


1. 将以下属性添加到  `public class Class1` 前面，将 `Class1` 标记为 UDF 类：
    
  ```cs
  [UdfClass]
  ```


  ```VB.net
  <UdfClass>_
  ```

2. 创建一个值为数字的函数（类型为 **double**），然后在函数中将数字乘以 9。该函数是一个非易失性 UDF 方法。将以下代码添加到  `Class1` 中：
    
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


    > **注释**
      > **IsVolatile** 属性的默认值为 **false**，这表示特定 UDF 方法为非易失性。因此，我们有充分的理由将非易失性 UDF 方法标记为  `[UdfMethod]`。无需将其标记为  `[UdfMethod(IsVolatile = false)]`。 
3. 使用 **System.DateTime.Today** 特性创建另一个返回最新状态的函数。函数为易失性 UDF 方法。将以下代码添加到 `Class1`：
    
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


### 构建项目


1. 在"构建"菜单上，单击"构建解决方案"。
    
  
2. 您应在您保存项目的目录中查找 SampleUdf.dll 程序集。 
    
  

### 完整代码

以下代码示例是上述步骤中所述 Class1.cs 示例文件中的完整代码。
  
    
    

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


## 另请参阅


#### 任务


  
    
    
 [步骤 1：创建项目并添加 UDF 引用](step-1-creating-a-project-and-adding-a-udf-reference.md)
  
    
    
 [步骤 3：部署和启用 UDF](step-3-deploying-and-enabling-udfs.md)
  
    
    
 [步骤 4：从单元格测试和调用 UDF](step-4-testing-and-calling-udfs-from-cells.md)
  
    
    
 [如何：创建调用 Web 服务的 UDF](how-to-create-a-udf-that-calls-a-web-service.md)
#### 概念


  
    
    
 [演练：开发托管代码 UDF](walkthrough-developing-a-managed-code-udf.md)
  
    
    
 [了解 Excel Services UDF](understanding-excel-services-udfs.md)
