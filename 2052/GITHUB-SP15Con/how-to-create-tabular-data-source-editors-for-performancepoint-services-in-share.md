---
title: 如何：为 SharePoint 2013 中的 PerformancePoint Services 创建表格数据源编辑器
ms.prod: SHAREPOINT
ms.assetid: 3136420a-f8a2-4677-8b69-1d5d9705d96f
---


# 如何：为 SharePoint 2013 中的 PerformancePoint Services 创建表格数据源编辑器
学习如何创建 PerformancePoint Services 的自定义表格格式数据源扩展名的编辑器组件。
## 什么是 PerformancePoint Services 的自定义数据源编辑器？
<a name="bk_intro"> </a>

在 PerformancePoint Services 中，自定义数据源编辑器使用户能够设置自定义表格格式数据源的属性。有关编辑器要求和功能的详细信息，请参阅  [用于自定义 PerformancePoint Services 对象的编辑器](http://msdn.microsoft.com/library/7c5924f1-91f3-436a-9d94-2e0dc454c8cc%28Office.15%29.aspx)。
  
    
    
以下过程和代码示例基于 [ 自定义对象示例](http://msdn.microsoft.com/library/af021d52-7562-4e7a-9de4-e1fc5784a59d%28Office.15%29.aspx) 中的 **SampleDataSourceEditor** 类。此编辑器是一类瘦 Web 应用程序，用户可利用它执行以下操作：修改数据源的名称和说明、输入股票代号和指定代理服务器地址和缓存文件位置。有关该类的完整代码，请参阅 [代码示例：检索和更新自定义表格格式数据源](#BKMK_ExampleCode)。
  
    
    
我们建议您将示例编辑器用作模板。该示例演示了如何调用 PerformancePoint Services API 中的对象，提供了简化库操作（例如创建和更新对象）调用的帮助程序对象，并演示了 PerformancePoint Services 开发的最佳实践。
  
    
    

## 为自定义 PerformancePoint Services 表格格式数据源创建编辑器
<a name="BKMK_ConfigDSEditor"> </a>


  
    
    

1. 安装 PerformancePoint Services，或者将您的扩展使用的 DLL（步骤 3 中列出）复制到您的计算机上。有关详细信息，请参阅  [开发方案中使用的 PerformancePoint Services DLL](http://msdn.microsoft.com/library/41e92619-8253-481d-82f9-35b6a6abc477%28Office.15%29.aspx)。
    
  
2. 在 Visual Studio 中，创建一个 C# 类库。如果您已为扩展创建了一个类库，请添加新 C# 类。
    
    您必须用强名称对您的 DLL 进行签名。此外，请确保您的 DLL 所引用的所有程序集都具有强名称。有关如何使用强名称对程序集进行签名以及如何创建公钥/私钥对的信息，请参阅  [How to: Create a public/private key pair](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114.aspx)。
    
  
3. 将以下 DLL 作为程序集引用添加到项目：
    
  - Microsoft.PerformancePoint.Scorecards.Client.dll
    
  
  - Microsoft.SharePoint.dll（由帮助程序类使用）
    
  

    示例编辑器还包含对 System.Core.dll、System.Web.dll、System.Web.Services.dll 和 System.Xml.Linq.dll 的程序集引用。可能需要其他项目引用，具体取决于您的扩展的功能。
    
  
4. 将示例中的以下类添加到项目中。您的编辑器使用这些帮助程序类与 PerformancePoint Services 存储库和缓存文件进行交互：
    
  - ExtensionRepositoryHelper.cs
    
  
  - DataSourceRepositoryHelper.cs
    
  
  - SampleDSCacheHandler.cs
    
  
5. 在编辑器类中，为 **Microsoft.PerformancePoint.Scorecards** 命名空间添加一个 **using** 指令。根据您的扩展的功能，可能需要其他 **using** 指令。
    
  
6. 从支持您的编辑器实现的基类继承。由于示例数据源编辑器是一个 Web 应用程序，因此它继承自  [Page](https://msdn.microsoft.com/library/System.Web.UI.Page.aspx) 类。其他实现可从基类（例如 [UserControl](https://msdn.microsoft.com/library/System.Windows.Forms.UserControl.aspx) 或 [WebPart](https://msdn.microsoft.com/library/System.Web.UI.WebControls.WebParts.WebPart.aspx) 类）派生。
    
  
7. 为可公开您希望用户查看或修改的属性的控件声明变量。首先，示例数据源编辑器为用户界面组件（一个 ASPX 页）中定义的 Web 服务器控件声明变量，并定义一个使用户能提交更改的按钮控件。然后，此编辑器调用  [CreateChildControls()](https://msdn.microsoft.com/library/System.Web.UI.Control.CreateChildControls.aspx) 方法以使控件在此页上可用。
    
    > **注释**
      > 编辑器独立于用户界面定义编程逻辑。有关创建编辑器的用户界面组件的说明不在本文档的讨论范围内。 

    示例数据源编辑器执行 **Page_Load** 方法中的步骤 8 到步骤 11。还可使用 **Page_Load** 执行以下操作：初始化并验证变量和控件、填充控件以及保存自定义数据源和帮助程序对象的状态信息。
    
  
8. 从查询字符串中检索参数并将它们设置为本地变量的值，如以下代码示例中所示。
    
  ```cs
  
// The URL of the site collection that contains the PerformancePoint Services repository.
string server = Request.QueryString[ClickOnceLaunchKeys.SiteCollectionUrl];

// The location of the data source in the repository.
string itemLocation = Request.QueryString[ClickOnceLaunchKeys.ItemLocation];

// The operation to perform: OpenItem or CreateItem.
string action = Request.QueryString[ClickOnceLaunchKeys.LaunchOperation];
  ```


    有关查询字符串参数的信息，请参阅 [用于自定义 PerformancePoint Services 对象的编辑器](http://msdn.microsoft.com/library/7c5924f1-91f3-436a-9d94-2e0dc454c8cc%28Office.15%29.aspx)。
    
  
9. 检索用于对存储库进行调用的 **DataSourceRepositoryHelper** 对象，如以下代码示例所示。
    
  ```cs
  
DataSourceRepositoryHelper = new DataSourceRepositoryHelper();
  ```

10. 基于查询字符串参数设置数据源位置，如以下代码示例所示。
    
  ```cs
  RepositoryLocation repositoryDataSourceLocation = RepositoryLocation.CreateFromUriString(itemLocation);
  ```

11. 从查询字符串中检索要执行的操作（ _OpenItem_ 或 _CreateItem_），然后检索或创建自定义数据源。
    
  - 若要检索自定义数据源，请使用 **DataSourceRepositoryHelper.Get** 方法。
    
  
  - 若要创建自定义数据源，请使用 **DataSource()** 构造函数，然后定义数据源的 [Name](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Name.aspx) 和 [SubTypeId](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.SubTypeId.aspx) 属性。 [SubTypeId](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.SubTypeId.aspx) 是该数据源的唯一标识符，它必须与您在 PerformancePoint Services web.config 文件中为自定义数据源指定的 **subType** 属性相匹配。
    
    > **注释**
      > 示例数据源编辑器不包括用于创建数据源对象的逻辑。有关创建自定义对象的示例，请参阅 [如何：为 SharePoint 2013 中的 PerformancePoint Services 创建报表编辑器](how-to-create-report-editors-for-performancepoint-services-in-sharepoint-2013.md)或 [如何：为 SharePoint 2013 中的 PerformancePoint Services 创建筛选器编辑器](how-to-create-filter-editors-for-performancepoint-services-in-sharepoint-2013.md)。 

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


    > **注释**
      > 默认情况下，用户只能从 PerformancePoint 仪表板设计器 创建自定义对象。若要使用户能够在 仪表板设计器 之外创建自定义对象，您必须添加一个菜单项以将  _CreateItem_ 请求从库中的内容类型发送到编辑器。有关详细信息，请参阅 [用于自定义 PerformancePoint Services 对象的编辑器](http://msdn.microsoft.com/library/7c5924f1-91f3-436a-9d94-2e0dc454c8cc%28Office.15%29.aspx)。 

    示例数据源编辑器执行 **buttonOK_Click** 和 **CreateCacheFile** 方法中的步骤 12 和步骤 13。还可使用 **buttonOK_Click** 调用 **AreAllInputsValid** 方法以验证控件内容并检索自定义数据源和帮助程序对象的状态信息。
    
  
12. 使用用户定义的更改来更新数据源。示例数据源编辑器调用 **DataSourceRepositoryHelper.Update** 方法以更新存储库中数据源对象的 [Name](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Name.aspx) 、 [Description](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Description.aspx) 和 [CustomData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.CustomData.aspx) 属性。可使用 [CustomData](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.DataSource.CustomData.aspx) 存储序列化的对象或字符串。示例编辑器使用它来存储用户定义的股票代号、用于存储股票代号报价值的缓存文件的位置以及代理服务器地址。
    
    > **注释**
      > 用户可以编辑自定义对象的  [Name](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Name.aspx) 、 [Description](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Description.aspx) 和 [Owner](https://msdn.microsoft.com/library/Microsoft.PerformancePoint.Scorecards.Element.Owner.aspx) （"负责人"）属性，并直接从 仪表板设计器 和 PerformancePoint Services 存储库中删除自定义对象。
13. 调用数据源提供程序以定义列映射（如果尚未定义列映射）。
    
  

## 代码示例：检索并更新SharePoint Server 2013 中的自定义 PerformancePoint Services 表格格式数据源
<a name="bk_example"> </a>

以下代码示例检索并更新自定义表格格式数据源。此代码来自为 ASPX 页中定义的控件提供编程逻辑的代码隐藏类。
  
    
    
在编译此代码示例之前，您必须如 [在 PerformancePoint Services 中为表格格式数据源编辑器创建并配置编辑器类](#BKMK_DefineDSEd)中所述配置您的开发环境。.
  
    
    



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


## 后续步骤
<a name="bk_next"> </a>

在创建数据源编辑器（如果需要，包括其用户界面）和数据源提供程序后，您将如 [如何：手动注册 PerformancePoint Services 扩展](http://msdn.microsoft.com/library/3aa6d340-4b05-46b3-9648-2b6e18e04e09%28Office.15%29.aspx)中所述部署扩展。
  
    
    

## 其他资源
<a name="bk_next"> </a>


-  [如何：为 SharePoint 2013 中的 PerformancePoint Services 创建表格数据源提供程序](how-to-create-tabular-data-source-providers-for-performancepoint-services-in-sha.md)
    
  
-  [SharePoint 2013 中的 PerformancePoint Services](performancepoint-services-in-sharepoint-2013.md)
    
  

