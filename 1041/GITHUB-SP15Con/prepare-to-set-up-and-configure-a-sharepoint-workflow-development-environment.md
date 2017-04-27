---
title: SharePoint ワークフロー開発環境のセットアップと構成を準備する
ms.prod: SHAREPOINT
ms.assetid: b6a3321f-4131-4a8e-9cb7-7a1b4ab9e26b
---


# SharePoint ワークフロー開発環境のセットアップと構成を準備する
Visual Studio 2012 を使用して、独立した  [SharePoint 用アプリ](http://msdn.microsoft.com/library/fp179930.aspx)として SharePoint 2013 ワークフローを開発するためのワークフロー開発環境をセットアップする方法について説明します。
## SharePoint 2013 でのワークフロー開発の概要

以前のバージョンの SharePoint にもワークフローはありましたが、SharePoint 2013 のワークフローでは次のようなプラットフォームの大幅な強化と改善が図られています。 
  
    
    

- SharePoint ワークフローが, .NET Framework 4.5 の一部である  [Windows Workflow Foundation 4.5](http://msdn.microsoft.com/library/dd489441%28v=vs.110%29) ベースになりました。
    
  
- ワークフロー実行エンジンである  [Workflow Manager](http://msdn.microsoft.com/library/windowsazure/jj193528%28v=azure.10%29.aspx) が SharePoint と切り離され、独立して実行されるようになりました。これにより、柔軟性と拡張性の両方が向上します (下位互換性を確保するため、SharePoint 2013 には従来の 2010 ワークフロー エンジンも含まれています)。
    
  
- C# コードを記述してワークフローを開発する代わりに、Visual Studio で宣言式を使用するワークフロー デザイナーを使用してワークフローを構築できるようになりました。
    
  
- SharePoint 2013 ワークフローは新しいアプリ モデルと統合されています。このため、SharePoint アドイン内にワークフローを実装することができます。
    
  
- SharePoint 2013 ワークフローは SharePoint Designer 2013 を使用して開発することもできます。詳細については、「 [SharePoint Designer および Visio でのワークフロー開発](workflow-development-in-sharepoint-designer-and-visio.md)」を参照してください。
    
  

### はじめに

最初に、以下の内容を参照して、新しいアプリ モデルと SharePoint アドインの基本的な考え方について理解してください。 
  
    
    

|||
|:-----|:-----|
| [SharePoint (開発者向け)](http://msdn.microsoft.com/ja-jp/sharepoint) <br/> |SharePoint 用アプリを中心に扱う SharePoint 開発者向けポータル サイト。  <br/> |
| [SharePoint アドイン](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx) <br/> |SharePoint 用アプリの概要、SharePoint 用アプリを作成する理由、SharePoint 2013 で SharePoint 用アプリを作成する際の基本的な考え方について説明します。  <br/> |
| [SharePoint 用アプリの新しい名前](http://msdn.microsoft.com/library/05b07b04-6c8b-4b7e-bd86-e32c589dfead%28Office.15%29.aspx) <br/> |Office 用アプリおよび SharePoint 用アプリの開発者向けサイトのポータル。  <br/> |
| [SharePoint 2013 開発の概要](sharepoint-2013-development-overview.md) <br/> |SharePoint 2013 は、SharePoint 用アプリおよびファーム ソリューションのための開発プラットフォームです。SharePoint 2013 の各種機能と開発の概要について説明します。  <br/> |
| [SharePoint 2013 ワークフローの基盤](sharepoint-2013-workflow-fundamentals.md) <br/> |プラットフォーム アーキテクチャの概要およびワークフロー相互運用機能ブリッジを含む SharePoint 2013 のワークフロー インフラストラクチャの概要について説明します。  <br/> |
   
次の手順では、最新のワークフロー開発環境がインストールされていることを確認します。開発を SharePoint サーバー マシン上で行う必要はありませんが、開発対象の SharePoint Server インストール環境が必要になります。
  
    
    
必要なコンポーネントは、次のとおりです。これらのアイテムは、下に示した順序でインストールする必要があります。
  
    
    

1. **SharePoint 環境のインストール**
    
  -  [SharePoint Server 2013 の更新プログラム (KB2767999)](http://support.microsoft.com/kb/2767999)
    
  
  - 必要に応じて、 [Office 365 開発向けサイト](http://msdn.microsoft.com/library/office/apps/fp179924%28v=office.15%29) に登録することもできます
    
  
2. **Workflow Manager 環境**
    
  -  [Workflow Manager 1.0 の累積的な更新プログラム (KB2799754)](http://support.microsoft.com/kb/2799754/ja-jp)
    
  
3. **Visual Studio 2012 開発環境のインストール**
    
  -  [Visual Studio 2012](http://www.microsoft.com/visualstudio/jpn/downloads#vs)
    
  
  -  [Visual Studio 2012 更新プログラム 2 (KB2797912)](http://support.microsoft.com/kb/2797912)
    
  
  -  [.NET Framework 4.5 更新プログラム (KB2750149)](http://support.microsoft.com/kb/2750149/ja-jp)
    
  
  -  [Visual Studio 2012 の Office Developer Tools](http://aka.ms/OfficeDevToolsForVS2012)
    
  

### "プレビュー" 版をお持ちの場合

SharePoint Server、ワークフロー マネージャー 1.0、または Office Developer Tools for Visual Studio 2013 のプレリリース ("プレビュー") 版 (2013 年 3 月以前のバージョン) をお持ちの場合は、インストール環境を更新する必要があります。該当する更新プログラムは、次のとおりです。
  
    
    

-  [SharePoint Server 2013 の更新プログラム (KB2767999)](http://support.microsoft.com/kb/2767999)
    
  
-  [Microsoft Azure サービス バス 1.0 の累積的な更新プログラム (KB2799752)](http://support.microsoft.com/kb/2799752?ln=ja-jp)
    
  
-  [Workflow Manager 1.0 の累積的な更新プログラム (KB2799754)](http://support.microsoft.com/kb/2799754/ja-jp)
    
  

### "プレビュー" 版で作成したワークフロー プロジェクトの更新も必要

リリース版の Visual Studio ワークフロー コンポーネントとそれらに関連する更新プログラムでは、パフォーマンス、拡張性、信頼性を強化するための変更が追加されています。これらのアップグレードでは、プレビュー版を使用して作成したワークフロー プロジェクトの更新が必要になります。
  
    
    
この更新を容易に行うことができるように、変換ツールが用意されています。変換ツールは CodePlex から入手できます。このツールの名称は、 [SharePoint 2013 Workflow Converter for Visual Studio 2012](http://wfconverter.codeplex.com/) です。
  
    
    
次に、ワークフロー プロジェクトの更新が必要な変更のサマリーを示します。
  
    
    

- **Item Guid** に対するアクティビティ参照が **Item Id** で置き換えられました。この変更には、次のような重要な影響があります。
    
  -  [LookupSPListItemGuid](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.Activities.LookupSPListItemGuid.aspx) および [GetCurrentItemGuid](https://msdn.microsoft.com/library/Microsoft.SharePoint.WorkflowServices.Activities.GetCurrentItemGuid.aspx) アクティビティが削除され、 **LookupSPListItemId** および **GetCurrentItemId** に置き換えられました。
    
  
  - **Item Guid** を使用する他のアクティビティでは、 **Item Id** が追加され、 **Item Guid** は表示されなくなります。 **Item Guid** を使用する既存のプロジェクトは引き続き動作します (ただし、項目が 5000 を超える大きなリストを除きます。この制約が変更の理由の 1 つです)。
    
  
- アプリで新しいワークフローのパッケージ形式が追加されました。
    
  
- XAML でのワークフロー アクティビティ アセンブリ参照が、実際の SP アクティビティ アセンブリではなく、新しいデザイン時のプロキシ アセンブリをポイントするように変更されました。
    
  

## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint アドインのオンプレミスの開発環境をセットアップする](http://msdn.microsoft.com/library/b0878c12-27c9-4eea-ae3b-7e79e5a8838d%28Office.15%29.aspx)
    
  
-  [SharePoint 2013 ワークフローの新機能](what-s-new-in-workflows-for-sharepoint-2013.md)
    
  
-  [SharePoint Designer および Visio でのワークフロー開発](workflow-development-in-sharepoint-designer-and-visio.md)
    
  
-  [SharePoint 2013 のワークフロー](workflows-in-sharepoint-2013.md)
    
  

