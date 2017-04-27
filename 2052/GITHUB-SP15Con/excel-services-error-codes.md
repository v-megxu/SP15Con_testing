---
title: Excel Services 错误代码
keywords: alerts
f1_keywords:
- alerts
ms.prod: SHAREPOINT
ms.assetid: ff128d67-f3ac-4a8f-ae8e-1e19e343014e
---


# Excel Services 错误代码

当 Excel Services 中发生错误时，=Excel Services 将在 SOAP 异常中生成错误和错误消息。下表显示了当 Excel Web Services 方法调用抛出 SOAP 异常时可访问的错误。 
  
    
    

您使用 **SoapException** 类的 [SubCode](http://msdn.microsoft.com/library/frlrfSystemWebServicesProtocolsSoapExceptionClassSubCodeTopic.aspx) 属性捕获错误代码。有关使用 **SubCode** 属性捕获错误代码的详细信息，请参阅 [如何：使用 SubCode 属性捕获错误代码](how-to-use-the-subcode-property-to-capture-error-codes.md)
有关 Excel Services 警报的详细信息，请参阅  [Excel Services 警告](excel-services-alerts.md)。 
  
    
    


## 错误代码

下表列出了 Excel Web Services 警报的错误代码及相关消息、解释和解决方法。 
  
    
    


|****Error Code****|****Message****|****Explanation****|****Resolution****|
|:-----|:-----|:-----|:-----|
|ApiInvalidArgument  <br/> |参数的值无效：{0}  <br/> |将参数的无效值传递到了 API 调用。  <br/> 0 = 参数的名称。它的值无效。  <br/> |对参数使用有效值。  <br/> |
|ApiInvalidCoordinate  <br/> |{1} 的 {0} 坐标无效。  <br/> |0 = 坐标名称（行、列、高度、宽度）  <br/> 1 = 参数的名称，其中包含坐标结构。  <br/> get 或 set 调用上 **RangeCoordinates** 类或 row\\column\\height\\width 参数的内容无效。 <br/> |对参数使用有效的坐标值。  <br/> |
|DimensionAndArrayMismatch  <br/> |所提供的数组的大小与目标区域的大小和形状不匹配。  <br/> |调用者试图将范围设置到工作簿中，但包含数组值的参数与目标范围不匹配。  <br/> |确保所提供数组的大小与目标范围的尺寸匹配（例如，2 列宽乘以 3 行高）。  <br/> |
|DiscontiguousRangeNotSupported  <br/> |范围请求不引用连续范围。Excel Services 仅支持连续范围。  <br/> |调用者在尝试设置或获取单元格范围时提供了一个不连续的范围。Excel Services 不支持非连续范围，仅支持连续范围。  <br/> |输入连续范围，如"A1:B7"或"A1"或"MyTable[#Data]"，而不是非连续范围，如"A1:B7, B12"或"A1,A3"。  <br/> |
|ExternalDataRefreshFailed  <br/> |无法检索下列连接的外部数据：  <br/> {0}  <br/> 数据源可能无法访问，可能没有响应，或已拒绝访问。  <br/> |尝试刷新工作簿内的数据源失败。  <br/> 0 是连接名称的 \\n 分隔列表。  <br/> |确保数据源可用并且您有权访问它。  <br/> |
|FileOpenAccessDenied  <br/> |您没有权限在 Excel Services 中打开此文件。  <br/> |调用 **OpenWorkbook** 方法失败，因为用户无权访问该文件。 <br/> |请与管理员联系。  <br/> |
|FileCorrupt  <br/> |您选择的文件无法打开，因为文件已被破坏，受信息权限管理保护，或者使用了 Excel Services 不支持的文件格式。Excel 可以打开此文件。  <br/> |调用 **OpenWorkbook** 方法失败，因为该文件已损坏。 <br/> |尝试再次打开该文件，或使用 Excel 打开该文件。  <br/> |
|FileOpenNotFound  <br/> |找不到您选择的文件。请检查文件名的拼写，并验证位置是否正确。  <br/> |调用 **OpenWorkbook** 方法失败，因为该文件不存在。 <br/> |确保文件未重命名、移动或删除，文件位于受信任的位置，且您有权访问该文件。如果问题仍然存在，请与管理员联系。  <br/> |
|FileOpenSecuritySettings  <br/> |由于 Excel Services 的安全设置，当前无法打开您选择的文件。  <br/> |调用 **OpenWorkbook** 方法失败，因为管理员的安全设置出于多种原因阻止其打开。例如，文件太大，即文件大小超出了管理员设置的限制。 <br/> |请与管理员联系。  <br/> |
|FormulaEditingNotEnabled  <br/> |在此版本的 Excel Services，没有启用编辑公式的功能。  <br/> |调用者试图向工作簿中写入公式。  <br/> |请勿尝试写入公式，因为它在此版本的 Excel Services 中不受支持。  <br/> |
|GenericFileOpenError  <br/> |打开所选的文件时出错。  <br/> |由于某个未知原因，Excel Services 无法打开该文件。  <br/> |等待几分钟，然后再次尝试打开该文件。如果问题仍然存在，请与管理员联系。  <br/> |
|InvalidSheetName  <br/> |工作簿中不存在您所请求的工作表。  <br/> |工作表名称找不到或无效。  <br/> |对工作表名称使用有效的值。  <br/> |
|InvalidOrTimedOutSession  <br/> |此时无法完成您所执行的操作，因为该会话在服务器上不再可用。您可以重新加载工作簿并创建一个新的会话，但您所做的任何更改都已丢失。  <br/> |调用  _sessionId_ 值无效或者已超时。 <br/> |在新的会话中重新加载工作簿。  <br/> |
|IRMedWorkbook  <br/> |请求的工作簿受 IRM 保护。Excel Services 无法加载受 IRM 保护的工作簿。  <br/> |调用 **OpenWorkbook** 方法失败，因为工作簿受信息权限管理 (IRM) 保护。 <br/> |仅传递不受 IRM 保护的工作簿。  <br/> |
|MaxSessionsPerUserExceeded  <br/> |已超出每个用户允许的会话数最大值。无法完成操作。  <br/> |已超出用户在任何给定时间内可以打开的会话最大数量。此限制由管理员设置。  <br/> |不要超出限制或与管理员联系。  <br/> |
|MultipleRequestsOnSession  <br/> |此会话正在处理某个操作。在会话中一次只能处理一个操作。  <br/> |在同一个会话中发出了多个请求。会话一次只能处理一个请求（也有个别例外情况）。  <br/> |请再次尝试执行该操作。  <br/> |
|NotMemberOfRole  <br/> |访问被拒绝。您没有执行此操作或访问此资源的权限。  <br/> |调用者没有访问该服务器的权限。  <br/> |请与管理员联系。  <br/> |
|ObjectTypeNotSupported  <br/> |提供的一个或多个对象类型不受 Excel Services 支持。已回滚操作。  <br/> |调用者试图向范围中写入不受支持的对象类型值。  <br/> |使用一个受支持的对象类型再次尝试此操作。  <br/> |
|OperationCanceled  <br/> |操作已取消。  <br/> |当前执行的操作已取消，因为用户调用 **CancelRequest** 方法。 <br/> |仅当您想取消当前操作时调用 **CancelRequest** 方法。 <br/> |
|RangeParseError  <br/> |Excel Services 无法分析范围请求。  <br/> |传递到具有 A1 后缀的方法（ **SetCellA1**、 **SetRangeA1**、 **GetCellA1** 和 **GetRangeA1**）的范围无法进行分析。  <br/> |使用 A1 表示法（例如"Sheet1!Range("A6:A15")"或有效的结构化引用（例如"[ShipCity].[#Headers]"）输入范围引用。  <br/> |
|RangeRequestAreaExceeded  <br/> |所请求范围的区域超过 1,000,000 个单元格。  <br/> |所请求的范围超出了 1,000,000 个单元格的限制。  <br/> |要返回包含 1,000,000 个以上单元格的范围，请使用多个调用。  <br/> |
|RetryError  <br/> |Excel Services 无法处理该请求。  <br/> |Excel Services 有时可能会进入资源不足的状态。在这种情况下，它可能会开始拒绝请求。  <br/> |等待几分钟，然后再次尝试执行此操作。  <br/> |
|SaveFailed  <br/> |保存该文件时出错。  <br/> |调用 **GetWorkbook** 方法失败。 <br/> |请再次尝试保存该文件。  <br/> |
|SetRangeFailure  <br/> |所请求的操作试图覆盖无法编辑的单元格的内容。  <br/> |调用者试图向包含受保护单元格的范围写入值。例如，单元格包含公式。  <br/> |Excel Services 只能编辑空单元格或包含可编辑值的单元格。  <br/> |
|SheetRangeMismatch  <br/> |作为工作表参数提供的工作表与范围参数中指定的工作表不同。  <br/> |针对  _sheetName_ 参数传递的工作表的名称与 _rangeName_ 参数中指定的工作表位置相匹配。 <br/> |当在范围和工作表参数中指定工作表时，确保工作表名称相同。例如  `Calculate(Sheet1, Sheet1!Range("A1"))`。  <br/> |
|SpecifiedRangeNotFound  <br/> |工作表中不存在请求的范围。  <br/> |传递到具有 A1 后缀的方法（ **SetCellA1**、 **SetRangeA1**、 **GetCellA1** 和 **GetRangeA1**）的范围未找到。  <br/> |确保指定的范围存在于工作表中。  <br/> |
|WorkbookNotSupported  <br/> |无法打开选定的文件，因为它包含 Excel Services 不支持的功能。在工作簿中找到一个或多个不受支持的功能：  <br/> {0}  <br/> |工作簿中包含不支持的功能。  <br/> 0 = 不受支持的功能名称的 \\n 分隔列表。  <br/> |请确保工作簿不包含 Excel Services 不支持的功能。  <br/> |
   

## 另请参阅


#### 任务


  
    
    
 [如何：使用 SubCode 属性捕获错误代码](how-to-use-the-subcode-property-to-capture-error-codes.md)
#### 概念


  
    
    
 [Excel Services 警告](excel-services-alerts.md)
  
    
    
 [Excel Services 已知问题和提示](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services 最佳实践](excel-services-best-practices.md)
