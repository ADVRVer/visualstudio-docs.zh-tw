---
title: "工具擴充功能的 SharePoint 程式撰寫模型概觀 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- SharePoint development in Visual Studio, extensibility object models
- SharePoint development in Visual Studio, extending tools
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 8eaa1f5d1cfe8120ec6a01c2fe7f646cf90be44a
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="overview-of-the-programming-model-of-sharepoint-tools-extensions"></a>SharePoint 工具擴充功能的程式撰寫模型概觀
  在 Visual Studio 中建立 SharePoint 工具的延伸模組時，您會從實作 SharePoint 工具公開的一或多個擴充性介面開始。 在大部分情況下，您也會使用 SharePoint 工具所提供的其他類型，在您的延伸模組中實作功能。 在某些情況下，您也可以使用 Visual Studio 和 SharePoint 所提供的其他物件模型中的類型。 您必須了解每個物件模型的用途，並了解如何使用它們彼此建立 SharePoint 工具擴充功能。  
  
## <a name="extending-the-sharepoint-tools-by-implementing-extensibility-interfaces"></a>藉由實作擴充性介面來擴充 SharePoint 工具  
 Visual Studio 使用 .NET Framework 4 中的 Managed Extensibility Framework (MEF)，為 SharePoint 工具提供擴充性模型。 MEF 是 API (在 System.ComponentModel.Composition 組件中實作)，可讓應用程式公開擴充性點，並在執行階段探索及載入擴充功能。 如需 MEF 的詳細資訊，請參閱[Managed Extensibility Framework &#40;MEF &#41;](/dotnet/framework/mef/index).  
  
 若要擴充 SharePoint 工具，請實作 Visual Studio 所公開的一個或多個擴充性介面。 您也必須視需要對您的介面實作套用 <xref:System.ComponentModel.Composition.ExportAttribute> 和其他 SharePoint 工具特定屬性。 下表列出您可以實作以擴充 SharePoint 工具的介面。  
  
|介面|描述|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider>|實作這個介面可定義 SharePoint 專案項目的新類型。 如需範例，請參閱[如何： 定義 SharePoint 專案項目類型](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension>|實作這個介面來擴充 Visual Studio 中已安裝的 SharePoint 專案項目的類型。 如需範例，請參閱[How to： 建立 SharePoint 專案項目擴充功能](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension>|實作這個介面來擴充 SharePoint 專案。 如需範例，請參閱[How to： 建立 SharePoint 專案擴充功能](../sharepoint/how-to-create-a-sharepoint-project-extension.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.Deployment.IDeploymentStep>|實作這個介面來定義新的部署步驟，可以在部署或撤回 SharePoint 專案項目時執行。 如需範例，請參閱[逐步解說： 建立 SharePoint 專案的自訂部署步驟](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>|實作這個介面來擴充現有的節點下**SharePoint 連接**節點**伺服器總管**視窗。 如需範例，請參閱[如何： 擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeProvider>|實作這個介面來定義新類型的節點下**SharePoint 連接**節點**伺服器總管**視窗。 如需範例，請參閱[如何： 擴充 SharePoint 節點在 伺服器總管](../sharepoint/how-to-extend-a-sharepoint-node-in-server-explorer.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IFeatureValidationRule>|實作這個介面來定義自訂功能驗證規則。 如需範例，請參閱[How to： 建立自訂功能和封裝驗證規則，SharePoint 方案的](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。|  
|<xref:Microsoft.VisualStudio.SharePoint.Validation.IPackageValidationRule>|實作這個介面來定義自訂封裝驗證規則。 如需範例，請參閱[How to： 建立自訂功能和封裝驗證規則，SharePoint 方案的](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。|  
  
 實作 SharePoint 工具的擴充功能之後，您必須在 Visual Studio 擴充功能 (VSIX) 封裝中部署延伸模組組件，才能啟用 Visual Studio 來探索及載入擴充功能。 如需詳細資訊，請參閱[部署 Visual Studio 中的 SharePoint 工具擴充功能](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)。  
  
## <a name="understanding-the-object-models-that-you-use-in-sharepoint-tools-extensions"></a>了解在 SharePoint 工具擴充功能中使用的物件模型  
 建立 SharePoint 工具的延伸模組時，您可以使用數個物件模型：  
  
-   *SharePoint 工具物件模型*。 此物件模型會提供您實作以建立 SharePoint 工具擴充功能以及其他相關的類型的擴充性介面。  
  
-   *Visual Studio 自動化和整合物件模型*。 使用這些物件模型來存取已超出 SharePoint 工具物件模型範圍的 Visual Studio 功能。  
  
    > [!NOTE]  
    >  藉由使用 SharePoint 專案服務，您可以將 SharePoint 工具物件模型中的某些物件轉換成 Visual Studio 自動化物件和整合物件模型中的物件，反之亦然。 如需詳細資訊，請參閱[轉換之間 SharePoint 專案系統類型與其他 Visual Studio 專案類型](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)。  
  
-   *SharePoint 伺服器和用戶端物件模型*。 使用這些物件模型來修改 SharePoint 網站，或從 SharePoint 工具擴充功能的內容擷取 SharePoint 網站的資料。  
  
### <a name="sharepoint-tools-object-model"></a>SharePoint 工具物件模型  
 每個 SharePoint 工具延伸模組會使用 SharePoint 工具物件模型中的類型來定義延伸模組的核心行為和功能。 下表描述此物件模型中包含的命名空間。  
  
|組件|命名空間|描述|  
|--------------|---------------|-----------------|  
|Microsoft.VisualStudio.SharePoint.dll|<xref:Microsoft.VisualStudio.SharePoint>|包含您用來擴充和自動化 SharePoint 專案系統的類型。 例如，您可以擴充內建的 SharePoint 專案和專案項目，或您可以建立您自己的專案項目。 如需詳細資訊，請參閱[擴充 SharePoint 專案系統](../sharepoint/extending-the-sharepoint-project-system.md)。|  
||<xref:Microsoft.VisualStudio.SharePoint.Deployment>|包含您用來擴充 SharePoint 專案的部署程序 (例如建立您自己的部署步驟和部署組態) 的類型。 如需詳細資訊，請參閱[擴充 SharePoint 封裝和部署](../sharepoint/extending-sharepoint-packaging-and-deployment.md)。|  
||<xref:Microsoft.VisualStudio.SharePoint.Explorer>|包含型別，您用於下擴充節點**SharePoint 連接**中的節點**伺服器總管**視窗中，或定義新類型節點。 如需詳細資訊，請參閱[擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。|  
||<xref:Microsoft.VisualStudio.SharePoint.Features>|包含用來存取 SharePoint 專案中功能定義的類型。|  
||<xref:Microsoft.VisualStudio.SharePoint.Packages>|包含用來存取 SharePoint 方案中封裝定義的類型。|  
||<xref:Microsoft.VisualStudio.SharePoint.Validation>|包含用來自訂 SharePoint 專案的功能和封裝驗證行為的類型。 如需詳細資訊，請參閱[How to： 建立自訂功能和封裝驗證規則，SharePoint 方案的](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)。|  
|Microsoft.VisualStudio.SharePoint.Commands.dll|<xref:Microsoft.VisualStudio.SharePoint.Commands>|包含型別，您可以使用它來建立自訂*SharePoint 命令*。 SharePoint 命令是從 SharePoint 工具擴充功能呼叫 SharePoint 伺服器物件模型的方法。 如需詳細資訊，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。|  
|Microsoft.VisualStudio.SharePoint.Explorer.Extensions.dll|<xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions>|包含型別，您可以使用來取得內建的相關資訊**伺服器總管**表示 SharePoint 網站，例如清單、 欄位或內容類型表示的節點上的個別元件的節點。 如需詳細資訊，請參閱[擴充 SharePoint 連線節點，在 伺服器總管](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)。|  
  
### <a name="visual-studio-automation-object-model"></a>Visual Studio Automation 物件模型  
 Visual Studio 自動化物件模型會提供可用來自動化 Visual Studio 專案 和 IDE 的 API。 使用 Visual Studio 物件模型來執行非 SharePoint 專案特定的專案相關工作，或在 Visual Studio 中執行其他一般自動化工作。 傳統上，此物件模型常用於 Visual Studio 增益集和巨集，但您也可以在 SharePoint 工具擴充功能中使用它。  
  
 Visual Studio 自動化物件模型的主要部分是在 EnvDTE.dll 組件中定義。 EnvDTE*版本*.dll 組件提供特定版本的 Visual Studio 中導入的其他功能。 這些組件隨附於 Visual Studio。  
  
 如需自動化物件模型的詳細資訊，請參閱[Visual Studio SDK 參考](../extensibility/visual-studio-sdk-reference.md)。  
  
### <a name="visual-studio-integration-object-model"></a>Visual Studio Integration 物件模型  
 整合物件模型提供應用程式開發介面可讓您建立將功能加入至 Visual Studio *VSPackage*。 VSPackage 是模組，藉由提供自訂功能，例如工具視窗、編輯器、設計工具、服務和專案來擴充 Visual Studio IDE。  
  
 如果您想要加入將與內建的 SharePoint 工具搭配使用的新 Visual Studio 功能，您可以使用整合物件模型。 例如，如果您建立可表示 SharePoint 網站自訂動作的自訂 SharePoint 專案項目，您也可以建立可實作自訂動作的設計工具的 VSPackage。 您可以將設計工具與自訂動作的捷徑功能表項目加入至表示中的自訂動作專案項目**方案總管 中**。 您可以開啟您的設計工具開啟其捷徑功能表 （以滑鼠右鍵按一下 自訂動作專案項目，或選擇它，然後選擇 Shift + F10 鍵），然後選擇**開啟**。  
  
 此物件模型是在隨附於 Visual Studio SDK 的組件集中定義。 此物件模型中的主要組件包括 Microsoft.VisualStudio.Shell.11.0.dll、Microsoft.VisualStudio.Shell.Interop.dll 和 Microsoft.VisualStudio.OLE.Interop.dll。  
  
 如需整合物件模型的詳細資訊，請參閱[Automation 模型概觀](/visualstudio/extensibility/internals/automation-model-overview)和[Visual Studio SDK 參考](/visualstudio/extensibility/visual-studio-sdk-reference)。  
  
### <a name="sharepoint-object-models"></a>SharePoint 物件模型  
 SharePoint 工具擴充功能可以使用 SharePoint API，來修改 SharePoint 網站，或從 SharePoint 網站擷取資料。 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 提供兩個不同的物件模型：伺服器物件模型和用戶端物件模型。  
  
 您可以在這兩個 SharePoint 工具擴充功能的物件模型中使用 API，但在每個物件模型的 SharePoint 工具擴充功能方面有一些優點和缺點。 如需詳細資訊，請參閱[呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)。  
  
|物件模型|描述|  
|------------------|-----------------|  
|伺服器物件模型|伺服器物件模型提供 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] 和 [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] 以程式設計的方式公開的所有功能的存取權。 此物件模型的設計是要由 SharePoint 伺服器上執行的 SharePoint 方案所使用。 此物件模型大部分是在 Microsoft.SharePoint.dll 組件中定義。 如需伺服器物件模型的詳細資訊，請參閱[使用 SharePoint Foundation 伺服器端物件模型](http://go.microsoft.com/fwlink/?LinkId=177796)。|  
|用戶端物件模型|用戶端物件模型是可以用來從遠端用戶端或伺服器與 SharePoint 資料交互操作的伺服器物件模型的子集。 其設計是為了將必須執行以執行一般工作的往返次數降到最低。 大部分的用戶端物件模型是在 Microsoft.SharePoint.Client.dll 和 Microsoft.SharePoint.Client.Runtime.dll 組件中定義。 如需有關用戶端物件模型的詳細資訊，請參閱[管理用戶端物件模型](http://go.microsoft.com/fwlink/?LinkId=177797)。|  
  
## <a name="see-also"></a>請參閱  
 [擴充 Visual Studio 中的 SharePoint 工具](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [呼叫 SharePoint 物件模型](../sharepoint/calling-into-the-sharepoint-object-models.md)   
 [使用 SharePoint 專案服務](../sharepoint/using-the-sharepoint-project-service.md)  
  
  