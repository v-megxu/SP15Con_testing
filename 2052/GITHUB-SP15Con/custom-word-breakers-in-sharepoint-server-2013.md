---
title: SharePoint Server 2013 中的自定义分词系统
ms.prod: SHAREPOINT
ms.assetid: d18b48d4-987c-4228-9932-30d5b30f86a2
---


# SharePoint Server 2013 中的自定义分词系统
学习 SharePoint Server 2013 中的断字。 
断字是其中一种关键自然语言处理 (NLP) 功能，这种功能支持搜索并可改进搜索结果（或回调）。分词系统将文本流划分为单独的字或标记，您可以基于这些字和标记进行额外的语言处理。分词系统特定于语言。除内置分词系统外，SharePoint 2013 中的搜索功能还支持使用自定义分词系统，以便用户可以根据其需要调整断字行为。有关分词系统自定义支持的列表语言，请参阅 [SharePoint Server 2013 中支持的分词系统自定义语言](#SP15_SupportedLanguages)。
  
    
    

有关如何编写分词系统的信息，请参考以下文章 
-  [实现分词系统](http://msdn.microsoft.com/zh-cn/library/ms693186%28v=vs.85%29.aspx)
    
  
-  [IWordBreaker 接口](http://msdn.microsoft.com/zh-cn/library/ms691079%28v=vs.85%29.aspx)
    
  

## 如何在 SharePoint Server 2013 中切换到自定义分词系统
<a name="SP15wordbreaker_howto"> </a>


> **警告**
> 替换现有分词系统时，自行承担修改注册表的风险。使用"注册表编辑器"或其他方法错误修改注册表可能会出现严重问题。这些问题可能要求您重新安装操作系统。Microsoft 无法确保可以解决这些问题。在建立索引和执行查询期间切换到不同的分词系统还可能引起严重问题。修改注册表前，请备份注册表并确保您知道如何在出现问题时还原注册表。 
  
    
    

遵循以下步骤将现有分词系统替换为自定义分词系统或将现有分词系统替换为其他语言的分词系统。
  
    
    

1. 打开"注册表编辑器"，然后按如下步骤操作：
    
1. 选择"开始"，然后选择"运行"。
    
  
2. 在"打开"对话框中，键入"Regedit"，然后选择"确定"。
    
  
2. 在"注册表编辑器"中，选择一下注册表子项：
    
    **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Office Server\\15.0\\Search\\Setup\\ContentIndexCommon\\LanguageResources\\Default\\** _下表中的语言_
    
  
3. 在右侧窗格中，打开"WBDLLPathOverride"注册表值的快捷菜单，然后选择"修改"。
    
  
4. 在"编辑字符串"对话框的"值数据"框中，键入您自定义分词系统 DLL 的路径，然后选择"确定"。新 DLL 应位于被替换的现有 DLL 所在的路径中。
    
  
5. 在右侧窗格中，打开"WBreakerClass"注册表值的快捷菜单，然后选择"修改"。
    
  
6. 在"编辑字符串"对话框的"值数据"框中，键入您自定义分词系统的类 ID，然后选择"确定"。
    
  
7. 重新启动 SharePoint 搜索主机控制程序和 SharePoint Server 2013。
    
  
8. 完全重新爬网。
    
  

## SharePoint Server 2013 中支持的分词系统自定义语言
<a name="SP15_SupportedLanguages"> </a>

以下语言支持分词系统自定义：
  
    
    
阿拉伯语
  
    
    
孟加拉语
  
    
    
保加利亚语
  
    
    
加泰罗尼亚语
  
    
    
中文（中华人民共和国）
  
    
    
中文（台湾）
  
    
    
克罗地亚语
  
    
    
捷克语
  
    
    
丹麦语
  
    
    
荷兰语（荷兰）
  
    
    
英语（美国）
  
    
    
爱沙尼亚语
  
    
    
芬兰语
  
    
    
法语（标准）
  
    
    
德语（标准）
  
    
    
希腊语
  
    
    
古吉拉特语
  
    
    
希伯来语
  
    
    
印度语
  
    
    
匈牙利语
  
    
    
冰岛语
  
    
    
印度尼西亚语
  
    
    
意大利语（默认）
  
    
    
日语
  
    
    
坎那达语
  
    
    
哈萨克语
  
    
    
韩语
  
    
    
拉脱维亚语
  
    
    
立陶宛语
  
    
    
马来语
  
    
    
马拉雅拉姆语
  
    
    
马拉地语
  
    
    
挪威语
  
    
    
波兰语
  
    
    
葡萄牙语（葡萄牙）
  
    
    
旁遮普语
  
    
    
罗马尼亚语
  
    
    
俄语
  
    
    
塞尔维亚语（西里尔）
  
    
    
斯洛伐克语
  
    
    
斯洛文尼亚语
  
    
    
西班牙语（现代排序）
  
    
    
瑞典语
  
    
    
泰米尔语
  
    
    
泰卢固语
  
    
    
泰语
  
    
    
土耳其语
  
    
    
乌克兰语
  
    
    
乌尔都语
  
    
    
越南语
  
    
    

## 其他资源
<a name="SP15wordbreakers_addresources"> </a>


-  [配置 SharePoint 2013 中的搜索功能](configure-search-in-sharepoint-2013.md)
    
  
-  [实现分词系统](http://msdn.microsoft.com/zh-cn/library/ms693186%28v=vs.85%29.aspx)
    
  
-  [IWordBreaker 接口](http://msdn.microsoft.com/zh-cn/library/ms691079%28v=vs.85%29.aspx)
    
  

