---
title: 扩展 Word Automation Services 中固定格式的导出功能
ms.prod: SHAREPOINT
ms.assetid: d8375505-432e-438e-971b-221a1d9bb601
---


# 扩展 Word Automation Services 中固定格式的导出功能
扩展 Microsoft Office 2013 中的 Word Automation Services 以替换固定格式的导出功能使用的库。
## Word 文件转换服务固定格式的导出功能简介

本文介绍如何扩展 Word Automation Services 的固定格式的导出功能以使用不同的固定格式的导出 DLL，以便第三方开发人员可以替换 Microsoft 提供的那些库。此机制需要并可扩展 Office 客户端固定格式的扩展性 COM 接口。有关详细信息，请参阅 [扩展 Office 2007 固定格式的导出功能](http://msdn.microsoft.com/zh-cn/library/aa338206%28office.12%29.aspx)。
  
    
    

## 发现

Word Automation Services 允许第三方开发人员替换以下一种或两种受支持的固定格式的输出：
  
    
    

- PDF
    
  
- XPS
    
  
若要替换每种格式，DLL 所在的目录必须与 Word Automation Services 的核心库 (Sword.dll)（安装路径：<<安装根目录>>\\WebServices\\ConversionService\\Bin\\Converter\\）的目录相同，且必须具有表 1 中指定的特定文件名。
  
    
    

**表 1. 固定格式的导出 DLL 的文件名**


|**格式**|**文件名**|
|:-----|:-----|
|PDF  <br/> |Renderpdf.dll  <br/> |
|XPS  <br/> |Renderxps.dll  <br/> |
   

## 初始化

DLL 必须导出一个带有以下签名的方法。
  
    
    

```

HRESULT HrGetDocExporter (
IMsoDocExporter **ppimde,
IMsoServerFileManagerSite *psfms,
PFNKeepAlive pfnKeepAlive
)
```

该函数需要 DLL 提供两个接口和一个方法指针，如下节所述。
  
    
    
如果该函数返回失败，则该服务不会回到 Microsoft 提供的导出程序。相反，该服务将报告转换已失败。
  
    
    

## IMsoDocExporter

 **IMsoDocExporter** 接口与编档在 MSDN 上的现有接口相同。有关详细信息，请参阅 [扩展 Office 2007 固定格式的导出功能](http://msdn.microsoft.com/zh-cn/library/aa338206%28office.12%29.aspx)。在上述方法成功返回后，此接口将执行转换。
  
    
    
除了上述文章介绍的要求外，固定格式的导出 DLL 的开发人员还必须注意该服务可以在不同于该服务在其上调用了 **HrGetDocExporter** 的线程的线程上调用提供的 **IMsoDocExporter**。DLL 必须能够处理此操作，而不会将该调用封送回调用 **HrGetDocExporter** 的线程中，因为该服务不会运行消息泵且封送的调用将无法完成（导致挂起和后续失败）。
  
    
    

## IMsoServerFileManagerSite

IMsoServerFileManagerSite 接口定义如下。
  
    
    

```

#undef  INTERFACE
#define INTERFACE  IMsoServerFileManagerSite
DECLARE_INTERFACE(IMsoServerFileManagerSite)
{
STDMETHOD_(BOOL, FGetHandle) (const WCHAR *pwzFileName, HANDLE *phFile, BOOL fRead, BOOL fWrite) PURE;
STDMETHOD_(BOOL, FCloseHandle) (HANDLE hFile) PURE;
};
```

此接口将公开以下方法。
  
    
    

**表 2. IMsoServerFileManagerSite 接口公开的方法**

|||
|:-----|:-----|
|方法  <br/> |说明  <br/> |
|**FGetHandle** <br/> |获取文件句柄。  <br/> |
|**FCloseHandle** <br/> |释放文件句柄。  <br/> |
   
此接口不是继承自 **IUnknown**。因此，允许固定格式的导出 DLL 在生命周期内保留对此该接口的引用。
  
    
    

### FGetHandle

固定格式的导出 DLL 调用此函数可获取要写入的文件句柄。不要尝试通过任何其他机制来打开文件，因为该服务在严格受限的环境中运行，不能访问文件系统中的大多数位置。
  
    
    

```

BOOL FGetHandle (
const WCHAR *pwzFile,
HANDLE *phFile,
BOOL fRead,
BOOL fWrite
)
```


**表 3. FGetHandle 参数**

|||
|:-----|:-----|
|参数  <br/> |说明  <br/> |
|**pwzFile** <br/> |指定固定格式的导出 DLL 要打开的文件的名称。不能是完整的文件路径，只能指定文件名（如 Output.pdf）。  <br/> |
|**phFile** <br/> |指定指定文件的句柄（如果该文件成功打开）。固定格式的导出 DLL 即可在正常文件操作中使用此句柄，直到通过调用 **FCloseHandle** 方法将其关闭为止。 <br/> |
|**fRead** <br/> |指定是否用读取权限打开文件。  <br/> |
|**fWrite** <br/> |指定是否用写入权限打开文件。此函数返回 TRUE 表示成功；返回 FALSE 表示失败。  <br/> |
   

### FCloseHandle

固定格式的导出 DLL 调用此函数可关闭通过调用 **FGetHandle** 方法获得的文件句柄。
  
    
    

```

BOOL FCloseHandle (
HANDLE phFile,
)
```

 *phFile*  参数指定要关闭的文件的句柄。如果此方法返回的值为 0，则表示操作失败。其他值均表示成功。
  
    
    

## PFNKeepAlive

当固定格式的导出 DLL 处于活动状态时，它必须定期调用 **KeepAlive** 函数（由管理员配置）以防止服务假定该固定格式的导出 DLL 挂起以及终止进程。
  
    
    
 `typedef void (*PFNKeepAlive)(void)`
  
    
    

## 其他资源
<a name="bk_addresources"> </a>

有关详细信息，请参阅以下资源：
  
    
    

-  [扩展 Office 2007 固定格式的导出功能](http://msdn.microsoft.com/zh-cn/library/office/aa338206%28v=office.12%29.aspx)
    
  

