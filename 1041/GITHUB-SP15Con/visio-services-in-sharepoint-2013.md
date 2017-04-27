---
title: SharePoint 2013 の Visio Services
ms.prod: SHAREPOINT
ms.assetid: ed8c5d12-e17d-4ceb-b195-601c26824370
---



# SharePoint 2013 の Visio Services
Visio Services in Microsoft SharePoint Server 2013 を使用すると、Microsoft SharePoint Server 2013 と Microsoft SharePoint Online のVisio .vsdx, .vsdm ファイル、および Visio Web 図面 (.vdw) を、プログラミングにより読み込み、表示、あるいは操作できます。
## SharePoint Server 2013 の Visio Services の新機能
<a name="visserv15_WhatsNew"> </a>

Visio Services in Microsoft SharePoint Server 2013 およびMicrosoft SharePoint Online の Visio Services には、新しい Microsoft Visio 2013 ファイル形式のサポート、Microsoft Business Connectivity Services (BCS) データソースのサポート、およびプログラミングによるコメントへのアクセスなど、新しい機能がいくつか追加されています。
  
    
    

### 新しいファイル形式
<a name="vis15_WhatsNew_NewFF"> </a>


|||
|:-----|:-----|
|![クラウドの中の動作の注意事項](images/mod_icon_incloud.gif)           <br/>![社内設置型の動作の注意事項](images/mod_icon_onpremises.gif)|Visio 2013では、Open Packaging Conventions (OPC) 標準 (ISO 29500, Part 2) と以前の Visio XML ファイル形式 (.vdx) の XML 要素に基づいて、新しいファイル形式 (.vsdx) がサポートされます。zip された、この XML ベースのファイル形式は、他の アプリケーションで使用されるファイル形式に似ています。  <br/> この新しいファイル形式を使用すると、Visio Web 図面 (.vdw) としてファイルを公開せずに、Visio 2013 図面を直接 SharePoint Server または SharePoint Online ライブラリに保存できます。このような場合でも、Visio Services は、Visio Web 図面ファイルの読み込みと表示が可能です。  <br/> Visio Services では、ブラウザーで Visio Web 図面 (.vdw) 形式のファイルを表示できます。また、新しいファイル形式の Visio 図面 (.vsdx) と Visio マクロ対応図面 (.vsdm) 形式を表示できるようになりました。  <br/> Visio Services の ECMAScript (JavaScript, JScript) オブジェクト モデルには、新しいファイル形式  [Vwa.VwaControl.getDiagramFileType 方法](http://msdn.microsoft.com/library/fd8ca95f-a3be-4000-bce8-3aaf1f48148c%28Office.15%29.aspx) をサポートする新しい API が追加されています。 [Vwa.DiagramFileType 列挙](http://msdn.microsoft.com/library/dd2f8a5d-a54b-44bd-a458-02efdcba0201%28Office.15%29.aspx) から返された値は、Visio Web Access Web パーツに表示されたファイルが Visio 図面 (.vsdx) または Visio Web 図面 (.vdw) のいずれであるかを示します。 <br/> Visio 2013の新しいファイル形式の詳細については、「 [Visio ファイル形式 (.vsdx) の概要](http://msdn.microsoft.com/library/69736f40-8f67-46c2-abf6-82dffecb2274%28Office.15%29.aspx)」を参照してください。  <br/> > **メモ**> Visio の新しいファイル (.vsdx および .vsdm) を表示できるのは、Visio Services のラスター形式のみです。Visio Web Drawings (.vdw) は、引き続き Silverlight で表示できます。           |
   

### Business Connectivity Services (BCS) データのサポート
<a name="vis15_WhatsNew_BCS"> </a>


|||
|:-----|:-----|
|![クラウドの中の動作の注意事項](images/mod_icon_incloud.gif)           <br/>![社内設置型の動作の注意事項](images/mod_icon_onpremises.gif)|Visio 2013 の図は、SharePoint Server 2013 サーバー上の Microsoft Business Connectivity Services (BCS) および SharePoint Online で作成された外部リストに接続できるようなりました。Visio Services では、データ更新で Visio の図を更新することができます。  <br/> > **メモ**> Visio Services では、SQL、SQL Azure、OLEDC、ODBC、およびカスタム データ プロバイダーを SharePoint Online のデータ ソースにすることはできません。           |
   

### コメント作成
<a name="vis15_WhatsNew_Commenting"> </a>


|||
|:-----|:-----|
|![クラウドの中の動作の注意事項](images/mod_icon_incloud.gif)           <br/>![社内設置型の動作の注意事項](images/mod_icon_onpremises.gif)|Visio 2013 には、コメント作成フレームワークが新しく追加されています。コメントは、特定の図形またはページに関係付けることができます。Visio Services には、図からコメントを取得できる JavaScript API が備わっています。  <br/> Visio ServicesJavaScript オブジェクト モデルのコメント作成 API について詳しくは、トピック「 [VwaPage.getPageComments 方法](http://msdn.microsoft.com/library/d1e7740c-e0fa-4823-b2b6-14551bb84c36%28Office.15%29.aspx)」と「 [VwaShape.getComments 方法](http://msdn.microsoft.com/library/fcdec9c2-a503-4315-b048-033cd5ac09dd%28Office.15%29.aspx)」をご覧ください。  <br/> |
   

### 拡張された再計算機能
<a name="vis15_WhatsNew_Commenting"> </a>


|||
|:-----|:-----|
|![クラウドの中の動作の注意事項](images/mod_icon_incloud.gif)           <br/>![社内設置型の動作の注意事項](images/mod_icon_onpremises.gif)|Visio Services では、ShapeSheet で数式を再計算できるようになりました。Data Graphics の更新に加え、Visio Services は、データとデータに基づく画像ですべての図形を更新できます。ShapeSheet のほとんどの関数は、再計算でサポートされます。  <br/> |
   

### エラー処理の改善
<a name="vis15_WhatsNew_Commenting"> </a>


|||
|:-----|:-----|
|![クラウドの中の動作の注意事項](images/mod_icon_incloud.gif)           <br/>![社内設置型の動作の注意事項](images/mod_icon_onpremises.gif)|Visio Servicesに表示した Visio 図面にデータの更新エラーが発生した場合、画面は図の静止画像に戻されるようになりました。Visio Servicesでは、対処方法を提示するエラー メッセージの数も増えています。  <br/> |
   

### 安全なストア認証
<a name="vis15_WhatsNew_Commenting"> </a>


|||
|:-----|:-----|
|![クラウドの中の動作の注意事項](images/mod_icon_incloud.gif)           <br/>![社内設置型の動作の注意事項](images/mod_icon_onpremises.gif)|以前は、外部のデータ ソース (SQL データベースなど) の認証設定は、Microsoft Excel のユーティリティを使用する以外に構成できませんでしたが、Visio 2013 では、Visio のクライアントから直接、図に接続されたデータを構成することができるようになりました。これにより、データ ソースを Visio Services で更新できます。  <br/> |
   

## Visio Services JavaScript オブジェクト モデル
<a name="visserv15_JSOM"> </a>


|||
|:-----|:-----|
|![クラウドの中の動作の注意事項](images/mod_icon_incloud.gif)           <br/>![社内設置型の動作の注意事項](images/mod_icon_onpremises.gif)|Visio Services の JavaScript オブジェクト モデルの  [Vwa 名前空間](http://msdn.microsoft.com/library/b67939fa-d3db-41ff-8864-eabd318ba7c4%28Office.15%29.aspx) を使用して、Visio Web Access Web Part に表示された Visio の図面へのアクセスをプログラムで行うことができます。JavaScript オブジェクト モデルを使用して、図、ページ、図形、図形のハイパーリンク、および図形の境界ボックスのプロパティに関するデータにアクセスすることができます。このアクセスにより、図形を強調するマッシュアップの作成、図へのオーバーレイの配置、図およびマウス イベントへの応答、およびビューポートのパンニングとズーミングのプロパティの変更などを行えます。 <br/> SharePoint ページへの Visio Web Access Web パーツの追加および Visio 2013の JavaScript API を使用したページのプログラミングの詳細については、「 [Visio Web Access Web パーツの Visio Web 図面のカスタマイズ](http://msdn.microsoft.com/ja-jp/library/ff394649.aspx)」を参照してください。  <br/> |
   

## Visio Services クラス ライブラリ
<a name="visserv15_Mref"> </a>


|||
|:-----|:-----|
|![社内設置型の動作の注意事項](images/mod_icon_onpremises.gif)| [Microsoft.Office.Visio.Server](https://msdn.microsoft.com/library/Microsoft.Office.Visio.Server.aspx) 名前空間で、Visio Services クラス ライブラリを使用して、カスタムの Visio Services データ プロバイダーを作成することができます。これらのデータ プロバイダーを使用して、SharePoint Server 2013 上でホストされた Visio 2013 の図のカスタム データ ソースのデータの更新をプログラムで行うことができます。 <br/> カスタム データ プロバイダーの作成と完全なエンドツーエンド ソリューションの操作の詳細については、「 [Visio Services でのカスタム データ プロバイダーの作成](http://msdn.microsoft.com/ja-jp/library/ff394595.aspx)」を参照してください。  <br/> |
   

## その他の技術情報
<a name="visserv15_Additional"> </a>


-  [Microsoft.Office.Visio.Server](https://msdn.microsoft.com/library/Microsoft.Office.Visio.Server.aspx)
    
  
-  [Vwa 名前空間](http://msdn.microsoft.com/library/b67939fa-d3db-41ff-8864-eabd318ba7c4%28Office.15%29.aspx)
    
  
-  [Visio Services でのカスタム データ プロバイダーの作成](http://msdn.microsoft.com/ja-jp/library/ff394595.aspx)
    
  
-  [Visio Web Access Web パーツの Visio Web 図面のカスタマイズ](http://msdn.microsoft.com/ja-jp/library/ff394649.aspx)
    
  
-  [開発者向け Visio の新機能](http://msdn.microsoft.com/library/7e3fb858-0ab8-bd2e-217c-c85b10d79785%28Office.15%29.aspx)
    
  
- エンド ユーザー向けの Visio 2013 プレビューの詳細については、「 [Visio の新機能](http://office.microsoft.com/ja-jp/HA102749364.aspx)」を参照してください。
    
  
