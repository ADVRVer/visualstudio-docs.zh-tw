---
title: "擴充物件自動化 Word 使用 |Microsoft 文件"
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
- Word [Office development in Visual Studio], automating
- extended objects [Office development in Visual Studio], Word
- automation [Office development in Visual Studio], Word
- host items [Office development in Visual Studio], Word
- automating Word
- controls [Office development in Visual Studio], Word host controls
- host controls, Word
- host controls [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], host controls
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: b3073f5f80e805f4c55e6924ada1be9a2ba139f6
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="automating-word-by-using-extended-objects"></a>使用擴充物件自動化 Word
  在 Visual Studio 中開發 Word 方案時，您可以在方案中使用 *「主項目」* (Host Item) 和 *「主控制項」*(Host Control)。 這些物件可以擴充 Word 物件模型 (也就是 Word 的主要 Interop 組件公開的物件模型) 中某些常用的物件，例如 <xref:Microsoft.Office.Interop.Word.Document> 和 <xref:Microsoft.Office.Interop.Word.ContentControl> 物件。 這些擴充物件的行為與它們所根據的 Word 物件一樣，但是這些物件會在物件中加入額外的事件和資料繫結功能。  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 VSTO 增益集和文件層級自訂中都提供主項目和主控制項，不過針對每種方案類型來說，可在其中使用主項目和主控制項的內容會有所不同。 如需詳細資訊，請參閱 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)。  
  
## <a name="document-host-item"></a>Document 主項目  
 Word 專案可讓您存取 <xref:Microsoft.Office.Tools.Word.Document> 主項目。 <xref:Microsoft.Office.Tools.Word.Document> 主項目可當成其他控制項 (包括主控制項與 Windows Form 控制項) 的容器使用，而且會在其介面維護控制項的相關資訊。 <xref:Microsoft.Office.Tools.Word.Document> 主項目也會提供與 Word 物件模型中的對應類別 <xref:Microsoft.Office.Interop.Word.Document> 大致相同的成員。  
  
 如需詳細資訊，請參閱 [Document Host Item](../vsto/document-host-item.md)。  
  
## <a name="word-host-controls"></a>Word 主控制項  
 有數個 Word 主控制項可以協助您建立、組織與自動化文件。 其大部分功能與匯入、呈現和保護資料相關。 這些主控制項能夠提供其原生 Word 物件模型對等用法所無法提供的事件與資料繫結功能。  
  
 在文件層級專案中，您可以於設計階段將任何主控制項加入文件，或於執行階段加入內容控制項和書籤控制項。 在 VSTO 增益集專案中，您可以於執行階段將內容控制項和書籤控制項加入任何開啟的文件。  
  
 如需可用於 Word 專案中之主控制項的詳細資訊，請參閱下列主題：  
  
-   [內容控制項](../vsto/content-controls.md)  
  
-   [書籤控制項](../vsto/bookmark-control.md)  
  
-   [XMLNode 控制項](../vsto/xmlnode-control.md)  
  
-   [XMLNodes 控制項](../vsto/xmlnodes-control.md)  
  
## <a name="see-also"></a>請參閱  
 [如何： 將內容控制項加入 Word 文件](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md)   
 [如何： 將 XMLNode 控制項加入 Word 文件](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)   
 [如何： 將 XMLNodes 控制項加入 Word 文件](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)   
 [如何： 調整書籤控制項的大小](../vsto/how-to-resize-bookmark-controls.md)   
 [逐步解說： 使用內容控制項建立範本](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)   
 [逐步解說： 內容控制項繫結至自訂 XML 組件](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)   
 [逐步解說： 建立書籤的捷徑功能表](../vsto/walkthrough-creating-shortcut-menus-for-bookmarks.md)   
 [Word 方案](../vsto/word-solutions.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  