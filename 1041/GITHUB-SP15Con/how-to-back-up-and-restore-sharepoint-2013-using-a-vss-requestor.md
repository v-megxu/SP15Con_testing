---
title: VSS リクエスターを使用して SharePoint 2013 のバックアップと復元を行う方法
ms.prod: SHAREPOINT
ms.assetid: cab5ba90-bd23-4cec-82d7-529e3f86ba88
---


# VSS リクエスターを使用して SharePoint 2013 のバックアップと復元を行う方法
 **概要:** Microsoft SharePoint 2013 のボリューム シャドウ コピー サービス (VSS) リクエスターを使用したバックアップと復元方法を説明します。
## リクエスターを使用したバックアップと復元

次の手順に従って VSS リクエスターを使用して、Microsoft SharePoint Foundation データのバックアップと復元を行います。
  
    
    

### リクエスターを使用してデータのバックアップと復元を行うには


1. SharePoint Foundation VSS ライター サービスを手動で開始します。[ **管理ツール**] を開き、[ **サービス**] に移動して開き、[ **Volume Shadow Copy**] と[ **SharePoint 2010 VSS Writer**] というサービスを開始します。
    
  
2. システム コンソールから  `STSADM -o registerwsswriter` コマンドを実行して Windows レジストリにライターを登録します。実行可能ファイルは %ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\BIN ディレクトリに格納されています。
    
  
3. すべての SharePoint Foundation サーバーで手順 1 と 2 を繰り返します。
    
  
4. リクエスターを使用してデータのバックアップと復元を行います。SharePoint Foundation からバックアップまたは復元するには、リクエスターを使用する (「 [ボリューム シャドウ コピー サービスの概要 (英語)](http://msdn.microsoft.com/ja-jp/library/aa384649%28VS.85%29.aspx)」) ことも、BETest テスト ユーティリティを使用する (「 [VSS SDK](http://www.microsoft.com/downloads/details.aspx?FamilyID=0B4F56E4-0CCC-4626-826A-ED2C4C95C871&amp;displaylang=en)」から入手可能) こともできます。 
    
  

## VSS 実行のセキュリティ

VSS には、バックアップと復元の対象となるすべてのサーバー インスタンス上でライターを実行するアカウントに対し、特殊な要件があります。
  
    
    

- 実行するアカウントは、VSS を呼び出す権限を所有している必要があります。既定では、VSS ライターは、対象となるサーバー インスタンス上の管理者またはバックアップ オペレーターのメンバーである必要があります。他のアカウントが VSS にアクセスできるようにレジストリ キーを構成することもできます。
    
  
- アカウントは、 **BACKUP DATABASE** と **RESTORE DATABASE** コマンドをデータベース サーバーに対して発行する権限を持っている必要があります。
    
  
- アカウントは、SQL Server に対して VDI を開く権限を持っている必要があります。そのためには、クライアントが SQL Server の sysadmin グループのメンバーである必要があります。
    
  
- アカウントは、SQL Server 上のマスター データベースの sys.master_files カタログ ビューに対して、クエリを実行できる必要があります。
    
  
また、SharePoint Foundation Timer サービス (owstimer.exe) によってホストされるように、ライター サービスは管理アプリケーション プール アカウントの下で実行する必要があります。このアカウントは、SharePoint Foundation の基本インストールの「ネットワーク サービス」アカウントです。 
  
    
    
 **注** このアカウントがローカル マシン管理者アカウントである可能性は非常に低いと考えられます。これは、処理アカウントがローカル システムとして実行する必要がある VSS の要件とは異なるからです。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 およびボリューム シャドウ コピー サービスの概要](overview-of-sharepoint-2013-and-the-volume-shadow-copy-service.md)
    
  

