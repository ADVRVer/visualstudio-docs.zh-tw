---
title: "InfoPath 解決方案 |Microsoft 文件"
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
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4e59b91ff6159af8f6e5736621c0443d3d96c8b5
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="infopath-solutions"></a>InfoPath 方案
  Visual Studio 提供的專案範本，可用來建立 Microsoft Office InfoPath 2013 與 InfoPath 2010 的 VSTO 增益集。 Office 2016 不提供 InfoPath。  
  
> [!NOTE]  
>  您可以仍建立的 VSTO 增益集 InfoPath 即使安裝了 Office 2016。 只安裝與 Office 2016 並行的 InfoPath 2013 或 Office 2013。  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  感興趣開發方案，擴充的 Office 體驗，跨[多個平台](https://dev.office.com/add-in-availability)嗎？ 查看新[Office 增益集模型](https://dev.office.com/docs/add-ins/overview/office-add-ins)。 Office 增益集有相較於 VSTO 增益集和方案、 較小的耗用量，您可以使用幾乎任何 web 程式設計技術，例如 HTML5、 JavaScript、 CSS3 和 XML 來建置。  
  
 InfoPath 的 VSTO 增益集類似於其他 Microsoft Office 應用程式的 VSTO 增益集。 這類方案是由應用程式載入的組件所組成。 無論開啟何種表單或表單範本，使用者都可以存取此組件的功能。 如需 VSTO 增益集的詳細資訊，請參閱下列主題： [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) 和 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)。  
  
> [!NOTE]  
>  Visual Studio 2015 不包含舊版 Visual Studio 曾提供的 InfoPath 表單範本專案。 在舊版 Visual Studio 中建立的 InfoPath 表單範本專案，也無法使用 Visual Studio 2015 開啟或編輯。 不過，您可以使用 Visual Studio Tools for Applications 開啟和編輯 InfoPath 表單範本專案。 如需詳細資訊，請參閱 [在 InfoPath 2010 中使用 VSTO 2008 專案](http://go.microsoft.com/fwlink/?LinkID=218903)。  
  
## <a name="automating-infopath-by-using-an-add-in"></a>使用增益集自動化 InfoPath  
 若要從在 Visual Studio 中使用 Office 開發工具建立的 Office VSTO 增益集存取 InfoPath 物件模型，請使用專案中 `Application` 類別的 `ThisAddIn` 欄位。 `Application` 欄位傳回的 <xref:Microsoft.Office.Interop.InfoPath.Application> 物件，代表 InfoPath 目前的執行個體。 如需詳細資訊，請參閱 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)。  
  
 當您從 VSTO 增益集呼叫 InfoPath 物件模型時，您使用的類型是由 InfoPath 的主要 Interop 組件所提供。 主要 Interop 組件的作用，如同 VSTO 增益集中 Managed 程式碼與 InfoPath 中 COM 物件模型之間的橋樑。 InfoPath 主要 Interop 組件中的所有類型，都是在 <xref:Microsoft.Office.Interop.InfoPath> 命名空間中定義。 如需 InfoPath 主要 Interop 組件的詳細資訊，請參閱 [有關 Microsoft Office InfoPath 主要 Interop 組件](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72)。 如需主要 interop 組件一般情況下，請參閱[Office 方案開發概觀 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)和[Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)。  
  
## <a name="customizing-the-user-interface-of-infopath-by-using-an-add-in"></a>使用增益集自訂 InfoPath 使用者介面  
 當您針對 InfoPath 建立 VSTO 增益集時，您會有數個不同的 UI 自訂選項。 下表列出其中一些選項。  
  
|工作|如需詳細資訊|  
|----------|--------------------------|  
|建立自訂工作窗格。|[自訂工作窗格](../vsto/custom-task-panes.md)|  
|在 InfoPath 的功能區中加入自訂索引標籤。|[自訂 InfoPath 的功能區](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 如需自訂 InfoPath 的 UI 及其他 Microsoft Office 應用程式的詳細資訊，請參閱[Office UI 自訂](../vsto/office-ui-customization.md)。  
  
## <a name="see-also"></a>請參閱  
 [有關 Microsoft Office InfoPath 主要 Interop 組件](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Office 方案開發概觀 &#40;VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [VSTO 增益集的架構](../vsto/architecture-of-vsto-add-ins.md)   
 [如何： 在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)   
 [Office 主要 Interop 組件](../vsto/office-primary-interop-assemblies.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [InfoPath 2010 中的 Office 程式開發](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  