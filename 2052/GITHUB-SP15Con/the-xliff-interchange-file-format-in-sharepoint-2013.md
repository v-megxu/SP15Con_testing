---
title: SharePoint 2013 中的 XLIFF 交换文件格式
ms.prod: SHAREPOINT
ms.assetid: 660c0f07-7030-4576-957e-b9f2cd0fa895
---


# SharePoint 2013 中的 XLIFF 交换文件格式
获取有关 XLIFF 交换文件格式的 SharePoint 2013 实现的信息，包括架构参考信息和 XML 示例。
## SharePoint 2013 中的 XLIFF 交换文件格式实现

SharePoint 2013 对变体功能和翻译服务功能提供 XML 本地化交换文件格式 (XLIFF) 应用程序支持。SharePoint Server 使用 XLIFF 将有关文件及其内容的信息以一种易于人工转换器理解的格式从 SharePoint Server传输到转换器中。
  
    
    
当提取 SharePoint Server HTML 页面提取为 XLIFF 格式时，SharePoint 2013 遵循 OASIS 发布的 [适用于 HTML 的 XLIFF 1.2 表示指南](http://docs.oasis-open.org/xliff/v1.2/xliff-profile-html/xliff-profile-html-1.2-cd02.mdl)。为了消除在要传输未修改的 SharePoint Server CDATA 内容时出现在 XLIFF 包中的可翻译元素与代码元素相混合的现象，交付的 SharePoint 2013 具有生成完全兼容 XLIFF 的 XLIFF 文档的功能，这些文档也能很好地与 SharePoint 2013 集成。将 XML 文件以 XLIFF 格式从  `sharepointservernv` 中导出时，人工转换器接收的数据会工整且已准备好进行翻译。
  
    
    
本文记录了在 OASIS 发布的 XLIFF 开放式标准文档 1.2 版中更普遍定义的 XLIFF 元素和属性的特定 SharePoint Server实现。有关特定 XLIFF 元素和属性的详细信息，请参阅  [XLIFF 1.2 规范](http://docs.oasis-open.org/xliff/xliff-core/xliff-core.mdl)。
  
    
    

  
    
    

**表 1. SharePoint 2013 中值得注意的 XLIFF 元素和属性**


|**元素**|**属性**|**备注**|
|:-----|:-----|:-----|
|Xml  <br/> | `version` <br/>  `encoding` <br/> |声明 XML 版本和编码。  <br/> |
|Xliff  <br/> | `version` <br/>  `xmlns` <br/> |包含 `version`属性和架构验证机制。  <br/> |
|File  <br/> | `original` <br/>  `source-language` <br/>  `target-language` <br/>  `datatype` <br/>  `tool-id` <br/> |对应于原始源文件，它在 中是变体功能的一个页面 GUID，其中包括源语言和目标语言（ `source-language` 和 `target-language`），这些语言可供机器翻译工具和人工翻译工具使用。  <br/>  `original` 属性包含一个用于标识原始源内容的 GUID。此值应保持不变，以帮助确保成功导入。 <br/> 对于所有 SharePoint 页面， `datatype` 属性也以 HTML 格式存储在 **File** 元素中。 <br/>  `tool-id` 属性是标识生成 XLIFF 文件的工具的 GUID。 <br/> |
|标头  <br/> |||
|Tool  <br/> | `tool-id` <br/>  `tool-name` <br/> |标识生成 XLIFF 文件的工具。  <br/> |
|Note  <br/> ||包含可能对本地化人员、开发人员或其他处理 XLIFF 文件的人员有用的信息。  <br/>  `note` 元素的值由 生成。 `note` 属性包含能够标识内容位置和类型的 GUID，用于提供上下文。 <br/> |
|正文  <br/> |||
|Trans-unit  <br/> | `id` <br/>  `datatype` <br/> | `id` 属性包含能够标识导入位置的 GUID。 <br/>  `datatype` 属性定义 **trans-unit** 元素中包含的数据类型。有关可用 `datatype` 属性值列表的信息，请参阅 XLIFF 开放式标准文档。 <br/> |
|Source  <br/> ||HTML 内容通常包含需要保留的标记。为此，SharePoint 2013 会将标记封装在 HTML 内容中，其中带有的标记在  [面向 HTML 的 XLIFF 1.2 表示指南](http://docs.oasis-open.org/xliff/v1.2/xliff-profile-html/xliff-profile-html-1.2-cd02.mdl)。  <br/> |
|Target  <br/> |ph（可选）  <br/> bpt（可选）  <br/> ept（可选）  <br/> sub（可选）  <br/> |HTML 内容通常包含需要保留的标记。为此，SharePoint 2013 会将标记封装在 HTML 内容中，其中带有的标记在  [面向 HTML 的 XLIFF 1.2 表示指南](http://docs.oasis-open.org/xliff/v1.2/xliff-profile-html/xliff-profile-html-1.2-cd02.mdl)。  <br/> |
|Bin-unit  <br/> ||可以通过 **bin-unit** 元素发送存储在 SharePoint 2013 中的文件，用来借助 XLIFF 实现本地化。可通过使用 [SharePoint 2013：在 XLIFF 文件中提取和插入 bin-unit 元素](http://code.msdn.microsoft.com/SharePoint-2013-Extract-fe686878)代码示例提取该文件，将其返回到原始文件格式。  <br/> |
|Bin-source  <br/> |||
|Bin-target  <br/> |||
|Internalfile  <br/> |form  <br/> ||
   

## 示例：SharePoint 2013 中的 XLIFF 标记

以下 XLIFF 交换文件格式的 XML 文档示例演示 SharePoint 2013 如何实现标准中定义的一些元素和属性。 
  
    
    

```XML

<?xml version="1.0" encoding="utf-8"?>
<xliff version="1.2" xmlns="urn:oasis:names:tc:xliff:document:1.2">
  <file original="ce2b8e40-b802-4196-b6cb-93e63eb4bb42" source-language="en-US" target-language="fr-CA" datatype="html">
    <header>
      <note>type=ListItem</note>
      <note>translatorType=Vendor</note>
      <note>packageGroupId=fb98837d-c4e0-48f1-9e59-874b61802cda</note>
      <note>webId=1c013046-821b-40d7-a1e0-689dd920f37d</note>
      <note>listId=58b11f3f-6549-47c5-bf13-a2dc4dfa03b3</note>
      <note>url=Pages/Type-or-edit-text-in-a-different-language.aspx</note>
      <note>sourceVersion=2</note>
    </header>
<body>
      <trans-unit id="fa564e0f-0c70-4ab9-b863-0177e6ddd247" datatype="plaintext">
        <source>Type or edit text in a different language</source>
        <note>fieldTitle=Title</note>
      </trans-unit>
      <trans-unit id="f55c4d88-1f2e-4ad9-aaa8-819af4ee7ee8" datatype="html">
        <source>
          <bpt id="1">&amp;lt;strong&amp;gt;</bpt>When you want to type documents in different languages, you can change your keyboard layout language--the language-specific characters typed when keyboard keys are pressed--so that you can type the special characters for each language. 
  <ept id="1">&amp;lt;/strong&amp;gt;</ept>
        </source>
        <note>fieldTitle=Page Content</note>
      </trans-unit>
    </body>
  </file>

```


  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [添加 SharePoint 2013 功能](add-sharepoint-2013-capabilities.md)
    
  
- 代码示例： [SharePoint 2013：在 XLIFF 文件中提取和插入 bin-unit 元素](http://code.msdn.microsoft.com/SharePoint-2013-Extract-fe686878)
    
  
-  [SharePoint 2013 中的机器翻译服务](machine-translation-services-in-sharepoint-2013.md)
    
  

  
    
    

