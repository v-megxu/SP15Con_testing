---
title: Word Automation Services の固定形式エクスポート機能の拡張
ms.prod: SHAREPOINT
ms.assetid: d8375505-432e-438e-971b-221a1d9bb601
---


# Word Automation Services の固定形式エクスポート機能の拡張
Microsoft Office 2013 の Word Automation Services を拡張し、固定形式エクスポート機能で使用されるライブラリを置き換えます。
## Word ファイル変換サービスの固定形式エクスポート機能の概要

この記事では、Microsoft から提供される固定形式エクスポート DLL をサードパーティの開発者が置き換えられるように、Word Automation Services の固定形式エクスポート機能を拡張して別の固定形式エクスポート DLL を使用する方法を説明します。これを行うには、Office クライアント固定形式拡張 COM インターフェイスを拡張する必要があります。詳細については、「 [Office (2007) 固定形式エクスポート機能の拡張](http://msdn.microsoft.com/ja-jp/library/aa338206%28office.12%29.aspx)」を参照してください。
  
    
    

## 検出

Word Automation Services を使用すると、サードパーティの開発者はサポートされている次の固定形式の出力のどちらかまたは両方を置き換えることができます。
  
    
    

- PDF
    
  
- XPS
    
  
それぞれの形式を置き換えるには、Word Automation Services のコア ライブラリ (Sword.dll) と同じディレクトリに DLL を配置し (インストール パス: <<インストール ルート>>\\WebServices\\ConversionService\\Bin\\Converter\\)、表 1 に示す特定の名前を DLL に付ける必要があります。
  
    
    

**表 1. 固定形式エクスポート DLL のファイル名**


|**形式**|**ファイル名**|
|:-----|:-----|
|PDF  <br/> |Renderpdf.dll  <br/> |
|XPS  <br/> |Renderxps.dll  <br/> |
   

## 初期化

DLL は、次のシグネチャが付いたメソッドをエクスポートする必要があります。
  
    
    

```

HRESULT HrGetDocExporter (
IMsoDocExporter **ppimde,
IMsoServerFileManagerSite *psfms,
PFNKeepAlive pfnKeepAlive
)
```

この関数は、以下のセクションで説明する 2 つのインターフェイスとメソッド ポインターを提供することを DLL に要求します。
  
    
    
関数の呼び出しが失敗した場合、サービスは Microsoft が提供するエクスポーターにフォールバックしません。代わりに、サービスは変換の失敗を報告します。
  
    
    

## IMsoDocExporter

 **IMsoDocExporter** インターフェイスは、MSDN に掲載されている既存のインターフェイスと同じものです。詳細については、「 [Office (2007) 固定形式エクスポート機能の拡張](http://msdn.microsoft.com/ja-jp/library/aa338206%28office.12%29.aspx)」を参照してください。前のメソッドの呼び出しが成功すると、このインターフェイスは変換を実行します。
  
    
    
前述の記事に示されている要件のほかに、固定形式エクスポート DLL の開発者は、サービスが **HrGetDocExporter** を呼び出したスレッドとは別のスレッド上の提供された **IMsoDocExporter** を呼び出せることを認識しておく必要があります。DLL は、 **HrGetDocExporter** を呼び出した元のスレッドに呼び出しをマーシャリングすることなくこれを処理する必要があります。サービスはメッセージ ポンプを実行せず、マーシャリングされた呼び出しは届かないからです (ハングした後、失敗に終わります)。
  
    
    

## IMsoServerFileManagerSite

IMsoServerFileManagerSite インターフェイスは次のように定義されます。
  
    
    

```

#undef  INTERFACE
#define INTERFACE  IMsoServerFileManagerSite
DECLARE_INTERFACE(IMsoServerFileManagerSite)
{
STDMETHOD_(BOOL, FGetHandle) (const WCHAR *pwzFileName, HANDLE *phFile, BOOL fRead, BOOL fWrite) PURE;
STDMETHOD_(BOOL, FCloseHandle) (HANDLE hFile) PURE;
};
```

このインターフェイスは次のメソッドを公開します。
  
    
    

**表 2. IMsoServerFileManagerSite インターフェイスが公開するメソッド**

|||
|:-----|:-----|
|メソッド  <br/> |説明  <br/> |
|**FGetHandle** <br/> |ファイル ハンドルを取得します。  <br/> |
|**FCloseHandle** <br/> |ファイル ハンドルを解放します。  <br/> |
   
このインターフェイスは **IUnknown** を継承しません。したがって、固定形式エクスポート DLL は存続期間中、このインターフェイスへの参照を保持できます。
  
    
    

### FGetHandle

固定形式エクスポート DLL はこの関数を呼び出して、書き込み先のファイル ハンドルを取得します。これ以外の方法でファイルを開くことはできません。サービスは、ファイル システムのほとんどの場所にアクセスできないきわめて制限された環境で実行されるからです。
  
    
    

```

BOOL FGetHandle (
const WCHAR *pwzFile,
HANDLE *phFile,
BOOL fRead,
BOOL fWrite
)
```


**表 3. FGetHandle のパラメーター**

|||
|:-----|:-----|
|パラメーター  <br/> |説明  <br/> |
|**pwzFile** <br/> |固定形式エクスポート DLL が開くファイルの名前を指定します。完全なファイル パスではなく、ファイル名のみを指定する必要があります (例: Output.pdf)。  <br/> |
|**phFile** <br/> |ファイルが正常に開いた場合に、指定したファイルのハンドルを指定します。これにより、固定形式エクスポート DLL は **FCloseHandle** メソッドを呼び出してファイルを閉じるまで、この HANDLE を通常のファイル操作で使用できるようになります。 <br/> |
|**fRead** <br/> |ファイルを読み取りアクセス権付きで開くかどうかを指定します。  <br/> |
|**fWrite** <br/> |ファイルを書き込みアクセス権付きで開くかどうかを指定します。成功した場合は TRUE が返り、失敗した場合は FALSE が返ります。  <br/> |
   

### FCloseHandle

固定形式エクスポート DLL はこの関数を呼び出して、 **FGetHandle** メソッドの呼び出しによって取得したファイル ハンドルを閉じます。
  
    
    

```

BOOL FCloseHandle (
HANDLE phFile,
)
```

phFile パラメーターは、閉じるファイルのハンドルを指定します。このメソッドによって返された値が 0 の場合、処理は失敗です。それ以外の値の場合は成功です。
  
    
    

## PFNKeepAlive

固定形式エクスポート DLL がアクティブなときは、この DLL がハングしているとサービスが判断してプロセスを終了することがないように、 **KeepAlive** 関数を (管理者が構成する) 一定の間隔で呼び出す必要があります。
  
    
    
 `typedef void (*PFNKeepAlive)(void)`
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>

詳細については、次の資料を参照してください。
  
    
    

-  [Office (2007) 固定形式エクスポート機能の拡張](http://msdn.microsoft.com/ja-jp/library/office/aa338206%28v=office.12%29.aspx)
    
  

