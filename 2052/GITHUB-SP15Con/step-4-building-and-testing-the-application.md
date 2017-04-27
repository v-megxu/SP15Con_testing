---
title: 步骤 4：构建和测试应用程序
ms.prod: OFFICE365
ms.assetid: f2feeecb-1b4c-4049-be4e-11d414f13d9f
---


# 步骤 4：构建和测试应用程序

在本步骤中，您将构建和测试您的应用程序。Visual Studio 提供多种方法，可从 IDE 构建和运行控制台应用程序，例如：
  
    
    


- 在不调试的情况下启动 ( **CTRL + F5**)
    
  
- 启动 ( **F5**)
    
  

## 构建、运行和调试应用程序


### 构建并运行应用程序


1. 在"调试"菜单上单击"在不调试的情况下启动"；或按 CTRL + F5。这可确保控制台窗口在程序执行完之后仍为打开状态。 
    
  
2. 应用程序将以下输出显示到控制台上。
    
    > **注释**
      > 这些值各不相同，具体取决于您的工作簿中的值、会话 ID，等等。 

  ```
  
The Credential is: System.Net.SystemNetworkCredential
Total rows in range: 18
Value in range is: 4245.955129
  ```

3. 按任意键关闭 SampleApplication.exe。
    
  

### "未找到文件"异常


1. 如果您提供的工作簿路径错误，您将收到以下代码捕获的"未找到文件"异常：
    
  ```cs
  
catch (SoapException e)
{
    Console.WriteLine("SOAP Exception Message: {0}", e.Message);
}
  ```


  ```VB.net
  
Catch e As SoapException
Console.WriteLine("SOAP Exception Message: {0}", e.Message)
End Try
  ```

2. 应用程序将以下 SOAP 异常输出显示到控制台上。
    
  ```
  
SOAP Exception Message: The file you selected could not be found. Check the spelling of the file name and verify that the location is correct.

  ```


### "索引超出范围"异常


1. 如果您尝试从范围外部获取值，将收到 **System.IndexOutOfRangeException** 异常。应用程序将以下输出显示到控制台上：
    
  ```
  
The Credential is: System.Net.SystemNetworkCredential
The sessionID is : 64.28e58e90-b757-4658-b1c4-890ad68ef6cbRmqR4IINXfkMeOJRG8Iq0Y
27tVk=110.33d3R6fqv7tr2jPyYiPwRu|!@en-US|en-US|+0480#0000-10-00-05T02:00:00:0000
#+0000#0000-04-00-01T02:00:00:0000#-0060
Total rows in range: 18
  ```

2. 然后您将收到一个未经处理的异常，其内容为：
    
  ```
  
An unhandled exception of type 'System.IndexOutOfRangeException' occurred in SampleApplication.exe
Additional information: Index was outside the bounds of the array.
  ```

3. 您可以通过添加另一个 **catch** 块以捕获 SOAP 异常 **catch** 块之后的异常（如下所示），来处理上述未经处理的异常：
    
  ```cs
  
catch (Exception e)
{
    Console.WriteLine("Exception Message: {0}", e.Message);
}
  ```


  ```VB.net
  
Catch e As Exception
Console.WriteLine("Exception Message: {0}", e.Message)
End Try
  ```


### 使用 F5 运行应用程序


1. 您可以通过单击"调试"菜单上的"启动"或者按 F5 来运行应用程序。为确保控制台窗口在程序执行完之后仍为打开状态，您可以将以下代码行添加到代码结尾（ **catch** 块之后）：
    
  ```cs
  
Console.ReadLine();
  ```


  ```VB.net
  Console.ReadLine()
  ```

2. 按任意键关闭 SampleApplication.exe。
    
  

## 另请参阅


#### 概念


  
    
    
 [访问 SOAP API](accessing-the-soap-api.md)
#### 其他资源


  
    
    
 [步骤 1：创建 Web 服务客户端项目](step-1-creating-the-web-service-client-project.md)
  
    
    
 [步骤 2：添加 Web 引用](step-2-adding-a-web-reference.md)
  
    
    
 [步骤 3：访问 Web 服务](step-3-accessing-the-web-service.md)
  
    
    
 [演练：使用 Excel Web Services 开发自定义应用程序](walkthrough-developing-a-custom-application-using-excel-web-services.md)
  
    
    
 [如何：使用脚本信任工作簿位置](http://msdn.microsoft.com/library/79ab6ced-7a0c-4275-b852-bb246fc6be57%28Office.15%29.aspx)
