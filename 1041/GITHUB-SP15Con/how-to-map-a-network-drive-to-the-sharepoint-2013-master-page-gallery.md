---
title: [方法] SharePoint 2013 マスター ページ ギャラリーへのネットワーク ドライブの割り当て
ms.prod: SHAREPOINT
ms.assetid: 7d416f6e-2471-4d03-97ae-4e8d907784c6
---


# [方法]: SharePoint 2013 マスター ページ ギャラリーへのネットワーク ドライブの割り当て
SharePoint Server 2013でデザイン マネージャーを使用してデザイン ファイルをアップロードできるように、ネットワーク ドライブをマスター ページ ギャラリーに割り当てる方法を説明します。
任意の Web デザイン ツールや HTML エディターで Web サイトの視覚デザインを作成した後、デザイン マネージャーを使用してそのデザインを SharePoint にインポートできます。これを行うには、デザイン ツールのファイルがサイトのマスター ページ ギャラリーに保存されるようにする必要があります。SharePoint はマスター ページ ギャラリーにあるファイルを検索するからです。ファイルを正しい場所に簡単に保存できるように、ネットワーク ドライブをマスター ページ ギャラリーに割り当てることをお勧めします。
  
    
    

最初に、マスター ページ ギャラリーの場所を調べます。
### マスター ページ ギャラリーの場所を調べるには


1. デザインの作成対象のサイトで、デザイン マネージャーを起動します (たとえば、[ **設定**] メニューの [ **デザイン マネージャー**] を選択します)。
    
    > **重要**
      > サイトが SharePoint Online でホストされている場合は、Office 365 資格情報を使用してサイトにサインインするときに、必ず [ **サインインしたまま処理を続ける**] チェック ボックスをオンにしてください。詳細については、「 [SharePoint Online サイトへネットワーク ドライブを割り当てる方法、および Explorer ビューをトラブルシューティングする方法](http://support.microsoft.com/kb/2616712/ja-jp)」を参照してください。 
2. 番号付きリストで、[ **デザイン ファイルのアップロード**] を選択します。
    
  
3. [デザイン マネージャー: デザイン ファイルのアップロード] ページにマスター ページ ギャラリーの場所が表示されます。通常、場所の末尾は  `/_catalogs/masterpage/` になります。この場所にネットワーク ドライブを割り当てます。
    
  
4. マスター ページ ギャラリーの場所を書き留めるか、クリップボードにコピーします。
    
  
デザイン ツールや HTML エディターを実行しているコンピューターで、先ほどコピーした場所にネットワーク ドライブを割り当てます。ネットワーク ドライブを割り当てる手順は、次のようにコンピューターのオペレーティング システムによって異なります。
- Windows 8 を実行しているコンピューターでは、Windows 8 版の記事「 [ネットワーク ドライブへのショートカットを作成する (ネットワーク ドライブを割り当てる)](http://windows.microsoft.com/ja-jp/windows-8/create-shortcut-to-map-network-drive)」に記載されている手順に従います。
    
  
- Windows 7 を実行しているコンピューターでは、Windows 7 版の記事「 [ネットワーク ドライブへのショートカットを作成する (ネットワーク ドライブを割り当てる)](http://windows.microsoft.com/ja-jp/windows7/create-a-shortcut-to-map-a-network-drive)」に記載されている手順に従います。
    
  
- Windows Vista を実行しているコンピューターでは、 版の記事「 [ネットワーク ドライブへのショートカットを作成する (ネットワーク ドライブを割り当てる)](http://windows.microsoft.com/ja-jp/windows-vista/create-a-shortcut-to-map-a-network-drive)」に記載されている手順に従います。
    
  
- Windows XP を実行しているコンピューターでは、記事「 [Windows XP でネットワーク ドライブの接続および切断を行う方法](http://support.microsoft.com/kb/308582/ja-jp)」に記載されている手順に従います。
    
  
- ** *それ以外のオペレーティング システムを実行しているコンピューターでは、そのオペレーティング システムで新しい場所へのショートカットを作成するための手順に従ってください。* ** SharePoint サイトに接続するために別の資格情報を指定する必要がある場合や、コンピューターにログオンするたびに接続を確立し直すように指定する必要がある場合があります。
    
  

## その他のリソース
<a name="bk_addresources"> </a>


-  [[方法]: SharePoint Server 2013 のサイトにマスター ページを適用する](how-to-apply-a-master-page-to-a-site-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 のサイト デザインの開発](develop-the-site-design-in-sharepoint-2013.md)
    
  
-  [SharePoint 2013 デザイン マネージャーのデバイス チャネル](sharepoint-2013-design-manager-device-channels.md)
    
  
-  [方法: SharePoint 2013 デザイン マネージャーでプレビュー ページを変更する](how-to-change-the-preview-page-in-sharepoint-2013-design-manager.md)
    
  
-  [SharePoint 2013 デザイン マネージャーのイメージ表示](sharepoint-2013-design-manager-image-renditions.md)
    
  

