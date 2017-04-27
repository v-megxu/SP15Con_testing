---
title: ペアリング コマンドレット Register-SPWorkflowService を使用する
ms.prod: SHAREPOINT
ms.assetid: 91fca6c2-60ca-4177-8560-2b310dac0e2c
---



# ペアリング コマンドレット Register-SPWorkflowService を使用する
コマンドレット **Register-SPWorkflowService** を使用して SharePoint Server 2013 と ワークフロー マネージャー をペアリングする方法について説明します。
ワークフローの開発をサポートするために Microsoft SharePoint Server 2013 をインストールして構成する場合、SharePoint Server 2013 と ワークフロー マネージャー のインストールを "ペアリング" する必要があります。ほとんどのシナリオでは、このペアリングはコマンドレット **Register-SPWorkflowService** を使用して簡単に実行できます。このコマンドレットは SharePoint インストールに含まれています。
  
    
    

重要な点は、このコマンドレットが役に立たないペアリング シナリオもあることです。 **Register-SPWorkflowService** は、次のペアリング シナリオでのみ役に立ちます。
- SharePoint Server 2013 と ワークフロー マネージャー がサーバー ボックスに併置されている 1 コンピューター サーバー ファーム。
    
  
- SharePoint Server 2013 と ワークフロー マネージャー が 3 つのコンピューターすべてに併置されている 3 コンピューター サーバー ファーム (4 番目のコンピューターの追加は、検索を別のコンピューターで行う場合や、ワークフロー マネージャー HA が必要な場合に行います。後者の場合は、3 つのコンピューターすべてにインストールする必要があります)。
    
  
- 併置されていない ワークフロー マネージャー サーバー ファームとペアリングされた 3 コンピューター SharePoint Server 2013 ファーム。
    
  
また、 **Register-SPWorkflowService** が現在のユーザーの資格情報を使用する点についても注意してください。
## コマンドレット設計


****


|**詳細**|**説明**|
|:-----|:-----|
|動詞  <br/> |登録  <br/> |
|名詞  <br/> |SPWorkflowService  <br/> |
|説明  <br/> |sps15short ファームを ワークフロー マネージャー ファームとペアリングします。このコマンドレットは、ファームごとに 1 回実行する必要があります。コマンドレットを実行する前に、コンピューターの証明書ストアと SharePoint 証明書ストアにルート CA 証明書をインストールする必要があります。この場合、コマンドレット **New-SPTrustedRootAuthority** を使用します (以下の手順を参照してください)。 <br/> |
|出力の型  <br/> |なし。  <br/> |
|構文  <br/> | `Register-SPWorkflowService -SPSite <URI or GUID representing an SPSite object> -WorkflowHostUri <workflow service endpoint URL> -ScopeName <string> [-PartitionMode] [-AllowOAuthHttp] [-Force]` <br/> |
   

## コマンドレットのパラメーター



|**パラメーター**|**型**|**説明**|
|:-----|:-----|:-----|
|SPSite          (必須)  <br/> |**SPSitePipeBind** <br/> |ペアリング エンドポイントとして機能する SharePoint Server ファームの長期使用できるサイト コレクションの URL。ペアリングの情報は、この URL から推定されます。  <br/> |
|WorkflowHostUri          (Required)  <br/> |String  <br/> |ペアリング用の ワークフロー マネージャー エンドポイントの URL。ワークフロー ホスト URI と共にポート番号を指定します。  <br/> |
|ScopeName  <br/> |String  <br/> |ペアリングされた SharePoint Server ファームを識別するためにワークフロー サービスが使用する名前。既定値は "SharePoint" です。複数の SharePoint ファームを ワークフロー マネージャー ファームにペアリングする場合にのみ、このパラメーターを指定する必要があります。  <br/> |
|PartitionMode  <br/> |SwitchParameter  <br/> |このパラメーターは、複数テナントの SharePoint ファームにのみ使用します。パーティション モードは、SharePoint サービスごとに指定します。このコマンドレットを実行した後に、SharePoint ファームで複数テナントを作成できます。そのため、コマンドレットは、SharePoint ファームの既存の状態から暗黙的にこのパラメーター値を推定できません。  <br/> |
|AllowOAuthHttp  <br/> |SwitchParameter  <br/> |HTTP での OAuth とメタデータの交換を有効にします。これはテストでは役立ちますが、運用モードでは役立ちません。HTTP をサポートするように SharePoint を構成する場合にのみ、使用してください。HTTP を使用するにように ワークフロー マネージャー を構成する必要はありません。  <br/> |
|Force  <br/> |SwitchParameter  <br/> | _ScopeName_ パラメーターを使用して強制的にスコープを作成するか、同じ _ScopeName_ に対応する既存のスコープを更新します。指定せず、同じ名前のスコープが存在する場合、コマンドレットはエラーをスローします。 <br/> |
   

## 例


```

PS> Register-SPWorkflowService -SPSite "https://myserver/mysitecollection" -WorkflowHostUri "http://workflow.example.com:12291" -ScopeName "SharePoint2" -PartitionMode -AllowOAuthHttp  -Force
```


## その他のリソース
<a name="bk_addresources"> </a>


-  [SharePoint Server 2013 のワークフローをインストールおよび構成する](http://technet.microsoft.com/ja-jp/library/jj658588.aspx)
    
  
-  [ビデオ シリーズ: SharePoint Server 2013 でワークフローをインストールして構成する](http://technet.microsoft.com/ja-jp/library/dn201724.aspx)
    
  
-  [Workflow Manager 1.0](http://msdn.microsoft.com/ja-jp/library/jj193528%28Azure.10%29)
    
  
