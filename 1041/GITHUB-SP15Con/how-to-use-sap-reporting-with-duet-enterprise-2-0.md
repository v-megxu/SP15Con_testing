---
title: Duet Enterprise 2.0 で SAP レポート機能を使用する方法
ms.prod: SHAREPOINT
ms.assetid: a54c6cd2-2283-440d-af55-e98e3212caa1
---


# Duet Enterprise 2.0 で SAP レポート機能を使用する方法

## 概要
<a name="bkmk_Introduction"> </a>

Duet Enterprise 2.0 では、簡単なカスタマイズを行うことで、作成した SharePoint アドイン内に Duet のレポート機能を統合することができます。
  
    
    
アプリでレポート機能を有効化するためには、Duet によってインストールされた隠し機能を使用します。アプリがインスタンス化されたときに、SAP のレポート機能を使用できるようにするためには、この機能をカスタム機能にステイプルする必要があります。
  
    
    

## 機能の有効化
<a name="bkmk_EnablingTheFeatures"> </a>

Duet のレポート機能を有効化するためには、順序に注意してアクティブ化の手順を実行する必要があります。
  
    
    

### アプリを対象範囲とする外部コンテンツ タイプに追加する機能を作成するには:


1. Duet レポート アプリの [ **ソリューション エクスプローラー**] で、プロジェクト名を右クリックします。[ **追加**]、[ **外部データ ソースのコンテンツ タイプ**] の順に選択します。[ **次へ**] をクリックします。
    
  
2. OData ソースとして SAP レポート機能のエンドポイントの URL を入力します。
    
  
3. エンティティを選択して、[ **完了**] を選択します。
    
  
4. 新しく作成した外部コンテンツ タイプを開き、LSI プロパティを表示します。 **ODataconnectionSettingsId** 以外のプロパティは、ファームを対象範囲とする外部コンテンツ タイプのプロパティと同じであることに注目してください。
    
  

### Duet の隠し機能を有効化する機能を作成するには:


1. プロジェクトに新しい機能をもう 1 つ追加します。タイトルに **AddDuetReporting** という名前を付けます。
    
    この機能には **AddReportingModel** および **DuetReportingForApps** 機能との依存関係があります。
    
  
2. 次のコードを **Elements** ファイルに追加します。
    
  ```
  
<?xml version="1.0" encoding="utf-8"?>
<Feature xmlns="http://schemas.microsoft.com/sharepoint/" Title="AddDuetReporting" Id="6a55705c-af12-455a-914b-8cf3a31c820e" Scope="Web">
  <ActivationDependencies>
    <ActivationDependency FeatureId="e1fe41d3-7fc3-458f-9a66-6ecf6a39bb2c" FeatureTitle="AddReportingModel" />
    <ActivationDependency FeatureId="9b60ccba-ebfd-4e38-87c8-3dea9cc2680a" FeatureTitle="SAPReportingForApps" />
  </ActivationDependencies>
</Feature>

  ```

アクティブ化の依存関係の順序が重要であることに注意してください。まず、外部コンテンツ タイプを作成してから **SAPReportingForApps** 機能をアクティブ化する必要があります。また、2 番目の機能 (ID: **9b60ccba-ebfd-4e38-87c8-3dea9cc2680a**) は Duet Enterprise 2.0 で提供されていますが、隠し機能としてマークされています。上記の方法で、開発者はこの機能を利用して、Duet のレポート機能をアプリに導入することができます。
  
    
    
 **DuetReportingForApps** 機能がアクティブ化されると、すべてのアーティファクト (レポート リスト、ライブラリ、フォームなど) とカスタマイズがアプリ サイトに導入されますが、アプリ サイトのテンプレートには標準のナビゲーション リンクが存在しないため、アプリ開発者がカスタムのページ要素を追加して Duet の機能 (レポート設定、ライブラリ リスト ビュー、フォームなど) を使用できるようにする必要があります。開発者は Duet のレポート機能に関する標準ドキュメントを参照して、機能とその UI 要素について理解を深める必要があります。開発者は、アプリの全般的なテーマにより適したカスタム UI を機能のエントリ ポイントに構築することもできます。
  
    
    

## 結果の表示
<a name="bkmk_ViewingTheResults"> </a>

既定のレポート設定ページを表示するには、 **~/Lists/ReportSetting/AllReportTemplate.aspx** に移動します。
  
    
    
レポート ドキュメント ライブラリの既定のビューを表示するには、 **~/ReportsLib/Forms/AllItems.aspx** に移動します。
  
    
    

## レポートのカスタマイズ
<a name="bkmk_CustomizingTheReports"> </a>

アプリ内では、(using HTML/JavaScript/Jquery などを使用して) 開発者が独自のカスタム UI を作成し、BCS CSOM を利用してより充実したユーザー エクスペリエンスを築くこともできます。以下のスクリーンショットは、OOB アーティファクトやクライアント側の BCS API を使用して HTML ベースのカスタム UI を構築した類似のアプリを示しています。
  
    
    

## その他のリソース
<a name="bk_addresources"> </a>


-  [Duet Enterprise 2.0 での開発](developing-with-duet-enterprise-2-0.md)
    
  
-  [[方法] SharePoint 2013 で OData ソースから外部コンテンツ タイプを作成する](how-to-create-an-external-content-type-from-an-odata-source-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 の Business Connectivity Services で OData ソースを使用する](using-odata-sources-with-business-connectivity-services-in-sharepoint-2013.md)
    
  

