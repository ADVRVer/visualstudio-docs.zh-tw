---
title: "如何： 以程式設計方式移動工作表在活頁簿內 |Microsoft 文件"
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
- worksheets, moving
- workbooks, moving worksheets in
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 5f0869ad6a63e4a499d9fdca2cbaa538d11eef0d
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>如何：以程式設計方式在活頁簿內移動工作表
  您可以透過程式設計方式變更工作表在活頁簿中相對於其他工作表的位置。 如果您不指定移動工作表的位置，Excel 會建立新的活頁簿來包含它。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-move-a-worksheet-in-a-document-level-customization"></a>在文件層級自訂中移動工作表  
  
1.  將活頁簿中的工作表總數指派給變數之後，再移動第一個工作表使它成為最後一個。  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]  
  
### <a name="to-move-a-worksheet-in-an-vsto-add-in"></a>在 VSTO 增益集中移動工作表  
  
1.  將活頁簿中的工作表總數指派給變數之後，再移動第一個工作表使它成為最後一個。  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]  
  
## <a name="see-also"></a>請參閱  
 [使用工作表](../vsto/working-with-worksheets.md)   
 [如何： 以程式設計方式隱藏工作表](../vsto/how-to-programmatically-hide-worksheets.md)   
 [如何： 以程式設計方式從活頁簿刪除工作表](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)   
 [如何： 以程式設計方式保護工作表](../vsto/how-to-programmatically-protect-worksheets.md)   
 [全域存取 Office 專案中的物件](../vsto/global-access-to-objects-in-office-projects.md)  
  
  