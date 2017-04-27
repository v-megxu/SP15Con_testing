---
title: SharePoint 2013 eDiscovery およびコンプライアンスの新機能
ms.prod: SHAREPOINT
ms.assetid: 39a1cc3f-c78d-478f-8c15-928b96386a52
---


# SharePoint 2013 eDiscovery およびコンプライアンスの新機能
SharePoint 2013 での電子情報開示と法令順守の新機能について説明します。これらの機能を使用し、民事訴訟の証拠の管理と回復を行います。
## SharePoint 2013 の電子情報開示と法令順守の新機能

SharePoint 2013 では、電子情報管理と法令順守機能を使用して、民事訴訟で使用する証拠の管理や回復、また企業の記録管理ができます。また SharePoint 2013 には Content Management Interoperability Services (CMIS) 相互運用基準に対応する組み込みのサポートもあります。CMIS についての詳細は、「 [OASIS の Web サイト](https://www.oasis-open.org/committees/tc_home.php?wg_abbrev=cmis)」の標準仕様を参照してください。
  
    
    

### SharePoint 2013 の電子情報開示

情報開示は民事訴訟において証拠の回復に使用される法的プロセスです。SharePoint Server 2010 は記録管理の機能の一部として、電子情報開示機能を提供します。SharePoint 2013 では、電子情報開示機能は大幅に拡張され、改定されました。電子情報開示の主な機能と API は以下のとおりです。
  
    
    

- **ケース マネージャー**: 記録管理者による、企業全体での情報開示プロジェクトの作成と管理、金額が肥大化し多様な種類になる可能性があるコンテンツの保留、コンテンツのスナップショットの保存が可能になります。
    
  
- **企業全体のアクセス**: 中央の場所からのコンテンツの保留と検索が可能になります。また検索の実行、SharePoint コンテンツへのアクセス、コンテンツの保留を、設定された任意の SharePoint で行うことも可能です。
    
  
- **インプレース保持**: 弁護人がコンテンツのスナップショットを保存できるようになり、コンテンツのスナップショットの状態を乱すことなく確実に変更を続けることができます。
    
  
- **分析**: 弁護人、管理者、記録管理者による電子情報開示活動に関するデータの取集と分析が可能になります。
    
  

### レコード管理プログラミングの新機能

.NET サーバー プログラミング モデルは SharePoint 2013 で更新され、プロジェクトの詳細管理とプロジェクトのメタデータ取得の新機能が搭載されました。クラスの新機能は次のとおりです。
  
    
    

-  [ProjectPolicy](https://msdn.microsoft.com/library/Microsoft.Office.RecordsManagement.InformationPolicy.ProjectPolicy.aspx) クラス。このクラスを使用し、プロジェクト ポリシーの詳細をカスタマイズできます。
    
  
-  [Microsoft.Office.RecordsManagement.Preservation](https://msdn.microsoft.com/library/Microsoft.Office.RecordsManagement.Preservation.aspx) のすべてのクラス。これらのクラスを使用すると、保留情報やステータス情報の管理方法をカスタマイズできます。
    
  
-  [Microsoft.Office.RecordsManagement.SearchAndProcess](https://msdn.microsoft.com/library/Microsoft.Office.RecordsManagement.SearchAndProcess.aspx) クラス。これらのクラスを使用し、検索パラメーターの作成と管理を行います。
    
  

### Content Management Interoperability Services (CMIS) プロデューサー

CMIS プロデューサーは SharePoint Server 2010 がリリースされてから数か月後に SharePoint Administrator's Toolkit の一部として導入されました。SharePoint 2013では、CMIS プロデューサーが完全に再設計されています。CMIS プロデューサーは、データの移行やスレートのリポジトリ グラフィカル ユーザー インターフェイスの作成を行う状況や、認証アプリケーションからコンテンツ管理システムにデータを保存する場合に特に有用です。CMIS プロデューサーは、作成、更新、削除、チェックイン、チェックアウトなどの基本的なドキュメント管理操作と、ドキュメントのバージョンとメタデータの管理をサポートします。
  
    
    
CMIS 標準は、相互運用に使用するコンテンツ管理システムに準拠する OASIS 標準です。
  
    
    
SharePoint 2013 での CMIS コネクタの拡張機能は、以下のとおりです。
  
    
    

- CMIS 1.0 のサポート
    
  
- SharePoint リスト Web サービスが稼働する、ほとんどの認証環境における機能
    
  
- クレーム環境での相互運用サポート
    
  
- 基本認証、NTLM 認証、Digest 認証、Kerberos プロトコルの移行と制約付きデリゲート、Windows クレーム認証、クレームの複数認証、クレームの混合認証など、その他の認証プロトコルとの相互運用のサポート
    
  
CMIS コンシューマー Web パーツは SharePoint 2013 から削除されています。
  
    
    

### プロジェクトの法令順守

サイト、その他大型のオブジェクトは、特定の利用ポリシーへの準拠が必要なことがあります。これらのシナリオをサポートするため、SharePoint 2013 の企業コンテンツ管理は SharePoint のサイト、SharePoint のサイト コンテンツ、関連するメールボックスにポリシーを適用し、関連するメールボックスにポリシー フローを適用する機能を提供します。
  
    
    

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 の eDiscovery](ediscovery-in-sharepoint-2013.md)
    
  

