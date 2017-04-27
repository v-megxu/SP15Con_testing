---
title: SharePoint 2013 サイトをテンプレートとして保存、ダウンロード、およびアップロードする
ms.prod: SHAREPOINT
ms.assetid: 2e637172-ddac-4a70-bd77-55a1645a3db1
---


# SharePoint 2013 サイトをテンプレートとして保存、ダウンロード、およびアップロードする
SharePoint サイト テンプレートを使用して堅牢なアプリケーションを設計および作成する方法について説明します。
豊富なデータ ソース セット、顧客向けのビューおよびフォーム、高度にカスタマイズされたワークフローなどが含まれる堅牢な SharePoint 2013 アプリケーションを設計および作成することができます。ビジネス ソリューション サイトを作成したら、それを SharePoint 環境ですぐに使い始めることができます。または、ソリューションをテンプレート化して別の環境で展開すれば、それを基に新しいサイトを作成できるようにユーザーに提供することも、Visual Studio でさらに開発を行うためにハンドオフすることもできます。
  
    
    


## SharePoint サイト テンプレートとは
<a name="bkmk_WhatIsTemplate"> </a>

SharePoint サイト テンプレートは、特定のビジネスのニーズに合わせて設計されている事前作成済みの定義です。これらのテンプレートをそのまま使用して固有の SharePoint サイトを作成し、必要なだけサイトをカスタマイズすることができます。チーム サイト、プロジェクト サイト、およびコミュニティ サイトなどの既定のサイト テンプレートは見覚えがあるかもしれません。
  
    
    
既定のテンプレートだけではなく、作成およびカスタマイズしたサイトに基づいて独自のサイト テンプレートを作成することもできます。これは、カスタム ソリューションを作成してそのソリューションを同僚、広範な組織、または外部組織と共有できるようにする強力な機能です。また、サイトをパッケージ化し、そのパッケージ化したサイトを、別の環境またはアプリケーション (Visual Studio など) で開き、そこでカスタマイズすることができます。
  
    
    
カスタマイズされたサイトまたはビジネス ソリューションをテンプレート化すると、非常に有用で強力な機能となります。ソリューションをテンプレートとしてパッケージ化する処理を一旦開始すると、ビジネス アプリケーション用のプラットフォームとして SharePoint の可能性が見えてきます。サイト テンプレート オプションは、このあらゆる可能性を実現します。
  
    
    
サイトをテンプレートとして保存する場合は、Web ソリューション パッケージ (WSP) を作成します。WSP は、ソリューション マニフェストを使用する CAB ファイルです。作成したソリューションは、SharePoint サイト コレクション用のソリューション ギャラリーに格納されます。テンプレートを保存すると、ソリューション ファイル (.wsp) が作成されてソリューション ギャラリーに格納され、そこでソリューションのダウンロードまたはアクティブ化を行えるようになります。
  
    
    

> **メモ**
> 作成する WSP は、完全信頼 SharePoint ソリューションの場合と同じ宣言形式を持つ部分信頼ユーザー ソリューションです。ただし、この場合は、完全信頼ソリューションがサポートする全範囲の機能要素タイプをサポートするわけではありません。 
  
    
    


### テンプレートに保存されるもの

SharePoint サイトをテンプレートとして保存する場合は、サイトのフレームワーク全体、すな わち、そのリストおよびライブラリ、ビューおよびフォーム、そしてワークフローを保存します。このようなコンポーネントに加えて、サイトのコンテンツ (たとえば、ドキュメント ライブラリに格納されているドキュメントなど) をテンプレートに含めることもできます。この機能は、使用を開始するユーザーにサンプル コンテンツを提供するのに便利です。ただし、この機能を使用すると、テンプレートのサイズが大きくなり、既定の 50 MB のサイト テンプレートの制限を超える可能性があります。
  
    
    
サイト内のオブジェクトの大部分は、テンプレートに含まれ、サポートされます。ただし、サポートされないオブジェクトと機能もいくつかあります。 
  
    
    

- **サポート対象** リスト、ライブラリ、外部リスト、データ ソース接続、リスト ビューおよびデータ ビュー、カスタム フォーム、ワークフロー、コンテンツ タイプ、カスタム アクション、ナビゲーション、サイト ページ、マスター ページ、モジュール、および Web テンプレート。
    
  
- **サポート対象外** カスタマイズされたアクセス許可、実行中のワークフロー インスタンス、リスト アイテム バージョン履歴、実行中のワークフローに関連付けられているワークフロー タスク、ユーザーまたはグループ フィールド値、分類フィールド値、発行ページおよび発行サイト、個人用サイト、ホチキス止め機能、SharePoint アドイン、リモート イベント レシーバー。
    
    > **メモ**
      > 発行サイトの場合は、サイト定義テンプレートを使用できます。詳細については、この記事で後述する「 [その他の技術情報](save-download-and-upload-a-sharepoint-2013-site-as-a-template.md#bkmk_additionalresources)」を参照してください。 

### SharePoint テンプレートを使用してできること

サイトをテンプレートとして保存する機能は非常に強力であり、さまざまな用途のカスタム サイトを提供できます。ここでは、サイトをテンプレートとして保存する機能によりすぐに得られるメリットについて説明します。
  
    
    

- **ソリューションの即時展開** テンプレートをソリューション ギャラリーに保存し、アクティブにして、他のユーザーがこのテンプレートを基に新しいサイトを作成できるようにします。テンプレートを選択し、そのテンプレートを基に新しいサイトを作成できます。この場合、サイトのコンポーネント、その構造、ワークフローなどは継承されます。ソリューションを作成するために Visual Studio は必要ありませんが、サーバーに直接アクセスしてサーバー管理コマンドを実行する必要があります。サイトをテンプレートとして保存し、それをアクティブにすれば、それで完了です。
    
  
- **移植性** ご使用の環境にカスタム ソリューションを展開することに加えて, .wsp ファイルをダウンロードし、それを移動させて別の SharePoint 環境に展開することもできます。サイトのカスタマイズはすべて、便宜上 1 つのファイルに格納されます。
    
  
- **拡張性** カスタマイズしたサイトを Web ソリューション パッケージとして Visual Studio で開き、テンプレートに対する追加の開発カスタマイズを実行し、それを SharePoint に展開することができます。結果として SharePoint のサイト開発は、SharePoint Designer 2013、Visual Studio、およびブラウザーを含むソリューション ライフサイクル (開発、ステージ、本番稼働移行) を順を追って行うことができます。
    
  
SharePoint でカスタム サイトの作成を開始すると、サイトを組織全体で移植可能になるソリューションに変換するさらなる利点が明らかになります。サイト テンプレートを使用する基本的な手順は、次のとおりです。
  
    
    

- サイトをテンプレートとしてソリューション ギャラリーに保存します。
    
  
- ソリューション ギャラリーから .wsp ファイルにサイト テンプレートをダウンロードします。
    
  
- .wsp ファイルをソリューション ギャラリーにアップロードします。
    
  
サイト テンプレートをソリューション ギャラリーに追加し、テンプレートがアクティブになった後は、次にサイトまたはサブサイトを作成するときに、[ **新しい SharePoint サイト**] ページの [ **テンプレートの選択**] セクションにある [ **カスタム**] タブでテンプレートを選択できるようになります。
  
    
    

## サイトをテンプレートとしてソリューション ギャラリーに保存する
<a name="bkmk_SaveTemplate"> </a>


1. サイト コレクションのトップレベル サイトに移動します。
    
  
2. [ **設定**] をクリックし、[ **サイトの設定**] をクリックします。
    
  
3. [ **サイトの操作**] セクションで、[ **テンプレートとしてのサイトの保存**] をクリックします。
    
  
4. [ **ファイル名**] ボックスで、テンプレート ファイルに使用する名前を指定します。
    
  
5. テンプレートの名前と説明を、[ **テンプレート名**] および [ **テンプレートの説明**] ボックスに指定します。
    
  
6. サイトのコンテンツをサイト テンプレートに含めるには、[ **コンテンツを含める**] ボックスを選択します。
    
    > **メモ**
      > サイトのコンテンツを含めると、テンプレートのサイズが大幅に増大する可能性があります。サイト テンプレートにおける既定のサイズ上限は 50 MB ですが、組織によっては上限がそれより低い場合があります。コンテンツはいつでも除外することができ、必要な内容を後で新しいサイトにコピーすることができます。あるいは、サイズの上限を引き上げることができます。たとえば、上限を最大許容値まで引き上げるには、以下の Stsadm コマンド構文を使用します。 >  `stsadm -o setproperty -pn max-template-document-size -pv 524288000`
7. [ **OK**] をクリックして、テンプレートを保存します。
    
    サイトにあるコンポーネントのすべてが有効である場合は、テンプレートが作成され、「操作は正常に完了しました。」というメッセージが表示されます。
    
  
8. 次のいずれかの操作を行います。
    
  - サイトに戻るには、[ **OK**] をクリックします。
    
  
  - サイト テンプレートに直接進むには、[ **ソリューション ギャラリー**] をクリックします。
    
  

## ソリューション ギャラリーからファイルにサイト テンプレートをダウンロードする
<a name="bkmk_DownloadTemplate"> </a>


1. サイト コレクションのトップレベル サイトに移動します。
    
  
2. [ **設定**] をクリックし、[ **サイトの設定**] をクリックします。
    
  
3. [ **Web デザイナー ギャラリー**] セクションで、[ **ソリューション**] をクリックします。
    
  
4. ソリューションをアクティブする必要がある場合は、それを選択し、[ **コマンド**] グループの [ **アクティブ化**] をクリックします。次に、[ **ソリューションのアクティブ化の確認**] 画面の [ **コマンド**] グループで [ **アクティブ化**] をクリックします。
    
  
5. ソリューションをダウンロードするには、ソリューション ギャラリーでその名前をクリックし、[ **保存**] をクリックします。次に、[ **名前を付けて保存**] ダイアログ ボックスで、ソリューションを保存する場所に移動し、[ **保存**] をクリックし、[ **閉じる**] をクリックします。
    
  

## ソリューション ギャラリーにサイト テンプレートをアップロードする
<a name="bkmk_UploadTemplate"> </a>


1. サイト コレクションのトップレベル サイトに移動します。
    
  
2. [ **設定**] をクリックし、[ **サイトの設定**] をクリックします。
    
  
3. [ **Web デザイナー ギャラリー**] セクションで、[ **ソリューション**] をクリックします。
    
  
4. ソリューションをアップロードするには、[ **コマンド**] グループの [ **アップロード**] をクリックし、次に [ **ドキュメントを追加します**] ダイアログ ボックスの [ **参照**] をクリックします。次に、[ **アップロードするファイルを選択**] ダイアログ ボックスで、ファイルを特定し、そのファイルを選択し、[ **開く**] をクリックし、[ **OK**] をクリックします。
    
  
5. ソリューションをアクティブにするには、[ソリューションのアクティブ化の確認] 画面の [ **コマンド**] グループで [ **アクティブ化**] をクリックします。
    
  

## その他の技術情報
<a name="bkmk_additionalresources"> </a>


-  [サイトの種類: WebTemplates とサイト定義](http://msdn.microsoft.com/ja-jp/library/ms434313.aspx)
    
  
-  [SharePoint 2013 でワークフローをパッケージ化して展開する方法の概要](http://msdn.microsoft.com/ja-jp/library/jj819316%28v=office.15%29.aspx)
    
  
-  [SharePoint 2013 でのファーム ソリューションの作成](http://msdn.microsoft.com/ja-jp/library/jj163902%28v=office.15%29.aspx)
    
  
-  [リスト テンプレートを使用してリストをコピーまたは移動する](https://support.office.com/ja-jp/article/Copy-or-move-a-list-by-using-a-list-template-77cbdf27-aa55-4ee3-a6f9-bb78c910b3d6)
    
  
-  [ライブラリ テンプレートを使用してライブラリをコピーまたは移動する](https://support.office.com/article/293d018a-c8b9-42d1-a1d1-beb0252c5cdf?omkt=en-us)
    
  
-  [[エクスプローラーで開く] を使用してライブラリ ファイルをコピーまたは移動する](http://office.com/redir/HA101811182.aspx)
    
  
