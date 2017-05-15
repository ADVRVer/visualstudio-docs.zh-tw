---
title: "移植、移轉及升級 Visual Studio 專案 | Microsoft Docs"
ms.custom: 
ms.date: 04/28/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 1512a12a163e38aaa1b1d02dab1c2b99f5c9b344
ms.openlocfilehash: ce24abc3837047025497ccf7a58f768f90607079
ms.contentlocale: zh-tw
ms.lasthandoff: 04/28/2017

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>移植、移轉及升級 Visual Studio 專案

一般來說，每個新版本的 Visual Studio 都會支援大多數舊版類型的專案、檔案和其他資產。 因此，您可以一如既往地使用這些項目；如果您不需要新版的功能，Visual Studio 會保留與 Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012 等舊版的回溯相容性 (請參閱[版本資訊](https://www.visualstudio.com/vs/release-notes/)，以了解哪些功能專屬於哪一個版本)。不過，有些類型的支援可能會隨時間而改變。 新版的 Visual Studio 可能不再支援某些類型，或需要將這些類型移轉與更新，導致它們不再具有回溯相容性。 本主題提供在 Visual Studio 2017 中受影響之專案類型的詳細資料。 如需 Visual Studio 2017 的支援類型清單，請參閱 [Visual Studio 2017 平台目標及相容性](https://www.visualstudio.com/productinfo/vs2017-compatibility-vs)主題。

> [!Note]
> 開啟特定專案類型時，需透過 [Visual Studio 安裝程式] 新增適當的工作負載。


## <a name="projects"></a>專案

下列清單描述 Visual Studio 2017 對使用舊版建立之專案的支援。 如果您在此處沒有看到應列出的專案或檔案類型，請參閱[本主題的 Visual Studio 2015 版本](https://msdn.microsoft.com/library/hh266747.aspx)，並記在下列註解中。

| 專案類型 | 支援 |
| --- | --- |
| .NET Core 專案 (.xproj) | 透過 Visual Studio 2015 建立的專案會使用預覽工具，其中包括 .xproj 專案檔。 使用 Visual Studio 2017 開啟 .xproj 檔案時，系統會提示您將檔案移轉為 .csproj 格式 (會建立 .xproj 檔案的備份)。 VS2015 和更早版本不支援這種 .NET Core 專案適用的 .csproj 格式，  且 .xproj 格式必須移轉為 .csproj，才能在 Visual Studio 2017 中受到支援。 如需詳細資訊，請參閱[將 .NET Core 專案移轉至 .csproj 格式 (英文)](https://docs.microsoft.com/dotnet/articles/core/migration/#visual-studio-2017)。|
| 已啟用 Application Insights 的 ASP.NET Web 應用程式和 ASP.NET Core Web 應用程式 | 對每位 Visual Studio 使用者來說，資源資訊會儲存在每個使用者執行個體的登錄中。 當使用者未開啟任何專案，而要搜尋 Azure Application Insights 資料時，就會使用此資訊。 Visual Studio 2015 使用的登錄位置和 Visual Studio 2017 不同，因此不會產生衝突。<br/><br/>在使用者建立 ASP.NET Web 應用程式或 ASP.NET Core Web 應用程式之後，資源就會存放在 .suo 檔案中。 只要 Visual Studio 支援在 Visual Studio 2015 和 Visual Studio 2017 中使用專案和方案，使用者即可在這兩個版本中開啟專案，資源資訊亦可用於這兩個版本。 不過，使用者必須在每個產品上進行一次驗證。 例如，如果專案是以 Visual Studio 2015 建立並在 Visual Studio 2017 中開啟，則使用者也需要在 Visual Studio 2017 上進行驗證。 |
| C#/Visual Basic Webform 或 Windows Form | 您可以在 Visual Studio 2017 和 Visual Studio 2015 中開啟專案。 |
| 資料庫單元測試專案 (.csproj、.vbproj)    | Visual Studio 2017 可以載入舊版的資料單元測試專案，但會使用全域組件快取版本的相依性。 若要升級單元測試專案以使用最新的相依性，請以滑鼠右鍵按一下方案總管，並選取 [轉換成 SQL Server 單元測試專案]。 |
| F# | Visual Studio 2017 可以開啟在 Visual Studio 2013 和 Visual Studio 2015 中建立的專案。 不過，若要在這些專案中啟用 Visual Studio 2017 的功能，請開啟專案屬性，並將目標 fsharp.core 變更為 F# 4.1。 |
| InstallShield<br/>MSI 安裝程式 | 在 Visual Studio 2010 中建立的安裝程式專案，可以透過 [Visual Studio Installer Projects 擴充功能](https://marketplace.visualstudio.com/items?itemName=UnniRavindranathan-MSFT.MicrosoftVisualStudio2013InstallerProjects) 的協助在較新版本中開啟。您也可以使用 [InstallShield Limited Edition](https://blogs.msdn.microsoft.com/visualstudio/2013/08/15/whats-new-in-visual-studio-2013-and-installshield-limited-edition/) 來維護這類專案。 |
| LightSwitch | Visual Studio 2017 不再支援 LightSwitch。 在 Visual Studio 2013 或 Visual Studio 2015 中，如果開啟使用 Visual Studio 2012 和更早版本所建立的專案，系統會將該專案升級，並僅可在 Visual Studio 2013 或 Visual Studio 2015 之後的版本中開啟。 |
| Microsoft Azure Tools for Visual Studio | 若要開啟這些類型的專案，請先安裝 [Azure SDK for .NET](http://azure.microsoft.com/downloads/)，然後再開啟專案。 如有必要，系統會更新您的專案。 |
| 模型檢視控制器架構 (ASP.NET MVC) | 針對 MVC 版本和 Visual Studio 的支援：<ul><li>Visual Studio 2010 SP1 支援 MVC 2 和 MVC 3；您可透過 [ASP.NET 4 MVC 4 for Visual Studio 2010 SP1 下載](https://www.microsoft.com/download/details.aspx?id=30683)來新增 MVC 4 的支援</li><li>Visual Studio 2012 只支援 MVC 3 和 MVC 4</li><li>Visual Studio 2013 只支援 MVC 4 和 MVC 5</li><li>Visual Studio 2017 和 Visual Studio 2015 支援 MVC 4 (您可以開啟現有專案，但不能建立新的專案) 和 MVC 5</li></ul><br/><br/>升級 MVC 版本：<ul><li>如需關於如何從 MVC 2 自動升級到 MVC 3 的詳細資訊，請參閱 [ASP.NET MVC 3 Application Upgrader](http://go.microsoft.com/fwlink/?LinkID=238178) (ASP.NET MVC 3 應用程式升級程式)。</li><li>如需關於如何從 MVC 2 手動升級至 MVC 3 的詳細資訊，請參閱 [Upgrading an ASP.NET MVC 2 Project to ASP.NET MVC 3 Tools Update](http://go.microsoft.com/fwlink/?linkid=238178) (將 ASP.NET MVC 2 專案升級至 ASP.NET MVC 3 工具更新)。</li><li>如需關於如何從 MVC 3 手動升級至 MVC 4 的詳細資訊，請參閱 [Upgrading an ASP.NET MVC 3 Project to ASP.NET MVC 4](http://www.asp.net/whitepapers/mvc4-release-notes) (將 ASP.NET MVC 3 專案升級至 ASP.NET MVC 4)。 如果您的專案是以 .NET Framework 3.5 SP1 為目標，則必須將目標重定為使用 .NET Framework 4。</li><li>如需如何將 MVC 4 手動升級為 MVC 5 的資訊，請參閱 [How to Upgrade an ASP.NET MVC 4 and Web API Project to ASP.NET MVC 5 and Web API 2](https://www.asp.net/mvc/overview/releases/how-to-upgrade-an-aspnet-mvc-4-and-web-api-project-to-aspnet-mvc-5-and-web-api-2) (如何將 ASP.NET MVC 4 和 Web API 專案升級至 ASP.NET MVC 5 和 Web API 2)。</li></ul> |
| 模型化 | 如果您允許 Visual Studio 自動更新專案，則可以在 Visual Studio 2015、Visual Studio 2013 或 Visual Studio 2012 中開啟專案。<br/><br/>Visual Studio 2015 和 Visual Studio 2017 之間的模型專案格式沒有變更，因此在任一版本都可以開啟和修改專案。 不過，Visual Studio 2017 的行為有下列差異：<ul><li>在功能表和範本中，模型專案現在稱為「相依性驗證」專案。</li><li>Visual Studio 2017 不再支援 UML 圖表。 UML 檔案在方案總管中的提列方式與之前相同，但會以 XML 檔案的形式開啟。 您可以使用 Visual Studio 2015 來檢視、建立或編輯 UML 圖表。</li><li>在 Visual Studio 2017 中建置專案模型時，系統將不再執行架構相依性的驗證。 相反地，系統會在每個程式碼專案建置時執行驗證。 此變更不會影響專案模型建立，但卻必須對要驗證的程式碼專案進行變更。 Visual Studio 2017 可以自動對程式碼專案進行必要的變更 ([詳細資訊](http://go.microsoft.com/fwlink/?LinkId=827800))。</li></ul> |
| MSI 安裝程式 (.vdproj) | 請參閱上方的＜InstallShield 專案＞。 | 
| Office 2007 VSTO | 需要針對 Visual Studio 2017 進行單向升級。 |
| Office 2010 VSTO | 如果專案是以 .NET Framework 4 為目標，您可以在 Visual Studio 2010 SP1 及更新版本中開啟該專案。 所有其他專案則需要單向升級。 |
| SharePoint 2010 | 當使用 Visual Studio 2017 開啟 SharePoint 方案專案時，便會將該專案升級至 SharePoint 2013 或 SharePoint 2016。 必須在 Visual Studio 2017 中安裝「.NET 桌面開發」工作負載以進行升級。<br/><br/>如需如何升級 SharePoint 專案的詳細資訊，請參閱[升級到 SharePoint 2013](https://technet.microsoft.com/library/cc303420.aspx)、[在 SharePoint Server 2013 中更新工作流程 (英文)](https://technet.microsoft.com/library/dn133867.aspx)，以及[針對資料庫附加升級建立 SharePoint Server 2016 伺服器陣列 (英文)](https://technet.microsoft.com/library/cc263026(v=office.16).aspx)。 |
| SharePoint 2016 | 在 Office Developer Tools Preview 2 中建立的 SharePoint 增益集專案，無法在 Visual Studio 2017 中開啟。 若要解決此問題，您必須將 `.csproj` 或 `.vbproj` 檔案中的 `MinimumVisualStudioVersion` 更新為 12.0，並將 `MinimumOfficeToolsVersion` 更新為 12.2。 |
| Silverlight | Visual Studio 2017 不支援 Silverlight 專案。 若要維護 Silverlight 應用程式，請繼續使用 Visual Studio 2015。 |
| SQL Server Reporting Services、SQL Server Analysis Services (SSDT、SSAS、MSAS、SSDT) | 這些專案類型的支援是透過 Visual Studio 程式庫中的下列兩個延伸模組來提供：[Microsoft Analysis Servides 模型專案](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftAnalysisServicesModelingProjects)和 [Microsoft 的 Visual Studio 報表專案](https://marketplace.visualstudio.com/items?itemName=ProBITools.MicrosoftReportProjectsforVisualStudio)。 |
| Visual C++ | 在 Visual Studio 2017 中，您可依原樣開啟使用 Visual Studio 2015 所建立的方案和專案，但在較舊版本的 Visual Studio 中建立的專案可能需要將專案升級，或將目標重定為較新的工具組，以便使用 Visual Studio 2017 來建置。 如需詳細資訊，請參閱 [Visual C++ 移植和升級指南](https://docs.microsoft.com/cpp/porting/visual-cpp-porting-and-upgrading-guide)。 |
| Visual Studio 擴充性/VSIX | 系統會更新含 MinimumVersion 14.0 或以下版本的專案，以宣告 MinimumVersion 15.0，如此一來，即無法在舊版的 Visual Studio 中開啟專案。 若要允許在舊版本中開啟專案，請將 MinimumVersion 設定為 `$(VisualStudioVersion)`。 另請參閱[如何︰將擴充性專案移轉至 Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)。 |
| Visual Studio Lab Management | 您可以使用 Microsoft Test Manager 或 Visual Studio 2010 SP1 和更新版本，開啟在這些版本中建立的環境。 不過，若是 Visual Studio 2010 SP1，Microsoft Test Manager 的版本必須符合 Team Foundation Server 的版本才能建立環境。 |
| Visual Studio Tools for Apache Cordova |這類專案可以在 Visual Studio 2017 中開啟，但不具備回溯相容性。 從 Visual Studio 2015 中開啟專案時，系統會提示您允許對專案進行修改。 這麼做會將專案升級為使用工具組 (而不是 `taco.json` 檔案)，來管理 Cordova 程式庫、其平台和外掛程式，以及其節點/npm 相依性的版本控制。 如需詳細資訊，請參閱[移轉指南](http://taco.visualstudio.com/docs/vs-taco-2017-migration/)。 |
| Windows Communication Foundation 與 Windows Workflow Foundation | 您可以在 Visual Studio 2017、Visual Studio 2015、Visual Studio 2013 和 Visual Studio 2012 中開啟這類專案。 |
| Windows Presentation Foundation | 您可以在 Visual Studio 2013、Visual Studio 2012 和 Visual Studio 2010 SP1 中開啟這類專案。 |
| Windows 市集/Windows Phone 應用程式 | Visual Studio 2017 不支援 Windows 市集 8.1 和 8.0 以及 Windows Phone 8.1 和 8.0 專案。 若要維護這些應用程式，請繼續使用 Visual Studio 2015。 若要維護 Windows Phone 7.x 專案，請使用 Visual Studio 2012。 |

