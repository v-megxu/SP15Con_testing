

# 向 SharePoint 2013 中的页面添加图像呈现
您所在市场中可能尚未推出 Office 商店或 SharePoint 商店。
  
    
    
![操作方法](images/mod_icon_badge_howto.png)
  
    
    

  
    
    

  
    
    
了解如何在 SharePoint 发布网站中使用图像呈现形式。
 * **适用范围：*** 
  
    
    


||
|:-----|
|**本文内容**          [使用图像呈现形式的先决条件](#AddImageRendition_Prerequisites)           [使用 RTF 编辑器指定图像呈现形式](#AddImageRendition_RichTextEditor)           [在图像 URL 中指定图像呈现形式](#AddImageRendition_ImageURL)           [在图像字段控件中指定图像呈现形式](#AddImageRendition_ImageFieldControl)           [其他资源](#AddImageRendition_AdditionalResources)|
   

在将图像添加到 SharePoint 发布网站中的页面上时，可以指定用于该图像的图像呈现形式。当此页面呈现在浏览器中时，将显示正确的图像大小。您可以在 RTF 编辑器、图像字段控件或图像 URL 中指定图像呈现形式。
  
    
    


## 使用图像呈现形式的先决条件
<a name="AddImageRendition_Prerequisites"> </a>

由于图像呈现形式依赖 SharePoint Server 2013 中的其他功能，因此需确保您满足本节中的先决条件，才能执行本主题中的过程。先决条件包括：
  
    
    

- **发布网站集** 您要在其中添加图像呈现形式的网站集必须已事先使用发布门户或产品目录网站集模板进行创建。或者，必须在要在其中使用图像呈现形式的网站集上启用发布功能。有关详细信息，请参阅 TechNet 库中的 [发布到 Internet、Intranet 和 Extranet 网站的概述](http://technet.microsoft.com/zh-cn/library/jj635881%28office.15%29.aspx)。
    
  
- **配置的 BLOB 缓存** 基于磁盘的 BLOB 缓存用于控制二进制大型对象 (BLOB)（例如，常用图像、音频和视频文件以及用于显示网页的其他文件（例如 .css 文件和 .js 文件））的缓存。必须在要在其中使用图像呈现形式的各个前端 Web 服务器上启用 BLOB 缓存。如果未启用 BLOB 缓存，则始终使用原始图像。有关详细信息，请参阅 TechNet 库中的 [为 Web 应用程序配置缓存设置](http://technet.microsoft.com/zh-cn/library/cc770229.aspx)。
    
  
- **图像呈现形式 ID** 如果要使用 **RenditionID** 参数或 **RenditionId** 属性，则必须知道要使用的图像呈现形式的 ID。使用"图像呈现形式"页可查看可用的图像呈现形式列表和每个图像呈现形式的 ID。有关详细信息，请参阅 [SharePoint 2013 设计管理器图像呈现形式](sharepoint-2013-design-manager-image-renditions.md)。
    
  

## 使用 RTF 编辑器指定图像呈现形式
<a name="AddImageRendition_RichTextEditor"> </a>

在页面中插入图像时，可以指定要使用的图像呈现形式，以便在呈现该页面时显示正确的图像大小。您可以在 RTF 编辑器中仅对正在编辑的页面所在的网站集中存储的图像指定图像呈现形式。
  
    
    

### 使用 RTF 编辑器指定图像呈现形式


1. 在"页面"选项卡上，选择"编辑"。
    
  
2. 选择"设置"图标，然后选择"添加页"。
    
  
3. 在"添加页"窗口中，输入页面的名称，然后选择"创建"。
    
  
4. 将指针置于"页面内容"字段中。
    
  
5. 在"插入"选项卡上，选择"图片"，然后选择"从 SharePoint"。
    
  
6. 找到要添加到该页面中的图像，选择该图像，然后选择"插入"。该图像将以完整大小显示。
    
  
7. 在"设计"选项卡的"选择"组中，选择"选择呈现形式"，然后选择一个图像呈现形式。图像将根据此图像呈现形式指定的大小显示。
    
    > **注释**
      > "选择呈现形式"命令仅适用于正在编辑的页面所在的网站集中存储的图像。 
8. 如果要裁剪图像呈现形式，则选择"选择呈现形式"，然后选择"编辑呈现形式"。
    
    有关裁剪图像呈现形式的详细信息，请参阅 [在 SharePoint 2013 中裁切图像呈现](3a6efae9-b18f-4032-b0db-809e611ce9b7.md)。
    
  

## 在图像 URL 中指定图像呈现形式
<a name="AddImageRendition_ImageURL"> </a>

您可以通过将 RenditionID、Width 或 Height 参数添加到图像 URL 中来指定图像呈现形式。
  
    
    
 **RenditionID** 使用 RenditionID 参数可以指定要使用的图像呈现形式的 ID。
  
    
    
 **Width** 使用 Width 参数可以指定图像呈现形式的宽度（以像素为单位）。SharePoint Server 会尝试查找具有指定宽度的图像呈现形式。然后，SharePoint Server 会尝试查找其宽度大于指定宽度的图像呈现形式。如果有多个符合此标准的图像呈现形式，SharePoint Server 会使用具有最接近指定值的宽度的图像呈现形式。如果没有宽度大于或等于指定宽度的图像呈现形式，则使用原始图像。
  
    
    
 **Height** 使用 Height 参数可以指定图像呈现形式的高度（以像素为单位）。SharePoint Server 会尝试查找具有指定高度的图像呈现形式。然后，SharePoint Server 会尝试查找其高度大于指定高度的图像呈现形式。如果有多个符合此标准的图像呈现形式，SharePoint Server 会使用具有最接近指定值的高度的图像呈现形式。如果没有高度大于或等于指定高度的图像呈现形式，则使用原始图像。
  
    
    
 **Width 和 Height** 如果已指定 Width 参数和 Height 参数，SharePoint Server 会尝试查找具有指定宽度和高度的图像呈现形式。然后，SharePoint Server 会尝试查找与指定宽度/高度比率最接近的呈现形式。如果有多个匹配项，则选择具有最接近所需大小的较大宽度/高度比率的图像呈现形式。
  
    
    

> **注释**
> 如果图像 URL 包括 RenditionID 参数以及 Width 和 Height 参数，则忽略 Width 和 Height 参数。 
  
    
    

以下示例演示如何使用 RenditionID 参数：
  
    
    



```HTML

<img src="/sites/pub/Assets/Lighthouse.jpg?RenditionID=2" />
```

以下示例演示如何使用 Width 和 Height 参数：
  
    
    



```HTML
<img src="/sites/pub/Assets/Lighthouse.jpg?Width=400&amp;Height=200" />
```


## 在图像字段控件中指定图像呈现形式
<a name="AddImageRendition_ImageFieldControl"> </a>

开发人员可以在图像字段控件中指定要使用的图像呈现形式。可以使用 **RenditionId** 属性设置图像呈现形式的 ID。有关详细信息，请参阅 **RenditionId**。
  
    
    

## 其他资源
<a name="AddImageRendition_AdditionalResources"> </a>


-  [SharePoint 2013 设计管理器图像呈现形式](sharepoint-2013-design-manager-image-renditions.md)
    
  
-  [在 SharePoint 2013 中裁切图像呈现](3a6efae9-b18f-4032-b0db-809e611ce9b7.md)
    
  
-  [在 SharePoint 2013 中开发网站设计](develop-the-site-design-in-sharepoint-2013.md)
    
  