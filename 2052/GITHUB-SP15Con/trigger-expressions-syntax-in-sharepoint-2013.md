---
title: SharePoint 2013 中的触发器表达式语法
ms.prod: SHAREPOINT
ms.assetid: d50536f6-d02e-4060-9286-634dfd06206c
---


# SharePoint 2013 中的触发器表达式语法
了解可用于创建触发条件以在 SharePoint Server 2013 中配置 Web 服务标注的触发表达式。 
## 触发表达式语法中使用的元素
<a name="SP15triggerex_elements"> </a>

可用于触发表达式的元素有：
  
    
    

- 运算符
    
  
- 托管属性值访问
    
  
- 文字
    
  
- 函数
    
  
- 常数
    
  

> **注释**
> 字符串" **Null**"是为值 **Null** 而保留的。
  
    
    


## 触发表达式语法中的运算符
<a name="SP15triggerex_operators"> </a>

表 1 按从高到低的优先顺序说明触发表达式语言支持的运算符。同一类别中的运算符的优先级相同。多种运算符具有两种版本的语法。
  
    
    

**表 1. 触发表达式语法支持的运算符**


|**类别**|**表达式**|**说明**|
|:-----|:-----|:-----|
|一元  <br/> |-  <br/> !、NOT  <br/> |算术否定  <br/> 逻辑否定  <br/> |
|乘  <br/> |*  <br/> /  <br/> %、mod  <br/> |乘  <br/> 除  <br/> 求余  <br/> |
|加  <br/> |+  <br/> -  <br/> &amp;  <br/> |加  <br/> 减  <br/> 字符串连接  <br/> |
|关系  <br/> |=、==  <br/> !=、<>  <br/> <  <br/> >  <br/> <=  <br/> >=  <br/> |等于  <br/> 不等于  <br/> 小于  <br/> 大于  <br/> 小于或等于  <br/> 大于或等于  <br/> |
|逻辑与  <br/> |&amp;&amp;、AND  <br/> |逻辑与  <br/> |
|逻辑或  <br/> |||、OR  <br/> |逻辑或  <br/> |
   

## 触发表达式中的托管属性访问
<a name="SP15triggerex_managed"> </a>

已爬网项中的托管属性通过其名称进行引用；名称不在引号 ("") 内且区分大小写。
  
    
    

## 触发表达式中的文字
<a name="SP15triggerex_literals"> </a>

以下数据类型可表达为文字： **String**、 **Int32**、 **Double** 和 **Boolean**。
  
    
    

## 触发表达式中的函数
<a name="SP15triggerex_functions"> </a>

各种函数，范围从数学函数（例如  `Floor`）到与特定数据类型一起使用的函数（例如  `Lists`）。这些函数可以单独使用，也可以嵌套使用。
  
    
    

-  `bool? ListContains<T>(IList<T> list, T obj)`
    
  
-  `int? Count<TElement>(IList<TElement> list)`
    
  
-  `TElement Item<TElement>(IList<TElement> list, int? index)`
    
  
-  `bool IsInsideRange(DateTime? date, long? fromTicks, long? toTicks)`
    
  
-  `DateTime Now()`
    
  
-  `DateTime? ToDate(string date, string format)`
    
  
-  `int? Day(DateTime? date)`
    
  
-  `int? DayOfWeek(DateTime? date)`
    
  
-  `int? DayOfYear(DateTime? date)`
    
  
-  `int? GetDatePart(DateTime? date, DatePartConstant datePartConstant)`
    
  
-  `int? Hour(DateTime? date)`
    
  
-  `int? Minute(DateTime? date)`
    
  
-  `int? Month(DateTime? date)`
    
  
-  `int? Quarter(DateTime? date)`
    
  
-  `int? Second(DateTime? date)`
    
  
-  `int? Year(DateTime? date)`
    
  
-  `long? GetDateDiff(DateTime? occursFirst, DateTime? occursLast, DatePartConstant datePartConstant)`
    
  
-  `string Extension(string arg)`
    
  
-  `string FileName(string arg)`
    
  
-  `string FileName(string arg, bool? excludeExtension)`
    
  
-  `bool IsNull(object value)`
    
  
-  `bool? IsDate(string input, string format)`
    
  
-  `object IfThenElse(bool? condition, object thenBranch, object elseBranch)`
    
  
-  `decimal? Ceiling(decimal? number)`
    
  
-  `decimal? Floor(decimal? number)`
    
  
-  `double? Ceiling(double? number)`
    
  
-  `double? Floor(double? number)`
    
  
-  `double? Sqrt(double? number)`
    
  
-  `bool? Contains(string arg, string contained)`
    
  
-  `bool? EndsWith(string arg, string suffix)`
    
  
-  `bool? IsMatch(string input, string pattern)`
    
  
-  `bool? IsMatch(string input, string pattern, int? start, RegexOptionConstant options)`
    
  
-  `bool? IsMatch(string input, string pattern, RegexOptionConstant options)`
    
  
-  `bool? IsNullOrEmpty(string input)`
    
  
-  `bool? StartsWith(string arg, string prefix)`
    
  
-  `int? IndexOf(string arg, string toFind)`
    
  
-  `int? IndexOfRegex(string input, string regex)`
    
  
-  `int? LastIndexOf(string arg, string toFind)`
    
  
-  `int? Length(string arg)`
    
  
-  `string Match(string input, string pattern)`
    
  
-  `string Match(string input, string pattern, int? start, int? length, RegexOptionConstant options)`
    
  
-  `string Match(string input, string pattern, int? start, RegexOptionConstant options)`
    
  
-  `string Match(string input, string pattern, RegexOptionConstant options)`
    
  
-  `string Substring(string arg, int? start)`
    
  
-  `string Substring(string arg, int? start, int? length)`
    
  
-  `string ToLower(string arg)`
    
  
-  `string Trim(string value)`
    
  

## 触发表达式中的常数
<a name="SP15triggerex_constants"> </a>

有两组常数可用于特定的函数： **DatePartConstant** 和 **RegexOptionConstant**。表 2 列出这些常数的其中两个示例及其用途。
  
    
    

**表 2. 触发表达式常数及其在 SharePoint 2013 中的使用**


|**常数组**|**示例**|**使用**|
|:-----|:-----|:-----|
|**DatePartConstant** <br/> |**Day**、 **Month**、 **Year**、 **Hour**、 **Minute**、 **Second**。  <br/> |用于 **GetDatePart** 函数 <br/> |
|**RegexOptionConstant** <br/> |**IgnoreCase** <br/> |用于 **IsMatch**、 **Match**、 **ReplaceRegex** 和 **IndexOfRegex** 函数。 <br/> |
   

## 其他资源
<a name="SP15triggerex_addresources"> </a>


-  [使用内容扩充 Web 服务标注进行自定义内容处理](custom-content-processing-with-the-content-enrichment-web-service-callout.md)
    
  
-  [如何：对 SharePoint Server 使用内容扩充 Web 服务标注](how-to-use-the-content-enrichment-web-service-callout-for-sharepoint-server.md)
    
  

  
    
    

