---
title: "逐步解說：為您的 PowerPoint 建立第一個 VSTO 增益集 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "增益集 [Visual Studio 中的 Office 程式開發], 建立第一個專案"
  - "應用程式層級增益集 [Visual Studio 中的 Office 程式開發], 建立第一個專案"
  - "Visual Studio 中的 Office 程式開發, 建立第一個專案"
  - "PowerPoint [Visual Studio 中的 Office 程式開發], 建立第一個專案"
ms.assetid: 52d1543a-c9cb-4ee1-aa5b-90759fce9d3a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 逐步解說：為您的 PowerPoint 建立第一個 VSTO 增益集
  本逐步解說示範如何建立 Microsoft Office PowerPoint 的 VSTO 增益集。  不論開啟哪一份簡報，您在這類方案中建立的功能都可供應用程式本身使用。  如需詳細資訊，請參閱 [Office 方案開發概觀 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)。  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   建立 PowerPoint 的 PowerPoint VSTO 增益集專案。  
  
-   撰寫使用 PowerPoint 物件模型將文字方塊加入每張新投影片的程式碼。  
  
-   建置和執行專案來進行測試。  
  
-   清除已完成的專案，使得 VSTO 增益集不再於開發電腦上自動執行。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## 建立專案  
  
#### 若要建立新的專案  
  
1.  啟動 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]。  
  
2.  在 \[檔案\] 功能表中，指向 \[新增\]，然後按一下 \[專案\]。  
  
3.  在範本窗格中，展開 \[Visual C\#\] 或 \[Visual Basic\]，然後展開 \[Office\/SharePoint\]。  
  
4.  在展開的 \[Office\/SharePoint\] 節點下，選取 \[Office 增益集\] 節點。  
  
5.  在專案範本清單中，選取 PowerPoint VSTO 增益集專案。  
  
6.  在 \[名稱\] 方塊中，輸入 **FirstPowerPointAddIn**。  
  
7.  按一下 \[**確定**\]。  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 會建立 **FirstPowerPointAddIn** 專案，並在編輯器中開啟 **ThisAddIn** 程式碼檔。  
  
## 撰寫可將文字加入每張新投影片的程式碼  
 接著，將程式碼加入 ThisAddIn 程式碼檔。  新的程式碼會使用 PowerPoint 的物件模型，將文字方塊加入每張新投影片。  根據預設，ThisAddIn 程式碼檔包含下列產生的程式碼：  
  
-   `ThisAddIn` 類別的部分定義。  這個類別提供您撰寫程式碼的進入點，並提供對 PowerPoint 物件模型的存取。  如需詳細資訊，請參閱 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。  `ThisAddIn` 類別的其餘部分則定義於您不應修改的隱藏程式碼檔中。  
  
-   `ThisAddIn_Startup` 和 `ThisAddIn_Shutdown` 事件處理常式。  當 PowerPoint 載入和卸載 VSTO 增益集時，會呼叫這些事件處理常式。  請使用這些事件處理常式，在 VSTO 增益集載入時將它初始化，以及在 VSTO 增益集卸載時清除它所用的資源。  如需詳細資訊，請參閱 [Office 專案中的事件](../vsto/events-in-office-projects.md)。  
  
#### 若要將文字方塊加入每張新的投影片  
  
1.  在 ThisAddIn 程式碼檔中，將下列程式碼加入 `ThisAddIn` 類別。  這段程式碼會定義 <xref:Microsoft.Office.Interop.PowerPoint.Application> 物件之 <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> 事件的事件處理常式。  
  
     當使用者將新投影片加入現用簡報時，這個事件處理常式會在新投影片頂端加入文字方塊，並將一些文字加入此文字方塊。  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_PowerPointAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  如果使用的是 C\#，請將下列程式碼加入 `ThisAddIn_Startup` 事件處理常式中。  這是連接 `Application_PresentationNewSlide` 事件處理常式和 <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> 事件時的必要程式碼。  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 若要修改每張新投影片，前面的程式碼範例可以使用下列物件：  
  
-   `ThisAddIn` 類別的 `Application` 欄位。  `Application` 欄位會傳回 <xref:Microsoft.Office.Interop.PowerPoint.Application> 物件，此物件代表 PowerPoint 目前的執行個體。  
  
-   <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> 事件之事件處理常式的 `Sld` 參數。  `Sld` 參數是 <xref:Microsoft.Office.Interop.PowerPoint.Slide> 物件，此物件代表新投影片。  如需詳細資訊，請參閱 [PowerPoint 方案](../vsto/powerpoint-solutions.md)。  
  
## 測試專案  
 當您建置和執行專案時，請確認文字方塊有出現在您加入簡報的新投影片中。  
  
#### 若要測試專案  
  
1.  按 **F5** 建置及執行專案。  
  
     當您建置專案時，程式碼會編譯為放置在專案建置輸出資料夾中的組件。  Visual Studio 也會建立一組登錄項目，以便 PowerPoint 探索和載入 VSTO 增益集，而且會設定開發電腦中的安全性設定，讓 VSTO 增益集可以執行。  如需詳細資訊，請參閱 [建置 Office 方案](../vsto/building-office-solutions.md)。  
  
2.  在 PowerPoint 中，將新投影片加入現用簡報。  
  
3.  確認下列文字已加入投影片頂端的新文字方塊中。  
  
     **This text was added by using code.**  
  
4.  關閉 PowerPoint。  
  
## 清除專案  
 當您完成專案開發時，請從開發電腦移除 VSTO 增益集組件、登錄項目和安全性設定。  否則，每次在開發電腦上開啟 PowerPoint 時，就會執行 VSTO 增益集。  
  
#### 若要清除專案  
  
1.  在 Visual Studio 中，按一下 \[建置\] 功能表上的 \[清除方案\]。  
  
## 後續步驟  
 現在您已經建立 PowerPoint 的基本 VSTO 增益集，可以從下列主題進一步了解如何開發 VSTO 增益集：  
  
-   您可以透過 PowerPoint VSTO 增益集執行的一般程式設計工作。  如需詳細資訊，請參閱 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)。  
  
-   使用 PowerPoint 物件模型。  如需詳細資訊，請參閱 [PowerPoint 方案](../vsto/powerpoint-solutions.md)。  
  
-   自訂 PowerPoint 的 UI，例如，透過將自訂索引標籤加入功能區，或建立您專屬自訂工作窗格的方式。  如需詳細資訊，請參閱 [Office UI 自訂](../vsto/office-ui-customization.md)。  
  
-   建置及偵錯 PowerPoint VSTO 增益集。  如需詳細資訊，請參閱[建置 Office 方案](../vsto/building-office-solutions.md)。  
  
-   部署 PowerPoint VSTO 增益集。  如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
## 請參閱  
 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)   
 [PowerPoint 方案](../vsto/powerpoint-solutions.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [建置 Office 方案](../vsto/building-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [Office 專案範本概觀](../vsto/office-project-templates-overview.md)  
  
  