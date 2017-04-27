---
title: Excel Services のベスト プラクティス
keywords: guidelines
f1_keywords:
- guidelines
ms.prod: OFFICE365
ms.assetid: 56fa3913-c156-49da-bed0-a6a106fc129f
---


# Excel Services のベスト プラクティス

このトピックでは、Excel Services を使用する際のベスト プラクティス推奨事項について説明します。
  
    
    


## 脅威の軽減


### 匿名アクセスと情報開示

以下の設定の組み合わせでは、プロセス アカウントがアクセスできる共有内の任意のファイルに匿名ユーザーがアクセスできるようになります。したがって、情報が開示される恐れがあるため、以下の設定の組み合わせは推奨されません。
  
    
    

- Microsoft SharePoint Foundation に対する匿名アクセスがオンになっている。
    
  
- UNC の信頼できる場所があり、[ **プロセス アカウント**] がオンになっている。
    
  

> **メモ**
> [ **プロセス アカウント**] は、すべての信頼できる場所に影響を与える Excel Services のグローバル設定です。 
  
    
    


### [プロセス アカウント] オプションを表示するには


1. [ **スタート**] メニューで、[ **すべてのプログラム**] をクリックします。
    
  
2. [ **Microsoft SharePoint 2010 製品**] をポイントし、[ **SharePoint サーバーの全体管理**] をクリックします。
    
  
3. [ **アプリケーション構成の管理**] の下で、[ **サービス アプリケーションの管理**] をクリックします。
    
  
4. [サービス アプリケーションの管理] ページで、[ **Excel Services アプリケーション**] をクリックします。
    
  
5. [ **Excel Services アプリケーション**] ページで、[ **グローバル設定**] をクリックします。
    
  
6. [ **セキュリティ**] セクションで、[ **ファイル アクセス方法**] の下に、[ **プロセス アカウント**] オプションが表示されます。
    
  

### サービス拒否攻撃

Web サービスに対するサービス拒否攻撃では、攻撃者は非常に大きい、それぞれ異なる要求を Web サービスに対して生成します。その目的は、Web サービスの入力値の 1 つ以上の限界値を探ろうとすることです。
  
    
    
Microsoft インターネット インフォメーション サービス (IIS) の設定を使用して、Web サービスの最大要求サイズを設定することをお勧めします。
  
    
    
 **system.web** 要素の中の **httpRuntime** 要素にある **maxRequestLength** 属性を使用して、サーバーに対して大きいファイルを送信することによって行われるサービス拒否攻撃を防止します。既定のサイズは 4096 KB (4 MB) です。
  
    
    
詳しくは、「 [<httpRuntime> Element](http://msdn.microsoft.com/library/e9b81350-8aaf-47cc-9843-5f7d0c59f369.aspx)」および「 [<maxRequestLength> Element](http://msdn.microsoft.com/library/fd52b2c5-5014-4e6f-b869-4ea666dc83d6.aspx)」を参照してください。
  
    
    

### 呼び出し元のアプリケーションと Web サービス コンピューターとの間のスニッフィング

呼び出し元のアプリケーションと Excel Web Services が異なるコンピューターに展開されている場合、攻撃者は、呼び出し元のアプリケーションと Web サービス間のデータ転送ネットワーク トラフィックを傍受することがあります。この脅威は "スニッフィッング" または "盗聴" とも呼ばれます。
  
    
    
この脅威を軽減するために、以下のことをお勧めします。
  
    
    

- SSL (Secure Sockets Layer) を使用してセキュリティで保護されたチャネルをセットアップし、クライアントとサーバー間のデータ転送を保護します。SSL プロトコルは、ネットワークに物理的にアクセスしてパケットのスニッフィッングを行う攻撃者からデータを保護するために役立ちます。
    
  
- Excel Web Services を使用するカスタム アプリケーションが閉じたネットワーク内で実行されている場合 (たとえば、Excel Web Services が企業内の Web フロントエンド コンピューターに展開されている場合) は、該当するネットワークを物理的に保護します。
    
  
詳細については、「 [Securing Your Network](http://msdn.microsoft.com/library/af62ece0-0dd7-4b8e-ad12-4d13f2d60816.aspx)」および「 [SOAP のセキュリティ](http://msdn.microsoft.com/ja-jp/library/aa912494.aspx)」を参照してください。
  
    
    
Excel Services のトポロジ、スケーラビリティ、パフォーマンス、およびセキュリティについては、Microsoft SharePoint Server 2010 TechCenter を参照してください。
  
    
    

### なりすまし

Web サービスのインターネット プロトコル (IP) アドレスおよびポートを乗っ取られる脅威を軽減するため、SSL を使用することをお勧めします。これは、攻撃者が要求を受け取って Web サービスの代わりに応答するようになる事態を防止するために役立ちます。
  
    
    
SSL 証明書は、少数のプロパティと一致することが確認されます。その 1 つに、メッセージの発信元の IP アドレスがあります。攻撃者は、Web サービスの SSL 証明書を持っていない限り、IP アドレスの「なりすまし」を実行できません。
  
    
    
詳細については、「 [Securing Your Network](http://msdn.microsoft.com/library/af62ece0-0dd7-4b8e-ad12-4d13f2d60816.aspx)」を参照してください。
  
    
    

## Excel Services のユーザー定義関数 (UDF)


### 厳密な名前の依存関係

場合によっては、ユーザー定義関数 (UDF) アセンブリが、一緒に展開される他のアセンブリに依存していることがあります。依存関係にあるこれらの DLL がグローバル アセンブリ キャッシュに入っている場合、または UDF アセンブリと同じフォルダーに入っている場合は、DLL の読み込みが成功します。
  
    
    
ただし、後者の場合は、Excel Calculation Services が同じ名前の別のアセンブリを既に読み込んでいる場合に、読み込みに失敗する可能性があります。(アセンブリに厳密な名前が付いていない、または同じ名前の別のバージョンが展開されて読み込まれている、のいずれかの理由で読み込みに失敗します。)
  
    
    
次のシナリオについて考えてみましょう。次のようなディレクトリ構成になっています。
  
    
    

1. C:\\Udfs\\Udf01
    
    Udf01 フォルダーの内容は次のとおりです。
    
  - Udf01.dll 
    
  
  - dependent.dll (厳密な名前が付いていない)
    
  

    Udf01.dll ファイルは dependent.dll ファイルに依存しています。
    
  
2. C:\\Udfs\\Udf02
    
    Udf02 フォルダーの内容は次のとおりです。
    
  - Udf02.dll (Interop.dll に依存している)
    
  
  - dependent.dll (厳密な名前が付いていない)
    
  

    Udf02.dll ファイルは dependent.dll ファイルに依存しています。Udf01.dll の依存関係と Udf02.dll の依存関係では、同じ名前が共有されています。しかし、Udf02.dll の dependent.dll ファイルは、Udf01.dll の dependent.dll ファイルと同じではありません。
    
  
次のようなフローを想定します。
  
    
    

1. Udf01.dll は、最初に読み込まれる DLL です。Excel Calculation Services は dependent.dll を探し、Udf01.dll の依存ファイルを読み込みます。この場合は、dependent.dll です。 
    
  
2. Udf02.dll は、Udf01.dll より後に読み込まれます。Excel Calculation Services は、Udf02.dll が dependent.dll に依存していることを認識します。しかし、"dependent.dll" という名前の DLL は既に読み込まれています。したがって、Udf02.dll の dependent.dll ファイルは読み込まれず、現在読み込まれている dependent.dll ファイルが依存関係として使用されます。
    
  
この結果、Udf02.dll が必要とするオブジェクト (この例では、dependent.dll ファイル) がメモリに読み込まれていない状態になります。
  
    
    
名前の衝突を防止するため、依存関係にあるオブジェクトには厳密な名前を付け、一意の名前を使用することをお勧めします。
  
    
    

## 全般


### マネージ コード DLL の名前

アセンブリの名前を確実に一意にするため、「 [Namespace Naming Guidelines](http://msdn.microsoft.com/library/c08bc0d8-9b3a-4564-9af6-71699f62e00d.aspx)」に従った完全修飾クラス名を使用してください。
  
    
    
たとえば、Namespace.ClassName ではなくCompanyName.Hierarchichal.Namespace.ClassName を使用します。
  
    
    

## 関連項目


#### タスク


  
    
    
 [方法: 場所を信頼する](how-to-trust-a-location.md)
#### 概念


  
    
    
 [Excel Services のアーキテクチャ](excel-services-architecture.md)
  
    
    
 [SOAP API にアクセスする](accessing-the-soap-api.md)
  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
  
    
    
 [Excel Services の既知の問題およびヒント](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services ブログ、フォーラム、リソース](excel-services-blogs-forums-and-resources.md)
