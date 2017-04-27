---
title: [方法] SharePoint 2013 の PerformancePoint Services 用に表形式のデータ ソース エディタを作成する
ms.prod: SHAREPOINT
ms.assetid: 3136420a-f8a2-4677-8b69-1d5d9705d96f
---


# [方法] SharePoint 2013 の PerformancePoint Services 用に表形式のデータ ソース エディタを作成する
PerformancePoint サービス のカスタムの表形式データ ソース拡張機能のエディター コンポーネントを作成する方法について説明します。
## PerformancePoint サービス のカスタムのデータ ソース エディターについて
<a name="bk_intro"> </a>

PerformancePoint サービス では、カスタムのデータ ソース エディターを使用して、カスタムの表形式データ ソースにプロパティをセットすることができます。 エディターの要件と機能の詳細については、「 [カスタム PerformancePoint Services オブジェクトのエディター](http://msdn.microsoft.com/library/7c5924f1-91f3-436a-9d94-2e0dc454c8cc%28Office.15%29.aspx)」を参照してください。
  
    
    
以下の手順とコード例は、 [カスタム オブジェクト サンプル](http://msdn.microsoft.com/library/af021d52-7562-4e7a-9de4-e1fc5784a59d%28Office.15%29.aspx)の **SampleDataSourceEditor** クラスに基づいています。エディターはシン Web アプリケーションで、エディターを使用して、データ ソースの名前と説明の変更、株式シンボルの入力、プロキシ サーバー アドレスとキャッシュ ファイルの場所の指定を行うことができます。クラスの完全なコードは、「 [コード例: カスタムの表形式データ ソースの取得と更新](#BKMK_ExampleCode)」を参照してください。
  
    
    
サンプル エディターをテンプレートとして使用することをお勧めします。サンプルは PerformancePoint サービス API のオブジェクトを呼び出す方法を示し、リポジトリ操作 (オブジェクトの作成、更新など) の呼び出しを容易にするヘルパー オブジェクトを提供し、PerformancePoint サービス 開発のためのベスト プラクティスを示します。
  
    
    

## カスタムの PerformancePoint サービス 表形式データ ソース用エディターを作成する
<a name="BKMK_ConfigDSEditor"> </a>


  
    
    

1. PerformancePoint サービス をインストールするか、拡張機能で使用する DLL (手順 3 で表示) をコンピューターにコピーします。詳細については、「 [開発シナリオで使用される PerformancePoint Services DLL](http://msdn.microsoft.com/library/41e92619-8253-481d-82f9-35b6a6abc477%28Office.15%29.aspx)」を参照してください。
    
  
2. Visual Studio で、C# クラス ライブラリを作成します。拡張機能用クラス ライブラリを既に作成している場合は、新規 C# クラスを追加します。
    
    DLL には厳密な名前で署名する必要があります。さらに、DLL によって参照されたすべてのアセンブリが厳密な名前を持つことを確認してください。厳密な名前を使用してアセンブリに署名する方法の詳細、および公開/秘密キーのペアを作成する方法の詳細については、「 [How to: Create a public/private key pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114.aspx)」を参照してください。
    
  
3. プロジェクトに、アセンブリ参照として以下の DLL を追加します。
    
  - Microsoft.PerformancePoint.Scorecards.Client.dll
    
  
  - Microsoft.SharePoint.dll (ヘルパー クラスが使用)
    
  

    サンプル エディターには、System.Core.dll、System.Web.dll、System.Web.Services.dll、および System.Xml.Linq.dll へのアセンブリ参照も含まれます。拡張機能によっては、その他のプロジェクト参照が必要になることがあります。
    
  
4. サンプルから以下のクラスをプロジェクトに追加します。エディターはこれらのヘルパー クラスを使用して PerformancePoint サービス リポジトリとキャッシュ ファイルを操作します。
    
  - ExtensionRepositoryHelper.cs
    
  
  - DataSourceRepositoryHelper.cs
    
  
  - SampleDSCacheHandler.cs
    
  
5. エディター クラスで、 **Microsoft.PerformancePoint.Scorecards** 名前空間の **using** ディレクティブを追加します。拡張機能によっては、その他の **using** ディレクディブが必要になることがあります。
    
  
6. エディターの実装をサポートする基本クラスから継承します。サンプルのデータ ソース エディターは Web アプリケーションのため、 [Page](https://msdn.microsoft.com/library/System.Web.UI.Page.aspx) クラスから派生できます。他の実装では、 [UserControl](https://msdn.microsoft.com/library/System.Windows.Forms.UserControl.aspx) クラス、 [WebPart](https://msdn.microsoft.com/library/System.Web.UI.WebControls.WebParts.WebPart.aspx) クラスなどの基本クラスから派生できます。
    
  
7. ユーザーが表示または変更できるプロパティを表示するコントロールの変数を宣言します。サンプル データ ソース エディターでは、最初にユーザー インターフェイス コンポーネント (ASPX ページ) で定義されている Web サーバー コントロールの変数を宣言します。サンプル エディターでは、ユーザーが変更を送信できるボタン コントロールも定義します。 [CreateChildControls()](https://msdn.microsoft.com/library/System.Web.UI.Control.CreateChildControls.aspx) メソッドを呼び出して、これらのコントロールをページで使用できるようにします。
    
    > **メモ**
      > エディターは、ユーザー インターフェイスとは別のプログラミング ロジックを定義します。エディターのユーザー インターフェイス コンポーネントを作成するための説明は、この文書の範囲外となります。 

    サンプルのデータ ソース エディターでは、手順 8. ～ 11. が **Page_Load** メソッドで実行されます。変数とコントロールの初期化と検証、コントロールへのデータの挿入、カスタム データ ソースとヘルパー オブジェクトの状態情報の保存にも、 **Page_Load** が使用されます。
    
  
8. クエリ文字列からパラメーターを取得し、それらを以下のコード例で示すローカル変数のための値として設定します。
    
  ```cs
  
// The URL of the site collection that contains the PerformancePoint Services repository.
string server = Request.QueryString[ClickOnceLaunchKeys.SiteCollectionUrl];

// The location of the data source in the repository.
string itemLocation = Request.QueryString[ClickOnceLaunchKeys.ItemLocation];

// The operation to perform: OpenItem or CreateItem.
string action = Request.QueryString[ClickOnceLaunchKeys.LaunchOperation];
  ```


    クエリ文字列パラメーターの詳細については、「 [カスタム PerformancePoint Services オブジェクトのエディター](http://msdn.microsoft.com/library/7c5924f1-91f3-436a-9d94-2e0dc454c8cc%28Office.15%29.aspx)」を参照してください。
    
  
9. 以下のコード例で示すように、リポジトリへの呼び出しを行うための **DataSourceRepositoryHelper** オブジェクトを取得します。
    
  ```cs
  
DataSourceRepositoryHelper = new DataSourceRepositoryHelper();
  ```

10. 以下のコード例で示すように、クエリ文字列パラメーターに基づいてデータ ソースの場所を設定します。
    
  ```cs
  RepositoryLocation repositoryDataSourceLocation = RepositoryLocation.CreateFromUriString(itemLocation);
  ```

11. クエリ文字列から実行する操作 ( _OpenItem_ または _CreateItem_) を取得し、カスタム データ ソースを取得または作成します。
    
  - カスタム データ ソースを取得するには、 **DataSourceRepositoryHelper.Get** メソッドを使用します。
    
  
  - カスタム データ ソースを作成するには、 **DataSource()** コンストラクターを使用し、データソースの [Name](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Name.aspx) と [SubTypeId](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.SubTypeId.aspx) プロパティを定義します。 [SubTypeId](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.SubTypeId.aspx) はデータ ソースの一意の識別子で、PerformancePoint サービス web.config ファイルのカスタム データ ソースの **subType** 属性と一致する必要があります。
    
    > **メモ**
      > サンプルのデータ ソース エディターに、データ ソース オブジェクトを作成するためのロジックは含まれていません。カスタム オブジェクト作成の例については、「 [[方法] SharePoint 2013 の PerformancePoint Services 用のレポート エディタを作成する](how-to-create-report-editors-for-performancepoint-services-in-sharepoint-2013.md)」または「 [[方法] SharePoint 2013 の PerformancePoint Services 用のフィルター エディタを作成する](how-to-create-filter-editors-for-performancepoint-services-in-sharepoint-2013.md)」を参照してください。 

  ```cs
  if (ClickOnceLaunchValues.OpenItem.Equals(action, StringComparison.OrdinalIgnoreCase))
{
    // Use the repository-helper object to retrieve the data source.
    datasource = dataSourceRepositoryHelper.Get(repositoryDataSourceLocation);
    if (datasource == null)
    {
        displayError("Could not retrieve the data source for editing.");
        return;
    }
}
else
{
    displayError("Invalid Action.");
    return;
}
  ```


    > **メモ**
      > 既定では、ユーザーは PerformancePoint ダッシュボード デザイナー からのみカスタム オブジェクトを作成できます。ユーザーに ダッシュボード デザイナー の外でカスタム オブジェクトを作成できるようにするには、リポジトリのコンテンツ タイプから  _CreateItem_ 要求をエディターに送るメニュー項目を追加する必要があります。詳細については、「 [カスタム PerformancePoint Services オブジェクトのエディター](http://msdn.microsoft.com/library/7c5924f1-91f3-436a-9d94-2e0dc454c8cc%28Office.15%29.aspx)」を参照してください。 

    サンプルのデータ ソース エディターでは、手順 12. ～ 13. が **buttonOK_Click** および **CreateCacheFile** メソッドで実行されます。また、 **buttonOK_Click** を使用すると **AreAllInputsValid** メソッドが呼び出され、コントロールのコンテンツの検証およびカスタム データ ソースとヘルパー オブジェクトのステータス情報の取得も行われます。
    
  
12. データ ソースをユーザー定義の変更で更新します。サンプル データ ソース エディターは **DataSourceRepositoryHelper.Update** メソッドを呼び出して、リポジトリのデータ ソース オブジェクトの [Name](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Name.aspx) 、 [Description](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Description.aspx) 、 [CustomData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.CustomData.aspx) プロパティを更新します。 [CustomData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.CustomData.aspx) を使用し、シリアル化されたオブジェクトまたは文字列を格納できます。サンプル エディターは、これを使用して、ユーザー定義の株式シンボル、株の時価を格納するキャッシュ ファイルの場所、プロキシ サーバーの場所を格納します。
    
    > **メモ**
      > カスタム オブジェクトの  [Name](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Name.aspx) 、 [Description](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Description.aspx) 、 [Owner](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Owner.aspx) ([ **責任者**]) プロパティを編集して、ダッシュボード デザイナー と PerformancePoint サービス リポジトリからカスタム オブジェクトを直接削除することができます。 
13. 列のマッピングがまだ定義されていない場合、データ ソースのプロバイダーを呼び出して、列のマッピングを定義します。
    
  

## コード例: SharePoint Server 2013 のカスタムの PerformancePoint サービス 表形式データソースの取得と更新
<a name="bk_example"> </a>

次のコード例で、カスタムの表形式データ ソースの取得と更新を行います。このコードはエディターの分離コード クラスのもので、[ASPX] ページに定義されたコントロールのプログラミング ロジックを提供します。
  
    
    
このコード例をコンパイルできるようにするには、「 [PerformancePoint Services で表形式データ ソースのエディター クラスを作成して設定する](#BKMK_DefineDSEd)」で説明しているように開発環境を設定する必要があります。
  
    
    



```cs

using System;
using System.IO;
using System.Web.UI;
using System.Web.UI.WebControls;
using Microsoft.PerformancePoint.Scorecards;
using System.Xml.Linq;

namespace Microsoft.PerformancePoint.SDK.Samples.SampleDataSource
{
    // Represents the class that defines the sample data source editor.
    public class SampleDataSourceEditor : Page
    {

        #region Members
        // Declare private variables for the ASP.NET controls defined in the user interface.
        // The user interface is an ASPX page that defines the controls in HTML.
        private TextBox textboxName;
        private TextBox textboxDescription;
        private TextBox textboxStockSymbols;
        private TextBox textboxXMLLocation;
        private TextBox textboxProxy;
        private Label labelErrorMessage;
        private Button buttonOK;
        #endregion

        #region Page methods and events
        // Make the controls available to this class.
        protected override void CreateChildControls()
        {
            base.CreateChildControls();

            if (null == textboxProxy)
                textboxProxy = FindControl("textboxProxy") as TextBox;
            if (null == textboxName)
                textboxName = FindControl("textboxName") as TextBox;
            if (null == textboxDescription)
                textboxDescription = FindControl("textboxDescription") as TextBox;
            if (null == textboxStockSymbols)
                textboxStockSymbols = FindControl("textboxStockSymbols") as TextBox;
            if (null == textboxXMLLocation)
                textboxXMLLocation = FindControl("textboxXMLLocation") as TextBox;
            if (null == labelErrorMessage)
                labelErrorMessage = FindControl("labelErrorMessage") as Label;
            if (null == buttonOK)
                buttonOK = FindControl("buttonOK") as Button;
        }

        // Handles the Load event of the Page control.
        // Methods that use a control variable should call the Control.EnsureChildControls
        // method before accessing the variable for the first time.
        protected void Page_Load(object sender, EventArgs e)
        {
            // Initialize controls the first time the page loads only.
            if (!IsPostBack)
            {
                EnsureChildControls();

                DataSourceRepositoryHelper dataSourceRepositoryHelper = null;
                try
                {
                    // Get information from the query string parameters.
                    string server = Request.QueryString[ClickOnceLaunchKeys.SiteCollectionUrl];
                    string itemLocation = Request.QueryString[ClickOnceLaunchKeys.ItemLocation];
                    string action = Request.QueryString[ClickOnceLaunchKeys.LaunchOperation];

                    // Validate the query string parameters.
                    if (string.IsNullOrEmpty(server) ||
                        string.IsNullOrEmpty(itemLocation) ||
                        string.IsNullOrEmpty(action))
                    {
                        displayError("Invalid URL.");
                        return;
                    }

                    // Retrieve the repository-helper object.
                    dataSourceRepositoryHelper =
                        new DataSourceRepositoryHelper();

                    // Set the data source location.
                    RepositoryLocation repositoryDataSourceLocation = RepositoryLocation.CreateFromUriString(itemLocation);

                    DataSource datasource;

                    // Retrieve the data source object by
                    // using the repository-helper object.
                    if (ClickOnceLaunchValues.OpenItem.Equals(action, StringComparison.OrdinalIgnoreCase))
                    {
                        datasource = dataSourceRepositoryHelper.Get(repositoryDataSourceLocation);
                        if (datasource == null)
                        {
                            displayError("Could not retrieve the data source for editing.");
                            return;
                        }
                    }
                    else
                    {
                        displayError("Invalid Action.");
                        return;

                    }

                    // Save the original data source and helper objects across page postbacks.
                    ViewState["action"] = action;
                    ViewState["datasource"] = datasource;
                    ViewState["datasourcerepositoryhelper"] = dataSourceRepositoryHelper;

                    // Populate the child controls.
                    if (null != datasource.Name)
                        textboxName.Text = datasource.Name.ToString();

                    if (null != datasource.Description)
                        textboxDescription.Text = datasource.Description.ToString();

                    if (null != datasource.CustomData)
                    {
                        string[] splitCustomData = datasource.CustomData.Split('&amp;');
                        if (splitCustomData.Length > 2)
                        {
                            textboxStockSymbols.Text = splitCustomData[0];
                            textboxXMLLocation.Text = splitCustomData[1].Replace(@"\\SampleStockQuotes.xml", string.Empty);
                            textboxProxy.Text = splitCustomData[2];
                        }
                    }
                }
                catch (Exception ex)
                {
                    displayError("An error has occurred. Please contact your administrator for more information.");
                    if (dataSourceRepositoryHelper != null)
                    {
                        // Add the exception detail to the server
                        // event log.
                        dataSourceRepositoryHelper.HandleException(ex);
                    }
                }
            }
        }

        // Handles the Click event of the buttonOK control.
        protected void buttonOK_Click(object sender, EventArgs e)
        {
            EnsureChildControls();

            // Verify that the required fields contain values.
            if (!AreAllInputsValid())
                return;

            // Clear any pre-existing error message.
            labelErrorMessage.Text = string.Empty;

            // Retrieve the data source and helper objects from view state.
            string action = (string)ViewState["action"];
            DataSource datasource = (DataSource)ViewState["datasource"];
            DataSourceRepositoryHelper datasourcerepositoryhelper = (DataSourceRepositoryHelper)ViewState["datasourcerepositoryhelper"];

            // Update the data source object with form changes.
            datasource.Name.Text = textboxName.Text;
            datasource.Description.Text = textboxDescription.Text;

            // Define column mappings if they aren't already defined.
            if (datasource.DataTableMapping.ColumnMappings.Count <= 0)
            {
                datasource.DataTableMapping = WSTabularDataSourceProvider.CreateDataColumnMappings();
            }

            // Save the data source to the repository
            // by using the repository-helper object.
            try
            {
                CreateCacheFile(datasource);

                datasource.Validate();

                if (ClickOnceLaunchValues.OpenItem.Equals(action, StringComparison.OrdinalIgnoreCase))
                {
                    datasourcerepositoryhelper.Update(datasource);
                }
                else
                {
                    displayError("Invalid Action.");
                }
            }
            catch (Exception ex)
            {
                displayError("An error has occurred. Please contact your administrator for more information.");
                if (datasourcerepositoryhelper != null)
                {
                    // Add the exception detail to the server event log.
                    datasourcerepositoryhelper.HandleException(ex);
                }
            }
        }
        #endregion

        #region Helper methods
        // Display the error string in the labelErrorMessage label.
        void displayError(string msg)
        {
            EnsureChildControls();

            labelErrorMessage.Text = msg;

            // Disable the OK button because the page is in an error state.
            buttonOK.Enabled = false;
            return;
        }

        // Validate the text box inputs.
        bool AreAllInputsValid()
        {
            if (string.IsNullOrEmpty(textboxProxy.Text))
            {
                labelErrorMessage.Text = "The proxy server address is required.";
                return false;
            }

            if (string.IsNullOrEmpty(textboxXMLLocation.Text))
            {
                labelErrorMessage.Text = "The location to save the cache file to is required.";
                return false;
            }

            if (string.IsNullOrEmpty(textboxName.Text))
            {
                labelErrorMessage.Text = "A data source name is required.";
                return false;
            }

            if (string.IsNullOrEmpty(textboxStockSymbols.Text))
            {
                labelErrorMessage.Text = "A stock symbol is required.";
                return false;
            }

            return true;
        }

        // Create the XML cache file at the specified location and
        // store it and the stock symbols in the CustomData
        // property of the data source.
        void CreateCacheFile(DataSource datasource)
        {
            string cacheFileLocation = string.Format("{0}\\\\{1}", textboxXMLLocation.Text.TrimEnd('\\\\'),
                                                     "SampleStockQuotes.xml");

            datasource.CustomData = string.Format("{0}&amp;{1}&amp;{2}", textboxStockSymbols.Text, cacheFileLocation, textboxProxy.Text);

            // Check if the cache file already exists.
            if (!File.Exists(cacheFileLocation))
            {
                // Create the cache file if it does not exist.
                XDocument doc = SampleDSCacheHandler.DefaultCacheFileContent;
                doc.Save(cacheFileLocation);
            }
        }
        #endregion
    }
}
```


## 次の手順
<a name="bk_next"> </a>

データ ソースのエディター (必要な場合は、そのユーザー インターフェイスも含める) とデータ ソースのプロバイダーを作成したら、「 [[方法] PerformancePoint Services の拡張機能を手動で登録する](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)」に説明されているように拡張機能を配置します。
  
    
    

## その他の技術情報
<a name="bk_next"> </a>


-  [[方法] SharePoint 2013 で PerformancePoint Services 用の表形式のデータ ソース プロバイダーを作成する](how-to-create-tabular-data-source-providers-for-performancepoint-services-in-sha.md)
    
  
-  [SharePoint 2013 の PerformancePoint Services](performancepoint-services-in-sharepoint-2013.md)
    
  

