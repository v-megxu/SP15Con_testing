---
title: VSS を使用して SharePoint 2013 で検索サービス アプリケーションをバックアップおよび復元する方法
ms.prod: SHAREPOINT
ms.assetid: 87ee28e6-8170-4dba-8c9d-f04ab9e632dc
---


# VSS を使用して SharePoint 2013 で検索サービス アプリケーションをバックアップおよび復元する方法
 **概要:** ボリューム シャドウ コピー サービス (VSS) を使用して、SharePoint 2013 で検索サービス アプリケーションのバックアップと復元を行う方法について説明します。
## ボリューム シャドウ コピー サービスを使用して SharePoint のバックアップと復元を行うための前提条件

SharePoint 2013 のバックアップおよび復元ソリューションをプログラミングするには、VSS の機能と SharePoint と VSS のインターフェイスについて理解する必要があります。
  
    
    

**表 2. ボリューム シャドウ コピー サービスを使用して SharePoint のバックアップと復元を行うための中心概念**


|**記事**|**説明**|
|:-----|:-----|
| [ボリューム シャドウ コピー サービス](http://msdn.microsoft.com/ja-jp/library/windows/desktop/bb968832%28v=vs.85%29.aspx)とその下位の記事。  <br/> |VSS とそのプログラミング方法について説明します。  <br/> |
| [Windows SharePoint Services およびボリューム シャドウ コピー サービス](http://msdn.microsoft.com/library/adae101a-078e-40b9-9cfa-db2cfb10270a%28Office.15%29.aspx)とその下位の記事。  <br/> |VSS と SharePoint の VSS とのインターフェイスを使用した SharePoint 2013 データのバックアップと復元に関する、概要およびステップバイステップの手順。  <br/> |
   

## ボリューム シャドウ コピー サービスを使用した検索サービス アプリケーションのバックアップと復元
<a name="Use"> </a>

次の手順は、VSS を使用するバックアップ/復元アプリケーションを作成する開発者を対象としています。IT 担当者の方で、SharePoint 2013 検索サービス アプリケーションのバックアップ方法または復元方法の手順をお探しの場合は、「 [SharePoint 2013 のバックアップと復旧](http://technet.microsoft.com/ja-jp/library/ee662536.aspx)」を参照してください。 
  
    
    
 **前提条件:** [Microsoft Windows SDK for Windows 7 と .NET Framework 4](http://www.microsoft.com/en-us/download/details.aspx?id=8279) をダウンロードして、検索サービス アプリケーション (SSA) を使用するサーバーと検索インデックス コンポーネントを使用する各サーバーにインストールします。特に vshadow.exe と betest.exe を `C:\\Program Files\\Microsoft SDKs\\Windows\\v7.1\\Bin\\x64\\vsstools` にインストールします。
  
    
    

> **ヒント**
> この記事に記載されている Windows PowerShell コマンドレットの詳細については、「 [SharePoint 2013 リファレンスの Windows PowerShell](http://technet.microsoft.com/ja-jp/library/ee890108.aspx)」を参照してください。 
  
    
    


### SharePoint VSS Writer を登録し、サーバーのバックアップと復元を準備するには


- 次のいずれかの方法で SharePoint VSS Writer を登録します。
    
  - [ **管理ツール**] で [ **サービス**] を開き、 **SharePoint VSS Writer** サービスを開始します。
    
  
  - コマンド コンソールを開き、 `stsadm.exe -o registerwsswriter` を実行します。stsadm ユーティリティは %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\BIN にあります。[ **管理ツール**] の [ **サービス**] でサービスが実行されていることを確認します。
    
  

### VSS を使用して SharePoint 検索サービス アプリケーションをバックアップするには


1. インデックス コンポーネントを含む各サーバーと、検索データベースがある SQL Server を実行するコンピューターの両方で、コマンド ラインから  `vshadow.exe -wm > writers.txt` を実行して VSS メタデータを取得します。作成される writers.txt ファイルには、サーバーに関連付けられたすべての VSS Writer が出力されます。
    
  
2. 次の手順に従い、検索データベースがある SQL Server を実行するコンピューターで、SSA のマニフェストを作成します。
    
1. XML ファイルを作成し、そのファイルに以下をコピーします。 
    
  ```XML
  
<BETest>
  <Writer writerid="SharePoint Services Writer ID">
    <Component logicalPath="PathSSA" componentName="SearchAppOffice" />
    <Component logicalPath="PathC" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="PathA" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="PathL" componentName="SearchAppOffice_LinksStore" />
  </Writer>
  <Writer writerid="SQL Server Writer ID">
    <Component logicalPath="PathDbSSA" componentName="SearchAppOffice" />
    <Component logicalPath="PathDbC" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="PathDbA" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="PathDbL" componentName="SearchAppOffice_LinksStore" />
  </Writer>
</BETest>

  ```

2. このファイルの 10 個のプレースホルダーは、最初の手順で生成した writer.txt の適切な値で置き換えます。次の表をガイドとして使用してください。 
    
    > **メモ**
      > 右側の列の  _SSA_ は、検索サービス アプリケーション名のプレースホルダーです。

   **表 2. writers.txt の SSA マニフェスト ファイルのプレースホルダーと値**


|**プレースホルダー**|**writers.txt 内の記載場所**|
|:-----|:-----|
| _SharePoint Services Writer ID_ <br/> |"SharePoint Services Writer" エントリの下にある WriterId GUID  <br/> |
| _PathSSA_ <br/> |"SharePoint Services Writer" エントリの検索サービス アプリケーション名と共に表示される論理パス エントリ  <br/> |
| _PathC_ <br/> |"SharePoint Services Writer" エントリの " _SSA__CrawlStore" という名前のコンポーネントについて表示される論理パス エントリ  <br/> |
| _PathA_ <br/> |"SharePoint Services Writer" エントリの " _SSA_ _AnalyticsReportingStore" という名前のコンポーネントについて表示される論理パス エントリ <br/> |
| _PathL_ <br/> |"SharePoint Services Writer" エントリの " _SSA__LinksStore" という名前のコンポーネントについて表示される論理パス エントリ  <br/> |
| _SQL Server Writer ID_ <br/> |"SqlServerWriter" エントリ以下に表示される WriterId GUID  <br/> |
| _PathDbSSA_ <br/> |"SqlServerWriter" エントリで、検索サービス アプリケーション名のコンポーネントについて表示される論理パス エントリ  <br/> |
| _PathDbC_ <br/> |"SqlServerWriter" エントリの " _SSA__CrawlStore" という名前のコンポーネントについて表示される論理パス エントリ  <br/> |
| _PathDbA_ <br/> |"SqlServerWriter" エントリの " _SSA__AnalyticsReportingStore" という名前のコンポーネントについて表示される論理パス エントリ  <br/> |
| _PathDbL_ <br/> |"SqlServerWriter" エントリの " _SSA__LinksStore" という名前のコンポーネントについて表示される論理パス エントリ  <br/> |
   

    これは SSA マニフェスト ファイルです。完成した SSA マニフェスト ファイルの例については、 [マニフェスト ファイルの例](#Examples)を参照してください。
    
  
3. 次の手順に従い、検索インデックス ファイルのマニフェストを作成します。インデックス コンポーネントがある各サーバーでこの手順を繰り返してください。
    
1. XML ファイルを作成し、そのファイルに以下をコピーします。
    
  ```XML
  
<BETest>
   <Writer writerid="SharePoint Services Writer ID">
      <Component logicalPath="PathIndex" componentName="NameIndex" />
   </Writer>
   <Writer writerid="OSearch15 Writer ID">
      <Component logicalPath="PathOSearch15" componentName="IndexComponentGroup" />
   </Writer>    
</BETest>
  ```

2. このファイルの 6 個のプレースホルダーは、最初の手順で生成した writer.txt の適切な値で置き換えます。次の表をガイドとして使用してください。
    
   **表 3. writer.txt の検索インデックス マニフェスト ファイルのプレースホルダーと値**


|**プレースホルダー**|**writers.txt の記載場所**|
|:-----|:-----|
| _SharePoint Services Writer ID_ <br/> |"SharePoint Services Writer" エントリの下にある WriterId GUID  <br/> |
| _PathIndex_ <br/> |"SharePoint Services Writer" エントリの "IndexComponentGroup" から始まる名前のコンポーネントについて表示される論理パス エントリ  <br/> |
| _NameIndex_ <br/> |"SharePoint Services Writer" エントリの "IndexComponentGroup" から始まる名前のコンポーネントについて表示される名前エントリ  <br/> |
| _OSearch15 Writer ID_ <br/> |"OSearch15 VSS Writer" エントリの下にある WriterId GUID  <br/> |
| _PathOSearch15_ <br/> |"OSearch15 VSS Writer" エントリの "IndexComponentGroup" から始まる名前のコンポーネントについて表示される論理パス エントリ。通常は空です。  <br/> |
| _IndexComponentGroup_ <br/> |"OSearch15 VSS Writer" エントリの "IndexComponentGroup" から始まる名前のコンポーネントについて表示される名前エントリ  <br/> |
   

    これは検索インデックス マニフェスト ファイルです。完成した検索インデックス マニフェスト ファイルの例については、 [マニフェスト ファイルの例](#Examples)を参照してください。
    
  
4. (省略可能) インデックス コンポーネントが格納されている各サーバーで、 **IndexComponent** フォルダーのサイズをメモします。この情報は、後でバックアップを確認するときに利用できます。
    
  
5. ファーム内の任意のサーバーで、SharePoint 管理シェルを開き、次の行を実行します。ここで、 _name of search service application_ は、バックアップする SSA です。以降、SharePoint 管理シェル ウィンドウは開いたままにします。
    
  ```
  
$ssa = Get-SpenterpriseSearchServiceApplication -Identity "name of search service application"
Suspend-SPEnterpriseSearchServiceApplication -Identity $ssa
  ```

6. 次の手順で、SSA データベースとインデックスのバックアップを実行します。
    
1. SSA データベースがあるサーバーで、コマンド ラインから次のコマンドを実行します。ここで、 _destination backup folder_ は、バックアップ ファイルのフォルダーのフル パスです。 _backup log file_ は、バックアップ ログ ファイルのフル パスと名前です。 _SSA manifest file_ は、SSA マニフェスト ファイルのパスとファイル名です。
    
  ```
  
betest.exe /v /b /d "destination backup folder" /s "backup log file" /x "SSA manifest file"
  ```

2. SharePoint 管理シェル ウィンドウを開いているサーバーで、次の行を実行します。ここで、 _topology file name_ は、トポロジ情報を含むエクスポートしたファイルのフル パスと名前です。このファイルは、SSA の復元手順で使用します。
    
  ```
  Export-SPEnterpriseSearchTopology -SearchApplication $ssa -Filename "topology file name"
  ```

3. ファイルが作成されたことを確認します。
    
  
4. インデックス コンポーネントがある各サーバーで、コマンド ラインから次を実行します。ここで、 _destination backup folder_ は、バックアップ ファイルのフォルダーのフル パスです。 _backup log file_ は、バックアップ ログ ファイルのフル パスと名前です。 _index manifest file_ は、インデックス マニフェストのパスとファイル名です。
    
  ```
  betest.exe /v /b /d "destination backup folder" /s "backup log file" /x "index manifest file"
  ```

5. (省略可能) バックアップされたインデックス フォルダーを確認します。フォルダー名とサイズが、前の手順でメモした情報と一致することを確認します。
    
  

### VSS を使用して SharePoint 検索サービス アプリケーションを復元するには


1. ファーム内の任意のサーバーで、SharePoint 管理シェルを開き、次の行を実行して、既存の検索サービス アプリケーションとそのプロキシを削除します。ここで、 _name of search service application_ は、復元する SSA で、 _name of proxy_ は、そのアプリケーション プロキシです。通常、 _name of SSA proxy_ は、SSA 名の末尾に "Proxy" という語を付けた名前になります。 `RemoveData` スイッチで、検索データベースが削除されることを確認します。
    
  ```
  $ssa = Get-SPEnterpriseSearchServiceApplication -Identity "name of search service application"
Remove-SPEnterpriseSearchServiceApplication -Identity $ssa -RemoveData
Remove-SPEnterpriseSearchServiceApplicationProxy -Identity "name of SSA proxy"
  ```

2. 同じサーバーで、コマンド ラインから次を実行し、SSA データベースを復元します。ここで、 _destination backup folder_ は、バックアップ ファイルのフォルダーのフル パスです。 _backup log file_ は、バックアップ ログ ファイルのフル パスと名前です。 _SSA manifest file_ は、SSA マニフェスト ファイルのパスとファイル名です。
    
  ```
  
betest.exe /v /r /d "destination backup folder" /s "backup log file" /x SSA_manifest_file
  ```

3. 同じサーバーで SharePoint 管理シェルを開き、次の行を実行して SSA を復元します。ここで、 _application pool name_ は、新しいプール名です。 _domain\\user_ は、アプリケーション プールのログインを行うユーザーのドメイン名です。 _name of the search service application_ は、SSA の名前です。 _topology_file_name_ は、SSA のバックアップ時に作成された typology ファイルのパスと名前です。
    
    > **ヒント**
      > このコードで、復元された SSA を実行するための新しいアプリケーション プール ID が作成されますが、 **Get-SPServiceApplicationPool** コマンドレットを実行して既存のアカウントを使用することもできます。

  ```
  $applicationPool = New-SPServiceApplicationPool -name "application pool name" -account "domain\\user"
Restore-SPEnterpriseSearchServiceApplication -Name "name of the search service application" -ApplicationPool $applicationPool -TopologyFile "topology_file_name" -KeepId
  ```

4. 次のコマンドレットを使用して、SSA 用のプロキシを作成します。 _name of the search service application_ と _name of SSA proxy_ には、手順 1 で使用したものと同じ値を使用することをお勧めします。
    
  ```
  
$ssa = Get-SpenterpriseSearchServiceApplication -Identity "name of search service application"
New-SPEnterpriseSearchServiceApplicationProxy -Name "name of SSA proxy" -SearchApplication $ssa
  ```

5. (省略可能) [ **サーバーの全体管理**] を開いて、SSA とそのプロキシが存在することを確認します。[ **サービス アプリケーションの管理**] を選択して、SSA とそのプロキシが表示されることを確認します。
    
  
6. (省略可能) サービス一覧の SSA をクリックし、開いたページで、[ **検索アプリケーションのトポロジ**] の表が、バックアップ手順でエクスポートしたトポロジと一致することを確認します。(また、コマンドレット **Get-SPEnterpriseSearchStatus** を使用してトポロジを確認することもできます)。
    
  
7. **インデックス コンポーネントがあるすべてのサーバー** で、次の手順を実行してインデックス ファイルを復元します。
    
1. **[管理ツール] > [サービス]** を使用するか、次のコマンドレットを SharePoint 管理シェルで実行して、ホスト コントローラー サービスを停止します。
    
  ```
  
stop-service SPSearchHostController
  ```

2. 同じサーバーで、コマンド ラインから次を実行します。ここで、 _index manifest file_ は、バックアップ手順で作成したインデックス マニフェストのパスとファイル名です。
    
  ```
  betest.exe /v /r /d "destination backup folder" /s "backup log file" /x "index manifest file"
  ```

3. (省略可能) フォルダー名とサイズが、バックアップ手順でメモしたものと一致することを確認します。
    
  
4. 各インデックス コンポーネントに対して次の手順を実行し、データ フォルダー以下のデータの名前を変更します。
    
1. SharePoint 管理シェルで、次のコマンドレットを実行します。
    
  ```
  Get-SPEnterpriseSearchVssDataPath
  ```

2. コマンドレットの出力から、各 GUID の最後の部分をメモします。たとえば、ある出力行が  `IndexComponentGroup_e255918b-6ab0-4d7c-8049-720b2744c62f` の場合、720b2744c62f をメモします。
    
  
3. [ **ファイル エクスプローラー**] (Windows Server 2008 では [ **Windows エクスプローラー**]) で、 `C:\\Program Files\\Microsoft Office Servers\\15.0\\Data\\Office Server\\Applications\\Search\\Nodes\\24488A\\IndexComponentN\\storage\\data` に移動します。ここで、 *N*  は、インデックス コンポーネントの番号です。
    
  
4. これらの各フォルダーには、先頭に "SP" が付き、12 桁の 16 進数とバージョン番号が続く名前のサブフォルダーがあります。12 桁の 16 進数が前の手順でメモした GUID の末尾と一致する各サブフォルダーについて、サブフォルダーの名前を importindex に変更します。この例では、サブフォルダー `SP720b2744c62f.1.I.1.0` の名前をimportindex に変更します。
    
  
5. **[管理ツール] > [サービス]** を使用するか、SharePoint 管理シェルで次のコマンドレットを実行して、ホスト コントローラー サービスを再開します。
    
  ```
  start-service SPSearchHostController
  ```

6. インデックス データ フォルダー名が前の名前に戻っていることを確認します (この例では、"SP720b2744c62f.1.I.1.0" です)。
    
  
8. (省略可能) **IndexComponent** フォルダーのサイズが、バックアップ手順でメモしたサイズと一致することを確認します。
    
  
9. SSA を再起動します。
    
  
10. 影響を受けるすべてのサーバーで、SharePoint 管理シェルの次のコマンドレットを実行し、検索アプリケーション サービスが正しく実行されていることを確認します。
    
  ```
  Get-SPEnterpriseSearchStatus
  ```

11. 新しいドキュメントのフィード処理と検索処理が機能していることを確認します。たとえば、クエリ "size>=0" を使用して、インデックスのサイズを確認します。また、新しいドキュメントを追加して、検索できることを確認します。
    
  

## マニフェスト ファイルの例
<a name="Examples"> </a>

 **SSA マニフェスト ファイル**
  
    
    

```XML
<BETest>
  <Writer writerid="da452614-4858-5e53-a512-38aab25c61ad">
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\2e1f9435-d714-4bcb-be8d-ae1214e2ea22" componentName="SearchAppOffice" />
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\b8bb09b8-a823-43b0-a131-7bd5464f91fb" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\20c0c0b5-2086-4b16-8ce8-2cecb5186ebe" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\15004c47-21ca-441e-80fe-9e068ef4ad14" componentName="SearchAppOffice_LinksStore" />
  </Writer>
  <Writer writerid="a65faa63-5ea8-4ebc-9dbd-a0c4db26912a">
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice" />
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice_CrawlStore" />
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice_AnalyticsReportingStore" />
    <Component logicalPath="DDDVSS4\\SQLEXPRESS" componentName="SearchAppOffice_LinksStore" />
  </Writer>
</BETest>

```

 **インデックス マニフェスト ファイル**
  
    
    



```XML

<BETest>
  <Writer writerid="da452614-4858-5e53-a512-38aab25c61ad">
    <Component logicalPath="3bca1050-c15a-4987-93dc-8f911d35a0ba\\cfbddb07-2409-4b3d-997b-ee1b936c3dbd" componentName="IndexComponentGroup_3bca1050-c15a-4987-93dc-8f911d35a0ba" />
  </Writer>
  <Writer writerid="0ff1ce15-0201-0000-0000-000000000000">
    <Component logicalPath="" componentName="IndexComponentGroup_3bca1050-c15a-4987-93dc-8f911d35a0ba" />
  </Writer>
</BETest>
```


## その他の技術情報
<a name="bk_addresources"> </a>


-  [Windows SharePoint Services およびボリューム シャドウ コピー サービス](http://msdn.microsoft.com/library/adae101a-078e-40b9-9cfa-db2cfb10270a%28Office.15%29.aspx)
    
  

