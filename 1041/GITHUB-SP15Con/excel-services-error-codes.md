---
title: Excel Services のエラー コード
keywords: alerts
f1_keywords:
- alerts
ms.prod: SHAREPOINT
ms.assetid: ff128d67-f3ac-4a8f-ae8e-1e19e343014e
---


# Excel Services のエラー コード

Excel Services は、Excel Services で発生するエラーに基づいて、SOAP 例外でエラーおよびエラー メッセージを生成します。次の表は、Excel Web Services メソッドの呼び出しが SOAP 例外をスローした場合にアクセスできるエラーを示します。 
  
    
    

エラー コードをキャプチャするには、 **SoapException** クラスの [SubCode](http://msdn.microsoft.com/library/frlrfSystemWebServicesProtocolsSoapExceptionClassSubCodeTopic.aspx) プロパティを使用します。エラー コードをキャプチャする **SubCode** プロパティの使用について、詳細は「 [SubCode プロパティを使用してエラー コードをキャプチャする方法](how-to-use-the-subcode-property-to-capture-error-codes.md)」を参照してください。
Excel Services のアラートについて、詳細は「 [Excel Services のアラート](excel-services-alerts.md)」を参照してください。 
  
    
    


## エラー コード

次の表は、Excel Web Services アラートのエラー コードと関連するメッセージ、説明、解決策を一覧表示したものです。 
  
    
    


|****Error Code****|****Message****|****Explanation****|****Resolution****|
|:-----|:-----|:-----|:-----|
|ApiInvalidArgument  <br/> |引数 {0} の値が無効です  <br/> |引数の無効な値が API の呼び出しに渡されました。  <br/> 0 = 引数の名前。この引数の値が無効です。  <br/> |引数に有効な値を使用します。  <br/> |
|ApiInvalidCoordinate  <br/> |{1} の{0}の座標が無効です。  <br/> |0 = 座標の名前 (行、列、高さ、幅)。  <br/> 1 = 座標構造を保持している引数の名前。  <br/> get または set 呼び出しでの **RangeCoordinates** クラスまたは row\\column\\height\\width パラメーターの内容が無効です。 <br/> |引数に有効な座標値を使用します。  <br/> |
|DimensionAndArrayMismatch  <br/> |指定した配列のサイズが、目的の範囲のサイズおよび形と一致しません。  <br/> |呼び出し元はブックに範囲を設定しようとしましたが、配列の値を含むパラメーターが目的の範囲と一致しません。  <br/> |指定した配列のサイズが目的の範囲のサイズと一致するようにしてください (えば、幅 2 列で高さ 3 行)。  <br/> |
|DiscontiguousRangeNotSupported  <br/> |範囲の要求が、隣接する範囲を参照していません。Excel Services では、隣接する範囲のみをサポートしています。  <br/> |呼び出し元は、セルの範囲を設定または取得しようとしたときに、連続していない範囲を指定しました。 Excel Services では、連続していない範囲はサポートしていません。連続した範囲のみをサポートします。  <br/> |「A1:B7, B12」または「A1,A3」などの連続していない範囲ではなく、「A1:B7」、「A1」、または「MyTable[#Data]」などの連続した範囲を入力します。  <br/> |
|ExternalDataRefreshFailed  <br/> |以下の接続の外部データを取得できません。  <br/> {0}  <br/> データ ソースに到達できないか、データ ソースが応答しないか、データ ソースへのアクセスが拒否された可能性があります。  <br/> |ブック内のデータ ソースの更新に失敗しました。  <br/> 0 は、接続名が \\n で区切られたリストです。  <br/> |データ ソースが利用可能であること、およびユーザーにアクセス権があることを確認します。  <br/> |
|FileOpenAccessDenied  <br/> |このファイルを Excel Services で開く権限がありません。  <br/> |ユーザーにファイルへのアクセス許可がないため、 **OpenWorkbook** メソッドの呼び出しが失敗しました。 <br/> |管理者に問い合わせてください。  <br/> |
|FileCorrupt  <br/> |選択したファイルは、壊れているか、Information Rights Management によって保護されているか、Excel Services がサポートしていないファイル形式のため、開くことができません。Excel はこのファイルを開くことができる場合があります。  <br/> |ファイルが壊れているため、 **OpenWorkbook** メソッドの呼び出しが失敗しました。 <br/> |再度ファイルを開くか、Excel を使用してファイルを開いてみます。  <br/> |
|FileOpenNotFound  <br/> |選択したファイルが見つかりませんでした。ファイルの名前と場所が正しいことを確認してください。  <br/> |ファイルが存在しないため、 **OpenWorkbook** メソッドの呼び出しが失敗しました。 <br/> |ファイルが名前変更、移動、または削除されていないこと、および信頼できる場所にあることを確認します。また、ユーザーがファイルにアクセスできることを確認します。問題が解決しない場合は、管理者に問い合わせてください。  <br/> |
|FileOpenSecuritySettings  <br/> |Excel Services のセキュリティの設定のため、選択したファイルは今の時点で開くことができません。  <br/> |**OpenWorkbook** メソッドの呼び出しが失敗しました。管理者のセキュリティ設定により、さまざまな理由からファイルが開けなくなっていることが原因です。理由とは、たとえばファイルが大きすぎる、つまりファイル サイズが管理者が設定した制限を超えているなどです。 <br/> |管理者に問い合わせてください。  <br/> |
|FormulaEditingNotEnabled  <br/> |Excel Services のこのリリースでは、数式を編集することはできません。  <br/> |呼び出し元がブックに数式を記述しようとしました。  <br/> |Excel Services のこのリリースでサポートされていないため、数式を記述しないでください。  <br/> |
|GenericFileOpenError  <br/> |選択したファイルを開くときにエラーが発生しました。  <br/> |Excel Services は、不明な理由により、ファイルを開くことができません。  <br/> |数分待ってから、再度ファイルを開いてみてください。 問題が解決しない場合は、管理者に問い合わせてください。  <br/> |
|InvalidSheetName  <br/> |要求したワークシートがブックにありません。  <br/> |シート名が見つからなかったか、無効でした。  <br/> |シート名に有効な値を使用します。  <br/> |
|InvalidOrTimedOutSession  <br/> |セッションがサーバー上で利用できなくなったため、この時点で実行した操作を完了できません。ブックを再度読み込んでから、新しいセッションを作成することができます。ただし、変更を行っていても失われました。  <br/> |呼び出し  _sessionId_ の値は、無効であるか、タイム アウトになっています。 <br/> |新しいセッションでブックを再度読み込んでください。  <br/> |
|IRMedWorkbook  <br/> |要求されたブックは IRM で保護されています。 Excel Services は IRM で保護されたブックを読み込むことができません。  <br/> |ブックが Information Rights Management (IRM) で保護されているため、 **OpenWorkbook** メソッドの呼び出しが失敗しました。 <br/> |IRM で保護されていないブックのみを渡します。  <br/> |
|MaxSessionsPerUserExceeded  <br/> |1 ユーザーが使用できるセッションの最大数を超えました。操作を完了できません。  <br/> |ユーザーが任意の時点に開くことができたセッションが最大数を超えています。この制限は管理者によって設定されます。  <br/> |制限を超えないようにするか、管理者に問い合わせてください。  <br/> |
|MultipleRequestsOnSession  <br/> |既にこのセッションでは操作を処理中です。セッションでは一度に 1 つの操作しか処理できません。  <br/> |同じセッションで複数の要求が発行されています。セッションは一度に 1 つの要求しか処理できません (少数の例外あり)。  <br/> |もう一度操作を実行してください。  <br/> |
|NotMemberOfRole  <br/> |アクセスが拒否されました。この操作を実行する、またはこのリソースにアクセスする許可がありません。  <br/> |呼び出し元には、サーバーへのアクセス権限がありません。  <br/> |管理者に問い合わせてください。  <br/> |
|ObjectTypeNotSupported  <br/> |Excel Services でサポートされていないオブジェクトの種類が指定されていました。操作はロールバックされました。  <br/> |呼び出し元は、サポートされていないオブジェクト型の値を範囲に書き込もうとしました。  <br/> |サポートされているオブジェクト型のいずれかを使用して操作をやり直してください。  <br/> |
|OperationCanceled  <br/> |操作は取り消されました。  <br/> |ユーザーが **CancelRequest** メソッドを呼び出しているため、現在実行中の操作が取り消されました。 <br/> |**CancelRequest** メソッドは、現在の操作を取り消す場合にのみ呼び出してください。 <br/> |
|RangeParseError  <br/> |範囲の要求を解析できませんでした。  <br/> |A1 サフィックス付きのメソッド ( **SetCellA1**、 **SetRangeA1**、 **GetCellA1**、 **GetRangeA1**) に渡された範囲が解析できませんでした。  <br/> |「Sheet1!Range("A6:A15")」などの A1 表記、または「[ShipCity].[#Headers]」などの有効な構造参照を使用して範囲参照を入力します。  <br/> |
|RangeRequestAreaExceeded  <br/> |要求された範囲の領域が 1,000,000 セルを超えています。  <br/> |要求された範囲が 1,000,000 のセル制限を超えています。  <br/> |1,000,000 セルを超える範囲を返すためには、複数の呼び出しを使用します。  <br/> |
|RetryError  <br/> |要求を処理できません。  <br/> |Excel Services は、時々リソース不足の状態に達することがあります。このような場合、要求が拒否され始めることがあります。  <br/> |数分待ってから、もう一度操作を実行してください.  <br/> |
|SaveFailed  <br/> |ファイルを保存するときにエラーが発生しました。  <br/> |**GetWorkbook** メソッドの呼び出しが失敗しました。 <br/> |再度ファイルを保存してみてください。  <br/> |
|SetRangeFailure  <br/> |要求された操作により、編集できないセルの内容が上書きされようとしました。  <br/> |呼び出し元が、保護されたセルがある範囲に値を書き込もうとしました。たとえば、セルに数式が含まれている場合などです。  <br/> |Excel Services が編集できるのは、空のセルまたは値を含むセルのみです。  <br/> |
|SheetRangeMismatch  <br/> |シート引数として指定されたシートが、範囲引数で指定されたシートと同じではありません。  <br/> | _sheetName_ パラメーターに渡されたシート名が、 _rangeName_ パラメーターで指定されたシートの場所と一致しません。 <br/> |範囲とシートの引数の両方にシートを指定する場合は、シート名が同じであることを確認してください。たとえば、 `Calculate(Sheet1, Sheet1!Range("A1"))` と指定します。 <br/> |
|SpecifiedRangeNotFound  <br/> |要求した範囲がシートにありません。  <br/> |A1 サフィックス付きのメソッド ( **SetCellA1**、 **SetRangeA1**、 **GetCellA1**、 **GetRangeA1**) に渡された範囲が見つかりませんでした。  <br/> |指定した範囲がシートに存在していることを確認します。  <br/> |
|WorkbookNotSupported  <br/> |Excel Services でサポートされていない機能が含まれているために、選択したファイルを開くことができません。次のサポートされていない機能のうち 1 つ以上がブック内で検出されました。  <br/> {0}  <br/> |ブックには、サポートされていない機能が含まれています。  <br/> 0 = サポートされていない機能名の \\n で区切られたリストです。  <br/> |Excel Services によってサポートされていない機能がブックに含まれないようにします。  <br/> |
   

## 関連項目


#### タスク


  
    
    
 [SubCode プロパティを使用してエラー コードをキャプチャする方法](how-to-use-the-subcode-property-to-capture-error-codes.md)
#### 概念


  
    
    
 [Excel Services のアラート](excel-services-alerts.md)
  
    
    
 [Excel Services の既知の問題およびヒント](excel-services-known-issues-and-tips.md)
  
    
    
 [Excel Services のベスト プラクティス](excel-services-best-practices.md)
