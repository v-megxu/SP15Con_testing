---
title: SharePoint 2013 ソリューションの仮想ディレクトリ
ms.prod: SHAREPOINT
ms.assetid: c26c4160-31be-4358-89cf-082b8a1e6a6c
---


# SharePoint 2013 ソリューションの仮想ディレクトリ
仮想ディレクトリ システムの変更が SharePoint 2013 の ファーム ソリューション 作成にどのような影響を与えるかについて説明します。
## ソリューションが新しい UI モード システムと互換性があるようにする

現在 Microsoft SharePoint 2010 Software Development Kit (SDK) を使用しているが、SharePoint 2013 の開発を行っている場合、作業時に検討する必要がある、仮想ディレクトリ システムの変更があります。この変更は、SharePoint 2010 モードと SharePoint 2013 モードのどちらでも、サイト コレクションを実行できるようにする、新しい SharePoint 2013 機能の副作用です。このモードは互換性レベルや UI バージョンと呼ばれることもあります。SharePoint では、仮想フォルダー  `_layouts` または `_controltemplates` 内のファイルに対して、サイト コレクションのモードに応じて、%ProgramFiles%\\Common Files\\Microsoft Shared\\web server extensions\\15\\ (15 ハイブ と呼ばれることもあります) または対応する14 ハイブ 内のファイルのバーションを使用する必要があります。SharePoint は、SharePoint 2013 ファイルを使用する必要があることを示すため、仮想ディレクトリ パス名の後ろに「/15」を追加します。その文字列が存在しない場合、SharePoint 2010 ファイルが使用されることを意味します。
  
    
    
この新しいシステムは、SharePoint 2013 のソリューションとアプリを開発する場合、特に SharePoint 2010 SDK を使用している場合に影響を与えます。(SharePoint 2013 モードでのみ動作する) すべての SharePoint アドイン と、SharePoint 2013 モードで動作するサイト コレクションでのみ使われることが判明しているすべての SharePoint ソリューションでは、ソリューションやアプリで作成したすべての  `_layouts` と `_controltemplates` の仮想パスに「/15」を手動で追加する必要があります (パスが *.aspx ファイルを指していない場合)。この文字列が SharePoint 2010 SDK のガイダンスにこの文字列が表示されていない場合でも、この操作が必要です。たとえば、SharePoint 2010 SDK で `~/_layouts/images/myimage.png` を使うように指示されている場合、SharePoint 2013 用の開発を行う際には、 `~/_layouts/15/images/myimage.png` を使用する必要があります。
  
    
    
ソリューションが両方のモードのサイト コレクションと互換性があるようにするには、現在のサイト コレクションのモードを判別するための分岐ロジックが必要で、それに従って仮想パスを作成する必要があります。すべての SharePoint クライアント オブジェクト モデルと REST インターフェイスでも使用可能な  [CompatibilityLevel](https://msdn.microsoft.com/library/Microsoft.SharePoint.SPSite.CompatibilityLevel.aspx) プロパティを利用すると、コードによるモードのチェックが可能になります。 [SPUtility](https://msdn.microsoft.com/library/Microsoft.SharePoint.Utilities.SPUtility.aspx) クラスもいくつかの新しいプロパティを備えており、ソリューション内での互換性レベルの管理をサポートします。これらのプロパティは、クライアント オブジェクト レベルでは使用できません。最後に SharePoint には、コードで現在の互換性レベルの検出に使用できる **UIVersion** プロパティを公開する、いくつかのコントロールが用意されています。
  
    
    

> **メモ**
> 仮想パスのファイルが *.aspx の場合、SharePoint は現在のサイト コレクションのモードを自動的に検出し、適切なハイブからファイルを返します。このため、仮想パスに「/15」を挿入する必要はありません。 
  
    
    


## その他の技術情報
<a name="bk_addresources"> </a>


-  [SharePoint 2013 でのファーム ソリューションの作成](build-farm-solutions-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のファーム ソリューションの展開を計画する](http://blogs.technet.com/b/mspfe/archive/2013/02/04/planning-deployment-of-farm-solutions-for-sharepoint-2013.aspx)
    
  
-  [SPUtility properties](http://msdn.microsoft.com/library/Properties.T:Microsoft.SharePoint.Utilities.SPUtility.aspx)
    
  

