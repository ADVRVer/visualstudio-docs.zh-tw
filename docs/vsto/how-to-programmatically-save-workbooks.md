---
title: "如何： 以程式設計方式儲存活頁簿 |Microsoft 文件"
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
- workbooks, saving in XML format
- workbooks, saving
- workbooks, saving backup copies
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 4d184d7122459b85b3ad20fbf8338a53f28bd6c8
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-save-workbooks"></a>如何：以程式設計方式儲存活頁簿
  儲存活頁簿有好幾種方式。 您可以儲存活頁簿，而不變更路徑。 如果活頁簿先前沒有儲存過，則應該指定路徑來儲存活頁簿。 如果沒有明確指定路徑，Microsoft Office Excel 會將這個檔案以建立時指定的名稱儲存在目前的資料夾中。 您也可以儲存活頁簿的複本，而不修改記憶體中的已開啟活頁簿。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="saving-a-workbook-without-changing-the-path"></a>不變更路徑以儲存活頁簿  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>儲存與文件層級自訂相關聯的活頁簿  
  
1.  請呼叫 ThisWorkbook 類別的 <xref:Microsoft.Office.Tools.Excel.Workbook.Save%2A> 方法。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomation#4](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#4)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>透過 VSTO 增益集儲存現用活頁簿  
  
1.  請呼叫 <xref:Microsoft.Office.Interop.Excel._Workbook.Save%2A> 方法，即可儲存現用活頁簿。 若要使用下列程式碼範例，請在 Excel VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#3)]  
  
## <a name="saving-a-workbook-with-a-new-path"></a>使用新路徑儲存活頁簿  
 您可以將指定的活頁簿儲存至新位置或使用新名稱儲存，也可以選擇性地指定檔案格式、密碼、存取模式等項目。  
  
> [!NOTE]  
>  要設定<xref:Microsoft.Office.Interop.Excel._Application.DisplayAlerts%2A>屬性**False**之前使用新路徑儲存活頁簿，因為以某些格式儲存需要互動。 此屬性設定為**False**會讓 Excel 使用所有預設值。  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>儲存與文件層級自訂相關聯的活頁簿  
  
1.  請呼叫 `ThisWorkbook` 類別的 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A> 方法。 若要使用下列程式碼範例，請在 `ThisWorkbook` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#5)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>透過 VSTO 增益集儲存現用活頁簿  
  
1.  呼叫 <xref:Microsoft.Office.Interop.Excel._Workbook.SaveAs%2A> 方法，即可將現用活頁簿儲存至新路徑。 若要使用下列程式碼範例，請在 Excel VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#4)]  
  
## <a name="saving-a-copy-of-the-workbook"></a>儲存活頁簿的複本  
 您可以將活頁簿的複本儲存至檔案，而不修改記憶體中的已開啟活頁簿。 如果您要建立備份複本而不修改活頁簿的位置，這個方法就很有用。  
  
#### <a name="to-save-a-workbook-associated-with-a-document-level-customization"></a>儲存與文件層級自訂相關聯的活頁簿  
  
1.  請呼叫 `ThisWorkbook` 類別的 <xref:Microsoft.Office.Tools.Excel.Workbook.SaveCopyAs%2A> 方法。 若要使用下列程式碼範例，請在 `ThisWorkbook` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#6)]  
  
#### <a name="to-save-the-active-workbook-in-a-vsto-add-in"></a>透過 VSTO 增益集儲存現用活頁簿  
  
1.  請呼叫 <xref:Microsoft.Office.Interop.Excel._Workbook.SaveCopyAs%2A> 方法，即可儲存現用活頁簿的複本。 若要使用下列程式碼範例，請在 Excel VSTO 增益集專案的 `ThisAddIn` 類別中執行程式碼。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#5)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以互動方式取消任何儲存或複製活頁簿的方法，都會在程式碼中引發執行階段錯誤。 例如，如果您的程序呼叫<xref:Microsoft.Office.Tools.Excel.Workbook.SaveAs%2A>方法，但不停用的提示，Excel，而且使用者按一下**取消**出現提示時，Excel 就會引發執行階段錯誤。  
  
## <a name="see-also"></a>請參閱  
 [使用活頁簿](../vsto/working-with-workbooks.md)   
 [Workbook 主項目](../vsto/workbook-host-item.md)   
 [如何： 以程式設計方式關閉活頁簿](../vsto/how-to-programmatically-close-workbooks.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Office 方案中的選擇性參數](../vsto/optional-parameters-in-office-solutions.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)  
  
  