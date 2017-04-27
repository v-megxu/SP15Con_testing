---
title: SharePoint 加载项与 SharePoint 解决方案比较
ms.prod: SHAREPOINT
ms.assetid: 0e9efadb-aaf2-4c0d-afd5-d6cf25c4e7a8
---


# SharePoint 加载项与 SharePoint 解决方案比较
了解何时应将 SharePoint 2013 扩展作为 SharePoint 外接程序进行开发，以及何时应将其作为 SharePoint 服务器场解决方案或无代码 沙盒解决方案 进行开发。
 * **适用范围：*** 
  
    
    

本文比较 SharePoint 外接程序、服务器场解决方案 和无代码 沙盒解决方案 (NCSS) 的使用案例。
- 新的 SharePoint 外接程序是可能包含基于云的逻辑和数据、SharePoint 组件、以及客户端脚本但不包含在 SharePoint 服务器上运行的自定义托管代码的自包含扩展。它们从 Office 商店或组织加载项目录中安装，并且可以安装到本地服务器场或 Microsoft SharePoint Online 上。有关 SharePoint 外接程序的概述，请参阅  [SharePoint 外接程序](http://msdn.microsoft.com/library/cd1eda9e-8e54-4223-93a9-a6ea0d18df70%28Office.15%29.aspx)。
    
  
- SharePoint服务器场解决方案 是 SharePoint 组件的程序包，这些组件从其可安装的位置上载到服务器场范围的库。无法通过 Office 商店 分发它们，并且它们不会安装在 SharePoint Online 上。它们可以包含在 SharePoint 场服务器上运行的自定义托管代码。有关 服务器场解决方案 基础知识的详细信息，请参阅 [解决方案概述](http://msdn.microsoft.com/library/1983cab9-4b29-494a-a62a-0f8e83908744%28Office.15%29.aspx)和 [场解决方案](http://msdn.microsoft.com/library/845f7524-b9ff-412b-aa29-3afacda91100%28Office.15%29.aspx)。
    
  
- NCSS 也是 SharePoint 组件的程序包；但是它们从其可安装的位置上载到网站集库。它们可以安装到本地服务器场或 SharePoint Online，但是它们无法通过 Office 商店分发。它们可以包含与 SharePoint 外接程序的类型几乎相同的描述性组件（如外接程序），而且它们可以具有 JavaScript，但不包含在 SharePoint 服务器上运行的自定义托管代码。外接程序和 NCSS 的部署系统中的差异向 NCSS 提供了一个更好的用于简短方案列表的开发选项。有关 沙盒解决方案 的信息，请参阅  [SharePoint 2010 中的沙盒解决方案](https://technet.microsoft.com/zh-cn/library/ee721992%28v=office.14%29.aspx)。
    
  

> **重要信息**
> 尽管开发仅包含声明性标记的 沙盒解决方案 和 JavaScript（我们称为无代码沙盒解决方案 (NCSS)）仍然可行，但我们已弃用 沙盒解决方案 中的自定义托管代码。我们已引入新的 SharePoint 加载项模型来替换使用托管代码所需的这些方案。加载项模型将 SharePoint 核心产品与加载项运行时分离，这会带来更大的灵活性并使你能够在所选环境中运行代码。我们意识到我们的客户已在编码的 沙盒解决方案 中进行了投资，我们将负责地逐步完成这些投资。现有编码 沙盒解决方案 在可预见的未来将继续在本地 SharePoint 场中工作。通过提供联机服务的动态特性，我们将根据客户需求确定编码的 沙盒解决方案 在 SharePoint Online 中所需的支持。NCSS 将继续受支持。所有未来投资都将继续使新的 SharePoint 加载项变得更丰富且更强大。因此我们建议所有的新开发都应该尽可能使用新加载项模型。如果你要开发 服务器场解决方案 或编码的 沙盒解决方案，我们建议你对其进行设计，以便它可以轻松演变为更加松散耦合的开发模型。 
  
    
    


## 随时开发加载项
<a name="AppWhenYouCan"> </a>

我们能向你提供的最重要指导是，在能够开发 SharePoint 外接程序而非 服务器场解决方案或 NCSS 时这样做。与经典解决方案相比，SharePoint 外接程序 具有以下好处：
  
    
    

- 为用户提供了最简单的发现、购买和安装过程。
    
  
- 为管理员提供了最安全的 SharePoint 扩展。
    
  
- 为你提供了基于 Microsoft 在线加载项商店的最简单的营销和销售系统。
    
  
- 最大程度地提高了你在开发未来升级时的灵活性。
    
  
- 最大程度地提高了你利用现有非 SharePoint 编程技能的能力。
    
  
- 采用更平稳且更灵活的方式集成基于云的资源。
    
  
- 使你的扩展具有与正在运行该加载项的用户的权限不同的权限。
    
  
- 使你能够使用跨平台标准，包括 HTML、REST、OData、JavaScript 和 OAuth。
    
  
- 使你能够利用 SharePoint 跨域 JavaScript 库访问 SharePoint 数据。或者，你可以使用与 OAuth 兼容的由 Microsoft 提供的安全令牌服务或使用数字证书获取对 SharePoint 数据的授权。
    
  

## 为最终用户设计加载项或 NCSS 并为管理员设计场解决方案
<a name="SPAppVsClassic_Overview"> </a>

SharePoint 外接程序 和 NCSS 使用某个 SharePoint 客户端对象模型或 REST 终结点访问 SharePoint 内容和组件。这些客户端 API 支持为最终用户设计的 SharePoint 扩展。（在此上下文中，"最终用户"是网站集管理员、网站所有者和网站成员。）服务器对象模型具有支持 SharePoint 管理、配置和安全性编程扩展的其他 API。它们包括管理中心、自定义 Windows PowerShell 命令、计时器作业和自定义备份的扩展。有关可开发的管理扩展的类型的详细信息，请参阅  [Windows SharePoint Services 管理](http://msdn.microsoft.com/library/cdcc1b8a-4144-446f-b471-03d4a754a8ab%28Office.15%29.aspx)。这些管理扩展在具有服务器场、Web 应用程序或网站集范围的 SharePoint 功能中部署。尽管加载项和 NCSS 可以由租户或网站集管理员安装，但 SharePoint服务器场解决方案 也由服务器场管理员安装。
  
    
    
服务器对象模型还具有针对列表、库和网站执行的创建、读取、更新和删除 (CRUD) 操作以及对其他 SharePoint 组件执行的操作的 API。这意味着，服务器对象模型可用于适用于最终用户的扩展，但出于上一节所述的原因，服务器场解决方案 通常不是此类扩展的最佳选择。因此，无法将 服务器场解决方案 安装到 Microsoft SharePoint Online 上也就不足为奇。由于 Microsoft 处理了 SharePoint Online 的所有管理工作，因此无需管理扩展。有关 SharePoint 中的各种 API 及其重叠位置的详细信息，请参阅 [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)。
  
    
    
客户端对象模型和 REST 终结点不复制服务器对象模型的面向管理的 API。此外，由于 SharePoint 外接程序 和 NCSS 都无法包含在 SharePoint 服务器上运行的自定义代码，因此它们无法调用这些管理 API。而且，SharePoint 外接程序必须具有网站范围；且 NCSS 中的功能具有网站集或网站范围，因而，面向管理的 SharePoint 扩展实际上无法用于 SharePoint 外接程序 或 NCSS。因此第二个指导原则（而非绝对原则）是加载项和 NCSS 适用于最终用户，而 服务器场解决方案适用于管理员。
  
    
    

## 为品牌或类似于模板的扩展设计 NCSS
<a name="SPAppVsClassic_Overview"> </a>

你可能会遇到少数 SharePoint 开发出现的一种情况，即加载项模型不是最适合的，但你也无法实现 服务器场解决方案，可能是因为解决方案需要安装在 SharePoint Online 上或者需要由网站集管理员安装。有两种使用广泛且重叠的解决方案。
  
    
    

- **品牌：**SharePoint 用户通常想要提供他们的 SharePoint 网站，包括 SharePoint Online 网站、使用自己的颜色、样式、布局和徽标的自定义外观。通常使用 NCSS 比使用 SharePoint 外接程序更容易实现此目的。SharePoint 外接程序 仅在其自己的加载项 Web 的外观上具有声明性控制。对于主机 Web，它可以通过声明方式仅添加功能区按钮和菜单项（以及加载项部件）。对主机 Web 或其父网站集、租赁或本地 SharePoint Web 应用程序的任何其他更改，均已通过使用某个 SharePoint 的客户端对象模型的代码或脚本完成。例如，新图标或 CSS 文件需要通过编程方式部署。此代码在安装后可以从加载项自行运行，或者它可以在加载项安装事件处理程序中运行。但是创建此代码可能需要投入大量的工作。此外，加载项需要网站集范围的权限以更改其自身加载项 Web 和主机 Web 之外的任何网站，并且它还需要租户范围的权限来不仅仅更改其父网站集。但是，可以将品牌 NCSS 部署和激活到任何网站集；它可能仅由几个纯声明性组件组成。 
    
    > **注释**
      > 请注意，SharePoint服务器场解决方案 在品牌方面的功能可能比 NCSS 或 SharePoint 外接程序 更强大，但是它们不是 SharePoint Online 上的选项。 
- **"类似于模板"扩展：**假设你需要为商业危机的协作分析和解决方案创建 SharePoint 的危机管理扩展。你的扩展包括若干自定义列表类型、无代码工作流以及其他 SharePoint 组件，所有这些内容都将组合到一个自定义 WebTemplate 中。假设你打包扩展并将其部署为 NCSS。在解决方案中的功能激活之后，用户可在发生危机时创建其 SharePoint 网站的危机管理子网。他们可以使用特定于危机的数据填充网站。另一方面，你可以实现与直接使用相同 SharePoint 组件集的 SharePoint 外接程序 相同的扩展。当在工作组网站上安装了加载项时，将立即创建子网（也称为"加载项 Web"）。此外，用户可使用相关数据填充网站。
    
    现在，发生第二次危机时出现了什么情况？如果你将扩展实现为 NCSS，用户仅可以从自定义 WebTemplate 创建另一个子网。但是，如果你将扩展实现为 SharePoint 外接程序，你的用户将遇到问题。他们无法在父网站上安装同一加载项的第二个实例。在主机 Web 上仅可以安装任何加载项的一个实例。最佳做法是创建父网站的一个子网站以用作安装加载项的其他实例的位置。当安装加载项时，将为加载项组件创建新的加载项 Web，它是父网站的一个子网。这一比较显示一个一般原则（而非绝对原则）：具有"类似于模板"字符的 SharePoint 扩展（即必须为每个特定用户案例配置的可用组件集，但本质上具有与相同的 SharePoint 网站关联的多个实例）与加载项模型相比，更适合 NCSS 部署模型。在此示例中，可变元素是危机，但是很容易想象类似于模板的 SharePoint 扩展，在该扩展中，实例根据地区、日期或任何数量的其他特性而不同。
    
  
有关如何扩展 SharePoint 外接程序可能性的信息，请参阅 [谨慎使用加载项事件处理程序](#AppEventHandlers)和 [用于创建扩展的加载项](#ExtensionFactories)。
  
    
    

## 按照加载项的方式执行操作
<a name="Questions"> </a>

如之前所述，SharePoint 外接程序 中不允许使用在 SharePoint 服务器上运行的自定义代码。这 *不是*  一个明显限制。它仅意味着，你的自定义业务逻辑将"向下"移至客户端设备或"向上"移至云。在任一情况下，你都可使用 [SharePoint REST/OData 服务](http://msdn.microsoft.com/library/f60ed19e-9840-4f39-911e-4676751a2f6b%28Office.15%29.aspx)访问 SharePoint 网站、列表和其他数据。也可以通过  [SharePoint JavaScript、Silverlight 或 .NET Framework 客户端对象模型](http://msdn.microsoft.com/library/8c086b11-2b8b-41ec-82ae-cd4fef0aeac6%28Office.15%29.aspx)远程访问 SharePoint 数据。最后，在 Windows Phone 上，可以通过 SharePointWindows Phone 对象模型访问 SharePoint。有关 SharePoint 2013 中的各种 API 集的详细信息，请参阅  [在 SharePoint 2013 中选择正确的 API 集](choose-the-right-api-set-in-sharepoint-2013.md)。
  
    
    
对于 SharePoint 外接程序 中的功能无法具有网站集、Web 应用程序或服务器场范围也是同样的道理。但是，你无需放弃某些用户界面 (UI) 元素或功能。它意味着组件的实现将不在 SharePoint 上实现，而是在客户端或远程 Web 应用程序或远程数据库上实现。
  
    
    
下表列出了无法在 SharePoint 外接程序 中部署的 SharePoint 组件，并描述了获取相同功能的"加载项方式"。
  
    
    


|**如果你需要以下各项的功能...**|**...尝试这些方法。**|
|:-----|:-----|
|自定义 Web 部件  <br/> |SharePoint 外接程序 可具有包含自定义 Web 部件的远程页。另一种选择是，在 SharePoint 网站页上的加载项部分中显示远程 Web 应用程序中的页面。远程页面与 Web 部件具有的 UI 控件和功能基本相同。有关详细信息，请参阅 [创建外接程序部件以安装 SharePoint 外接程序](http://msdn.microsoft.com/library/a2664289-6c56-4cb1-987a-22367fad55eb%28Office.15%29.aspx)。  <br/> |
|事件接收器和功能接收器  <br/> |SharePoint 外接程序可包含具有相同功能的远程事件接收器。有关详细信息，请参阅 [处理 SharePoint 外接程序中的事件](http://msdn.microsoft.com/library/c050d056-8548-4496-a053-016779d723d9%28Office.15%29.aspx)。  <br/> |
|自定义字段（列）  <br/> |加载项可部署基于某个 [现有字段类型](http://msdn.microsoft.com/zh-cn/library/microsoft.sharepoint.spfieldtype.aspx%28Office.15%29.aspx)的新字段（列）。 [Calculated](http://msdn.microsoft.com/library/8703373d-bb55-4132-8c5f-37a41c383f81%28Office.15%29.aspx) 和 [Computed](http://msdn.microsoft.com/zh-cn/library/microsoft.sharepoint.spfieldcomputed.aspx%28Office.15%29.aspx) 字段类型相当灵活。另一种选择是，通过使用自定义控件或网格在远程网页中向你提供数据。 <br/> |
|基于 SharePoint  [服务应用程序框架](http://msdn.microsoft.com/library/6d0300d2-5b5c-4477-a9e2-17594aea5a7d%28Office.15%29.aspx)构建的自定义 Web 服务  <br/> |可以将自定义 Web 服务作为远程服务开发。  <br/> |
|应用程序页  <br/> |SharePoint 外接程序 可包括可从安装了加载项的所有网站访问的远程网页。加载项还可以使用网站页上的任何内置 SharePoint Web 部件。  <br/> |
   
下面列出的某些 SharePoint 组件用于最终用户方案中，但在 SharePoint 加载项模型中没有任何等效项，而且不能在 NCSS 中部署。对于这些组件，你必须使用 服务器场解决方案。
  
    
    

- **自定义网站定义** 但是自定义 WebTemplates（功能类似于网站定义）在 NCSS 和 SharePoint 外接程序 中均可用。有关详细信息，请参阅 [使用模板和定义](http://msdn.microsoft.com/library/1edf6d4d-eddb-4cb5-9034-ed394e8a3e01%28Office.15%29.aspx)。
    
  
- **委派控件** 有关详细信息，请参阅 [委派控件（控件模板化）](http://msdn.microsoft.com/library/e979328d-4985-4ed6-9085-7ff32a998dfc%28Office.15%29.aspx)。
    
  
- **自定义主题**
    
  
- **自定义操作组和自定义操作隐藏**
    
  
- **用户控件（.ascx 文件）** 实际上，任何方案都不需要这些组件。
    
  

### 谨慎使用加载项事件处理程序
<a name="AppEventHandlers"> </a>

通过创建适用于安装的加载项、更新的加载项和加载项卸载事件的处理程序，你可以克服 SharePoint 外接程序的某些限制。这些处理程序是托管在 SharePoint 场外（可能在云中）的 Web 服务器上的 Web 服务。它们可以使用 SharePoint 客户端对象模型或 REST API 来在 SharePoint 组件（包括主机 Web 中的组件）上执行 CRUD 操作。理论上，你可以使用此类处理程序克服之前讨论的 **品牌** 和 **类似于模板扩展** 项中的某些部署限制。但是，当没有其他方法来向客户提供使用案例所需的功能时，我们建议你仅使用此类处理程序作为最后的方法。当确定是否创建处理程序时，请考虑以下事项：
  
    
    

- 通过编程方式部署到主机 Web 需要加载项请求对主机 Web 的"完全控制"权限。需要此权限级别的加载项无法通过 Office 商店 出售。
    
  
- 到主机 Web 的组件部署会危害将 SharePoint 组件放置在具有其自己的域的加载项 Web 中的安全优势。
    
  
- 与可用于加载项 Web 组件和 NCSS 中的描述性部署标记相比，广泛的部署代码将需要大量创建和调试工作。
    
  
- 在创建加载项事件处理程序时必须遵循某些重要的最佳做法。如果你的代码出现错误，则它必须包括回滚逻辑以放弃它已完成的所有操作。它还必须警告有关 SharePoint 基础结构的错误，以便基础结构可以回滚它已完成的所有操作。
    
  
- 加载项事件处理程序无法包含 SharePoint 外接程序（称为托管的 SharePoint）的类型。
    
  
有关加载项事件处理程序的详细信息，请参阅 SDK 节点 [处理 SharePoint 外接程序中的事件](http://msdn.microsoft.com/library/c050d056-8548-4496-a053-016779d723d9%28Office.15%29.aspx)。有关回滚逻辑的信息，请参阅 [在 SharePoint 外接程序中创建更新事件的处理程序](http://msdn.microsoft.com/library/0fa088c5-54c6-482c-84ed-51c4f77c4127%28Office.15%29.aspx)主题的 **将回滚逻辑添加到处理程序** 部分。后面的主题是在加载项更新的事件上下文中编写的，而基本原则适用于所有加载项事件处理程序。
  
    
    

### 用于创建扩展的加载项
<a name="ExtensionFactories"> </a>

使用 SharePoint 客户端对象模型或其 REST API 来解决 SharePoint 外接程序的组件部署问题的另一种方法是，使 CRUD 代码位于加载项本身中，而不是位于加载项事件处理程序中。然后该加载项将成为适用于自定义扩展类型的一种工厂。例如，SharePoint 托管的加载项可以使用 SharePointJavaScript 对象模型在主机 Web 或者租户或 Web 应用程序中的任意位置上执行部署和其他 CRUD 操作。有关其他示例，请参阅  [SharePoint 2013 中网站设置技术和远程设置](http://blogs.msdn.com/b/vesku/archive/2013/08/23/site-provisioning-techniques-and-remote-provisioning-in-sharepoint-2013.aspx) 的 **远程设置快速简介** ，它介绍了如何使用提供商托管的 SharePoint 外接程序 在内置子网设置中提供子网设置（与 SharePoint 的设置非常相似）。但是，存在大量需重新创造的方面，因此创建工厂 SharePoint 外接程序 需要投入大量工作。此外，此类加载项无法通过 Office 商店出售，因为该加载项需要主机 Web 的"完全控制"。
  
    
    

## 其他资源
<a name="bk_addresources"> </a>


-  [SharePoint 2013 中的编程模型](programming-models-in-sharepoint-2013.md)
    
  
-  [使用解决方案](http://msdn.microsoft.com/library/0da0518c-24eb-48e0-89bd-21282fdeef94%28Office.15%29.aspx)
    
  

