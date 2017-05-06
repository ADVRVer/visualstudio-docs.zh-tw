---
title: "Excel 物件模型概觀"
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
  - "Excel 物件模型"
  - "物件模型 [Visual Studio 中的 Office 程式開發], Excel"
  - "物件模型 [Visual Studio 中的 Office 程式開發], Office"
  - "物件 [Visual Studio 中的 Office 程式開發], Office 物件模型"
  - "Office 物件模型"
  - "Range 物件"
  - "Workbook 類別"
  - "Worksheet 物件"
ms.assetid: e4b2e46b-ea6c-4a88-a416-a7d4f495fc33
caps.latest.revision: 66
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 65
---
# Excel 物件模型概觀
  若要開發使用 Microsoft Office Excel 的方案，您可以與 Excel 物件模型提供的物件進行互動。  本主題將介紹最重要的物件：  
  
-   <xref:Microsoft.Office.Interop.Excel.Application>  
  
-   <xref:Microsoft.Office.Interop.Excel.Workbook>  
  
-   <xref:Microsoft.Office.Interop.Excel.Worksheet>  
  
-   <xref:Microsoft.Office.Interop.Excel.Range>  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 這個物件模型密切遵循其使用者介面。  <xref:Microsoft.Office.Interop.Excel.Application> 物件代表整個應用程式，而每個 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件都包含 `Worksheet` 物件的集合。  其中，代表儲存格的主要抽象物件是 <xref:Microsoft.Office.Interop.Excel.Range> 物件，它可以讓您使用個別儲存格或儲存格群組。  
  
 除了 Excel 物件模型之外，Visual Studio 中的 Office 專案還提供*「主項目」*\(Host Item\) 和*「主控制項」*\(Host Control\)，以擴充 Excel 物件模型中的部分物件。  主項目和主控制項的行為與它們所擴充的 Excel 物件相同，但還具有其他功能 \(例如資料繫結功能和額外事件\)。  如需詳細資訊，請參閱[使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md) 和[主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)。  
  
 本主題提供 Excel 物件模型的簡短概觀。  如需可以了解整個 Excel 物件模型的資源，請參閱[使用 Excel 物件模型文件](#ExcelOMDocumentation)。  
  
 ![視訊的連結](../vsto/media/playvideo.png "視訊的連結") 如需相關示範影片，請參閱[如何：在 Excel 2007 增益集中使用事件處理常式](http://go.microsoft.com/fwlink/?LinkID=130291)和[如何：使用圖案在 Excel 中建立泡泡圖](http://go.microsoft.com/fwlink/?LinkID=130313)。  
  
## 存取 Excel 專案中的物件  
 當您建立 Excel 的新 VSTO 增益集專案時，Visual Studio 會自動建立 ThisAddIn.vb 或 ThisAddIn.cs 程式碼檔。  您可以使用 `Me.Application` 或 `this.Application`，來存取 Application 物件。  
  
 當您建立 Excel 的新文件層級專案時，可以選擇建立新的 Excel 活頁簿或 Excel 範本專案。  Visual Studio 會在新的 Excel 專案中，自動為活頁簿和範本專案建立下列程式碼檔。  
  
|Visual Basic|C\#|  
|------------------|---------|  
|ThisWorkbook.vb|ThisWorkbook.cs|  
|Sheet1.vb|Sheet1.cs|  
|Sheet2.vb|Sheet2.cs|  
|Sheet3.vb|Sheet3.cs|  
  
 您可以在專案中使用 `Globals` 類別，從個別的類別之外存取 `ThisWorkbook`、`Sheet1`、`Sheet2` 或 `Sheet3`。  如需詳細資訊，請參閱[全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)。  不論程式碼是放在其中一個 `Sheet`*n* 類別或 `ThisWorkbook` 類別中，下列範例都會呼叫 `Sheet1` 的 <xref:Microsoft.Office.Interop.Excel._Worksheet.PrintPreview%2A> 方法。  
  
 [!code-csharp[Trin_VstcoreExcelAutomation#82](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#82)]
 [!code-vb[Trin_VstcoreExcelAutomation#82](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#82)]  
  
 由於 Excel 文件包含高度結構化的資料，因此物件模型不僅層級分明，而且非常明確。  Excel 提供了數百個可以與您互動的物件，不過您不妨先從一個非常小的可用物件子集開始，逐步學習這個物件模型。  這些物件包含下列四個項目：  
  
-   應用程式  
  
-   活頁簿  
  
-   工作表  
  
-   範圍  
  
 使用 Excel 執行的大部分工作都是以這四個物件及其成員為中心。  
  
### Application 物件  
 Excel <xref:Microsoft.Office.Interop.Excel.Application> 物件代表 Excel 應用程式本身。  <xref:Microsoft.Office.Interop.Excel.Application> 物件會公開有關執行中應用程式、套用至該執行個體的選項，以及目前在執行個體中開啟之使用者物件的大量資訊。  
  
> [!NOTE]  
>  請勿在 Excel 中，將 <xref:Microsoft.Office.Interop.Excel.Application> 物件的 <xref:Microsoft.Office.Interop.Excel.ApplicationClass.EnableEvents%2A> 屬性設定為 **false**。  將這個屬性設定為 false，會導致 Excel 無法引發任何事件，包括主控制項的事件在內。  
  
### Workbook 物件  
 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件代表 Excel 應用程式中的單一活頁簿。  
  
 Visual Studio 中的 Office 程式開發工具會藉由提供 <xref:Microsoft.Office.Tools.Excel.Workbook> 類型，來擴充 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件。  這個類型可讓您存取 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件的所有功能。  如需詳細資訊，請參閱[Workbook 主項目](../vsto/workbook-host-item.md)。  
  
### 工作表物件  
 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件是 <xref:Microsoft.Office.Interop.Excel.Worksheets> 集合的成員。  <xref:Microsoft.Office.Interop.Excel.Worksheet> 的許多屬性、方法和事件都與 <xref:Microsoft.Office.Interop.Excel.Application> 或 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件所提供的成員完全相同或類似。  
  
 Excel 提供 <xref:Microsoft.Office.Interop.Excel.Sheets> 集合，做為 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件的屬性。  <xref:Microsoft.Office.Interop.Excel.Sheets> 集合的每個成員都是 <xref:Microsoft.Office.Interop.Excel.Worksheet> 或 <xref:Microsoft.Office.Interop.Excel.Chart> 物件。  
  
 Visual Studio 中的 Office 程式開發工具會藉由提供 <xref:Microsoft.Office.Tools.Excel.Worksheet> 類型，來擴充 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件。  這個類型可讓您存取 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件的所有功能，以及新功能 \(例如可以裝載 Managed 控制項和處理新事件\)。  如需詳細資訊，請參閱[Worksheet 主項目](../vsto/worksheet-host-item.md)。  
  
### 範圍物件  
 <xref:Microsoft.Office.Interop.Excel.Range> 物件是您在 Excel 應用程式中最常使用的物件。  若要操作 Excel 中的任何區域，您必須先將其表示為 <xref:Microsoft.Office.Interop.Excel.Range> 物件，然後再搭配該範圍的方法和屬性使用。  <xref:Microsoft.Office.Interop.Excel.Range> 物件代表一個儲存格、一個資料列、一個資料行、含有一或多個不一定連續之儲存格區塊的儲存格選取範圍，或甚至是多個工作表上的儲存格群組。  
  
 Visual Studio 會藉由提供 <xref:Microsoft.Office.Tools.Excel.NamedRange> 和 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 類型，來擴充 <xref:Microsoft.Office.Interop.Excel.Range> 物件。  這些類型具有與 <xref:Microsoft.Office.Interop.Excel.Range> 物件相同的大部分功能，以及新功能 \(例如資料繫結功能和新事件\)。  如需詳細資訊，請參閱 [NamedRange 控制項](../vsto/namedrange-control.md) 和 [XmlMappedRange 控制項](../vsto/xmlmappedrange-control.md)。  
  
##  <a name="ExcelOMDocumentation"></a> 使用 Excel 物件模型文件  
 如需 Excel 物件模型的完整資訊，您可以參閱 Excel 主要 Interop 組件 \(PIA\) 參考和 VBA 物件模型參考。  
  
### 主要 Interop 組件參考  
 Excel PIA 參考文件說明 Excel 主要 Interop 組件中的類型。  您可以從下列位置取得這份文件：[Excel 2010 主要 Interop 組件參考](http://go.microsoft.com/fwlink/?LinkId=189585)。  
  
 如需 Excel PIA 設計的詳細資訊，例如 PIA 中類別和介面的差異以及 PIA 中實作事件的方式，請參閱 [Office 主要 Interop 組件中的類別和介面概觀](http://go.microsoft.com/fwlink/?LinkId=189592)。  
  
### VBA 物件模型參考  
 VBA 物件模型參考記載公開給 Visual Basic for Applications \(VBA\) 程式碼時的 Excel 物件模型。  如需詳細資訊，請參閱 [Excel 2010 物件模型參考](http://go.microsoft.com/fwlink/?LinkId=199768)。  
  
 VBA 物件模型參考中的所有物件和成員都會對應至 Excel PIA 中的類型和成員。  例如，VBA 物件模型參考中的 Worksheet 物件會對應至 Excel PIA 中的 <xref:Microsoft.Office.Interop.Excel.Worksheet> 物件。  雖然 VBA 物件模型參考提供大部分屬性、方法和事件的程式碼範例，但如果您想要在以 Visual Studio 建立的 Excel 專案中使用這些程式碼範例，則必須將這個參考中的 VBA 程式碼轉譯為 Visual Basic 或 Visual C\#。  
  
### 相關主題  
  
|標題|描述|  
|--------|--------|  
|[Excel 方案](../vsto/excel-solutions.md)|說明如何建立 Microsoft Office Excel 的文件層級自訂和 VSTO 增益集。|  
|[使用範圍](../vsto/working-with-ranges.md)|提供示範如何使用範圍執行常見工作的範例。|  
|[使用工作表](../vsto/working-with-worksheets.md)|提供示範如何使用工作表執行常見工作的範例。|  
|[使用活頁簿](../vsto/working-with-workbooks.md)|提供示範如何使用活頁簿執行常見工作的範例。|  
  
  