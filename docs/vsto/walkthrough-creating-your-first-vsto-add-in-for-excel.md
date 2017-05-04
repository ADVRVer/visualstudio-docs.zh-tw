---
title: "逐步解說：建立 Excel 的第一個 VSTO 增益集 | Microsoft Docs"
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
  - "應用程式層級增益集 [Visual Studio 中的 Office 程式開發]，建立第一個專案"
  - "Visual Studio 中的 Office 程式開發，建立第一個專案"
  - "增益集 [Visual Studio 中的 Office 程式開發]，建立第一個專案"
  - "Excel [Visual Studio 中的 Office 程式開發]，建立第一個專案"
ms.assetid: a855e2be-3ecf-4112-a7f5-ec0f7fad3b5f
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 逐步解說：建立 Excel 的第一個 VSTO 增益集
  本入門逐步解說將示範如何建立 Microsoft Office Excel 的應用程式層級增益集。 不論開啟哪一份活頁簿，您在這類方案中建立的功能都可供應用程式本身使用。  
  
 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]  
  
 這個逐步解說將說明下列工作：  
  
-   建立 Excel 的 Excel VSTO 增益集專案。  
  
-   撰寫可使用 Excel 物件模型的程式碼，儲存活頁簿時便可加入文字。  
  
-   建置和執行專案來進行測試。  
  
-   清除已完成的專案，使得 VSTO 增益集不再於開發電腦上自動執行。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [部署 Office 方案](../vsto/deploying-an-office-solution.md) 或 。  
  
## 建立專案  
  
#### 在 Visual Studio 中建立新的 Excel VSTO 增益集專案  
  
1.  啟動 [部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
2.  在 \[檔案\][部署 Office 方案](../vsto/deploying-an-office-solution.md) 功能表中，指向 \[新增\]，然後按一下 \[專案\]。  
  
3.  在範本窗格中，展開 \[Visual C\#\][部署 Office 方案](../vsto/deploying-an-office-solution.md) 或 \[Visual Basic\]，然後展開 \[Office\/SharePoint\]。  
  
4.  在展開的 \[Office\/SharePoint\][部署 Office 方案](../vsto/deploying-an-office-solution.md) 節點下，選取 \[Office 增益集\] 節點。  
  
5.  在專案範本清單中，選取 \[Excel 2010 增益集\][部署 Office 方案](../vsto/deploying-an-office-solution.md) 或 \[Excel 2013 增益集\]。  
  
6.  在 \[名稱\][部署 Office 方案](../vsto/deploying-an-office-solution.md) 方塊中，輸入 **FirstExcelAddIn**。  
  
7.  按一下 \[確定[部署 Office 方案](../vsto/deploying-an-office-solution.md)\]。  
  
     [部署 Office 方案](../vsto/deploying-an-office-solution.md) 會建立 **FirstExcelAddIn** 專案，並在編輯器中開啟 ThisAddIn 程式碼檔。  
  
## 撰寫程式碼以將文字加入儲存的活頁簿  
 接著，將程式碼加入 ThisAddIn 程式碼檔。 新程式碼會使用 Excel 物件模型，將未定案文字插入現用工作表的第一列中。 現用工作表是使用者儲存活頁簿時所開啟的工作表。 根據預設，ThisAddIn 程式碼檔包含下列產生的程式碼：  
  
-   [部署 Office 方案](../vsto/deploying-an-office-solution.md) 類別的部分定義。 這個類別提供您撰寫程式碼的進入點，並提供對 Excel 物件模型的存取。 如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。[部署 Office 方案](../vsto/deploying-an-office-solution.md) 類別的其餘部分則定義於您不應修改的隱藏程式碼檔中。  
  
-   [部署 Office 方案](../vsto/deploying-an-office-solution.md) 和  事件處理常式。 當 Excel 載入和卸載 VSTO 增益集時，會呼叫這些事件處理常式。 請使用這些事件處理常式，在 VSTO 增益集載入時將它初始化，以及在增益集卸載時清除它所用的資源。 如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
#### 將一行文字加入儲存的活頁簿  
  
1.  在 ThisAddIn 程式碼檔中，將下列程式碼加入 [部署 Office 方案](../vsto/deploying-an-office-solution.md) 類別。 新的程式碼會定義 [部署 Office 方案](../vsto/deploying-an-office-solution.md) 事件的事件處理常式，該事件是在儲存活頁簿時所引發的。  
  
     當使用者儲存活頁簿時，事件處理常式會將新文字加入現用工作表開頭。  
  
     [!code-csharp[Trin_ExcelAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  如果使用的是 C\#，請將下列必要的程式碼加入 [部署 Office 方案](../vsto/deploying-an-office-solution.md) 事件處理常式中。 這段程式碼是用來連接 [部署 Office 方案](../vsto/deploying-an-office-solution.md) 事件處理常式和  事件。  
  
     [!code-csharp[Trin_ExcelAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ExcelAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 若要在儲存活頁簿時修改活頁簿，前面的程式碼範例可以使用下列物件：  
  
-   類別的 [部署 Office 方案](../vsto/deploying-an-office-solution.md) 欄位。[部署 Office 方案](../vsto/deploying-an-office-solution.md) 欄位會傳回  物件，此物件代表 Excel 目前的執行個體。  
  
-   事件的事件處理常式的 [部署 Office 方案](../vsto/deploying-an-office-solution.md) 參數。[部署 Office 方案](../vsto/deploying-an-office-solution.md) 參數是  物件，此物件代表儲存的活頁簿。 如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
## 測試專案  
  
#### 測試專案  
  
1.  按 F5[部署 Office 方案](../vsto/deploying-an-office-solution.md) 建置及執行專案。  
  
     當您建置專案時，程式碼會編譯到包含在專案建置輸出資料夾中的組件。 Visual Studio 也會建立一組登錄項目，以便 Excel 探索和載入 VSTO 增益集，而且會設定開發電腦中的安全性設定，讓 VSTO 增益集可以執行。 如需詳細資訊，請參閱[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
2.  在 Excel 中儲存活頁簿。  
  
3.  請確認已將下列文字加入活頁簿。  
  
     **This text was added by using code.**  
  
4.  關閉 Excel。  
  
## 清除 Project  
 當您完成專案開發時，請從開發電腦移除 VSTO 增益集組件、登錄項目和安全性設定。 否則，每次在開發電腦上開啟 Excel 時，VSTO 增益集將會繼續執行。  
  
#### 清除開發電腦上已完成的專案  
  
1.  在 Visual Studio 中，按一下 \[建置\][部署 Office 方案](../vsto/deploying-an-office-solution.md) 功能表上的 \[清除方案\]。  
  
## 後續步驟  
 現在您已經建立 Excel 的基本 VSTO 增益集，可以從下列主題進一步了解如何開發 VSTO 增益集：  
  
-   您可以透過 VSTO 增益集執行的一般程式設計工作：[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
-   Excel VSTO 增益集特有的程式設計工作：[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
-   使用 Excel 的物件模型：[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
-   自訂 Excel 的使用者介面 \(UI\)，例如，將自訂索引標籤加入功能區，或建立您專屬的自訂工作窗格：[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
-   建置及偵錯 Excel VSTO 增益集：[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
-   部署 Excel VSTO 增益集：[部署 Office 方案](../vsto/deploying-an-office-solution.md)。  
  
## 請參閱  
 [Office 方案開發概觀 &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Excel 方案](../vsto/excel-solutions.md)   
 [VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)   
 [Excel 物件模型概觀](../vsto/excel-object-model-overview.md)   
 [Office UI 自訂](../vsto/office-ui-customization.md)   
 [建置 Office 方案](../vsto/building-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [Office 專案範本概觀](../vsto/office-project-templates-overview.md)  
  
  