---
title: "逐步解說：在執行階段於 VSTO 增益集中，將控制項加入文件 | Microsoft Docs"
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
  - "增益集 [Visual Studio 中的 Office 程式開發]，加入控制項"
  - "應用程式層級增益集 [Visual Studio 中的 Office 程式開發]，加入控制項"
  - "控制項 [Visual Studio 中的 Office 程式開發]，在執行階段加入文件"
  - "文件 [Visual Studio 中的 Office 程式開發]，在執行階段加入控制項"
ms.assetid: ab6dff40-9964-468a-938c-a71a3ac23718
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# 逐步解說：在執行階段於 VSTO 增益集中，將控制項加入文件
  您可以使用 VSTO 增益集，將控制項加入任何開啟的 Microsoft Office Word 文件。 本逐步解說將示範如何使用功能區，讓使用者將 <xref:Microsoft.Office.Tools.Word.Controls.Button> 或 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 加入文件。  
  
 **適用對象：**本主題資訊適用於 Word 2010 的 VSTO 增益集專案。 如需詳細資訊，請參閱[依 Office 應用程式和專案類型提供的功能](../vsto/features-available-by-office-application-and-project-type.md)。  
  
 這個逐步解說將說明下列工作：  
  
-   建立新的 Word VSTO 增益集專案。  
  
-   提供可將控制項加入文件的使用者介面 \(UI\)。  
  
-   在執行階段將控制項加入文件。  
  
-   移除文件的控制項。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## 必要條件  
 您需要下列元件才能完成此逐步解說：  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 或 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]。  
  
## 建立新的 Word 增益集專案  
 請從建立 Word VSTO 增益集專案開始。  
  
#### 建立新的 Word VSTO 增益集專案  
  
1.  建立名為 **WordDynamicControls** 的 Word VSTO 增益集專案。 如需詳細資訊，請參閱[如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  加入 **Microsoft.Office.Tools.Word.v4.0.Utilities.dll** 組件的參考。 本逐步解說稍後會需要用到此參考，以透過程式設計的方式將 Windows Forms 控制項加入文件。  
  
## 提供可將控制項加入文件的 UI  
 將自訂索引標籤加入 Word 功能區。 使用者可以選取索引標籤上的核取方塊，將控制項加入文件。  
  
#### 提供可將控制項加入文件的 UI  
  
1.  在 \[專案\] 功能表中，按一下 \[加入新項目\]。  
  
2.  選取 \[**加入新項目**\] 對話方塊中的 \[**功能區 \(視覺化設計工具\)**\]。  
  
3.  將新功能區的名稱變更為 **MyRibbon**，然後按一下 \[加入\]。  
  
     **MyRibbon.cs** 或 **MyRibbon.vb** 檔案會在功能區設計工具中開啟，並顯示預設索引標籤和群組。  
  
4.  在功能區設計工具中，按一下 \[group1\] 群組。  
  
5.  在 \[屬性\] 視窗中，將 \[group1\] 的 \[Label\] 屬性變更為 \[加入控制項\]。  
  
6.  從 \[工具箱\] 的 \[Office 功能區控制項\] 索引標籤，將 **CheckBox** 控制項拖曳至 \[group1\]。  
  
7.  按一下 \[CheckBox1\] 予以選取。  
  
8.  在 \[屬性\] 視窗中變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**addButtonCheckBox**|  
    |**標籤**|**加入按鈕**|  
  
9. 將第二個核取方塊加入 \[group1\]，然後變更下列屬性。  
  
    |屬性|值|  
    |--------|-------|  
    |**名稱**|**addRichTextCheckBox**|  
    |**標籤**|**加入 RTF 控制項**|  
  
10. 在功能區設計工具中，按兩下 \[加入按鈕\]。  
  
     在程式碼編輯器中，隨即開啟 \[加入按鈕\] 核取方塊的 <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 事件處理常式。  
  
11. 返回功能區設計工具並按兩下 \[加入 RTF 控制項\]。  
  
     在程式碼編輯器中，隨即開啟 \[加入 RTF 控制項\] 核取方塊的 <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 事件處理常式。  
  
 稍後在本逐步解說中，您將會把這些程式碼加入這些事件處理常式，以加入和移除使用中文件的控制項。  
  
## 加入和移除使用中文件的控制項  
 在 VSTO 增益集程式碼中，您必須將使用中文件轉換成<xref:Microsoft.Office.Tools.Word.Document>*主項目*，才能加入控制項。 在 Office 方案中，Managed 控制項只能加入主項目，主項目是做為控制項的容器。 在 VSTO 增益集專案中，主項目可以在執行階段使用 GetVstoObject方法建立。  
  
 將方法加入`ThisAddIn`類別，可以呼叫該類別來加入或移除使用中文件的 <xref:Microsoft.Office.Tools.Word.Controls.Button> 或 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 。 稍後在本逐步解說，您將從功能區上之核取方塊的 <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 事件處理常式呼叫這些方法。  
  
#### 加入和移除使用中文件的控制項  
  
1.  在**方案總管**中，按兩下 ThisAddIn.cs 或 ThisAddIn.vb，在程式碼編輯器中開啟該檔案。  
  
2.  將下列程式碼加入 `ThisAddIn` 類別。 此程式碼會宣告 <xref:Microsoft.Office.Tools.Word.Controls.Button> 和 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 物件，它們代表將會加入文件的控制項。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#1)]  
  
3.  將下列方法加入 `ThisAddIn` 類別中。 當使用者按一下功能區上的 \[加入按鈕\] 核取方塊時，如果已選取核取方塊，則此方法會將 <xref:Microsoft.Office.Tools.Word.Controls.Button> 加入文件目前的選取範圍，如果已清除核取方塊則會移除 <xref:Microsoft.Office.Tools.Word.Controls.Button>。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#2)]  
  
4.  將下列方法加入 `ThisAddIn` 類別中。 當使用者按一下功能區上的 \[加入 RTF 控制項\] 核取方塊時，如果已選取核取方塊，則此方法會將 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> 加入文件目前的選取範圍，如果已清除核取方塊則會移除 <xref:Microsoft.Office.Tools.Word.RichTextContentControl>。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#3)]  
  
## 儲存文件時移除按鈕控制項  
 在儲存文件然後關閉時，不會保存 Windows Forms 控制項。 不過，每個控制項的 ActiveX 包裝函式會保留在文件中，而當使用者重新開啟文件時，會看到這個包裝函式的框線。 有幾種方式可以在 VSTO 增益集中清除動態建立的 Windows Forms 控制項。 在本逐步解說中，您會以程式設計方式，在儲存文件時移除 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控制項。  
  
#### 儲存文件時移除按鈕控制項  
  
1.  在 ThisAddIn.cs 或 ThisAddIn.vb 程式碼檔中，將下列方法加入 `ThisAddIn` 類別。 這個方法是 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件的事件處理常式。 如果已儲存的文件有與它相關的 <xref:Microsoft.Office.Tools.Word.Document> 主項目，事件處理常式會取得主項目並移除 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控制項 \(如果存在的話\)。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/ThisAddIn.vb#4)]  
  
2.  在 C\# 中，將下列程式碼加入 `ThisAddIn_Startup` 事件處理常式。 在 C\# 中連接 `Application_DocumentBeforeSave` 事件處理常式和 <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> 事件時需要此程式碼。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/ThisAddIn.cs#5)]  
  
## 當使用者按一下功能區上的核取方塊時，加入和移除控制項  
 最後，修改您加入功能區之核取方塊的 <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click> 事件處理常式，來加入或移除文件的控制項。  
  
#### 當使用者按一下功能區上的核取方塊時，加入和移除控制項  
  
1.  在 MyRibbon.cs 或 MyRibbon.vb 程式碼檔案中，將產生的 `addButtonCheckBox_Click` 和 `addRichTextCheckBox_Click` 事件處理常式取代為下列程式碼。 此程式碼會重新定義這些事件處理常式，呼叫您稍早在本逐步解說中加入 `ThisAddIn` 類別的 `ToggleButtonOnDocument` 和 `ToggleRichTextControlOnDocument` 方法。  
  
     [!code-csharp[Trin_WordAddInDynamicControlsWalkthrough#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/CS/MyRibbon.cs#6)]
     [!code-vb[Trin_WordAddInDynamicControlsWalkthrough#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControlsWalkthrough/VB/MyRibbon.vb#6)]  
  
## 測試方案  
 從功能區上的自訂索引標籤選取控制項，將此控制項加入文件。 當您儲存文件時，會移除 <xref:Microsoft.Office.Tools.Word.Controls.Button> 控制項。  
  
#### 若要測試方案  
  
1.  請按 F5 執行您的專案。  
  
2.  在使用中文件中，按數次 ENTER，在文件加入新的空白段落。  
  
3.  選取第一個段落。  
  
4.  按一下 \[增益集\] 索引標籤。  
  
5.  在 \[加入控制項\] 群組中，按一下 \[加入按鈕\]。  
  
     按鈕隨即出現在第一個段落中。  
  
6.  選取最後一個段落。  
  
7.  在 \[加入控制項\] 群組中，按一下 \[加入 RTF 控制項\]。  
  
     Rich text 格式內容控制項會加入最後一個段落。  
  
8.  儲存文件。  
  
     按鈕會從文件中移除。  
  
## 後續步驟  
 您可以從下列主題進一步了解 VSTO 增益集的控制項：  
  
-   如需示範如何在執行階段將許多其他類型的控制項加入文件，並在重新開啟文件時重新建立控制項的範例，請參閱 Word 增益集動態控制項範例：[Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)。  
  
-   如需示範如何使用 Excel VSTO 增益集，將控制項加入工作表的逐步解說，請參閱[逐步解說：在執行階段於 VSTO 增益集專案中，將控制項加入工作表中](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)。  
  
## 請參閱  
 [Word 方案](../vsto/word-solutions.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [在 Office 文件中保存動態控制項](../vsto/persisting-dynamic-controls-in-office-documents.md)   
 [如何：將 Windows Form 控制項加入至 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何：將內容控制項加入至 Word 文件](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)  
  
  