---
title: 方法 埋め込まれたブックと Bing 地図を使ったマッシュアップの作成
ms.prod: EXCEL
ms.assetid: 3cfeb8d7-84b8-4673-bc92-b176cba4ac3e
---


# 方法: 埋め込まれたブックと Bing 地図を使ったマッシュアップの作成

この記事では、埋め込まれた Excel ブックと Bing 地図を組み合わせる強力な Web ベースのマッシュアップについて説明します。
  
    
    


## "Destination Explorer" について

Destination Explorer は、ユーザーが地域、目的地の種類 (都市または公園)、地域における特定の目的地を選択し、天気情報や目的地への月ごとの訪問者数を確認できるマッシュアップです。
  
    
    
ユーザーが UI からさまざまなオプションを選択する際、イベントを処理して OneDrive 上のブックに変更内容を反映するのに JavaScript が使用されます。ブックは、変更内容に基づいて自体を再計算し、コールバック関数を使用し終えると Destination Explorer に通知します。ユーザーが変更した内容に基づいて、Destination Explorer は、Travel ブックからより多くのデータを取得し、Bing 地図のビューを更新し、グラフを非表示にし、現在表示されているグラフを入れ替えます。
  
    
    
 **"Travel ブック"**
  
    
    
Destination Explorer は、すべての目的地名、天気と訪問者数の統計、月ごとの訪問者数と月ごとの訪問者のデータを表示する 2 つのグラフを含む、埋め込まれたブックに大きく依存しています。
  
    
    
 **Excel Services JavaScript API**
  
    
    
このマッシュアップは、ブックを埋め込んで操作するのに Excel Services JavaScript API を使用します。Excel Services JavaScript API は、コード内の API ソースの場所を参照するだけで使用できます。Excel Services JavaScript API にアクセスできるようになると、プログラムを使った Excel ブック埋め込みと作業が可能になります。
  
    
    
 **Bing 地図 JavaScript API**
  
    
    
このマッシュアップでも、Bing 地図 API を使用して Bing 地図内のブックで選択された場所を表示します。他のすべての JavaScript ライブラリと同様、コード内の API ライブラリを参照するだけでマッシュアップに Bing 地図を含めることができます。
  
    
    

## "Destination Explorer" マッシュアップの作成

このマッシュアップを作成するには、3 つの基本的な手順に従います。
  
    
    

1. OneDrive 上にブックを保存します。詳細については、 [OneDrive](https://onedrive.live.com/about/ja-jp/) ページを参照してください。
    
  
2. ページにブックを埋め込みます。OneDrive からのブックの埋め込みの詳細については、 [こちら](http://office.microsoft.com/ja-jp/excel-help/share-it-embed-an-excel-workbook-on-your-blog-HA102029502.aspx?CTT=5&amp;origin=HA102775335)を参照してください。
    
  
3. Bing 地図とマッシュアップします。この手順は、次のセクションで詳しく説明されています。
    
  

  
    
    

## Excel Services と Bing 地図のマッシュアップ

OneDrive 上のパブリック フォルダーにブックを保存し、ホスト Web ページにブックを埋め込んだ後に、埋め込まれたブック上の操作と Bing 地図の機能が組み合わされ、Destination Explorer マッシュアップが作成されます。
  
    
    
統合は、次の 3 つの手順で行われます。
  
    
    

- マッシュアップのページ構造を作成する
    
  
- 埋め込まれたブックのグラフと Bing 地図を初期化する
    
  
- 適切なコールバック関数を作成する
    
  

1. **マッシュアップのページ構造を作成する**
    
    Web ページの HTML 選択コントロールには、ページが読み込まれたとき、またはユーザーが現在の地域または目的地の種類を変更したときに Travel ブックからのデータが読み込まれます。この選択コントロールの定義 (目的地) は、 **スニペット 1** に表示されます。 **スニペット 1** には、ページ上の **chartDiv** 、 **chartDiv2** 、 **mapDiv** などの他の重要な要素の定義も含まれます。chart div 要素は、Travel ブックで定義されている 2 つのグラフのコンテナーです。map div は、Bing 地図のコンテナーです。
    
    **スニペット 1: Web ページの構造化**
    


  ```HTML
  
<!-- HTML omitted for brevity -->
    <select id="destinations" style="width: 150px" name="destinations"
      onchange="onDestinationChange()">
    </select>
    <!-- HTML omitted for brevity -->
    <div id="chartDiv" style="width: 483px; height: 318px"></div>
    <div id="chartDiv2" style="width: 483px; height: 318px; display: none"></div>
    <!-- HTML omitted for brevity -->
    <div id="mapDiv" style="position:relative; width:693px; height:400px;"></div>
    <!-- HTML omitted for brevity -->

  ```

2. **埋め込まれたブックのグラフと Bing 地図を初期化する**
    
    次の手順は、ページが読み込まれたときに Excel コンポーネントと Bing 地図を初期化します。埋め込まれた Excel ブックをプログラムでアクセスするには、ファイル トークンを使って参照する必要があります。ブックの適切なファイル トークンを取得する方法の詳細については、「 [http://msdn.microsoft.com/ja-jp/library/hh315812.aspx](http://msdn.microsoft.com/ja-jp/library/hh315812.aspx%28Office.15%29.aspx)」を参照してください。
    
    **スニペット 2** のコードによって、 **Page_Load** イベント ハンドラーで 3 つの主要なタスクが完了します。最初に、Travel ブックへの参照を確立して、Web ページ上の **chartDiv** 要素にあるグラフ 1 という名前のグラフを表示します。次に、 **GetMap** という名前の単純な関数を呼び出して、Bing 地図を初期化します。最後に、Travel ブックに 2 つ目の参照を作成して、 **chartDiv2** 要素にあるグラフ 2 とい名前のグラフを表示します。
    
    **スニペット 2: ページの初期化**
    


  ```
  
// Use this file token to reference your OneDrive hosted workbook in Excel's APIs
    var fileToken = "TOKEN TO YOUR WORKBOOK GOES HERE";
    var map;
    var ewaChart = null;
    var ewaChart2 = null;
  
    // Set the page event handlers for onload and unload.
    if (window.attachEvent) {
    window.attachEvent("onload", Page_Load);
    }
    else {
    // For some browsers window.attachEvent does not exist.
    window.addEventListener("DOMContentLoaded", Page_Load, false);
    }
  
    hideCharts();
     
    // Page load event handler
    function Page_Load() {
     
    // Load Excel Chart
    var props = {
    item: "Chart 1",
    uiOptions: {
    showParametersTaskPane: false
    },
    interactivityOptions: {
    allowTypingAndFormulaEntry: true,
    allowParameterModification: false,
    allowSorting: false,
    allowFiltering: false,
    allowPivotTableInteractivity: false
    }
    };
    Ewa.EwaControl.loadEwaAsync(fileToken, "chartDiv", props, onEwaChartLoaded);
     
    // Load the Bing map
    GetMap();

    // Load the 2nd Excel Chart
    var props = {
    item: "Chart 2",
    uiOptions: {
    showParametersTaskPane: false
    },
    interactivityOptions: {
    allowTypingAndFormulaEntry: true,
    allowParameterModification: false,
    allowSorting: false,
    allowFiltering: false,
    allowPivotTableInteractivity: false
    }
    };
    Ewa.EwaControl.loadEwaAsync(fileToken, "chartDiv2", props, onEwaChart2Loaded);
    }
     
    // Setup the Bing Map's initial view
    function GetMap() {
     
    map = new Microsoft.Maps.Map(document.getElementById("mapDiv"),
    { credentials: "YOUR CREDENTIALS",
    center: new Microsoft.Maps.Location(37.2802459560, -112.738963),
    mapTypeId: Microsoft.Maps.MapTypeId.road,
    zoom: 3 });

  ```

3. **適切なコールバック関数を作成する**
    
    Excel Services JavaScript API の関数へのすべての呼び出しでは、通常、コールバックを関数へのパラメーターとして扱います。コールバック パラメーターは、Excel Services JavaScript API への呼び出しが完了したときに実行する必要のある JavaScript の関数の名前です。 **EwaControl.loadEwaAsync** 関数で使用されているコールバックは、 **スニペット 2** で確認できます。
    


  ```
  
Ewa.EwaControl.loadEwaAsync(fileToken, "chartDiv", props, onEwaChartLoaded);
  ```


    ここで使用されるコールバックは、 **onEwaChartLoaded** です。これによって、Excel Services JavaScript API への次の呼び出しチェーンと Destination Explorer 内のコールバックを起動します。このチェーンで使用されるコールバックは次の通りです。
    
  - **onEwaChartLoaded()** - この関数は、グラフに関連付けられている Excel Web Access コントロールへの参照を保存します。コントロールを取得すると、メソッド **getRangeA1Async()** を呼び出して、OutputTopFiveDetails という名前で表される範囲を取得します。
    
  
  - **onGotDetailRange()** - **getRangeA1Async()** への呼び出しによって、値ではなく範囲が返されるため、このコールバックによってメソッド **getValuesAsync()** が呼び出され、範囲に関連付けられている値を取得します。
    
  
  - **onGotDetailValues()** - 範囲に関連付けられている値が後で使用するために変数に格納され、このメソッドは Destination Explorer で定義される次のメソッドを呼び出します。
    
  - **loadDestinations()** - 選択要素を範囲 OutputTopFiveDetails 内の目的地に設定します
    
  
  - **updateMap()** - 必要に応じて地図を更新します
    
  
  - **updateChart()** - 必要に応じてグラフを更新します
    
  

    **スニペット 3** で示されるコールバックのチェーンの目的は、HTML ページに示されるデータを更新することです。Travel ブックには、データの変更に使用する別のコールバック関数のチェーンがあります。たとえば、地域を北米からヨーロッパに変更すると、目的地の一覧の再設定、地図の更新、グラフの非表示などの操作を実行する必要があります。最初に目的地の一覧を再設定する必要があり、それには Excel のデータの更新が含まれます。 **スニペット 3** には、これらのタスクのためのコードが示されています。 **updateExcel()** という名前の関数と、 **onGotRange()** という名前の関連付けられているコールバックは、Travel ブックの入力ワークシートの値を変更するためのいくつかの作業を処理します。
    
    **スニペット 3: Travel ブックの入力を変更するためのコールバック チェーン**
    


  ```
  // Event handler called when user selects a different region.
    function onRegionChange() {
    currentDestination = '';
    var e = document.getElementById("regions");
    currentRegion = e.options[e.selectedIndex].text;
    updateExcel();
    }
     
    // Event handler called when user selects a different destination.
    function onDestinationChange() {
    var select = document.getElementById('destinations');
    var i = select.selectedIndex;
    currentDestination = select.options[i].text;
    updateChart();
    updateMap(false);
    }
    // Event handler called when user selects a different destination type.
    function onTypeChange(type) {
    currentDestination = '';
    currentDestinationType = type;
    updateExcel();
    }
     
    // Called from onTypeChange and onRegionChange when user selects a different destination type or region
    function updateExcel() {
    ewaChart.getActiveWorkbook().getRangeA1Async("Input!Inputs", onGotRange, 0);
    ewaChart2.getActiveWorkbook().getRangeA1Async("Input!Inputs", onGotRange, 1);
    }
     
    // Callback - called from updateExcel - sets input values according to user selections
    function onGotRange(result) {
    var range = result.getReturnValue();
    var values = new Array(2);
    values[0] = new Array(1);
    values[0][0] = currentRegion;
    values[1] = new Array(1);
    values[1][0] = currentDestinationType;
    range.setValuesAsync(values, null, null);
     
    // Initiate process of refreshing the script variable detailRangeValues
    if (result.getUserContext() == 0)
    ewaChart.getActiveWorkbook().getRangeA1Async("Output!OutputTopFiveDetails", onGotDetailRange, null);
    }

  ```


## まとめ
<a name="bk_addresources"> </a>

このチュートリアルでは、Web 開発者が Excel Services や他のテクノロジを使用して、リッチで対話的なマッシュアップを作成する方法の例を示します。
  
    
    

