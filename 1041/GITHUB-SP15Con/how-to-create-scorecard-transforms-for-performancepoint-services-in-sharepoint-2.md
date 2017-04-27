---
title: [方法] SharePoint 2013 の PerformancePoint Services 向けにスコアカード変換を作成する
ms.prod: SHAREPOINT
ms.assetid: 16117716-6ce5-4890-a829-5312f76164d0
---


# [方法] SharePoint 2013 の PerformancePoint Services 向けにスコアカード変換を作成する
SharePoint Server 2013 の PerformancePoint サービス 用のカスタムのスコアカード変換を作成する方法を説明します。
## PerformancePoint サービス のスコアカード変換の概要
<a name="bk_intro"> </a>

PerformancePoint サービス のスコアカード変換では、スコアカード ビューをダッシュボードに表示する前に、その外観、コンテンツ、または機能を変更できます。詳細については、 [PerformancePoint Services スコアカード変換の概要](http://msdn.microsoft.com/library/d69d171b-827a-48a8-a3e1-7aaf0bfbc7f8%28Office.15%29.aspx) を参照してください。
  
    
    

## PerformancePoint サービス スコアカードの変換を作成する
<a name="BKMK_CreateClass"> </a>


1. PerformancePoint サービス をインストールします。または、PerformancePoint サービス と一緒にインストールされた DLL をコンピューターにコピーします。詳細は、 [開発シナリオで使用される PerformancePoint Services DLL](http://msdn.microsoft.com/library/41e92619-8253-481d-82f9-35b6a6abc477%28Office.15%29.aspx) を参照してください。
    
  
2. Visual Studio で、C# クラス ライブラリを作成します。拡張機能用に既にクラス ライブラリを作成済みの場合は、新しい C# クラスを追加します。
    
    DLL には厳密な名前で署名する必要があります。さらに、DLL によって参照されるすべてのアセンブリが厳密な名前を持つことを確認してください。厳密な名前を使用してアセンブリに署名する方法の詳細、および公開/秘密キーのペアを作成する方法の詳細については、 [How to: Create a Public/Private Key Pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114.aspx) を参照してください。
    
  
3. Microsoft.PerformancePoint.Scorecards.Client.dll をアセンブリ参照としてプロジェクトに追加します。
    
  
4. 次の名前空間について **using** ディレクティブを追加します。
    
  - **Microsoft.PerformancePoint.Scorecards**
    
  
  - **Microsoft.PerformancePoint.Scorecards.Extensions**
    
  
  - **System.Collections.Generic**
    
  
5.  [IGridViewTransform](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.IGridViewTransform.aspx) インターフェイスを実装します。
    
  
6.  [GetId](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.IGridViewTransform.GetId.aspx) メソッドを上書きして、変換の文字列識別子を返すようにします。 [GetId](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.IGridViewTransform.GetId.aspx) は、PerformancePoint サービス web.config ファイルで変換用に登録されている **key** 属性と同じ文字列を返す必要があります。スコアカード変換の登録の詳細については、 [[方法] PerformancePoint Services の拡張機能を手動で登録する](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx) を参照してください。
    
  
7.  [GetTransformType](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.IGridViewTransform.GetTransformType.aspx) メソッドを上書きして、変換の実行タイミングを指定します。変換を実行するポイントは、 [GridViewTransformType](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.GridViewTransformType.aspx) 列挙に定義されているそのタイプ ( **PreQuery**、 **PostQuery**、または **PreRender**) によって決まります。詳細については、 [PerformancePoint Services スコアカード変換の概要](http://msdn.microsoft.com/library/d69d171b-827a-48a8-a3e1-7aaf0bfbc7f8%28Office.15%29.aspx) を参照してください。
    
  
8.  [Execute](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Extensions.IGridViewTransform.Execute.aspx) メソッドを上書きして、スコアカードを変換する方法を定義します。以下のコード例は、スコアカード ビューに列を追加する方法と、空のスコアカード セルの書式設定を変更する方法を示します。
    
  
DLL の署名と構築を行った後、 [[方法] PerformancePoint Services の拡張機能を手動で登録する](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx) の説明のとおりに拡張機能をインストールします。
## コード例 1: PerformancePoint サービス スコアカードに列を追加する
<a name="bk_example1"> </a>

以下のコード例は、列のリーフ レベルで KPI を含むレンダリングされたスコアカード ビューに列を追加する **PreQuery** 変換を作成しています (スコアカード ビューの KPI の下にメンバーが含まれる場合、列は追加されません)。
  
    
    
このコード例をコンパイルできるようにするには、 [PerformancePoint サービス スコアカードの変換を作成する](#BKMK_CreateClass)で説明されているように開発環境を設定する必要があります。
  
    
    



```cs

using System;
using System.Collections.Generic;
using Microsoft.PerformancePoint.Scorecards;
using Microsoft.PerformancePoint.Scorecards.Extensions;

namespace Microsoft.PerformancePoint.SDK.Samples.ScorecardTransforms.PreQuery
{

    // Represents the class that adds columns of data to a scorecard view. 
    public class AddColumnTransform : IGridViewTransform
    {

        // Set transform type to PreQuery.
        public GridViewTransformType GetTransformType()
        {
            return GridViewTransformType.PreQuery;
        }

        // Return the string identifier of your transform. This value must
        // match the key attribute registered in the web.config file.
        public string GetId()
        {
            return "AddColumn";
        }

        // Run the transform to add a column. 
        public void Execute(GridViewData viewData, PropertyBag parameters, IGlobalCache cache)
        {
            // Verify the scorecard definition.
            if (viewData == null)
            {
                throw new ArgumentException("Parameter cannot be null", "viewData");
            }
                     
            List<GridHeaderItem> leafRowHeaders = viewData.RootRowHeader.GetAllLeafHeadersInTree();

            foreach (GridHeaderItem rowHeader in leafRowHeaders)
            {
                if (rowHeader.HeaderType == ScorecardNodeTypes.Kpi)
                {
                    Kpi kpi = cache.GetKpi(rowHeader.LinkedKpiLocation);
                    if (kpi != null &amp;&amp; viewData.RootColumnHeader != null)
                    {

                        // Create the column header and add it to the root.
                        GridHeaderItem theNewColumn = GridHeaderItem.CreateDetailsHeader(kpi.Owner.DisplayName);

                        // Set the GUIDs for the data headers.
                        // Setting the DefinitionGuid property to the
                        // same value as the root column header enables
                        // Dashboard Designer to display the scorecard. 
                        // Note: Do not try to modify or delete the new
                        // column from within Dashboard Designer.
                        theNewColumn.DefinitionGuid = viewData.RootColumnHeader.DefinitionGuid;
                        theNewColumn.Parent = viewData.RootColumnHeader;
                        theNewColumn.Guid = new Guid();

                        // Insert the column at the end of the collection
                        // of child elements.
                        if (viewData.RootColumnHeader.Children.Count != 0)
                        {
                            viewData.RootColumnHeader.Children.Insert(viewData.RootColumnHeader.Children.Count, theNewColumn);
                        }
                                                                         
                        break;
                    }
                }
            }
            viewData.RootColumnHeader.LinkAndIndexTreeFromRoot();
        }
    }
}
```


## コード例 2: PerformancePoint サービス スコアカードの空のセルの書式設定を変更する
<a name="bk_example2"> </a>

以下のコード例では、空のスコアカード セルにグレーの背景色を適用する **PreQuery** 変換を作成します。
  
    
    

> **メモ**
> このコード例をコンパイルできるようにするには、 [PerformancePoint サービス スコアカードの変換を作成する](#BKMK_CreateClass)で説明されているように開発環境を設定する必要があります。 さらに、 **System.Drawing** アセンブリへの参照をプロジェクトに追加する必要があります。
  
    
    


```cs

using System;
using System.Collections.Generic;
using Microsoft.PerformancePoint.Scorecards;
using Microsoft.PerformancePoint.Scorecards.Extensions;

namespace Microsoft.PerformancePoint.SDK.Samples
{

    // Represents a transform that applies a grey background color to empty scorecard cells.
    public class GreyEmptiesTransform : IGridViewTransform
    {

        // Set the transform type to "PreRender".
        public GridViewTransformType GetTransformType()
        {
            return GridViewTransformType.PreRender;
        }

        // Return the string identifier of the transform.
        public string GetId()
        {
            return "GreyEmptyCells";
        }

        // Run the transform.
        public void Execute(GridViewData viewData, PropertyBag parameters, IGlobalCache cache)
        {
            // Validate parameters. 
            if (viewData == null)
            {
                throw new ArgumentException("Parameter cannot be null", "viewData");
            }

            // Get the headers under the root row header.
            List<GridHeaderItem> nonLeafRowHeaders = viewData.RootRowHeader.GetAllHeadersInTree();

            // Get the leaf headers under the root column header.
            List<GridHeaderItem> leafColumnHeaders = viewData.RootColumnHeader.GetAllLeafHeadersInTree();

            foreach (GridHeaderItem rowHeader in nonLeafRowHeaders)
            {
                foreach (GridHeaderItem columnHeader in leafColumnHeaders)
                {
                    // Get scorecard cells.
                    GridCell cell = viewData.Cells[rowHeader, columnHeader];

                    if (cell.IsCellEmpty || string.IsNullOrEmpty(cell.ActualValue.ToString()))
                    {
                        GridFormatInfo emptyFormat = new GridFormatInfo(viewData.DefaultCellFormatInfo);
                        emptyFormat.BackColor = new GridColor(System.Drawing.Color.Gray);
                        cell.FormatInfo = emptyFormat;
                    }
                    viewData.Cells[rowHeader, columnHeader] = cell;
                }
            }
        }
    }
}


```


## その他の技術情報
<a name="bk_addResources"> </a>


-  [SharePoint 2013 の PerformancePoint Services](performancepoint-services-in-sharepoint-2013.md)
    
  
-  [PerformancePoint Services スコアカード](http://msdn.microsoft.com/library/e77eccdb-82b3-483a-bb91-dfdc716400dd%28Office.15%29.aspx)
    
  

