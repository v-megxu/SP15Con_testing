---
title: SharePoint 2013 でのファーム ソリューションの作成
ms.prod: SHAREPOINT
ms.assetid: 96c32f08-ad93-49af-b8d0-9d194a48cc79
---


# SharePoint 2013 でのファーム ソリューションの作成
ファーム ソリューションを使用した SharePoint 2013の管理拡張機能の開発、パッケージ化、展開に関するドキュメントの概要を紹介します。
## ファーム ソリューションの概要
<a name="WhatAreFarmSolutions"> </a>

SharePoint 2013には、SharePoint 管理機能の拡張機能をインストールするための独自のシステムが備わっており、これは他の Windows アプリケーションおよびプラットフォームとは異なります。MSI ファイルや ClickOnce テクノロジは使用されていません。代わりに、拡張機能のアセンブリ、XML、その他のファイルが "ソリューション パッケージ" という 1 つのファイルにバンドルされます。ソリューション パッケージは .cab ベースの形式ですが, .wsp ファイル拡張子を持ちます。パッケージには、SharePoint 機能とそのすべての子コンポーネントだけでなく SharePoint 機能に展開されていない特定の種類のコンポーネントを含めることができます。ファーム管理者はファーム レベルの保存場所にパッケージをアップロードして、そこからパッケージを展開して SharePoint 機能をアクティブ化できます。
  
    
    
SharePoint アドインとは異なり、ファーム ソリューションには、SharePoint サーバーに展開されて SharePoint サーバー オブジェクト モデルを呼び出すコードが含まれます。これらのアセンブリは常に、完全信頼で実行されています。さらに、ファーム ソリューションの機能には、SharePoint アドインの機能の Web サイト範囲に加えて、サイト コレクション、Web アプリケーション、またはファーム全体をカバーする範囲を含めることができます。ファーム ソリューションのこうした側面は、時として、ソリューションの入手先がよく知られた信頼できる発行元でない場合にファーム管理者がインストールしたがらないという事態につながります。このため、主にエンド ユーザーによって使用される SharePoint 拡張機能は、ファーム ソリューションではなく SharePoint アドインとして開発する必要があります。ファーム ソリューションは、カスタム タイマー ジョブ、ユーザー設定の Windows PowerShell コマンドレット、全体管理の拡張機能など、SharePoint 管理機能のカスタマイズに使用する必要があります。SharePoint アドインのその他のメリットとファーム ソリューションの使用の詳細については、「 [SharePoint アドインと SharePoint ソリューションの比較](sharepoint-add-ins-compared-with-sharepoint-solutions.md)」を参照してください。
  
    
    

## ファーム ソリューションの開発者用ドキュメントの紹介
<a name="Guide"> </a>

ファーム ソリューションの開発に関しては、SharePoint 2010 以降ほとんど変わっていないため、このセクションでは SharePoint 2010 SDK へのリンクを示します。混乱を避けるため、SharePoint 2010 SDK を使用して SharePoint 2013の開発を行う際には必ず以下の点に注意してください。
  
    
    

- SharePoint 2010 SDK の "セキュリティで保護されたソリューション" への参照が多くあります。カスタム コードを使ったサンドボックス ソリューションは SharePoint 2013では使用されていません。「コードなし」サンドボックス ソリューションは使用可能です。
    
  
- ファーム ソリューションは主に管理拡張機能に使用するという推奨は、SharePoint 2010 には当てはまりません。したがって、SharePoint 2010 SDK のサンプルおよびその他のドキュメントの多くが ファーム ソリューションとして展開されているエンドユーザー用拡張機能に関するものになっている可能性があります。
    
  
- SharePoint 2010 SDK の "server-side (サーバー側)" および "server code (サーバー コード)" という語は、SharePoint サーバー オブジェクト モデルを呼び出すコードを示します。これらの用語はリモート Web サーバー (SharePoint ファームの外部にある Web サーバー) で動作するコードを意味 *していません*  。SharePoint 2010 および SharePoint 2013の両方で、リモート Web サーバーから SharePoint を呼び出すコードは、必ず SharePoint *クライアント*  オブジェクト モデルの 1 つを使用します。SharePoint 2010 SDK では、そのようなコードは "client-side (クライアント側)" または "client code (クライアント コード)" と呼ばれます。
    
  
- SharePoint 2010 のファーム ソリューションのアセンブリは、コード アクセス セキュリティ (CAS) ポリシーを使用して展開できます。このポリシーは、SharePoint 2013、すなわち完全信頼で実行される SharePoint 2013のファーム ソリューションのすべてのアセンブリで無視されます。
    
  

### パッケージ化および展開

ファーム ソリューションのパッケージ化、インストール、更新、ローカライズの基本については、「 [ソリューションの概要](http://msdn.microsoft.com/library/1983cab9-4b29-494a-a62a-0f8e83908744%28Office.15%29.aspx)」およびノード「 [ファーム ソリューション](http://msdn.microsoft.com/library/845f7524-b9ff-412b-aa29-3afacda91100%28Office.15%29.aspx)」で説明されています。ファーム ソリューションに含める特定の SharePoint コンポーネントの開発については、SharePoint 2010 SDK の関連ノードで説明されています。ファーム ソリューション内のほとんどのコンポーネントは、1 つまたは複数のユーザー設定の SharePoint 機能にカプセル化する必要があります。SharePoint 機能の設計および作成の詳細については、SharePoint 2010 SDK の「 [フィーチャーを操作する](http://msdn.microsoft.com/library/ce5f5ce5-1429-439e-9261-2c4ba9788cc1%28Office.15%29.aspx)」ノードを参照してください。
  
    
    

### 管理拡張機能

SharePoint ファームの管理機能の拡張に関するガイドは、SharePoint 2010 SDK の「 [Windows SharePoint Services の管理](http://msdn.microsoft.com/library/cdcc1b8a-4144-446f-b471-03d4a754a8ab%28Office.15%29.aspx)」ノードに含まれます。このノードには、全体管理の拡張、ユーザー設定の Windows PowerShell コマンドレットの作成、アップグレードおよび移行のカスタマイズ、バックアップのカスタマイズ、および SharePoint イベント ログのカスタマイズに関する説明が含まれています。1 つのセクションでは、SharePoint ファームの状態とパフォーマンスを測定するシステムのカスタマイズ方法を説明しています。カスタム タイマー ジョブの作成方法については、「 [[方法] すべての Web サーバーでコードを実行する](http://msdn.microsoft.com/library/1bbb11b4-a342-4bed-9e7a-b8b13edd0ccc%28Office.15%29.aspx)」を参照してください。
  
    
    

## このセクションの内容
<a name="Guide"> </a>

このセクションのトピックでは、SharePoint ソリューションの開発方法の変更点について説明します。
  
    
    

-  [[方法] クライアント側レンダリングを使用して、フィールド タイプをカスタマイズする](how-to-customize-a-field-type-using-client-side-rendering.md)
    
  
-  [SharePoint 2013 の URL とトークン](urls-and-tokens-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 ソリューションの仮想ディレクトリ](virtual-directories-in-sharepoint-2013-solutions.md)
    
  

## その他の技術情報
<a name="SP15buildfarm_addlresources"> </a>


-  [SharePoint 2013 でのプログラミング モデル](programming-models-in-sharepoint-2013.md)
    
  

