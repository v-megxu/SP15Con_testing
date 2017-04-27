---
title: 方法 SharePoint 2013 でバイナリ ラージ オブジェクト (BLOB) をクロールする
ms.prod: SHAREPOINT
ms.assetid: 99b3dd51-1651-4300-a2de-33681f4cc258
---


# 方法: SharePoint 2013 でバイナリ ラージ オブジェクト (BLOB) をクロールする
データベース BCS インデックス コネクタの BDC モデル ファイルを編集して SharePoint 2013 の検索 クローラーを有効化し、SQL Server データベースに格納されているバイナリ ラージ オブジェクト (BLOB) データをクロールする方法を確認します。
## BLOB データのクロール
<a name="HowToCrawlBlobs_CrawlingBlobData"> </a>

Business Data Connectivity (BDC) Service では、外部システムからの BLOB データのストリーミングに便利な BLOB データ型の読み取りをサポートします。BLOB データ型の読み取りを使用するには、外部データを含むデータベース テーブルが BLOB データ型をサポートするように設定する必要があります。次に、外部コンテンツ ソースの BCS インデックス コネクタの BDC モデル ファイルに **StreamAccessor** メソッドを追加します。
  
    
    

## BLOB データの SQL Server データベース テーブルの構成
<a name="HowToCrawlBlobs_ConfiguringSQL"> </a>

Microsoft SQL Server データベース テーブルには、BLOB データの拡張子または MIME タイプのどちらかを指定する列が必要です。データベース テーブル スキーマにこの情報を含む列がない場合は、スキーマに追加する必要があります。以下の表は、この列を含むデータベース テーブル スキーマのサンプルと、データベース テーブルに格納されるサンプルの値を示しています。
  
    
    

**表 1. データベース テーブル スキーマのサンプル**


|**列の名前**|**データ型**|
|:-----|:-----|
|Id  <br/> |Int  <br/> |
|DisplayName  <br/> |nvarchar(50)  <br/> |
|拡張子  <br/> |nvarchar(50)  <br/> |
|データ  <br/> |varbinary(MAX)  <br/> |
|ContentType  <br/> |nvarchar(MAX)  <br/> |
   

**表 2. データベース テーブル値のサンプル**


|**Id**|**表示名**|**拡張子**|**データ**|**コンテンツの種類**|
|:-----|:-----|:-----|:-----|:-----|
|1  <br/> |File1  <br/> |.docx  <br/> |0x504B…  <br/> |application/vnd.openxmlformats-officedocument.wordprocessingml.document  <br/> |
|2  <br/> |File2  <br/> |.doc  <br/> |0xD…  <br/> |application/msword  <br/> |
|3  <br/> |File3  <br/> |.txt  <br/> |OxE…  <br/> |text/plain  <br/> |
   

## BDC モデル ファイルを編集して BLOB データのクロールを有効にする
<a name="HowToCrawlBlobs_BDCModelFile"> </a>

データベース テーブルに BLOB データの拡張子または MIME タイプ情報が含まれていることを確認したら、Microsoft SharePoint Designer を使用して、BLOB データを含むテーブルに基づく外部コンテンツ タイプを作成できます。その後、すべての操作を作成できます。詳細については、「 [[方法] 外部コンテンツ タイプを作成する](http://msdn.microsoft.com/library/811b458c-e209-46df-ba02-8db02bc658db%28Office.15%29.aspx)」と「 [[方法] SQL Server テーブルに基づく外部コンテンツ タイプを作成する](http://msdn.microsoft.com/library/5c42a679-d71d-46c6-aabc-d63c6cad3846%28Office.15%29.aspx)」を参照してください。 
  
    
    
BLOB 外部コンテンツ タイプを作成したら、クロールを有効にするために BDC モデル ファイルを変更する準備が整います。SharePoint Designer ではこのような変更を行うことはできません。そのため、BDC モデル ファイルをエクスポートし、XML エディターを使用して手動で変更する必要があります。
  
    
    

### BLOB 外部コンテンツ タイプの BDC モデル ファイルをエクスポートするには


1. SharePoint Designer の左側のナビゲーションで [ **外部コンテンツ タイプ**] をクリックして、そのサイトのサービス アプリケーションの BDC メタデータ ストアに定義されている外部コンテンツ タイプを表示します。
    
  
2. [ **外部コンテンツ タイプ**] リストで、BLOB 外部コンテンツ タイプを選択します。次に、サーバー リボン で [ **BDC モデルのエクスポート**] をクリックします。
    
  
3. [ **BDC モデル名**] テキスト ボックスに名前を入力し、次に [ **OK**] をクリックします。
    
  
4. BDC モデル (.bdcm) ファイルを保存する場所を選択し、[ **保存**] をクリックします。
    
  

### BLOB 外部コンテンツ タイプのクロールを有効にするには


1. XML エディターで、前のセクションで作成した BDC モデル ファイルを開きます。
    
  
2. BLOB フィールドを返す新しいメソッドを作成します。以下の例に示すように、このメソッドに対して **StreamAccessor** 型のメソッド インスタンスを定義する必要があります。
    
    > **メモ**
      > この例のテーブル名は Attachment です。 

  ```XML
  
<Method Name="GetData">
  <Properties>
    <Property Name="RdbCommandText" Type="System.String">SELECT Data FROM [dbo].[Attachment] WHERE [Id] = @Id </Property>
    <Property Name="RdbCommandType" Type="System.Data.CommandType, System.Data, Version=2.0.0.0, Culture=neutral, 
      PublicKeyToken=b77a5c561934e089">Text</Property>
  </Properties>
  <Parameters>
    <Parameter Direction="In" Name="@Id">
      <TypeDescriptor TypeName="System.Int32" IdentifierName="Id" Name="Id" />
    </Parameter>
    <Parameter Name="StreamData" Direction="Return">
      <TypeDescriptor TypeName="System.Data.IDataReader, System.Data, 
        Version=2.0.3600.0, Culture=neutral, 
        PublicKeyToken=b77a5c561934e089" 
        IsCollection="true" Name="DataReaderTypeDescriptorName">
        <TypeDescriptors>
          <TypeDescriptor TypeName="System.Data.IDataRecord, System.Data, 
            Version=2.0.3600.0, 
            Culture=neutral, 
            PublicKeyToken=b77a5c561934e089" 
            Name="DataRecordTypeDescriptorName">
            <TypeDescriptors>
              <TypeDescriptor TypeName="System.Data.SqlTypes.SqlBytes, System.Data, 
                Version=2.0.3600.0, 
                Culture=neutral, 
                PublicKeyToken=b77a5c561934e089" Name="Data" />
            </TypeDescriptors>
          </TypeDescriptor>
        </TypeDescriptors>
      </TypeDescriptor>
     </Parameter>
    </Parameters>
  <MethodInstances>
    <MethodInstance Name="DataAccessor" 
      Type="StreamAccessor" 
      ReturnParameterName="StreamData" 
      ReturnTypeDescriptorName="Data">
      <Properties>
<!-- If extension field is available-->
        <Property Name="Extension" Type="System.String">Extension</Property>
<!--If MimeType is available-->
        <Property Name="ContentType" Type="System.String">ContentType</Property>
<!--If attachments is to be displayed in profile pages, add the following property-->
        <Property Name="MimeTypeField" Type="System.String">ContentType</Property>
      </Properties>
    </MethodInstance>
  </MethodInstances>
</Method>
  ```


    すべての BLOB の MIME タイプが同じ場合は、前の例のコード行 
  
    
    
 `<Property Name="ContentType" Type="System.String">ContentType</Property>`
  
    
    
 を、このコード行
  
    
    
 `<Property Name=" ContentType " Type="System.String">application/vnd.openxmlformats-officedocument.wordprocessingml.document</Property>` に置き換えることができます。
    
  
3. Business Connectivity Services サービス アプリケーションの管理 UI を使用して、モデル ファイルを再インポートします。 
    
  
4. 外部コンテンツ タイプのコンテンツ ソースを作成します。
    
  
5. コンテンツ ソースのフル クロールを開始します。 
    
  

## その他の技術情報
<a name="SP15Crawlblobs_addlresources"> </a>


-  [SharePoint 2013 の検索コネクタ フレームワーク](search-connector-framework-in-sharepoint-2013.md)
    
  
-  [[方法] 外部コンテンツ タイプを作成する](http://msdn.microsoft.com/library/811b458c-e209-46df-ba02-8db02bc658db%28Office.15%29.aspx)
    
  
-  [XML スニペット: StreamAccessor メソッドのモデリング](http://msdn.microsoft.com/library/bd60cc2e-f7f6-421c-9d2a-60e8512b9893%28Office.15%29.aspx)
    
  

